## Header
This is the course header. This will be added on top of every page. Do to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Expressions and Control Structures
 
 
---

##### What will happen if we declared `else` statement without any `if` statement?  

- [ ]  Compiler checks for the condition in the else statement
- [ ]  It will be executed
- [x]  Error message will appear
- [ ]  Nothing will happen
  
Hint: Else statement
         
Explanation: Else statement can be defined only when the `if` statement is defined prior to it and they should be continuous i.e, no codes should lie between them.

Sub Topics: decision-making
 

---

##### Which of the following is/are correct?  

- [x]  We can have multiple `if` statements continously
- [ ]  We can have only one `if` statement continuously
- [ ]  We can have multiple `else` statement under `if` statements continously
- [x]  We can have only one `else` statement under `if` statements continuously
  
Hint: noHint
         
Explanation: We can have multiple `if` statements continuosly but only one else statement after a single or multiple `if` statement.

Sub Topics: decision-making
 

---

##### Can we define `else if` block in Solidity?  

- [ ]  Else if block can be defined but only inside the struct
- [x]  Else if block doesn't exist in Solidity so we can't define it
- [ ]  Else if can be defined but only above the `if` block
- [ ]  Else if can be defined but only below the `else` block
  
Hint: Doesn't exist
         
Explanation: Else if doesn't exist in solidity. `Else if` is also a statement like `if` but it will be executed only if all of the preceding `if` or `else if` statements in the code block are false. Else if do exist in other programming langiages like c,c++, JavaScript.

Sub Topics: decision-making
 

---

##### Is it possible to convert non-boolean to boolean in solidity example `if(1)`?  

- [x]  No
- [ ]  Yes
  
Hint: Boolean
         
Explanation: We cannot do type conversion from non-boolean to boolean in solidity

Sub Topics: decision-making
 

---

##### What is the datatype inside the paranthesis of an `if` statement?  

- [ ]  Int
- [ ]  String
- [x]  Boolean
- [ ]  Address
  
Hint: noHint
         
Explanation: The paranthesis in if statement contains a condition so the data type should be either true or false hence it is boolean value.

Sub Topics: decision-making
 

---

##### How many parameters are required for defining a `for` loop in Solidity?  

- [ ]  three
- [ ]  four
- [x]  one
- [ ]  two
  
Hint: noHint
         
Explanation: The `for` loop takes three parameters, one of which is required and the other two are optional. The required parameter must be a conditional statement.
```solidity
for(first param;second param(required);third param){
  //body of the loop
}
```


Sub Topics: loops-keywords
 

---

##### What is the data type of the required parameter in the `for` loop?  

- [x]  Boolean
- [ ]  Integer
- [ ]  String
- [ ]  Struct
  
Hint: noHint
         
Explanation: The required argument should be a conditional statement, hence the data type is boolean.

Sub Topics: loops-keywords
 

---

##### How many times is the primary argument(first) within the `for` loop is executed?  

- [ ]  Infinite
- [x]  One
- [ ]  Three
- [ ]  It will execute as long as the condition is true
  
Hint: noHint
         
Explanation: The first argument in the `for` loop is executed only once.

Sub Topics: loops-keywords
 

---

##### Is it possible to define single line if/else statement?  

- [ ]  No it is not possible
- [ ]  It is possible only when if/else statements is defined inside function modifiers
- [x]  Yes it is possible
- [ ]  None of the above
  
Hint: If/else statments
         
Explanation: We can define single if/else statements with/without curly braces.

Sub Topics: decision-making
 

---

##### How many times will the third parameter be execute if the body of `for` loop is executed n times?
for example in the below case the body of the for loop will execute for 5 times.
```solidity
for(uint i=1;i<=5;i++){
  sum+=i;
}
```
  

- [ ]  n+1 times
- [x]  n times
- [ ]  n-1 times
- [ ]  one
  
Hint: noHint
         
Explanation: The third parameter will be executed the same number of times as the `for` loop body. As shown in the example the third parameter `i++` will execute for 5 times which is same for the body of the loop.

Sub Topics: loops-keywords
 

---

##### Why are loops not preferred in solidity?  

- [x]  Loops will consume lot of gas for computation
- [ ]  Loops will cause bugs in the contract
- [ ]  Loops are not preferred as it is complex to use
- [ ]  None of These
  
Hint: Gas Fees
         
Explanation: Loops require a lot of computation, so gas fees can get pretty high.

Sub Topics: loops-keywords
 

---

##### What is the difference between for loop and while loop?  

- [ ]  The while loop will continue to run even when the condition is false
- [ ]  For loops involve curly braces while while loops don't
- [ ]  The for loop can be used inside a function, but the while loop can be used anywhere in the contract
- [x]  While loops can take only one parameter, for loops can take three parameters
  
Hint: Parameters/Arguments
         
Explanation: The `while` loop requires only one parameter, and that is the conditional statement. The `for` loop can take three parameters.

Sub Topics: loops-keywords
 

---

##### When will the while loop terminate?  

- [x]  When the condition is false
- [ ]  After 100 iterations
- [ ]  When the gas fees execeeds 15000 wei
- [ ]  When the condition is true
  
Hint: Condition
         
Explanation: The while loop will terminate only when the condition inside the loop is false.

Sub Topics: loops-keywords
 

---

##### What is the do-while loop's specialty?  

- [ ]  It consumes very less gas
- [x]  The loop is executed for atleast one time
- [ ]  It can be defined anywhere in the contract
- [ ]  The loop will terminate automatically after 1000 iterations
  
Hint: noHint
         
Explanation: The Do-while loop is executed at least once, but if the condition inside the while or for loop is false, it will not execute.

Sub Topics: loops-keywords
 

---

##### What keywords are used to define a do-while loop?  

- [ ]  `for` keyword only
- [ ]  `while` keyword only
- [x]  Both `do` and `while` keywords
- [ ]  Both `if` and `while` keywords
  
Hint: noHint
         
Explanation: The do-while loop is defined using two keywords `do` and `while`.

Sub Topics: loops-keywords
 

---

##### What will happen if the condition in the do-while loop is false?  

- [ ]  The loop will not execute at all
- [x]  The loop is executed for one time
- [ ]  The program will crash
- [ ]  None of the above
  
Hint: noHint
         
Explanation: The do-while loop is executed for atleast one time. It doesn't matter if the condition is false the loop will execute for one time.

Sub Topics: loops-keywords
 

---

##### What is the purpose of break keyword?  

- [x]  To terminate the loop
- [ ]  To make a jump for next iteration
- [ ]  To stop a function's execution
- [ ]  It is used to handle errors
  
Hint: Termination
         
Explanation: The break keyword is used to stop the execution of a loop or to terminate the loop. It is mostly used with if/else statements.

Sub Topics: loops-keywords
 

---

##### What is the use of the continue keyword?  

- [ ]  It is used to handle errors
- [ ]  Used for making a contract object
- [ ]  Used for making external calls
- [x]  Used to skip rest of the steps in current iteration and start with next iteration
  
Hint: noHint
         
Explanation: The keyword "continue" is mostly used with conditional statements in order to skip the current iteration of a loop.

Sub Topics: loops-keywords
 

---

##### Where can we use a return keyword?  

- [ ]  It can be used only inside contructor function
- [ ]  It can be defined in for loops without a function
- [x]  Only inside a function
- [ ]  None of these
  
Hint: noHint
         
Explanation: The "return" keyword can be used only inside a function or within the body of a function.

Sub Topics: loops-keywords
 

---

##### What will happen if the compiler encounters an `break` keyword inside a nested for loop?  

- [ ]  All the for loops are terminated
- [x]  The for loop in which the break keyword is encountered will be terminated
- [ ]  No change will occur
- [ ]  None of the above
  
Hint: noHint
         
Explanation: When the compiler encounters the `break` keyword, it will stop the current iteration or terminate the loop in which the `break` keyword is defined.

Sub Topics: loops-keywords
 

---

##### In Solidity, is it possible to return a value from a function without using the return keyword?  

- [x]  Yes
- [ ]  No
  
Hint: noHint
         
Explanation: We can return a value from a function by assigning the return variable to the value we want to return. Example in the below snippet the product of the arguments is returned without the return keyword.
```solidity
   function product(uint x, uint y) public pure returns (uint answer) {
      answer = x * y; //product is returned just by assigning the value to the defined variable
   }
```


Sub Topics: loops-keywords
 

---

##### the data types of returning values should be specified in the function using the keyword `returns`.
  

- [x]  True
- [ ]  False
  
Hint: noHint
         
Explanation: We need to specify the data type of returning values in the function using the keyword `returns`.

Sub Topics: loops-keywords
 

---

##### How to perform an internal function call?  

- [ ]  It can be called using contract's deployed address and assigning it to the contract object
- [x]  It can be done by using function identifier
- [ ]  Internal function calls can be called only through constructor function using the function's identifier
- [ ]  Internal function calls can be called only through function modifier using the function's identifier
  
Hint: Identifier
         
Explanation: Internal function calls can be executed by using the function's identifier with arguments if they exist. The function that is being called should be defined in the same contract.
Below code snippet is an example for internal function call.
```solidity
uint public addition = add(1, 2); // making an internal call using the function's identifier

function add(uint a, uint b) public pure returns (uint output) {
    output = a + b;
}

```


Sub Topics: func-call
 

---

##### Why passing memory references to internally-called functions is very efficient?  

- [ ]  It is because EVM store memory of all internal function calls until the deployed contract is destroyed or demolished
- [ ]  It is beacause internal function calls stores data into the storage data
- [x]  It is because internal function calls are translated into simple jumps inside the EVM hence the current memory is not cleared
- [ ]  None of the above
  
Hint: noHint
         
Explanation: Internal function calls are translated into simple jumps inside the EVM. This has the effect that the current memory is not cleared, i.e. passing memory references to internally-called functions is very efficient.

Sub Topics: func-call
 

---

##### In the following expression, can you spot the error in the code?
 ```solidity
 function add(uint x, uint y) public pure {
    return x+y;
 }
 ```
  

- [ ]  The `return(uint)` is missing in the above snippet
- [x]  The `returns(uint)` is missing in the above snippet
- [ ]  The `pure` keyword should be removed
- [ ]  The value should be returned within the parenthesis i.e, it should be `return(x+y)` instead of `return x+y`
  
Hint: Return keyword
         
Explanation: The data type of returning values should be specified before returning in a function. The `returns(uint)` is missing in the above snippet. The solution is given below.
```solidity
function add(uint x, uint y) public pure returns (uint) {
    return x+y;
}
```


Sub Topics: loops-keywords
 

---

##### Recursion is which type of function call?  

- [x]  Internal
- [ ]  External
- [ ]  Delegate call
- [ ]  It is a special type of function call
  
Hint: noHint
         
Explanation: Recursion is an internal function call where the function is called from within the same contract.

Sub Topics: func-call
 

---

##### Which of the following is correct?
statement 1 - Internal function call can occur anywhere in a contract.
statement 2 - Only uint/int, String and boolean can be returned using return keyword.
  

- [ ]  Statement 2 is correct but Statement 1 is incorrect
- [x]  Statement 1 is correct but Statement 2 is incorrect
- [ ]  Both are correct
- [ ]  Neither is correct
  
Hint: noHint
         
Explanation: Internal function call can occur anywhere inside the contract for example it can occur inside function arguments, if/else statements, contructor function, etc. We can also return address and bytes using return keyword.

Sub Topics: func-call
 

---

##### Which of the options regarding the statements below are correct?
statement 1 - External calls can be done only to the deployed contracts
statement 2 - External contract's deployed address is necessary to perform an external call
  

- [ ]  Statement 2 is correct but Statement 1 is incorrect
- [ ]  Statement 1 is correct but Statement 2 is incorrect
- [x]  Both are correct
- [ ]  Neither is correct
  
Hint: Externalcall
         
Explanation: In order to make an external call, you need the deployed address of the contract. This means that external calls can only be made to contracts that have already been deployed.

Sub Topics: func-call
 

---

##### What will happen if the external contract is not defined or imported in solidity file while making an external call?  

- [ ]  The external call will be sent sucessfully
- [x]  The code will not compile
- [ ]  In that the call will only be successful if the function that is called is not a payable function
- [ ]  None of the above
  
Hint: noHint
         
Explanation: The compiler will show an declaration error and the external call will not occur

Sub Topics: func-call
 

---

##### What is the correct syntax for an external call?  

- [ ]  `functionIdentifier(arguments)`
- [ ]  `contractobject.functionIdentifier(addr,arguments)` , where `addr` is the  address of the external contract
- [x]  `contractobject.functionIdentifier(arguments)`
- [ ]  `functionIdentifier(addr,arguments)` , where `addr` is the  address of the external contract
  
Hint: noHint
         
Explanation: The correct syntax for making an external call is `contractobject.functionIdentifier(arguments)`

Sub Topics: func-call
 

---

##### Arrange the following steps in a correct way
1. Address of the external contract is set to the contract object
2. External call is made using the contract object
3. Contract object is created using the exact identifier for the external contract
4. External contract is defined in the sol file
  

- [ ]  1->2->3->4
- [x]  4->3->1->2
- [ ]  4->3->2->1
- [ ]  2->4->1->3
  
Hint: Externalcall
         
Explanation: First, we need to either import or define the external contract in the file where the caller contract is located. 
Then, we create an object for the external contract. After creating the contract object, we set the deployed address 
of the external contract to the contract object. Finally, we make the external call using the contract object.


Sub Topics: func-call
 

---

##### What is used by solidity to check the existence of a contract  

- [ ]  keccac function
- [x]  extcodesize opcode
- [ ]  ABI of the deployed contract
- [ ]  None of the above
  
Hint: noHint
         
Explanation: Solidity uses the `extcodesize` opcode to check that the contract that is about to be called actually exists (it contains code) and causes an exception if it does not.

Sub Topics: func-call
 

---

##### Which of the following is correct about external function call?  

- [x]  External function calls do not cost any gas until there is no changes in the state of the blockchain
- [ ]  External calls doesn't require any address it can made just calling the function using its identifier
- [x]  External contract should be defined or imported for making an external function call
- [ ]  External call costs gas even it doesn't change the state of the blockchain
  
Hint: noHint
         
Explanation: External function calls don't cost any gas unless the blockchain state changes. To make an external call, you need the deployed contract address. 
You also need to have the external contract defined or imported in the Solidity file where the caller contract is located.


Sub Topics: func-call
 

---

##### How errors are handled during external call?  

- [ ]  Errors are handled using `break` keyword during external call
- [ ]  Errors are handled using events during external call
- [x]  Errors are handled using try/catch statements during external call
- [ ]  Errors are handled using if/else statements during external call
  
Hint: noHint
         
Explanation: The errors are handled using try/catch statements during external call.

Sub Topics: func-call
 

---

##### What needs to be done before making an external call in which the called function will transfer ether from the external contract?  

- [ ]  The external contract should be removed from the file
- [x]  Before making an external call, always check the balance of the external contract to make sure it has enough ether. If the contract doesn't have enough, you'll need to send more ether to it before proceeding
- [ ]  The caller contract should have its own object defined
- [ ]  None of the above
  
Hint: noHint
         
Explanation: Before making an external call, we must check the balance of that external contract to ensure it has a sufficient amount of ether. If it doesn't have a good amount of ether, we must send ether to that 
external contract before making the call. This is because in order to make a transaction, the contract must hold some ether.


Sub Topics: func-call
 

---

##### In the following expression, can you spot the error in the code?
```solidity
  contract CallerContract {
      ExternalContract call;

      function callSend(address payable addr) public {
          call.send(addr);
      }
  }

```
  

- [ ]  The function should be called `ExternalContract.call.send(addr)` instead of `call.send(addr)`
- [ ]  The `payable` keyword should be removed
- [x]  The deployed address of the external contract is not set to the contract object
- [ ]  No error in the code
  
Hint: noHint
         
Explanation: The code above will throw an error because the deployed address of the external contract is not set to the contract object.
The correct code is shown below

```solidity
contract CallerContract {
    ExternalContract call;

    function set(ExternalContract addr) external {
        call = addr;
    }

    function callSend(address payable addr) public {
        call.send(addr);
    }
}
```


Sub Topics: func-call
 
