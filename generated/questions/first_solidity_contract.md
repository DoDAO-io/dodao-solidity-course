## Header
This is the course header. This will be added on top of every page. Do to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Your First Solidity Smart Contract
 
 
---

##### Which of the following is a valid pragma verion declaration in Solidity?  

- [x]  `pragma solidity 0.6.12;`
- [x]  `pragma solidity ^0.6.12;`
- [x]  `pragma solidity >=0.4.0 <0.6.0;`
- [ ]  `pragma solidity -0.5.2;`
  
Hint: noHint
         
Explanation: pragma solidity 0.6.12  - Only compiles with version 0.6.12
pragma solidity ^0.6.12 - Compiles with version 0.6.12 and above
pragma solidity >=0.4.0 <0.6.0 - Compiles with all versions between 0.4.0 and 0.6.0.


Sub Topics: smart-contract
 

---

##### A Solidity Contract file has a pragma versioning `pragma solidity ^0.5.2;`. With which of the following compilers will the contract run?  

- [ ]  Compiler version 0.5.1
- [ ]  Compiler version 0.4.1
- [x]  Compiler version 0.5.5
- [ ]  Compiler version 0.6.1
  
Hint: Think of what condition is applicable with `^` symbol in solidity versioning.
         
Explanation: A source file with the line above does not compile with a compiler earlier than version 0.5.2, and it also does not work on a compiler starting from version 0.6.0 (this second condition is added by using ^).

Sub Topics: smart-contract
 

---

##### Which of the following statements is incorrect regarding pragmas in solidity?  

- [x]  In Solidity `pragma` keyword is only used to specify the version of the compiler the code should compile with.
- [ ]  The `pragma` keyword is used to enable certain compiler features or checks.
- [ ]  The following code will only compile with compiler version 0.6.12, `pragma solidity 0.6.12;`.
- [x]  If you import another file, the pragma from that file will automatically apply to the importing file.
  
Hint: ABI coder pragma can be used to select between the two implementations of the ABI encoder and decoder and experimental pragma can be used to enable features of the compiler or language that are not yet enabled by default.
         
Explanation: The pragma keyword is used to enable certain compiler features or checks. A pragma directive is always local to a source file, so you have to add the pragma to all your files if you want to enable it in your whole project. If you import another file, the pragma from that file does not automatically apply to the importing file.
By using pragma abicoder v1 or pragma abicoder v2 you can select between the two implementations of the ABI encoder and decoder. It can be used to enable features of the compiler or language that are not yet enabled by default. The following experimental pragmas are currently supported: ABIEncoderV2 , SMTChecker.


Sub Topics: smart-contract
 

---

##### Which of the following pragma declarations is incorrect?  

- [ ]  pragma experimental SMTChecker;
- [ ]  pragma abicoder v1;
- [ ]  pragma solidity ^0.5.2;
- [x]  pragma version 0.6.2;
  
Hint: noHint
         
Explanation: By using pragma abicoder v1 or pragma abicoder v2 you can select between the two implementations of the ABI encoder and decoder.
If you use pragma experimental SMTChecker;, then you get additional safety warnings which are obtained by querying an SMT solver.


Sub Topics: smart-contract
 

---

##### If you want to import a file in your solidity code which of the following will be a correct but inefficient way to do so?  

- [ ]  import * as symbolName from "filename";
- [ ]  import "filename" as symbolName;
- [ ]  import {symbol1 as alias, symbol2} from "filename";
- [x]  import "filename";
  
Hint: All import statements are correct.
         
Explanation: The statement `import "filename";` imports all global symbols from “filename” into the current global scope. This form is not recommended for use, because it unpredictably pollutes the namespace. If you add new top-level items inside “filename”, they automatically appear in all files that import like this from “filename”. It is better to import specific symbols explicitly.

Sub Topics: smart-contract
 

---

##### Which of the following statements regarding solidity files is correct?
Statement 1 - It is a better practice to modularize code by writing contracts in different source files and using imports.
Statement 2 - The export declaration is used to export functions from a Contract.
  

- [x]  Statement 1 is true but Statement 2 is false.
- [ ]  Statement 2 is true but Statement 1 is false.
- [ ]  Both are true.
- [ ]  Neither is true.
  
Hint: noHint
         
Explanation: Solidity supports import statements to help modularise your code that are similar to those available in JavaScript (from ES6 on). 
However, Solidity does not support the concept of a default export.


Sub Topics: smart-contract
 

---

##### Which of the following comments is invalid in a Solidity Code?  

- [x]  /This is a single line comment.
- [ ]  //This is a single line comment.
- [ ]  ///This is a single line comment.
- [x]  /*This is a single line comment.
  
Hint: noHint
         
Explanation: Single-line comments (//) and multi-line comments (/*...*/) are possible in Solidity. 
Additionally, there is another type of comment called a NatSpec comment, they are written with a triple slash (///) or a double asterisk block (/** ... */) and they should be used directly above function declarations or statements.


Sub Topics: smart-contract
 

---

##### In the context of NatSpec comments which of the following is true?  

- [x]  NatSpec stands for Ethereum Natural Language Specification Format.
- [ ]  NatSpec comments provide tags and in case if no tags are used , the solidity compiler will interpret (///) as (//).
- [x]  The Solidity compiler only interprets tags if they are external or public.
- [ ]  Comments in solidity can only be made using (//) for Single-line and (/*...*/) for multi-line.
  
Hint: Solidity supports NatSpec comments in addition to the simple single/multi line comments.
         
Explanation: NatSpec stands for Ethereum Natural Language Specification Format.
If no tags are used then the Solidity compiler will interpret a /// or /** comment in the same way as if it were tagged with @notice.
The Solidity compiler only interprets tags if they are external or public. You can use similar comments for internal and private functions, but those will not be parsed.


Sub Topics: smart-contract
 

---

##### What does the basic structure of a contract contain?  

- [ ]  Pragma directive
- [ ]  Name of the contract
- [ ]  Data and functions
- [x]  All of the above
  
Hint: noHint
         
Explanation: Each contract can contain declarations of State Variables, Functions, Function Modifiers, Events, Errors, Struct Types and Enum Types.


Sub Topics: smart-contract
 

---

##### What does a simple function definition in Solidity contain?  

- [ ]  Modifier definitions
- [ ]  Fallback definition
- [x]  Function header and code
- [ ]  Event
  
Hint: noHint
         
Explanation: The basic syntax is shown here.
```
  function function-name(parameter-list) scope returns() {
    //statements
  }
```


Sub Topics: state-variables-and-functions
 

---

##### Regarding constructors in solidity which statement is correct?  

- [ ]  Constructor overloading is supported.
- [x]  A constructor is optional.
- [ ]  The contract deployed on the blockchain will also contain the constructor code.
- [ ]  None of these
  
Hint: Only one constructor is allowed.
         
Explanation: A constructor is optional. Only one constructor is allowed, which means overloading is not supported.
After the constructor has executed, the final code of the contract is stored on the blockchain. 
The deployed code does not include the constructor code or internal functions only called from the constructor.


Sub Topics: state-variables-and-functions
 

---

##### Which of the options regarding the statements below are correct?
Statement 1 - A contract in the sense of Solidity is a collection of code (its functions) and data (its state) that resides at a specific address on the Ethereum blockchain.
Statement 2 - Contracts in Solidity are similar to classes in object-oriented languages.
  

- [ ]  Statement 1 is correct but Statement 2 is incorrect.
- [ ]  Statement 2 is correct but Statement 1 is incorrect.
- [x]  Both are correct.
- [ ]  Neither is correct.
  
Hint: noHint
         
Explanation: Contracts in Solidity are similar to classes in object-oriented languages. They contain persistent data in state variables, and functions that can modify these variables.


Sub Topics: smart-contract
 

---

##### Which of the following options are correct based on the code snippet below?
```
contract OriginCoordinates {
    uint constant x_coordinate;
    uint immutable y_coordinate;

    constructor(){
        x_coordinate=0;
        y_coordinate=0;
    }


    function get() public view returns (uint,uint) {
        return (x_coordinate,y_coordinate);
    }
}
```
  

- [ ]  This code will not compile as solidity functions cannot have multipe return values.
- [ ]  This code will not compile because State Variables declared immutable cannot be initialised in a constructor.
- [x]  This code will not compile because State Variables declared constant cannot be initialised in a constructor.
- [ ]  The code has no errors and can be deployed.
  
Hint: Check the declaration of the state variables.
         
Explanation: The state variable x_coordinate cannot be initialized in the constructor as it is declared as constant.
For constant variables, the value has to be fixed at compile-time, while for immutable, it can still be assigned at construction time.


Sub Topics: state-variables-and-functions
 

---

##### Which of the following statements is correct regarding functions?  

- [x]  Functions outside of a contract are also called 'free functions'.
- [ ]  Functions declared as view can modify the state variables.
- [x]  In Solidity the function is simply invoked by writing the name of the function where it has to be called.
- [x]  Functions can have multiple return values.
  
Hint: noHint
         
Explanation: Functions can be declared view in which case they promise not to modify the state, they can also be declared pure in which case they promise not to read from or modify the state.


Sub Topics: state-variables-and-functions
 

---

##### Which of the following options is correct regarding "free functions"?  

- [ ]  Free functions in solidity are functions declared inside a contract with public Visibility.
- [x]  Their code is included in all contracts that call them.
- [ ]  They can access state variables and internal functions directly.
- [x]  A free function behaves like an internal function of the contract that called it.
  
Hint: Free functions in Solidity are functions created outside of the scope of a contract.
         
Explanation: A free function behaves like an internal function of the contract that called it. 
The main difference is that a free function cannot directly access state variables and internal functions of contracts.


Sub Topics: state-variables-and-functions
 

---

##### What does the following syntax do? 
`import * as symbolName from "filename";`
  

- [ ]  This statement imports all global symbols from “filename” into the current global scope.
- [x]  This statement creates a new global symbol symbolName whose members are all the global symbols from "filename".
- [ ]  This statement imports symbolName member from "filename".
- [ ]  None of these.
  
Hint: noHint
         
Explanation: The following example creates a new global symbol symbolName whose members are all the global symbols from "filename":
`import * as symbolName from "filename";` which results in all global symbols being available in the format symbolName.symbol.


Sub Topics: smart-contract
 

---

##### In which scenarios is a fallback function triggered?  

- [ ]  Contract received ether and no data.
- [ ]  Contract received data but no function matched the function called.
- [ ]  Contract sent insufficient gas.
- [x]  Both A & B
  
Hint: noHint
         
Explanation: A fallback function is called in two cases- A contract receives only Ether and no data,
or when no function calls matched even though the account received data.


Sub Topics: state-variables-and-functions
 

---

##### What happens when an event is called?  

- [ ]  When called, events flag an error to the caller.
- [ ]  They provide a condition under which event a function calling the event should be executed.
- [x]  They cause the arguments to be stored in the transactions log - a special data structure in the blockchain.
- [ ]  None of these.
  
Hint: noHint
         
Explanation: Events are inheritable members of contracts. When you call them, they cause the arguments to be stored in the transactions log - a special data structure in the blockchain.

Sub Topics: events-modifiers
 

---

##### What are events used for?  

- [x]  Events can be used to communicate with external users about a transaction that happened on the blockchain.
- [ ]  They are used for error handling.
- [x]  They can be used to inform a user of any action that happened on the blockchain and can thus ease the development of outside systems in cooperation with smart contracts.
- [ ]  None of these.
  
Hint: When called, events cause the arguments to be stored in the transactions log - a special data structure in the blockchain.
         
Explanation: Events are used to inform external users that something happened on the blockchain. Smart contracts themselves cannot listen to any events.
All information in the blockchain is public and any actions can be found by looking into the transactions close enough but events are a shortcut to ease the development of outside systems in cooperation with smart contracts.


Sub Topics: events-modifiers
 

---

##### In the following snippet, what is the purpose of the code?
```
address owner;
string private name;
constructor() {
  owner = msg.sender;
}
modifier onlyOwner() {
  require(msg.sender == owner, 'Not Owner');
  _;
}
function setName(string memory newName) public onlyOwner{
  name = newName;
}
```
  

- [x]  Upon contract creation, the owner address is initialized to the user who deployed the contract.
- [x]  The function setName can only be called by the owner of the contract.
- [ ]  onlyOwner is a function which will throw an error each time it is called by a non-owner.
- [x]  onlyOwner can be used to modify the behaviour of a function.
  
Hint: Function modifiers can be used to change the behaviour of functions in a declarative way.
         
Explanation: In the code, constructor sets the creator of the contract to the owner variable . The `onlyOwner` modifier checks that the caller of the function is the owner. the function `setName` uses the modifier `onlyOwner`. If the caller of the function is not the owner then the function does not execute.

Sub Topics: smart-contract
 

---

##### Which of the following can be used to restrict access of a function?  

- [ ]  function
- [x]  function modifier
- [ ]  event
- [ ]  constructor
  
Hint: noHint
         
Explanation: Modifiers assist in the execution of a functions behavior. They can be used to restrict access of a function.


Sub Topics: events-modifiers
 

---

##### Where is `_;` instruction used in Solidity?  

- [ ]  It is used in a function.
- [ ]  It is used in aconstructor.
- [x]  It is used in a modifier.
- [ ]  It can be used anywhere at the file level.
  
Hint: noHint
         
Explanation: In Solidity, `_;` is used inside a modifier to specify when the function should be executed.

Sub Topics: events-modifiers
 

---

##### What is the returned value when `set` is called first then `get`.
```
contract UnderScore {
    uint a;
    constructor(){
        a=10;
    }
    modifier m(){
      _;
      if(a<=15){
          a=a+10;
      }
    }
    function set() public m {
        a=a+10;
    }
    function get() public view returns (uint) {
        return a;
    }
}
```
  

- [ ]  10
- [ ]  15
- [x]  20
- [ ]  30
  
Hint: Notice how the function set will execute because of the modifier m.
         
Explanation: In Solidity, `_;` is used inside a modifier to specify when the function should be executed. As the modifier has `_;` before the modifier statements, so the function code will execute first and then the modifier code. The function set will update the value of a to 20 and then the modifier code will check if the value is greater than 15 or not.

Sub Topics: events-modifiers
 

---

##### Which of the following is a correct declaration of a function?  

- [ ]  public function foo() view returns(){}
- [ ]  public view function foo() returns(){}
- [ ]  function foo() view returns() public{}
- [x]  function foo() public view returns(){}
  
Hint: noHint
         
Explanation: The basic syntax of a function is shown below.
```
  function function-name(parameter-list) scope returns() {
    //statements
  }
```


Sub Topics: state-variables-and-functions
 

---

##### Which of the following options are true regarding the statements below.  
Statement 1 - A constructor can be either public or internal.  
Statement 2 - A constructor code is executed once when a contract is created and it is used to initialize contract state.
  

- [ ]  Statement 1 is true but Statement 2 is false.
- [ ]  Statement 2 is true but Statement 1 is false.
- [x]  Both are true.
- [ ]  Neither is true.
  
Hint: noHint
         
Explanation: A constructor is an optional funtion and is used to initialize state variables of a contract.
It is executed once when a contract is created and it is used to initialize contract state.
A constructor can be either public or internal.


Sub Topics: smart-contract
 

---

##### Which of the following is true about function modifier `_;`?  

- [x]  Specified at the entry of a function and executed after the function ends.
- [x]  Specified at the entry to a function and executed before the function begins.
- [ ]  Specified at the exit of a function and executed after the function ends.
- [ ]  None of these.
  
Hint: noHint
         
Explanation: “_;” is a special code only used in the function modifier. It' indicates where “the rest” of the function code should go by merging the function source with the modifier code.
"_;" can be used to execute the function modifier and then the function or execute the function and then the function modifier by placing "_;" before or after the modifier code.


Sub Topics: events-modifiers
 

---

##### How many constructors can be there in a Solidity contract?  

- [x]  1
- [ ]  2
- [ ]  3
- [ ]  Many
  
Hint: noHint
         
Explanation: A contract can have only one constructor.

Sub Topics: smart-contract
 

---

##### Which of the following is true regarding `_;` used in function modifiers?  

- [x]  “_;” is a special code only used in the function modifier.
- [x]  It' indicates where “the rest” of the function code should go by merging the function source with the modifier code.
- [x]  Having `_;` more than once in a modifier is valid.
- [ ]  option 4
  
Hint: noHint
         
Explanation: “_;” is a special code only used in the function modifier. Having `_;` more than once in a modifier is valid.
It instructs solidity to run the code in the function. It' indicates where “the rest” of the function code should go by merging the function source with the modifier code.


Sub Topics: events-modifiers
 

---

##### What will be the value of a,b and c when function func() is called?
```
contract C {
    uint a;
    uint b;
    uint c;

    modifier modA() {
        a = a + 1;
        _;
    }

    modifier modB() {
        b = b + 1;
        _;
        b = b + 1;
        _;
    }

    function func() public modA modB {
        c = c + 1;
    }
}

```
  

- [ ]  0,0,0
- [x]  1,2,2
- [ ]  0,0,1
- [ ]  1,2,1
  
Hint: noHint
         
Explanation: The default value of uint is zero so when func() is called modA code will run first, the `_;` will be replaced by modifier's code and the `_;` in the modB modifier's is replaced by the func function's code. Therefore `a=1` , `b=2` and `c=2`.

Sub Topics: events-modifiers
 

---

##### Which of the following is true about modifiers?  

- [ ]  A function can have any number of modifiers.
- [ ]  Visibility modifiers for a function should come before custom access modifiers.
- [ ]  Modifiers can be without any parameters.
- [x]  All the above.
  
Hint: noHint
         
Explanation: A function can have any number of modifiers.
Visibility modifiers for a function should come before custom access modifiers.
Modifiers can be without any parameters.


Sub Topics: events-modifiers
 

---

##### Which of tshe following options is true regarding the below statemens?
Statement 1 - It is allowed to emit an event in function modifiers.
Statement 2 - A modifier can update a state variable when used with a function declared as view.
  

- [x]  Statement 1 is true but Statement 2 is false.
- [ ]  Statement 2 is true but Statement 1 is false.
- [ ]  Both are true.
- [ ]  Neither is true.
  
Hint: noHint
         
Explanation: A function declared as view can only read the state variables and not make updates to them , any modifiers attached to such function can also not make changes to the state of variables.

Sub Topics: events-modifiers
 

---

##### What does the indexed keyword do in events?  

- [ ]  All indexed arguments will be stored in the data part of the log.
- [x]  indexed keyword is used to log values as topics rather than data part of the log.
- [x]  The indexed keyword helps you to filter the logs to find the wanted data.
- [ ]  None of these.
  
Hint: noHint
         
Explanation: You can add the attribute indexed to up to three parameters which adds them to a special data structure known as “topics” instead of the data part of the log. The indexed keyword helps you to filter the logs to find the wanted data.
All non-indexed arguments will be stored in the data part of the log.


Sub Topics: events-modifiers
 

---

##### Which of the following scenarios will result in a runtime time errors?  

- [ ]  out-of-gas error
- [ ]  data type overflow error
- [ ]  divide by zero error
- [x]  All of these
  
Hint: noHint
         
Explanation: Some of the runtime errors are out-of-gas error, data type overflow error, divide by zero error, array-out-of-index error, etc.

Sub Topics: errors
 

---

##### Error handling and validations in Solidity can be done using which of the following?  

- [ ]  revert
- [ ]  require
- [ ]  assert
- [x]  All of these
  
Hint: noHint
         
Explanation: Error handling and validations in solidity is done using revert, require, assert and try/catch.

Sub Topics: errors
 

---

##### Which of the following scenarios will cause a Panic type exception to be generated?  

- [x]  If you call assert with an argument that evaluates to false.
- [x]  If an arithmetic operation results in underflow or overflow.
- [x]  If you divide or modulo by zero.
- [ ]  Calling require(x) where x evaluates to false.
  
Hint: noHint
         
Explanation: A Panic exception is generated in the following situations.
    * If you call assert with an argument that evaluates to false.
    * If an arithmetic operation results in underflow or overflow.
    * If you divide or modulo by zero.
  Calling require(x) where x evaluates to false will result in an Error exception.


Sub Topics: errors
 

---

##### Consider the statements below regarding Error(string) and Panic(uint256) type error signatures.
Statement 1 - Error(string) is used for regular error conditions while Panic(uint256) is used for errors that should not be present in bug-free code.
Statement 2 - Panic type exception occurs via require and Error via assert.
  

- [x]  Statement 1 is true but Statement 2 is false.
- [ ]  Statement 2 is true but Statement 1 is false.
- [ ]  Neither is true.
- [ ]  Both are true.
  
Hint: noHint
         
Explanation: Solidity supports two error signatures: Error(string) and Panic(uint256). Error(string) is used for regular error conditions while Panic(uint256) is used for errors that should not be present in bug-free code.
Panic is generated by calling assert with an argument showing false and error is generated by calling require with an argument showing false.


Sub Topics: errors
 

---

##### Which of the following scenarios will cause an Error type exception to be generated?  

- [ ]  Calling require(x) where x evaluates to false.
- [ ]  If you perform an external function call targeting a contract that contains no code.
- [ ]  If you use revert() or revert("description").
- [x]  All of these.
  
Hint: noHint
         
Explanation: An Error exception is generated by the compiler in the following cases-
  * Calling require(x) where x evaluates to false.
  * If you perform an external function call targeting a contract that contains no code.
  * If you use revert() or revert("description").


Sub Topics: errors
 

---

##### Which of the following options in correct regarding errors?  

- [x]  The two ways if (!condition) revert(...); and require(condition, ...); are equivalent.
- [x]  Using a custom error instance will usually be much cheaper than a revert.
- [x]  Using revert() causes a revert without any error data while revert("description") will create an Error(string) error.
- [ ]  None of these.
  
Hint: noHint
         
Explanation: Using revert() causes a revert without any error data while revert("description") will create an Error(string) error.
Using a custom error instance will usually be much cheaper than a string description, because you can use the name of the error to describe it, which is encoded in only four bytes.
The two ways if (!condition) revert(...); and require(condition, ...); are equivalent as long as the arguments to revert and require do not have side-effects, for example if they are just strings.


Sub Topics: errors
 

---

##### To check an integer overflow/underflow , which of the following function should be used?  

- [ ]  revert
- [x]  assert
- [ ]  require
- [ ]  None of these
  
Hint: noHint
         
Explanation: Assert should only be used to test for internal errors, and to check invariants. 
Properly functioning code should never create a Panic, not even on invalid external input.
In this case integer overflow/underflow is undesirable and will lead to a bug wich needs to be fixed.


Sub Topics: errors
 

---

##### Which of the following catch blocks is valid ?  

- [ ]  `catch Error(string memory reason) { ... }`
- [ ]  `catch Panic(uint errorCode) { ... }`
- [ ]  `catch (bytes memory lowLevelData) { ... }`
- [x]  All of these
  
Hint: noHint
         
Explanation: Solidity supports different kinds of catch blocks depending on the type of errors.
  * `catch Error(string memory reason) { ... }`, This catch clause is executed if the error was caused by `revert("reasonString")` or `require(false, "reasonString")`.
  * `catch Panic(uint errorCode) { ... }`, If the error was caused by a panic, i.e. by a failing assert, division by zero, invalid array access, arithmetic overflow and others, this catch clause will be run.
  * `catch (bytes memory lowLevelData) { ... }`, This clause is executed if the error signature does not match any other clause, if there was an error while decoding the error message, or if no error data was provided with the exception. The declared variable provides access to the low-level error data in that case.
  * We can just use catch { … } if we are not interested in error data.


Sub Topics: custom-errors-and-try-catch
 

---

##### Which of the following options is correct regarding the statements below,
Statement 1 - Solidity has special functions like the receive ether function and the fallback function.
Statement 2 - The declaration `receive() external payable { ... }` is not a valid function declaration.
  

- [x]  Statement 1 is true but Statement 2 is false.
- [ ]  Statement 2 is true but Statement 1 is false.
- [ ]  Both are true.
- [ ]  Neither is true.
  
Hint: noHint
         
Explanation: A Receive Ether Function is declared using `receive() external payable { ... }` (without the function keyword). 
This function cannot have arguments, cannot return anything and must have external visibility and payable state mutability. It can be virtual, can override and can have modifiers.


Sub Topics: state-variables-and-functions
 

---

##### Which of the following options is correct?  

- [ ]  It is not necessary for functions to be bound to a specific contract.
- [ ]  Free functions cannot have visibility.
- [ ]  Free functions are like internal functions.
- [x]  All of these.
  
Hint: noHint
         
Explanation: Functions can be defined at file-level. Such functions are called “free functions” (as opposed to functions bound to a specific contract).
Free functions are always internal functions and are meant to replace internal library functions and their very special behaviour.
A free function behaves like an internal function of the contract that called it. The main difference is that a free function cannot directly access state variables and internal functions of contracts.


Sub Topics: state-variables-and-functions
 

---

##### What effect does a "require" keyword have on an if/else statement when it's false?  

- [ ]  It goes to the next function.
- [ ]  It triggers the fallback function.
- [x]  It stops the contract and returns any unused gas.
- [ ]  None of these.
  
Hint: noHint
         
Explanation: `require` accepts a single argument and returns a boolean value after evaluation, it also has a custom string message option. If false then exception is raised and execution is terminated. The unused gas is returned back to the caller and the state is reversed to its original state.

Sub Topics: errors
 
