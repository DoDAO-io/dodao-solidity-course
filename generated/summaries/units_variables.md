## Header
This is the course header. This will be added on top of every page. Do to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Units and variables
 
 **Units**        
- Ether Units
  * In Solidity, we can use wei, gwei or ether to specify a subdenomination of Ether.
  * Lowest unit is wei and $1e12$ represents $1 * 10^{12}$.
  * `1 wei = 1;`
  * `1 gwei = 1e9;`
  * `1 ether = 1e18;`

- Time Units
  * We can use seconds, minutes, hours, days and weeks as suffix to denote time.
  * Lowest unit of time is `seconds`.
  * `1 seconds = 1;`
  * `1 minutes = 60 seconds;`
  * `1 hours = 60 minutes;`
  * `1 day = 24 hours;`
  * `1 week = 7 days;`  
 
 **Globally available Variables**        
- There are special variables and functions which always exist in the global namespace and are mainly used to provide 
  information about the blockchain or are general-use utility functions.
- These are of various types having specific properties.
  * Block and Transaction properties.
  * ABI Encoding and Decoding functions.
  * Members of bytes and string.
  * Error handling methods.
  * Mathematical and Cryptographic functions.
  * Members of address type.
  * Contract related.
  * Type Information.   

  Few of the important functions of each type will be discussed in the following sections.
 
 **Block and Transaction properties**        
- `blockhash(uint blockNumber) returns (bytes32)`: Gives hash of the given block and will only work for the 256 most recent block due to the reason of scalability.
- `block.basefee (uint)`: current blocks base fee.
- `block.chainid (uint)`: current chain id.
- `block.coinbase (address payable)`: current block miners address.
- `block.difficulty (uint)`: current block difficulty.
- `block.gaslimit (uint)`: current block gaslimit.
- `block.number (uint)`: current block number.
- `block.timestamp (uint)`: current block timestamp as seconds since unix epoch.
- `gasleft() returns (uint256)`: remaining gas.
- `msg.data (bytes calldata)`: complete calldata.
- `msg.sender (address)`: sender of the message (current call).
- `msg.sig (bytes4)`: first four bytes of the calldata (i.e. function identifier).
- `msg.value (uint)`: number of wei sent with the message.
- `tx.gasprice (uint)`: gas price of the transaction.
- `tx.origin (address)`: sender of the transaction (full call chain).
- The code snippet below demonstrates the use of some of the Block and transaction properties.
  ```
    contract C {
      function blockInfo() public view returns(uint,uint,bytes32,address){
          address sender=msg.sender;
          uint blockNum=block.number;
          uint blockTime=block.timestamp;
          bytes32 hash=blockhash(blockNum);
          return (blockNum,blockTime,hash,sender);
      }
    }
  ```
  The output of the function `blockInfo` is:-
  ```
    0:uint256: 27
    1:uint256: 1661098178
    2:bytes32: 0x0000000000000000000000000000000000000000000000000000000000000000
    3:address: 0x5B38Da6a701c568545dCfcB03FcB875f56beddC4
  ```
- The values of all members of msg can change for every external function call.
- `block.timestamp` and `blockhash` as a source of randomness are not secure. Timestamp and the blockhash can be influenced by the miners.
 
 **ABI Encoding and Decoding functions.**        
- To send data to the contract, we need to send it in a way that the contract can read it. That is, they need to be encoded.
- Solidity has a global variable called abi that has an encode and decode method, so we can use it to encode the parameters of any function.
- `abi.encode(...) returns (bytes memory)`: ABI-encodes the given arguments.
- `abi.decode(bytes memory encodedData, (...)) returns (...)`: ABI-decodes the given data, while the types are given in parentheses as second argument. 
  Example: `(uint a, uint[2] memory b, bytes memory c) = abi.decode(data, (uint, uint[2], bytes))`
- The example below demonstrates encoding and decoding.
  ```
  contract Encode {
    function encode(string memory _string1, uint _uint) public pure returns (bytes memory) {
            return (abi.encode(_string1, _uint));
        }
    function decode(bytes memory data) public pure returns (string memory _str1, uint _number) {
            (_str1, _number) = abi.decode(data, (string, uint));            
        }
    }
  ```
  On calling function `encode` with values (Hi , 5), returns bytes array 
  `0:bytes: 0x0000000000000000000000000000000000000000000000000000000000
  0000400000000000000000000000000000000000000000000000000000000000000005
  0000000000000000000000000000000000000000000000000000000000000003486920
  0000000000000000000000000000000000000000000000000000000000`  
  The encoded data can be decoded by calling function `decode` with the above bytes array.
  The returned values are 
  ```
    0:string: _str1 Hi
    1:uint256: _number 5
  ```
- `abi.encodePacked(...) returns (bytes memory)`: Performs packed encoding of the given arguments.
- `abi.encodeWithSelector(bytes4 selector, ...) returns (bytes memory)`: ABI-encodes the given arguments starting from the second and prepends the given four-byte selector.
- `abi.encodeWithSignature(string memory signature, ...) returns (bytes memory)`: Equivalent to `abi.encodeWithSelector(bytes4(keccak256(bytes(signature))), ...)`.
- `abi.encodeCall(function functionPointer, (...)) returns (bytes memory)`: ABI-encodes a call to functionPointer with the arguments found in the tuple. Performs a full type-check, ensuring the types match the function signature. Result `equals abi.encodeWithSelector(functionPointer.selector, (...))`abi.decode.
 
 **Mathematical and Cryptographic Functions**        
- `addmod(uint x, uint y, uint k) returns (uint)`
  - This functions will compute the expression `(x + y) % k`.
  - The code snippet below shows the use of the addmod functions.
    ```
    contract C {
      function foo() public pure returns(uint){
          return addmod(1,4,3);
      }
    }
    ``` 
    The function `foo` will return the modulous of `(1 + 4)` with 3 which is 2.
  - The addition is performed with arbitrary precision and does not wrap around at $2^{256}$.

- `mulmod(uint x, uint y, uint k) returns (uint)`
  - This function will compute the expression `(x * y) % k`.
  - - The code snippet below shows the use of the mulmod functions.
    ```
    contract C {
      function bar() public pure returns(uint){
          return mulmod(5,7,3);
      }
    }
    ```
    The function `bar` will return the modulous of `(5 * 7)` with 3 which is 2.
  - The multiplication is performed with arbitrary precision and does not wrap around at $2^{256}$.

- `keccak256(bytes memory) returns (bytes32)`
  - This function will compute and return the Keccak-256 hash of the input.

- `sha256(bytes memory) returns (bytes32)`
  - This function will compute and return the SHA-256 hash of the input.
 
 **Contract Related Functions**        
- `this`: `this` is the pointer to the current instance of the type derived from Address which is the current contract.
- `selfdestruct(address payable recipient)`: Destroy the current contract, sending its funds to the given Address and end execution.
 
 **Functions for Type Information**        
The expression type(X) can be used to retrieve information about the type X.
Currently, there is limited support for this feature (X can be either a contract or an integer type).
The following properties are available for a contract type C:
- `type(C).name`
  - The name of the contract.

- `type(C).creationCode`
  - Memory byte array that contains the creation bytecode of the contract.

- `type(C).runtimeCode`
  - Memory byte array that contains the runtime bytecode of the contract.

In addition to the properties above, the following properties are available for an interface type I: 

- `type(I).interfaceId`
  - A bytes4 value containing the EIP-165 interface identifier of the given interface I.

The following properties are available for an integer type T:

- `type(T).min`
  - The smallest value representable by type T.

- `type(T).max`
  - The largest value representable by type T.

- The following code demonstrates the use of type(T). The function `foo` will return -128 which is the minimum value of `int8` value type and 255 which is the maximum value of `uint8` value type.
  ```
  contract C {
    function foo() public pure returns(int,uint){
        return (type(int8).min,type(uint8).max);
    }
  }
  ```
 
 
