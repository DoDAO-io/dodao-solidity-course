## Header
This is the course header. This will be added on top of every page. Do to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Expressions and Control Structures
 
 
---

##### What will happen if we declared `else` statement without any if statement?  

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

##### How much parameters are required for defining a for loop in Solidity?  

- [ ]  three
- [ ]  four
- [x]  one
- [ ]  two
  
Hint: noHint
         
Explanation: The for loop takes three parameters, one of which is required and the other two are optional. The required parameter must be a conditional statement.

Sub Topics: loops-keywords
 

---

##### What is the data type of the required parameter in the for loop?  

- [x]  Boolean
- [ ]  Integer
- [ ]  String
- [ ]  Struct
  
Hint: noHint
         
Explanation: The required argument should be a conditional statement, hence the data type is boolean.

Sub Topics: loops-keywords
 

---

##### How generally the primary argument withinside the for loop is executed?  

- [ ]  Infinite
- [x]  One
- [ ]  Three
- [ ]  It will execute as long as the condition is true
  
Hint: noHint
         
Explanation: The first argument in the for loop is executed only once.

Sub Topics: loops-keywords
 

---

##### Is it possible to define single line if/else statement?  

- [ ]  No it is not possible
- [ ]  It is possible only when if/else statements is defined inside function modifiers
- [x]  Yes it is possible
- [ ]  None of the above
  
Hint: If/else statments
         
Explanation: We can define single if/else statements without curly braces.

Sub Topics: decision-making
 

---

##### How many times the third parameter will execute if the body of for loop is executed n times?  

- [ ]  n+1 times
- [x]  n times
- [ ]  n-1 times
- [ ]  one
  
Hint: noHint
         
Explanation: The third parameter will be executed the same number of times as the for loop body.

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
         
Explanation: The for loop requires one parameter and can take two optional parameters. The while loop only requires one parameter, which is a conditional statement.

Sub Topics: loops-keywords
 

---

##### When will the loop terminate?  

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

- [ ]  For keyword only
- [ ]  While keyword only
- [x]  Both do and while keywords
- [ ]  Both if and while keywords
  
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
- [x]  Use to skip iteration
  
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
         
Explanation: When the compiler encounters the `break` keyword, it will stop the current iteration or terminate the loop altogether.

Sub Topics: loops-keywords
 
