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

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: block-transaction
 
