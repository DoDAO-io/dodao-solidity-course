## Header
This is the course header. This will be added on top of every page. Do to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Your First Solidity Smart Contract
 
 **Structure of a smartcontract**        
The source code of a solidity contract begins with a license identifier to avoid any potential legal issues that could arise if the code is published as open source. The compiler version is specified using the keyword 
`pragma` and can be placed anywhere within the contract, though it is generally considered best practice to specify it at the top of the document. For single-line comments, we need to use `//`. For multiline comments, we need to use `/*comments here */`. 
Solidity comments can also be written in `NatSpec` format. Developers use it for documenting return variables, functions, and so on. To define a single-line comment in this format, we need to use `///` for multiline, we need to use `/** comments here */`. 
`import` keyword is used for importing files from other resources

Solidity has a special kind of function called a `constructor` function. This function will be called automatically when you deploy your contract. You can define a constructor function using the keyword 'constructor' followed by the function's code.

```solidity
//SPDX-License-Identifier:MIT 
pragma solidity ^0.8.2; // compiler version is specified using the keyword pragma

import "priceconverter.sol"; // this is normal importing
import "priceconverter.sol" as pc; // if you want to import one file but with different name
import { price1 as p1, price2 } from "storagefactory.sol"; // If we want to import only specific variables or functions from a file

contract SolidityStructure {
    address public owner;

    constructor() {
        owner = msg.sender;
    }
    // this is a single line comment

    /* this is a 
        multi line comment */

    /* msg.sender is the address that has called or initiated a function or created a transaction. 
            But at the time of deployment it will be the address of the deployer of the contract */

    /// This is NatSpec single line comment

    /**
    This is NatSpec multi line comment
    */
}

```
In the above snippet, the constructor function will only be called once when the contract is deployed. This function will assign the deployer address to the `owner`. `msg.sender` is the address that has called or 
initiated a function or created a transaction. But at the time of deployment it will be the address of the deployer of the contract.
 
 **Statevariables and Functions**        

State variables are variables that are stored permanently on the blockchain. They can be declared as `constant` and `immutable`, but immutable can be redeclared in the constructor. Constant and immutable variables reduce the gas cost.
Functions in solidity are essentially just like any other programming language - they are pieces of code that can be executed by simply calling the function. Functions can be declared inside or outside of a contract. 
The functions which are declared outside of the contract are referred to as free functions. Free functions don't have access to variables that are inside the contract and they also don't have visibility. 
This means that we cannot add `public` and `external` keywords.

`fallback` and `recieve` are special functions. The `fallback` will be executed if:
1. None of the other functions match the function identifier 
2. If ether is transferred to the contract with some call data

If ether is sent to a contract without any call data, the receive function will be executed. If receive is not defined, fallback will be executed. The `fallback` and `receive` functions must be defined with the `payable` keyword and visibility. 
There are two keywords which can restrict the state mutability of a function: `view` and `pure`. `view`will restrict the function to read-only but if `pure` is defined, that function will not be able to read or write.


```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.5;

contract SimpleProgram {
    uint public value = 23;
    uint public answer = add(value, 1); // calling the free function add
    address immutable owner;

    constructor() {
        owner = msg.sender; // redelcaring the immutable variable
    }

    uint public product = multiply(value, 2); // calling the function multiply

    function multiply(uint a, uint b) public pure returns (uint) { // function inside the contract with pure keyword
        return a * b;
    } 
    // Data types of arguments and returning values should be defined for a function

    receive() external payable { // recieve function declaration
        setValue(24);
    }

    function setValue(uint x) internal {
        value = x;
    }

    function check_value() public view returns (uint) {
        // view keyword restrict the function check_a to read only
        return value;
    }

    fallback() external payable { // fallback function declaration
        setValue(12);
    }


}

function add(uint a, uint b) pure returns (uint sum) {    // free function
    sum = a + b;
}

```
 
 **Events and Function modifiers**        
Events are a way of logging data in the blockchain. They are declared using the keyword `event` and logged using the keyword `emit`. Once they are logged, they can be viewed in etherscan if the smart contract has been deployed in 
Ethereum or one of its testnets. Function modifiers are a declarative way of changing the behavior of functions. The modifier is declared using the keyword `modifier`. Function modifiers are added as a keyword to the functions. 
They are used to check a condition before the function is executed.
Syntax for declaring the modifier:
```solidity
modifier Identifier {
    //code comes here
}
```
The below snippet shows how to use events and function modifiers. whenever function `setValue` executes the event is logged as `emit Log(x,msg.sender)` defines emitting of the event with the message value and the senders address.
The `_;`is a special keyword inside the modifier which tells the compiler to execute the parent function i.e, in this case `setValue` function. 

```solidity
//SPDX-License-Identifier:MIT
pragma solidity ^0.8.0;

contract FunctionModifiers {
    address public immutable owner;
    uint public favourite_number = 7;
    event Log(uint , address );// declaration of the event
    // Identifiers for event's arguments is not mandatory
    constructor() {
        owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "not owner");// declaration of the modifier
        _; // this will tell the compiler to execute the parent function
    }

    function setValue(uint x) public onlyOwner returns (uint v) { // adding modifier to the function
        favourite_number = x;
        emit Log(x,msg.sender); // event is logged using the emit keyword
        v = x;
    }
}

```
 
 **Error Handling**        
Solidity uses state-reverting exceptions to handle errors. Such an exception reverts all changes made to the state in the current call (and all its sub-calls) and flags an error to the caller. Solidity has many functions for error handling. 
Compile time or runtime errors can occur. Error handling can be done using assert, require, revert, try-catch and custom errors.

 #### Assert 
 The `assert` function creates an error of type `Panic(uint256)` when used. It is primarily employed to check for internal errors and conditions that must always evaluate to be true. If the condition in the assert statement fails, 
 it implies that there is a bug in the smart contract. The assert function takes one required parameter, which is the condition, and an optional parameter of the type string.
 
 #### Require
 The `require` function is used to test for errors that usually occur, whereas the assert function is used to test for errors that should never happen. The require function takes one required parameter, which is a condition, 
 and an optional string parameter.

 require exception is triggered for the following cases:
 * Calling require(x) where x evaluates to false.
 * If you perform an external function call targeting a contract that contains no code.
 * If you use revert() or revert("description").
 * If your contract receives Ether via a public function without payable modifier.
 * If your contract receives Ether via a public getter function.

 #### Revert
 Revert is a function that is similar to require but does not evaluate any conditions. It is used to generate exceptions, display errors, and revert the function calls. Calling a revert statement implies an exception is thrown, 
 the unused gas is returned, and the state reverts to its original state.

 The below code snippet explains how to use assert, revert and require.    
 
 ```solidity
 contract Errors{
   address immutable public owner;
   constructor(){
       owner = msg.sender;
   }
   function foo(uint x)public view{
       assert(msg.sender!= owner); // if caller of the function is not the owner exception is thrown 
       require(x==1,"the value 0 is not supported");// if the parameter equals one require exception is thrown and state is reverted
       if(x>100){
           revert("the value exceeded");// state is reverted of the value of x exceed 100
       }

   }

 }
 ```
 
 **Custom Errors and try-catch**        
In a `try-catch` statement, the try block will execute some code. If it gets any errors, the caught statement will be executed. A failure in an external call can be caught using a try/catch statement.
The `try` keyword has to be followed by an expression representing an external function call or a contract creation (`new ContractName()`). One try block can have many catch blocks.
Custom errors help to reduce gas costs as the error message can be customized. They are defined using the keyword `error`. `try-catch` must be defined inside a function.

In the below snippet we are defining a try-catch block for an external call. If the try block executes sucessfully the `getOwner` variable will be assugned a value which will be equal to the address of the account from which the contract
`External contract` is deployed. If there is an error catch blocks will be executed. The custom error is defined as `Logic` in the below snippet. Custom error is thrown when the input/argument of the function `testCustom_error` is greater than 10. 

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.5;

contract Errors{
    ExternalContract object;
    error Logic(string message);// defining the custom error
    address public getOwner;
    function setupOject(ExternalContract addr) public{ // creating the object of the external contract
        object = addr;
    }
  
    function callExternalContract() public returns(string memory returnmessage){ 
        // data location must be specified for data types like arrays, structs and strings if it is passed as an argument to a function
        try object.viewAdress() returns(address addressOwner){ // making external call using try catch
            getOwner= addressOwner;
            return string("sucess");
        }catch Error(string memory message){ 
            return message;
        }catch Panic(uint){
            return "panic-error";
        }

    }
    
    function testCustom_error(uint x) public pure {
        if (x > 10) {
            revert Logic("the value exceeded 10");// state is reverted with the custom error Logic
        }
    }


}

contract ExternalContract{ // this is our external
    address public immutable owner;
    constructor(){
        owner = msg.sender;
    }
    function viewAdress() public view returns(address){
        return owner;
    }

}

```
 
 
