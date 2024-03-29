## Header
This is the course header. This will be added on top of every page. Do to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Your First Solidity Smart Contract
 
 **Structure of a smartcontract**        
#### Versioning of solidity compiler
The compiler version will be in the form MAJOR.MINOR.PATCH example(0.8.7) which indicates the major release 0 with 8th minor release and 7th patch. 

#### Structure of a smart-contract in solidity

```solidity
//SPDX-License-Identifier:MIT
pragma solidity ^0.8.2;

import "@chainlink/contracts/src/v0.8/interfaces/AggregatorV3Interface.sol";

contract HelloWorld {
    string word = "helloworld";
    // this is a single line comment

    /* this is a 
        multi line comment */
}
```

Every Solidity source file should have a license identifier in order to avoid legal issues when the code is published as open source. The Solidity compiler recognizes SPDX license identifiers, which are machine-readable. 
You can specify the license identifier anywhere in the code, but it's recommended to put it at the top of each file.

The compiler that will be used to compile the Solidity file must be specified using the keyword "pragma" followed by the caret (^) symbol and the version number. The caret symbol indicates that any Solidity 
compiler with a version of the same major and minor value and patch number greater than the specified version can be used to compile the file. Example in the above code version compiler with 0.8.7 can be used to compile the above code but 0.9.2 and 0.8.0 can't be used to compile the above file. 
Every solidity file must be saved as `.sol` for compiling. Single line comments starts with `//`. Multiline comments starts with `/*` and ends with `*/`.

`import` keyword is used for importing files from other resources. Solidity also include constructor functions. Constructors are functions which will be executed automatically for one time when a contract is deployed.
You can also write your Solidity comments in the Ethereum Natural Language Specification Format (NatSpec). It defines a special form of comments in Solidity contracts. Developers use it for documenting return variables, functions, and so on.
You can write single or multi-line comments in Solidity, and use two types of syntax, start the line with /// to include a single-line comment and start with /**and end with /* to include a multi-line comment.
example code snippet.

```solidity
//SPDX-License-Identifier:MIT
pragma solidity ^0.8.2;

import "priceconverter.sol"; // this is normal importing
import "priceconverter.sol" as pc; // if you want to import one file but with different name
import { price1 as p1, price2 } from "storagefactory.sol"; // If we want to import only specific variables or functions from a file

contract SolidityStructure {
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    /* msg.sender is the address that has called or initiated a function or created a transaction. 
            But at the time of deployment it will be the address of the deployer of the contract */

    /// @author admin
}
```

In the above snippet, the constructor function will only be called once when the contract is deployed. This function will assign the deployer address to the `owner`. `msg.sender` is the address that has called or 
initiated a function or created a transaction. But at the time of deployment it will be the address of the deployer of the contract.
 
 **Statevariables and Functions**        

State variables are variables whose values are permanently stored in contract storage. State variables can be declared as `constant` or `immutable`. The constant variables cannot be redeclared after assigning but immutable variables
can be redeclared using constructor. Constant or immutable can be declared only for variables of the type string, int or uint, boolean, address and enums. Using constant and immutable can reduce the gas cost.

Functions in Solidity are like small pieces of code that can be executed. The way you write a function in Solidity is similar to how you would write one in c, c++, or JavaScript, except for a few small differences. 
Functions are usually written inside a contract, but they can also be written outside of contracts. These functions that are written outside of contracts are called "free functions". Free functions don't have 
access to variables inside the contracts, but other contracts can call them. Free functions also don't have visibility, which means we cannot use the public or external keyword for them. We need to define the 
data type for function arguments and return types. 

We can return values from a function in two ways:
One way is to normally return the value using the return keyword. Another way is to define a return variable and assign the return value to that variable. The function `add` below defines a return variable `sum`. 
Therefore, we can return the value by just assigning the value to the sum as shown in the below snippet.


```solidity
contract SimpleProgram {
    uint public constant value = 23;
    uint public answer = add(value, 1);
    address immutable owner;

    constructor() {
        owner = msg.sender;
    }

    uint public product = multiply(value, 2);

    function multiply(uint a, uint b) public returns (uint) {
        return a * b;
    }
}

function add(uint a, uint b) pure returns (uint sum) {
    sum = a + b;
}

```
The above code snippet shows that the owner variable is assigned the deployer or contract owner address during the constructor time. However, you cannot reassign a constant variable like an immutable variable. 
The simpleProgram contract is calling the free function `add` to add two numbers together and assigning the return value from the function to a variable `answer`.

#### Others functions and features in solidity
The `fallback` and `receive` functions are two special types of functions that are often used together. The `fallback` function is a function that is called if none of the other functions match the function 
identifier or if ether is transferred to the contract with some data. The `receive` function is a function that is called when someone sends ether to a contract. If the contract does not have a `receive` function, 
then the `fallback` function will be executed. If ether is sent with some data directly to the contract, then the `fallback`function will be executed even if a `receive` function is defined. 
While defining the recieve function payable keyword must be added in order to receive ether. Visibility of receive and fallback functions must be defined.

There are two keywords which can restrict functions: `pure` and `view`. If `pure` is used in a function, that function will not be able to read or write. If `view` is used in a function, 
that function will not be able to write, but will have read access. 

Sample code explaining how to use recieve and fallback functions.
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.5;

contract SolidityCourse {
    uint public value = 0;

    receive() external payable {
        setValue(24);
    }

    function setValue(uint x) internal {
        value = x;
    }

    function check_value() public view returns (uint answer) {
        // view keyword restrict the function check_a to read only
        answer = value;
    }

    fallback() external {
        setValue(12);
    }
}

```
 
 **Events and Function modifiers**        
#### Events

Events are inheritable members of contracts. When you call them, they cause the arguments to be stored in the transactions log - a special data structure in the blockchain.
Events are defined within the contracts as global and called within their functions. Events are declared by using the event keyword as follows , `event <eventName>(parameters) ;`.

```solidity
contract Events{
  event Log(uint value, address member );
  function deposit() public payable{
      emit Log(msg.value,msg.sender);
  }
}

```
The `deposit` function is called whenever a user sends Ether to the contract. The value that is sent and the sender's address are logged and stored in the blockchain as an event. `emit Log(msg.value,msg.sender);` defines emitting of the event with the message value and the senders address. 
These events are very useful for maintaining transaction logs. They can be viewed in `Etherscan` if the contract is deployed in Ethereum or any of its testnets. Events are ways to communicate with a client application or front-end website that something has happened on the blockchain. 
The above event Deposit can be detected from the JavaScript API by filtering for `Deposit`.

#### Function Modifiers

Function modifiers can be used to change the behaviour of functions in a declarative way. A modifier can be used automatically to check a condition prior to execution of the function.
We need to use `modifier` keyword in order to define a modifier then we need to give identifier to that modifier, the syntax will look something likje this
```solidity
modifier Identifier {
    //code comes here
}
```
In the below snippet, the owner variable is assigned the address of the deployer of the contract as discussed before. The function modifier `onlyOwner` is added to the function `setValue` just by adding the identifier of the 
modifier as a keyword to the function `setValue`. When the function `setValue` is called, the compiler checks into the keywords and finds the modifier, then jumps to the `onlyOwner` function. If the condition in the require 
statement is true, the code in the modifier will run. If the condition is false, the transaction will be reverted with a message stating "not owner". The `_;` will execute the code of the `setValue` function. 
If `_;` is declared before the require statement, the parent function's code will be executed first, and then the require statement will be executed. So if the require statement is passed, the parent 
function's code will be executed, i.e. the `setValue` function's code will be executed. In simple terms modifier's helps to manupulate the functions.

```solidity
//SPDX-License-Identifier:MIT
pragma solidity ^0.8.0;

contract FunctionModifiers {
    address public immutable owner;
    uint public favourite_number = 7;

    constructor() {
        owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "not owner");
        _;
    }

    function setValue(uint x) public onlyOwner returns (uint v) {
        favourite_number = x;
        v = x;
    }
}

```
 
 **Error Handling**        
Solidity uses state-reverting exceptions to handle errors. Such an exception undoes all changes made to the state in the current call (and all its sub-calls) and flags an error to the caller.
Solidity has many functions for error handling. Errors can occur at compile time or runtime. Solidity is compiled to byte code and there a syntax error check happens at compile-time, while runtime 
errors occur mainly while executing the contracts. Some of the runtime errors are out-of-gas error, data type overflow error, divide by zero error, array-out-of-index error, etc.
Error handling can be done using assert, revert, require, "try-catch" and custom errors.

#### Assert 
Assert is used to check conditions which should be true always. The assert function creates an error of type Panic(uint256). Assert should only be used to test for internal errors, and to check invariants. Properly functioning code should never create a Panic, 
not even on invalid external input. If this happens, then there is a bug in your contract which you should fix.

A Panic exception is generated in the following situations.
* If you call assert with an argument that evaluates to false.
* If an arithmetic operation results in underflow or overflow.
* If you divide or modulo by zero.
* If you convert a value that is too big or negative into an enum type.
* If you call .pop() on an empty array.
* If you access an array or an array slice at an out-of-bounds or negative index.
* If you allocate too much memory or create an array that is too large.
* If you call a zero-initialized variable of internal function type.

#### Require
The require function takes two parameters. The first argument is the condition and the second is the custom string text which will be displayed if the condition returns false. this second parameter is optional.
If false then exception is raised and execution is terminated. The unused gas is returned back to the caller and the state is reversed to its original state.

require exception is triggered for the following cases:
* Calling require(x) where x evaluates to false.
* If you perform an external function call targeting a contract that contains no code.
* If you use revert() or revert("description").
* If your contract receives Ether via a public function without payable modifier.
* If your contract receives Ether via a public getter function.

```solidity
//SPDX-License-Identifier:MIT
pragma solidity ^0.8.0;

contract FunctionModifiers {
    address public owner;
    uint public favourite_number = 7;

    constructor() {
        owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == owner);
        _;
    }

    function setValue(uint x) public onlyOwner {
        favourite_number = x;
    }
}
```
In the above snippet require exception will be triggered if `msg.sender` is not equal to `owner` i.e, the address which is calling or acessing the function is not equal to the deployer's address. 

#### Revert
This statement is similar to the require statement. It does not evaluate any condition and does not depends on any state or statement. It is used to generate exceptions, display errors, and revert the function calls.
Calling a revert statement implies an exception is thrown, the unused gas is returned and the state reverts to its original state. Revert is used to handle the same exception types as require handles, but with little bit more complex logic.
revert takes an optional argument of string type.

```solidity
function checker(uint x) public pure returns(bool y){
    if(x>=10){
        revert("value exceeded");
    }
    else{
        return true;
    }
}
```
 
 **Custom Errors and try-catch**        
#### Try Catch in Solidity
In a try catch statement, the try block will execute some code. If it gets any errors, the caught statement will be executed. A failure in an external call can be caught using a try/catch statement.
A external call is a function calling from one contract to another contract. 
An example of an external call.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract A {
    function add(uint x, uint y) public returns (uint sum) {
        sum = x + y;
    }
}

contract B {
    A object_of_a; // this is an object of contract A
    uint public answer = 0;

    function setContract(A addr) public {
        // we need to pass the address of deployed a contract
        object_of_a = addr;
    }

    function callAdd() public {
        answer = object_of_a.add(12, 3);
    }
}
```
In the above code we are creating the object of contract `A` by its address(deployed address of A). Then we are calling the function `add` from contract `B`. This is called as "external call". 

An example of try catch block is shown below. The try keyword has to be followed by an expression representing an external function call or a contract creation (new ContractName()). Solidity supports different kinds of catch blocks depending on the type of errors.
one try block can have multiple catch blocks. Different catch blocks are explained in single comments in the below please go through it for better understanding. We can just use catch { … } if we are not interested in error data.

```solidity
interface DataFeed { function getData(address token) external returns (uint value); }

contract FeedConsumer {
    DataFeed feed;
    uint errorCount;
    function rate(address token) public returns (uint value, bool success) {
        // Permanently disable the mechanism if there are
        // more than 10 errors.
        require(errorCount < 10);
        try feed.getData(token) returns (uint v) {
            return (v, true);
        } catch Error(string memory /*reason*/) {
            // This is executed in case revert was called inside getData and a reason string was provided.
            errorCount++;
            return (0, false);
        } catch Panic(uint /*errorCode*/) {
            // This is executed in case of a panic,
            // i.e. a serious error like division by zero
            // or overflow. The error code can be used
            // to determine the kind of error.
            errorCount++;
            return (0, false);
        } catch (bytes memory /*lowLevelData*/) {
            // This is executed in case revert() was used.
            errorCount++;
            return (0, false);
        }
    }
}
```

#### Custom Errors
Creating custom errors in your code can actually help you conserve gas usage. How? Well, normal errors come with pre-written, lengthy error messages that can really guzzle up a lot of gas. However, when you create a 
custom error using the `error` keyword, you can specify the message yourself. These custom errors can be called using a conditional and revert statement.

An example of an custom error is shown below.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.5;

contract CustomError {
    error Logic(string message);

    function testCustom_error(uint x) public pure {
        if (x > 10) {
            revert Logic("the value exceeded 10");
        }
    }
}

```
By using the keyword `error`, we have defined a custom error name called `Logic`. If the value of x exceeds 10, the transaction will be reverted and our custom error message will be shown. 
The values that need to be logged at the time of an error should be specified/defined in the argument of our custom error.
 
 
