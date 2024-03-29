## Header
This is the course header. This will be added on top of every page. Do to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Expressions and Control Structures
 
 **Decision Making**        
If/else statements are used for making decisions and for checking conditions in order to run a program. If the compiler encounters an `if` statement, it checks the condition(s) specified in that statement. 

If the condition(s) are true, it executes the code inside the body of the `if` statement. If the condition(s) are false, the compiler jumps to the next line after the block. The compiler will check all 
the `if` statements but it is not the case with `else`. The `else` block is executed if and only if all of the preceding `if` statements in the code block are false. We can have multiple `if` blocks, but we can have only one `else` block under an `if` block. 

The `else` statement can be defined only when the `if` statement is defined prior to it and they should be continuous - no other codes should lie in between `if` and `else` blocks. If/else statements can be declared only inside functions or function modifiers. 
If/else statements are very useful to handle the logic of our code.

If/else statements in Solidity are similar to other programming languages like JavaScript and Python, but the main difference is that type conversion from non-boolean to boolean is not available in Solidity. 
This means that `if (1)` is not a valid statement in Solidity. We can also have single line if/else statements. 

syntax for if/else statements
```sol
if(expression){ //condition
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
The code snippet above defines the if/else blocks inside the function `checkValue`. When the function is called with an argument, every if block will be validated. The compiler checks all the `if` blocks and then goes to the `else` statement if none of the `if` blocks validate to true. For example if the value of `x` is 20 the `if statement-3` is executed and as well as `else statement-2` is executed. If the value of `x` is 0 `else statement-1` is executed because all the if statements above it fails the condition. Similarly `if statement-4` is also executed as the condition is true.
 
 **For, While, Do While Loops**        
#### For Loops
For loops are used to iterate and loop through different conditions. You can define for loops only inside a function or function modifier, similar to if/else statements.
For loop is defined by the keyword `for`. It takes three parameters, two of which are optional and one required. The parameters are seperated by semi-colon. The first parameter is optional, where variables can be initialized. 
The second parameter is a condition that belongs to the data type boolean. If this condition fails, the loop will terminate. The third parameter is also optional and can be used for incrementing and decrementing values or altering 
them as needed. Anything can be done in the optional parameters - for example, in the first parameter we can do operations instead of initializing variables, and in the third parameter we can initialize variables or do other operations.

##### Working of for loop 
The compiler will execute the first parameter of the for loop only once. It will then check the condition and, if it's true, execute the body of the for loop. After executing the third parameter, it will check the condition again. 
This process repeats until the condition is false.

Loops usually have three parameters, with the first parameter being executed only once at the start of the loop, the second parameter being the condition which is validated for the whole iteration of the loop, and the third parameter 
being executed for every iteration except the first iteration. If the condition inside the loop is always true, however, the loop will become an infinite loop and the program will crash.

Syntax of the for loop 
```solidity
for(first parameter; second parameter(condition); third parameter){
  //body of the for loop
}
```

An example of using for loop in solidity

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.5;

contract Loops {
    uint public sum = 0;

    function Summation(uint n) public { // this function will do summation till n and add it to the variable sum
        for (uint i = 0; i <= n; i++) { // for loop is used for iterating till n
            sum += i; 
        }
    }
}

```
The value of the `sum` variable is initially set to zero. When the `Summation` function is called with any positive integer as an argument, the for loop starts executing. The value of `i` is set to zero and the compiler 
checks for the condition `i<=n`. If that condition is true, it will execute the body and then execute the third parameter (`i++`). It will then check the condition again to see if it is true. If so, the process will repeat. 
The loop will only terminate if the condition is not met, which in this case is when `i>n`. Upon completion of the loop, we should get a sum that is equal to the summation of 0 to n.

#### While loop 
While loops are very similar to `for` loops in that they can be used for iteration. The main difference between the two types of loops is that while loops only take one parameter instead of three. The parameter passed into a while loop is a condition. 
If that condition is not met, the while loop will terminate. The while loop is defined using the keyword `while`. The while loop will continue to execute until the condition is true. However, if the given condition is always true, 
it will become an infinite loop and the program will crash.

Syntax for while loop
```solidity
while(condition){

    //body of while loop

}
```
An example of using while loop in solidity
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.5;

contract Loops {
    uint public evensum = 0;

    function sumEven(uint n) public {// this function will do summation of even numbers till n
        uint i = 0;
        while (i <= n) {  // while loop is used for iteration
            if (i % 2 == 0) sum += i; // if statement for filtering even numbers till n
            i++;
        }
    }
}

```
In the code snippet above, we have initialized a variable called `evensum` with a value of zero. The function `sumEven` is called with a positive integer, and 
if the condition `i<=n` is true, the while loop will start executing. The loop will continue until the condition is no longer true - in this case, when `i>n`. 
This code results in the sum of all even numbers from 0 to n.

#### Do-While loop
Do while loops are completely similar to while loop the main difference is the do while loop is executed atleast one time. Do-while loop is executed once for even false condition.
Syntax for do while loop
```solidity
do{
  // Body of the do while loop
}while(condition); // semi-colon is necessary

```
Example showing how to use do while loop.
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.5;

contract Loops {
    uint public i = 0;

    function doWhile() public {
        do { // do while loop is used for iteration
            i++;
        } while (1 > 2); // false condition
    }
}

```
In the above code, we have initialized `i=0`. When the function `doWhile` gets called, it executes the do-while loop. Even though the condition `1>2` is false, the loop will execute for at least one time, 
meaning the value of `i` will be one when the function is called once. If the function is called `n` times, the loop will execute `n` times and thus the value of `i` will be `n`.
We have used a false condition to demonstrate how do-while loops work.

In general, it's best to minimize the use of loops in Solidity code in order to reduce gas fees. By avoiding loops, you can save a lot of gas because it prevents computationally-heavy operations.
 
 **Break, Continue and return keywords**        
#### Break
Break is a keyword which is used to break or terminate the running loop. It is a very useful keyword. In some situation we need to terminate the loop after a certain condition is met in that case we may use
`break` keyword. Break keyword is used inside loops mostly with if/else statements. When compiler encounters break keyword it jumps out of the loop.

Example showing the usage of break keyword
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.5;

contract Keywords {
    uint[] numbers = [1, 2, 3, 4, 5];
    event elementcheck(string message);

    function checkNumber(uint n) public {
        for (uint i = 0; i < n; i++) {
            if (numbers[i] == n) {
                emit elementcheck("element is found");
                break;
            }
        }
    }
}

```
In the code snippet provided, `numbers` is an array of unsigned integers. If `checkNumber` is called with a positive number as an argument, the for loop will be executed and the if condition will validate the condition `numbers[i]==n`.
If that condition is satisfied,  the event will be emitted and the loop will be terminated using the break keyword.

#### Continue
The `continue` keyword is used to skip an iteration of a loop. In some cases, we need to skip an iteration of the loop when certain conditions are met. If the compiler encounters the `continue` keyword, it will jump to 
the next iteration of the loop. This means that the control is transferred to the loop check condition. If the condition is true, the next iteration starts.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.5;

Example showing the usage of continue keyword
contract Keywords {
    uint public sumeven = 0;

    function summationOfEven(uint n) public {
        // this function will sum even numbers from one to n
        for (uint i = 0; i <= n; i++) {
            if (i % 2 != 0) {
                continue; // continue keyword helps skipping the odd numbers in this case
            } else {
                sumeven += i;
            }
        }
    }

    function reset() public {
        // rests the value of sumeven to zero
        sumeven = 0;
    }
}

```
In the code snippet above, we have initialized `sumeven=0`. When the function `summationOfEven` is called with a positive integer n, the for loop is executed. If the condition `i%2!=0` is satisfied, 
the keyword `continue` will transfer control to the loop check condition and start the next iteration. In this case, `continue` helps us to skip iterations of odd numbers.

#### Return 
Return is a keyword which is used to return values/objects from a function. Whenever `return` is called the function will stop execution and return the value provided in the return statement.
We can return values from a function in two ways: One way is to normally return the value using the `return` keyword. Another way is to define a return variable and assign the return value to that
variable. The function `add` below defines a return variable `sum`. 

Therefore, we can return the value by just assigning the value to the sum as shown in the below snippet.
```solidity
function1(uint x)public returns(uint){
  return x%2; returning using the return keyword
}

function2(uint y)public returns(uint answer){
  answer = y%2; // returning the value by assigning return variable answer
}

```
In the above snippet both the functions performs same operation when an argument is passed to but they are returning values it in different ways.

Example of using return keyword 

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.5;

contract Keywords {
    function sum(uint a, uint b) public pure returns (uint, uint, uint, uint) {
        return (a + b, b % a, a % b, a * b);
    }
}
```
 
 **Internal and External function calls**        
#### Internal function calls
Internal function calls are function calls that happen inside the contract. You can do an internal function call by directly using the function's identifier. Recursive calling also counts as an internal function call.
These function calls are translated into simple jumps inside the EVM. This has the effect that the current memory is not cleared, i.e. passing memory references to internally-called functions is very efficient. 
You can use the function's identifier to do an internal function call, no matter where the function is defined. As long as it's defined in the contract, the internal function call will take place. 
You can call internal functions at any point in your code - for example, you could use them as other function's arguments, or inside if/else statements.

Example of an internally called function is shown below
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.5;

contract FunctionCall {
    uint public addition = add(1, 2);
    uint public product = multiply(add(2, 3), add(2, 1));

    function add(uint a, uint b) public pure returns (uint output) {
        output = a + b;
    }

    function multiply(uint a, uint b) public pure returns (uint) {
        return a * b;
    }

    function validate() public {
        if (add(1, 2) <= multiply(1, 3)) {
            addition = 100;
        }
    }
}

```
In the snippet above, we make four internal function calls. The first call is `add(1,2)` and the second and third calls are made within the argument of the function call `product`.


#### External function calls
External function calls are basically function calls to other contracts. In order to make an external function call, the parent contract should have defined the object of the callable contract and the 
deployed address of the callable contract should be assigned to the created contract object. External function calls can be made using `object.functionIdentifier` - for example `g.send(8)`, where `g` is the 
object of the callable contract and `send` is a function of that contract. For error handling during external calls, we use try/catch statements.
EVM considers a call to a non-existing contract to always succeed, so Solidity  uses the extcodesize opcode to check that the contract actually exists before calling it.  If the contract does not exist, an exception is thrown. Hence, the contract to which  the call is made should be defined in the file or imported into the file.
A function call from one contract to another is not considered its own transaction; rather,  it's seen as a message call that's part of an overall transaction. However, an external  function call will be treated as a transaction if it modifies the state of the blockchain.
Example of an external call is shown below
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.5;

contract CallerContract {
    ExternalContract call;

    function set(ExternalContract addr) external {
        call = addr;// setting the contract object
    }

    function callSend(address payable addr) public {// address should be payable
        call.send(addr);
    }
}

contract ExternalContract {
    function send(address payable addr) external payable {
        (bool sucess, ) = addr.call{value: 100}(""); //sending 100 wei
        require(sucess, "transaction failed"); 
    }

    receive() external payable {}
}

```
In the code snippet above, we are calling the `send` function in the `ExternalContract` using the `CallerContract`. To do this, we first create a contract object of `ExternalContract` by its deployed address. 
We then make an external call, setting the deployed address to the contract object `call`. The `call.send` function will send ether (in wei) to the address provided in the argument. However, before making the external call, 
we need to make sure that the `ExternalContract` has some ether in it, so that it can send ether. Hence, we send ether to the `ExternalContract` before making the external call. The `ExternalContract` should have ether more than the sending value i.e, ether should be more than 100 wei in this case. 
 
 
