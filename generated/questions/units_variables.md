## Header
This is the course header. This will be added on top of every page. Do to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Units and variables
 
 
---

##### Which of the following is a valid subdemonination of Ether in the latest version of Solidity?  

- [x]  wei
- [x]  gwei
- [ ]  finney
- [ ]  szabo
  
Hint: noHint
         
Explanation: A literal number can take a suffix of `wei`, `gwei` or `ether` to specify a subdenomination of Ether. 
The denominations `finney` and `szabo` have been removed in version 0.7.0.


Sub Topics: units
 

---

##### Which of the following is not a valid unit of time ?  

- [ ]  `seconds`
- [ ]  `minutes`
- [ ]  `hours`
- [x]  `years`
  
Hint: noHint
         
Explanation: `seconds`, `minutes`, `hours`, `days` and `weeks` can be used to specify units of time.

Sub Topics: units
 

---

##### What is the value of 1 gwei?  

- [ ]  1 gwei = 1 ether
- [ ]  1 gwei = $10^9$ ether
- [x]  1 gwei = $10^9$ wei
- [ ]  1 gwei = $10^18$ wei
  
Hint: noHint
         
Explanation: - Lowest unit is wei and $1e12$ represents $1 * 10^{12}$.
  - `1 wei = 1;`
  - `1 gwei = 1e9;`
  - `1 ether = 1e18;`


Sub Topics: units
 

---

##### Which of the following properties is used to get information about the current block?  

- [ ]  `blockhash`
- [ ]  `basefee`
- [ ]  `gaslimit`
- [x]  All of these.
  
Hint: noHint
         
Explanation: `blockhash` gives the hash of the current block, `block.basefee` gives current blocks base fee and `block.gaslimit` gives the gaslimit of the current block.


Sub Topics: block-transaction
 

---

##### Which of the following is true regarding block and transaction properties?  

- [x]  block.timestamp` and `blockhash` as a source of randomness are not secure.
- [x]  The block hashes are not available for all blocks.
- [x]  Block difficulty represents the ease with which a block can be mined.
- [ ]  msg.value contains the amount of ether sent in the transaction.
  
Hint: noHint
         
Explanation: `block.timestamp` and `blockhash` as a source of randomness are not secure. Timestamp and the blockhash can be influenced by the miners.
The block hashes are not available for all blocks for scalability reasons. You can only access the hashes of the most recent 256 blocks.
`msg.value` contains the amount of wei (ether / 1e18) sent in the transaction.
The difficulty of a block is a measure of how difficult it is to mine a block.


Sub Topics: block-transaction
 

---

##### Which of the following options is correct regarding the code below?
```
    function randMod() public view returns(uint){
      return uint(keccak256(abi.encodePacked(block.timestamp))) % 2;
    }
```
  

- [x]  The function `randMod` will return a random integer in the range [0,1].
- [ ]  The function `randMod` will return a random integer in the range [0,2].
- [x]  `block.timestamp` should not be used to generate random numbers.
- [ ]  This function can be used to make a dApp where we generate an integer where a certain number is the winning number.
  
Hint: `block.timetamp` is current block timestamp as seconds which will change every second.
         
Explanation: block.timestamp returns current block timestamp as seconds which will change every second so it can be used as a source of randomness. 
Taking the Keccak-256 hash of the value will result in a byte32 type random value whose modulous with 2 will give either 0 or 1.
However it should not be used to make applications using randoms because the contract can be influenced by miners.
A miner running a node, can publish a transaction only to his own node and not share it. 
The functions `randMod` can be run until a function returns a winning value and then the miner can share the transaction.


Sub Topics: block-transaction
 

---

##### What is `msg` in Solidity?  

- [x]  The `msg` is a special global variable that contain properties which allow access to the blockchain.
- [x]  Values of all members of `msg` can change for every external function call.
- [ ]  Values of all members of `msg` cannot change for every external function call.
- [x]  The `msg.sender` special global variable is used to obtain the current users address.
  
Hint: noHint
         
Explanation: The `msg` global variables in particular are special global variables that contain properties which allow access to the blockchain. 
For instance, `msg.sender` is always the address where the current (external) function call came from.
he values of all members of msg, including msg.sender and msg.value can change for every external function call.


Sub Topics: block-transaction
 

---

##### What does `abi` stand for?  

- [x]  application binary interface
- [ ]  application binding interface
- [ ]  audio binary interface
- [ ]  application binding information
  
Hint: noHint
         
Explanation: ABI stands for application binary interface.

Sub Topics: encoding-decoding
 

---

##### WHat is the need for encoding/decoding in Solidity?  

- [ ]  There is no need.
- [x]  Data needs to be encoded in a machine readible format to communicate with a contract.
- [ ]  Encoding is necessary to make the data human readible.
- [ ]  ABI is exactly like API.
  
Hint: noHint
         
Explanation: In general, an ABI is the interface between two program modules, one of which is often at the level of machine code. 
The interface is the de facto method for encoding/decoding data into/out of the machine code.
It is very similar to API (Application Program Interface), a human-readable representation of a codes interface. 
ABI defines the methods and structures used to interact with the binary contract, just like API does but on a lower-level.


Sub Topics: encoding-decoding
 

---

##### A bytes array is given as followes which contains the abi encoding of an address and an int:
```
  0x0000000000000000000000005b38da6a701c568545dcfcb03fcb875f56beddc4  
  000000000000000000000000000000000000000000000000000000000000007f
```
Can you decode this string manually to retrieve the address and the int?
  

- [x]  (0x5B38Da6a701c568545dCfcB03FcB875f56beddC4,127)
- [ ]  (0x5B38Da6a701c568545dCfcB03FcB875f56beddC4,7)
- [ ]  (0x5B38Da6a701c568545dCfcB03FcB875f56beddC4,7f)
- [ ]  (0x0000000000000000000000005b38da6a701c568545dcfcb03fcb875f56beddc4,127)
  
Hint: Address holds a 20 byte value.
         
Explanation: A quick analysis of the result shows us that it has 64 bytes.
This is because the encoding occurs in multiples of 32 bytes.
The first 32 bytes contain the address (20 bytes) and the other 32 bytes contain the integer, 7f. 
Encoding is always in hexadecimal, and 7f in hex is 127.


Sub Topics: encoding-decoding
 

---

##### what is the difference between abi.encode and abi.encodePacked?  

- [ ]  They use different methods for encoding.
- [x]  Types encoded with encode get zero padded whearas with encodePacked they do not.
- [ ]  Types encoded with encodePacked get zero padded whearas with encode they do not.
- [ ]  There is no difference.
  
Hint: noHint
         
Explanation: Through abi.encodePacked(), Solidity supports a non-standard packed mode where:
- types shorter than 32 bytes are neither zero padded nor sign extended and
- dynamic types are encoded in-place and without the length.
- array elements are padded, but still encoded in-place.


Sub Topics: encoding-decoding
 

---

##### What does tx stand for?  

- [ ]  tax
- [x]  transaction
- [ ]  gas
- [ ]  None of these.
  
Hint: noHint
         
Explanation: tx stands for "transaction".

Sub Topics: block-transaction
 

---

##### Which of the following is not a member of global variable `tx`?  

- [ ]  gasprice
- [ ]  origin
- [x]  gaslimit
- [ ]  None of these
  
Hint: noHint
         
Explanation: `tx.gasprice (uint)`: gas price of the transaction.  
`tx.origin (address)`: sender of the transaction (full call chain).  
whearas gaslimit is a member of block, `block.gaslimit (uint)`: gives the current block gaslimit.


Sub Topics: block-transaction
 

---

##### Which of the following is not an available Mathematical function?  

- [ ]  addmod
- [x]  submod
- [ ]  mulmod
- [x]  divmod
  
Hint: noHint
         
Explanation: The function addmod takes parameters (uint x, uint y, uint k) and will compute the expression `(x + y) % k`.
The function mulmod takes parameters (uint x, uint y, uint k) and will compute the expression `(x * y) % k`.


Sub Topics: math-functions
 

---

##### Which of the following expressions will the function `mulmod(uint x, uint y, uint k) returns (uint)` compute?  

- [ ]  `(x * y) * k`
- [ ]  `(x % y) * k`
- [ ]  `(x % k) * y`
- [x]  `(x * y) % k`
  
Hint: noHint
         
Explanation: explanation

Sub Topics: math-functions
 

---

##### What is the output of the following function?
```
function func() public pure returns(uint){
     return mulmod(addmod(4,5,2),7,2);
  }
```
  

- [ ]  3
- [ ]  0
- [x]  1
- [ ]  None of these
  
Hint: noHint
         
Explanation: addmod(4,5,2) will evaluate (4+5)%2 which is equal to 1. mulmod of (1,7,2) is (1*7)%2 which is 1.


Sub Topics: math-functions
 

---

##### Which of the following are not valid cryptographic hashing functions?  

- [ ]  keccak256
- [ ]  sha256
- [ ]  ripemd160
- [x]  All of these
  
Hint: noHint
         
Explanation: `keccak256(bytes memory) returns (bytes32)`: computes the Keccak-256 hash of the input.  
`sha256(bytes memory) returns (bytes32)`: computes the SHA-256 hash of the input.  
`ripemd160(bytes memory) returns (bytes20)`: compute RIPEMD-160 hash of the input.  


Sub Topics: math-functions
 

---

##### Which of the following options is correct regarding the statements below?  
Statement 1-The keccak256 (SHA-3 family) algorithm computes the hash of an input to a fixed length output. 
Statement 2- It can be decoded in reverse to retrieve the original input.
  

- [x]  Statement 1 is true but Statement 2 is false.
- [ ]  Statement 2 is true but Statement 1 is false.
- [ ]  Both are true.
- [ ]  Neither is true.
  
Hint: noHint
         
Explanation: The keccak256 (SHA-3 family) algorithm computes the hash of an input to a fixed length output. 
The input can be a variable length string or number, but the result will always be a fixed bytes32 data type.
It is a one-way cryptographic hash function, which cannot be decoded in reverse.


Sub Topics: math-functions
 

---

##### Which of the following is true regarding keccak256 hash function?  

- [x]  Size of the output of the fuction does not depend on size of input.
- [ ]  Size of the output of the fuction depends on the size of input.
- [x]  Small change in input results in massive change in output.
- [x]  The output of the function is a bytes32 data type.
  
Hint: noHint
         
Explanation: The input can be a variable length string or number, but the result of the hash function will always be a fixed bytes32 data type.
The slightest modification or change in the string results in a massive change in the hash digest.


Sub Topics: math-functions
 

---

##### A collision occurs in a hash function when two different inputs produce the same output. 
You are calculating the hash of two strings using `keccak256(abi.encodePacked(_string1, _string2));`.
Which of the following options is correct?
  

- [ ]  Collision is not possible with keccak256 hashing function.
- [x]  There can be certain cases when the two strings will result in a collision.
- [x]  Collision can be prevented using `abi.encode`.
- [x]  Hashing is an important aspect of cryptographic security for digital wallets and transactions on the blockchain.
  
Hint: Is it possible for a input in `abi.encodePacked(_string1, _string2)` to produce similar output with a different input? 
Think of how encoding is done with `abi.encodePacked`.

         
Explanation: Take for example the following inputs:
(AAA, BBB) -> AAABBB,      
(AA, ABBB) -> AAABBB  
They are supposed to be different from each other, but when concatenated as a single string, they actually will produce the same output.
On encoding the input with `abi.encode`, you will have padded zeroes while in abi.encodePacked you do not. Therefore with `abi.encodePacked`, there will always be a collision if the two strings of the two different inputs concatenate to the same string.
If there is likelihood of inputs resulting in outputs that can cause a collision it is recommended to use abi.encode instead of abi.encodePacked.


Sub Topics: math-functions
 

---

##### Which of the following options is correct regarding tx.origin and msg.sender?
  

- [x]  The `tx.origin` global variable refers to the original external account that started the transactions.
- [x]  msg.sender refers to the immediate account (it could be external or another contract account) that invokes the function.
- [ ]  Both functions can be used interchangeably.
- [x]  Both can produce the same output when invoked.
  
Hint: noHint
         
Explanation: The `tx.origin` global variable refers to the original external account that started the transactions.  
msg.sender refers to the immediate account (it could be external or another contract account) that invokes the function.


Sub Topics: block-transaction
 

---

##### Which of the following cannot be used to concatenate two strings `a` and `b`?  

- [x]  `a+b`
- [ ]  `string(bytes.concat(bytes(a),bytes(b)));`
- [ ]  `string(abi.encodePacked(a,' ',b));`
- [ ]  `string.concat(a,b);`
  
Hint: noHint
         
Explanation: Solidity doesn't provide built-in string concatenation and string comparison. Comparision like (a==b) can also not be done.

Sub Topics: bytes-strings
 

---

##### Which of the following options is not correct regarding hashing functions?  

- [ ]  The SHA-256 is weaker than Keccak-256.
- [ ]  Even the slightest alteration or modification to the input string has a significant impact on the hash digest.
- [x]  Keccak-256, a cryptographic function, is part of Solidity (SHA-256 Family).
- [ ]  None of these.
  
Hint: noHint
         
Explanation: Keccak-256, a cryptographic function, is part of Solidity (SHA-3 Family). 
This function computes the hash of an input to a fixed-length output, yielding a singular 32-byte hash from any number of inputs. 
Even the slightest alteration or modification to the string has a significant impact on the hash digest.
The SHA-256 is weaker than Keccak-256.


Sub Topics: math-functions
 

---

##### Which of the following is not an error handling function?  

- [ ]  assert
- [ ]  require
- [ ]  revert
- [x]  request
  
Hint: noHint
         
Explanation: `assert`, `require`, `revert` is used for error handling in Solidity.


Sub Topics: error-handling
 

---

##### What is the unit of `tx.gasprice`?  

- [x]  Ether
- [ ]  wei
- [ ]  kwei
- [ ]  gwei
  
Hint: noHint
         
Explanation: The unit is wei.
Wei is the lowest possible denomination that can be handled by Solidity.


Sub Topics: encoding-decoding
 

---

##### Which of the following is the correct way to return the address of the current contract in a function?  

- [x]  `return address(this);`
- [ ]  `return this;`
- [ ]  `return this.MyContract;`
- [ ]  None of these.
  
Hint: noHint
         
Explanation: The `this` keyword in Solidity refers to the current contract. It is convertible to the address type using `address(this)`.


Sub Topics: contract-related
 

---

##### What is the `this` keyword in Solidity?  

- [x]  The `this` keyword in Solidity refers to the current contract.
- [ ]  The `this` keyword in Solidity refers to the current contracts address.
- [ ]  The `this` keyword in Solidity refers to the instance of the function from where it is called.
- [ ]  None of these.
  
Hint: noHint
         
Explanation: The `this` keyword in Solidity refers to the current contract. It is convertible to the address type using `address(this)`.

Sub Topics: contract-related
 

---

##### Which function is used to destroy a contract?  

- [ ]  suicide
- [ ]  revert
- [x]  selfdestruct
- [ ]  assert
  
Hint: noHint
         
Explanation: `selfdestruct(address payable recipient)`: is used to destroy the current contract, sending its funds to the given Address and end execution.

Sub Topics: contract-related
 

---

##### What is the return type for keccak256 hash function?  

- [ ]  uint8
- [ ]  bytes20
- [ ]  uint 32
- [x]  bytes32
  
Hint: noHint
         
Explanation: `keccak256(bytes memory) returns (bytes32)`: computes the Keccak-256 hash of the input in the form of a bytes32 type output.


Sub Topics: math-functions
 

---

##### How will you retrieve the current contracts balance?  

- [ ]  this.balance
- [x]  address(this).balance
- [ ]  balance(this)
- [ ]  MyContract.balance
  
Hint: this keyword referss to the current contracts instance.
         
Explanation: `this` keyword referss to the current contracts instance. 
`address(this)` will give the address of the current contract. `address(this).balance` will retrieve the balance associated with the current contract.


Sub Topics: contract-related
 

---

##### Which of the following is not a way of sending ether?  

- [ ]  send
- [ ]  transfer
- [ ]  call
- [x]  codehash
  
Hint: noHint
         
Explanation: In Solidity, there are three ways in which one can send ether. Namely transfer(), send() and call().


Sub Topics: address-properties
 

---

##### Which of the following options is correct regarding send and transfer?  

- [x]  Send is similar to transfer. But if the payment fails, it will not revert.
- [ ]  Transfer is similar to send. But if the payment fails, it will not revert.
- [x]  The syntax of the transfer function looks like: `receivingAddress.transfer(amount);`.
- [ ]  The syntax of the transfer function looks like: `transfer(receivingAddress,amount);`.
  
Hint: noHint
         
Explanation: Send is similar to transfer. But if the payment fails, it will not reverts.
"The syntax of the transfer function looks like: `receivingAddress.transfer(amount);`."


Sub Topics: address-properties
 

---

##### What is the difference between transfer and call?  

- [x]  transfer reverts if the send falis.
- [x]  transfer forwards 2,300 gas stipend.
- [x]  call forwards all available gas, allows specifying how much gas to forward.
- [ ]  call reverts on failure.
  
Hint: noHint
         
Explanation: - `address.transfer()`
  - throws on failure.
  - forwards 2,300 gas stipend, safe against reentrancy.
- `address.call.value().gas()()`
  - returns false on failure.
  - forwards all available gas, allows specifying how much gas to forward.


Sub Topics: address-properties
 

---

##### Which of the following is not correct?  

- [ ]  Both send and transfer have a gas limit of 2300 gas.
- [x]  send/transfer is better than call.
- [ ]  transfer is hardcoded to prevent re-entrancy attacks while call is not.
- [ ]  As the amount of gas forwarded in send and transfer is very low, the called contract can run out of gas.
  
Hint: noHint
         
Explanation: Send and transfer forwards 2300 gas to the receiving contract.
Since the amount of gas forwarded to the called smart contract is very low, the called smart contract can easily run out of gas.
Using call allows for re-entrancy attacks. The receiver contract calls the function again where the call() statement is given. If the sender contract is improperly coded, it can result in draining larger amounts of funds from it than planned.


Sub Topics: block-transaction
 

---

##### What is incorrect with the following expresion: `address(this).balance = 0`.  

- [ ]  The expression is correct and will compile.
- [ ]  The expression will assign balance of current contracts address to 0.
- [x]  The expression will give typeError.
- [ ]  None of these.
  
Hint: `.balance` returns a uint256 type value.
         
Explanation: You cannot do address(this).balance = 0 , because address(this).balance is a number not a variable.


Sub Topics: address-properties
 

---

##### Which of the following options is correct regarding the statements below?
Statement 1- `block.number` givess the the block on the blockchain where the contract is mined in.
Statement 2- `block.number` also corresponds to the block number of the block which includes the transaction of ETH sent to a contract function.
  

- [ ]  Statement 1 is true but Statement 2 is false.
- [ ]  Statement 2 is true but Statement 1 is false.
- [ ]  Both are true.
- [x]  Neither is true.
  
Hint: noHint
         
Explanation: Any Solidity method call that changes the state is a transaction. 
To log or return the block info of that transaction, you can use block.number. 
This is possible because that method call can only take effect on the state once the block that the transaction belongs to is mined and upon mining, those properties expose all that info about that block.


Sub Topics: block-transaction
 

---

##### Which of the following is not a special variable available in the global namespace?  

- [ ]  msg
- [ ]  tx
- [ ]  block
- [x]  None of these.
  
Hint: noHint
         
Explanation: There exist special variables like `msg`, `tx`, and `block` in solidity which exist in the global namespace and are mainly used to provide information about the blockchain.


Sub Topics: block-transaction
 

---

##### What does `abi.encodeWithSelector` do?  

- [ ]  It is similar to `abi.encodePacked(FUNC_SELECTOR, _param1, _param2)`.
- [x]  ABI-encodes the given arguments starting from the second and prepends the given four-byte selector.
- [ ]  ABI-encodes all the the given arguments .
- [ ]  None of these.
  
Hint: noHint
         
Explanation: ABI-encodes the given arguments starting from the second and prepends the given four-byte selector.
`abi.encodePacked` doesn't do this. It does a packed encoding of all arguments combined.


Sub Topics: encoding-decoding
 

---

##### Which of the following is equivalent to `abi.encodeWithSignature(string memory signature, ...)`?  

- [x]  `abi.encodeWithSelector(bytes4(keccak256(bytes(signature))), ...)`
- [ ]  `abi.encodePacked(signature, ...)`
- [ ]  `abi.encodeWithSelector(signature, ...)`
- [ ]  None of these
  
Hint: noHint
         
Explanation: `abi.encodeWithSelector` ABI-encodes the given arguments starting from the second and prepends the given four-byte selector, 
`abi.encodeWithSignature(string memory signature, ...)` is equivalent to `abi.encodeWithSelector(bytes4(keccak256(bytes(signature))), ...)`.


Sub Topics: encoding-decoding
 

---

##### Why does `msg.sig` return first four bytes of the calldata as a function identifier?  

- [x]  Using four bytes is a tradeoff as even big contracts have maximum five-to-twenty methods.
- [ ]  4 bytes can be used to denote any number of methods in a contract.
- [x]  There can be a total of 4294967296 different methods in any single contract.
- [ ]  A collision can never happen using 4 bytes.
  
Hint: noHint
         
Explanation: You can address in theory $2^{32}$ (4294967296 as 4 bytes have 32 bits) different methods in any single contract.
It seems enough for any possible contract, giving furthermore the presence of a code size limit of 24 kbytes or so (The major of them have five-to-twenty methods).
Choosing 4 bytes is a reasonable choice because, the probability of a collision is very low so you are assured in any case of a lot of unique entries for methods in the single contract.


Sub Topics: block-transaction
 
