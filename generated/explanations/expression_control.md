## Header
This is the course header. This will be added on top of every page. Do to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Expressions and Control Structures
 
 **Decision Making**        
If/else statements are used for making decisions and for checking conditions in order to run a program. If the compiler encounters an `if` statement, it checks the condition(s) specified in that statement. 
If the condition(s) are true, it executes the code inside the body of the `if` statement. If the condition(s) are false, the compiler jumps to the next line after the block. The compiler will check all 
the `if` statements but it is not the case with `else`. The `else` block is executed if and only if all of the preceding `if`statements in the code block are false. We can have multiple `if` blocks, but we can have only one `else` block under an `if` block. 
The `else` statement can be defined only when the `if` statement is defined prior to it and they should be continuous - no other codes should lie in between `if` and `else` blocks. If/else statements can be declared only inside functions or function modifiers. 
If/else statments are very useful to handle the logic of our code.

If/else statements in Solidity are similar to other programming languages like JavaScript and Python, but the main difference is that type conversion from non-boolean to boolean is not available in Solidity. 
This means that `if (1)` is not a valid statement in Solidity. We can also have single line if/else statements. 

syntax for if/else statements
```
if(expression//condition){
//body
}
if(condition) body; single line if statement
else {
  body of else block
}

```
Example of a contract demonstrating the usage of if/else statements.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.5;

contract DecisionMaking {
    event Log(string message);

    function checkValue(uint x) public {
        if (x > 100) { // if statement-1
            emit Log("x is greater than hundred");
        }
        if (x > 50 && x <= 100) // if statement-2
            emit Log("x is greater than fifty but less than hundred");
        if (x > 1 && x <= 50) { // if statement-3
            emit Log("x is greater than one but less than fifty");
        } else emit Log("x is less than 1"); // else statement-1
        if (x == 0) emit Log("x is equal to zero"); // if statement-4
        else {
            emit Log("x is not equal to zero"); // else statement-2
        }
    }
}
```
The code snippet above defines the if/else blocks inside the function `checkValue`. When the function is called with an argument, every if block will be validated. The compiler checks all the `if` blocks and then goes 
to the `else` statement if none of the `if` blocks validate to true. For example if the value of `x` is 20 the `if statement-3` is executed and as well as `else statement-2` is executed. If the value of `x` is 0 `else statement-1` is executed
because all the if statements above it fails the condition. Similarly `if statement-4` is also executed as the condition is true.
 
 **For, While, Do While Loops**        
- for Loops
- while Loops
- do while loops
 
 **Break and Continue Keywords**        
- Break Keyword
- Continue keyword
- Return keyword
 
 **Internal and External Function Calls**        
- Internal call
- External call
 
 
