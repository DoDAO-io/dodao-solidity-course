## Header
This is the course header. This will be added on top of every page. Do to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Units and variables
 
 **Units**        
### Ether Units
  While using Ethereum, we may encounter different units, such as Wei and Gwei. In Solidity, we can use wei, gwei or ether to specify a subdenomination of Ether. 
  Wei is the smallest unit of measurement. One Wei is worth 0.000000000000000001 Ether (or 10-18). Because it cannot deal with decimal numbers, the EVM (Ethereum Virtual Machine) employs Wei as its base unit. Gwei, another common unit, is 1000000000 Wei, or 0.000000001 (or 10-9) Ether. 
  
  Following are unit conversions on basis of 1 Wei
  - `1 Wei = 1;`
  - `1 Kwei = 1e3;`
  - `1 Mwei = 1e6;`
  - `1 Gwei = 1e9;`
  - `1 Szabo = 1e12;`
  - `1 Finney = 1e15;`
  - `1 Ether = 1e18;`
  - `1 Kether = 1e21;`
  - `1 Mether = 1e24;`
  - `1 Gether = 1e27;`
  - `1 Tether = 1e30;`
    
  The following code snippet demonstrates a simple function to convert the total `wei` and `gwei` (default unit in Solidity) to Ether.
    
  ```solidity
    contract ConvertUnits {
      function etherToGWei(uint value_ether) public pure returns (uint){
        return value_ether*(10**9);
      }
      function gweiToEther(uint gwei) public pure returns (uint){
        return gwei/(10**9);
      }
      function etherToWei(uint value_ether) public pure returns (uint){
        return value_ether*(10**18);
      }
      function weiToEther(uint value_wei) public pure returns (uint){
        return value_wei/(10**18);
      }
    }
  ```
### Time Units
  After literal numbers, units of time can be specified by adding suffixes like seconds, minutes, hours, days, and weeks where seconds are the base unit. We can use seconds, minutes, hours, days and weeks as suffix to denote time. Lowest unit of time is `seconds`.  
  
  Below are some time unit examples from solidity. 
  - `1 seconds = 1;`
  - `1 minutes = 60 seconds;`
  - `1 hours = 60 minutes;`
  - `1 day = 24 hours;`
  - `1 week = 7 days;`  

  On calling function `func` below, the value of `block.timestamp` returns 1661554329 seconds however the returned value will be 143558295494400 seconds because `block.timestamp` gets multiplied with 24*60*60 due to the `days` time denomination.

  ```
    contract C
    {
      function func() public view returns(uint){
          return block.timestamp * 1 days;
      }
    }
  ```
  After version 0.5.0, solidity no longer uses the suffix "years" for the reasons of leap units(i.e. leap year).
 
 **Globally available Variables**        
A Variable is basically a placeholder for the data which can be manipulated at runtime. Variables allow users to retrieve and change the stored information. There are special variables and functions which always exist in the global namespace and are mainly used to provide information about the blockchain or are general-use utility functions.

These are of various types having specific properties.
  - Block and Transaction properties.
  - ABI Encoding and Decoding functions.
  - Members of bytes and string.
  - Error handling methods.
  - Mathematical and Cryptographic functions.
  - Members of address type.
  - Contract related.
  - Type Information.
 
 **Block and Transaction properties**        
A key idea in Ethereum is the concept of blocks. Blocks serve as transactional containers. Multiple transactions are contained in a block. The number of transactions in each block varies depending on the gas limit and block size. A blockchain is created by chaining the blocks together. Each block has a parent block, and the header of each block contains the parent block's hash. Only the first block, also referred to as the genesis block, lacks a parent.

Below are block and transaction properties with their functionalities 
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

The code snippet below demonstrates the use of some of the Block and transaction properties.
  ```
    pragma solidity ^0.8.0;

    contract Block{
        ///////// block functions //////////////

        function basefee()public view returns(uint){
            return block.basefee;
        }//output: "0": "uint256: 1"

        function chainid()public view returns(uint){
            return block.chainid;
        }//output: "0": "uint256: 1"

        function coinbase()public view returns(address payable){
            return block.coinbase;
        }//output: "0": "address: 0x8945A..."

        // try this with pragma solidity ^0.6.0;
        // function gaselimit()public view returns(uint){
        //     return block.gaselimit;
        // }//output: "0": "uint256: 1"

        function number()public view returns(uint){
            return block.number;
        }//output: "0": "uint256: 2"

        function blockhash_()public view returns(bytes32){
            return blockhash(number());
        }//output: "0": "bytes32: 0x0000000000000000000000000000000000000000000000000000000000000000"

        function timestamp()public view returns(uint){
            return block.timestamp;
        }//output: "0": "uint256: 1667312686"

        function gasleft_()public view returns(uint256){
            return gasleft();
        }//output: "0": "uint256: 2978818"

        /////////// msg functions //////////////

        function data()public pure returns(bytes calldata){
            return msg.data;
        }//output: "0": "bytes: 0x73d4a13a"

        function sender()public view returns(address){
            return msg.sender;
        }//output: "0": "address: 0x5B38Da6a701c568545dCfcB03FcB875f56beddC4"

        function sig()public pure returns(bytes4){
            return msg.sig;
        }//output: "0": "bytes4: 0x00a7029b"

        function value()internal view returns(uint){
            return msg.value;
        }//output: "0": "uint256: 2978818"

        ////////// tx functions ////////////

        function gasprice()public view returns(uint){
            return tx.gasprice;
        }//output: "0": "uint256: 1"

        function origin()public view returns(address){
            return tx.origin;
        }//output: "0": "address: 0x5B38Da6a701c568545dCfcB03FcB875f56beddC4"

    }

  ```
The values of all members of msg can change for every external function call. In solidity `block.timestamp` and `blockhash` are sources of randomness are not secure. Timestamp and the blockhash can be influenced by the miners.
 
 **ABI Encoding and Decoding functions.**        
In the context of computer science, an ABI (Application Binary Interface) is an interface between two programme modules, most commonly between operating systems and user programmes. ABI, like API, defines the methods and structures used to interact with the binary contract at a lower level. The ABI instructs the function caller to encode the necessary information, such as function signatures and variable declarations, in a format that the EVM can understand in order to call that function in bytecode; this is known as ABI encoding.

To send data to the contract, we need to send it in a way that the contract can read it. That is, they need to be encoded. Solidity has  global variable i.e, abi that has an encode and decode method, so we can use it to encode the parameters of any function. 

ABI encoding is mostly automated, handled by compilers such as REMIX or wallets that interact with the blockchain. JSON is used to represent contract ABI. There are specific instructions for encoding and decoding a contract ABI.

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
- `abi.encodeCall(function functionPointer, (...)) returns (bytes memory)`: ABI-encodes a call to functionPointer with the arguments found in the tuple. Performs a full type-check, ensuring the types match the function signature. Result `equals abi.encodeWithSelector(functionPointer.selector, (...))`abi.decode. `abi.encodeCall` not works with interfaces. 

```
  pragma solidity ^0.8.0;

  interface IERC20 {
      function transfer(address, uint) external;
  }

  contract ABI{
      function packedEncoding(string memory str)public pure returns(bytes memory){
          return abi.encodePacked(str);
      }
      // input: "string str": "dodao"
      // output: "0": "bytes: 0x646f64616f"

      function encodeWithSelector(bytes4 selector)public pure returns(bytes memory){
          return abi.encodeWithSelector(selector);
      }
      // input: "bytes4 selector": "0x00a7029b"
      // output: "0": "bytes: 0x00a7029b"

      function encodeWithSignature(string memory sign)public pure returns(bytes memory){
          return abi.encodeWithSignature(sign);
      }
      // input: "string sign": "dodao"
      // output: "0":bytes: 0x8b1babe1"

      function encodeCall(address to, uint amount) external pure returns (bytes memory) {
          // Typo and type errors will not compile
          return abi.encodeCall(IERC20.transfer, (to, amount));
      }
      // input: "address to": "0x9fA9594f233f14ac5B6Da660C3943b5925dB76bf", "uint256 amount": "10"
      // output: "0": "bytes: 0xa9059cbb0000000000000000000000009fa9594f233f14ac5b6da660c3943b5925db76bf000000000000000000000000000000000000000000000000000000000000000a"
  }

```
 
 **Mathematical and Cryptographic Functions**        
### Mathematical Functions

Solidity provide some inbuilt mahematical functions.

- `addmod(uint x, uint y, uint k) returns (uint)`
  This functions will compute the expression `(x + y) % k`. The addition is performed with arbitrary precision and does not wrap around at $2^{256}$.
  
  The code snippet below shows the use of the addmod functions.
    ```
    contract C {
      function foo() public pure returns(uint){
          return addmod(1,4,3);
      }
    }
    ``` 
  The function `foo` will return the modulous of `(1 + 4)` with 3 which is 2.

- `mulmod(uint x, uint y, uint k) returns (uint)`
  This function will compute the expression `(x * y) % k`. The multiplication is performed with arbitrary precision and does not wrap around at $2^{256}$.
  
  The code snippet below shows the use of the mulmod functions.
    ```
    contract C {
      function bar() public pure returns(uint){
          return mulmod(5,7,3);
      }
    }
    ```
    The function `bar` will return the modulous of `(5 * 7)` with 3 which is 2.

### Cryptographic Functions

- `keccak256(bytes memory) returns (bytes32)`
  keccak256 function will compute and return the Keccak-256 hash of the input. Keccak-256 is part of Solidity (SHA-3 Family). It computes the hash of an input to a fixed-length output, yielding a singular 32-byte hash from any number of inputs. It ca be used to create a deterministic, one-of-a-kind ID from a set of data
  
  This cryptographic hash function can only be used in one direction and cannot be reversed. It create cryptographic signature with a small size (by signing the hash instead of a larger input)

- `sha256(bytes memory) returns (bytes32)`
  This function will compute and return the SHA-256 hash of the input. It is weaker than Keccak-256.

  ```
    pragma solidity ^0.5.12;

    contract Hash
    {
      // Function to generate the hash value
      function keccak256Hashing(string memory str)public pure returns (uint){
        return uint(keccak256(abi.encodePacked(str)));
      }
        //input: "string str": "dodao"
        //output: "0": "uint256: 62920377089785550187964950488199234079585613826859085810147954743834678498217"
        
        function sha256Hashing(bytes memory str)public pure returns(bytes32){
            return sha256(str);
        }
        //input: "bytes str": "0x00a7029b"
        //output: "0": "bytes32: 0xdc7c72d57fc518d68eb821c27ca812a3b41a0a38ac1c0a38c5a1fca8259d67ac"
    }
  ```
 
 **Members of bytes and string**        
### Strings

  Strings are a reference type of data type in Solidity that stores the location of the data rather than directly storing the data into the variable. They are dynamic arrays that can hold a variety of characters such as numbers, special characters, spaces, and alphabets. Strings in Solidity use UTF-8 encoding to store data. Both Double quote(" ") and Single quote(' ') can be used to represent strings in solidity, just like JavaScript.
  
  - `string.concat(...) returns (string memory)`: Concatenates variable number of string arguments to one string array.

### Bytes
  Bytes are 8-bit signed integers. Everything in memory is stored in bits that have binary values of 0 and 1. Solidity also includes a byte data type for storing data in binary format. In most programming languages, bytes are represented by a single data type. However, Solidity supports multiple byte types. It provides data types ranging from bytes1 to bytes32 inclusive, to represent different byte lengths as needed. Fixed sized byte arrays are value types that implement these.

  - `bytes.concat(...) returns (bytes memory)`: 
    Concatenates variable number of bytes and bytes1, …, bytes32 arguments to one byte array.

  The Contract C below demonstrates the use of `bytes.concat` and `string.concat` to concatenate two strings a and b.
  ```
  contract C
  {
    function testStringConcat(string memory a,string memory b) public pure returns (string memory) {
          return string.concat(a , b);
      }

      function testByteConcat(string memory a,string memory b) public pure returns (string memory){
          return string(bytes.concat(bytes(a), " ", bytes(b)));
      } 
  }
  ```
 
 **Error Handling Functions**        
Solidity has a plethora of error-handling functions. Errors can occur during compile or runtime. Solidity is compiled to byte code, and a syntax error check occurs at compile time, whereas runtime errors are difficult to detect and occur primarily during contract execution. Out-of-gas error, data type overflow error, divide by zero error, array-out-of-index error, and so on are examples of runtime errors. Solidity had a single throw statement until version 4.10, so to handle errors, multiple if...else statements must be implemented for checking the values and throwing errors, which consumes more gas. After version 4.10, new error-handling constructs assert, require, and revert statements were added, and the throw function was made absolute.

Assert has the same syntax as the require statement. After evaluating the condition, it returns a boolean value. The programme will either continue to execute or throw an exception based on the return value. Instead of returning unused gas, the assert statement consumes the entire gas supply and then returns the state to its original state. Before the contract is executed, Assert is used to validate the current state and function conditions. Some cases with assert type exceptions
  - An assert is called with a condition that yields a false result.
  - A function's zero-initialized variable is called.
  - Converting a large or negative value to an enum.
  - A value is modulo or divided by zero.
  - Accessing an array with an index that is either too large or too small.

- `assert(bool condition)`: 
  Causes a Panic error and thus state change reversion if the condition is not met - to be used for internal errors.

The `require` statements declare the prerequisites for running the function, i.e. the constraints that must be met before executing the code. It takes a single argument and after evaluation returns a boolean value; it also has a custom string message option. If false, an exception is thrown and the execution is terminated. The unused gas is returned to the caller, and the state is reset to its original setting.

- `require(bool condition)`: 
  reverts if the condition is not met - to be used for errors in inputs or external components.

- `require(bool condition, string memory message)`: 
  reverts if the condition is not met - to be used for errors in inputs or external components. Also provides an error message.

Revert is comparable to the require statement. It does not evaluate any condition or rely on any state or statement. It's used to throw exceptions, show errors, and revert the function call. This statement includes a string message that describes the problem with the exception's information. A revert statement implies that an exception is thrown, the unused gas is returned, and the state is reset to its original state. Revert is used to handle the same types of exceptions that require does, but with slightly more complex logic.

- `revert()`: 
  abort execution and revert state changes.

- `revert(string memory reason)`: 
  abort execution and revert state changes, providing an explanatory string.

```
  pragma solidity ^0.6.0;

  contract ErrorHandling{
      // "require" 
      function Odd(uint n) public view returns(bool){
          require(n % 2 != 0);
          return true;
      }
      // input: 10
      // output: 
      //     call to ErrorHandling.Odd errored: VM error: revert.
      //     revert The transaction has been reverted to the initial state.

      // input: 9
      // output: "0": "bool: true"

      bool result;
      function assertCheck(uint n1, uint n2) public {
          uint sum = n1 + n2;
          assert(sum<=255);
          result = true;
          // return result;
          // if return result used the below error happens 
          //     TypeError: Different number of arguments in return statement than in returns declaration.
          //     return result;
          //     ^-----------^
      }

      function checkResultAfter_assertCheck(uint n1, uint n2)public returns(bool){
          assertCheck(n1,n2);
          return result;
      } 
      // input: 10, 20
      // output: "0": "bool: true"

      // input: 100, 200
      // output: "0": "bool: false"
      // transact to ErrorHandling.checkResultAfter_assertCheck errored: VM error: invalid opcode.
      // The execution might have thrown.

      function revertCheck(uint n1, uint n2) public view returns(string memory, uint){
          uint sum = n1 + n2;
          if(sum < 0 || sum > 255){
              revert(" Overflow Exist");
          }
          else{
              return ("No Overflow", sum);
          }   
      }
      // input: 100, 200
      // output: "error": "Failed to decode output: Error: overflow (fault=\"overflow\", operation=\"toNumber\", value=\"3963877391197344453575983046348115674221700746820753546331534351508065746944\", code=NUMERIC_FAULT, version=bignumber/5.5.0)"

      // input: 10, 20
      // output: "0": "string: No Overflow", "1": "uint256: 30"
  }
    
```
 
 