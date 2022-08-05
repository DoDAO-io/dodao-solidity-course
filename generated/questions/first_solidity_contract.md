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


Sub Topics: solidity-compiler
 

---

##### A Solidity Contract file has a pragma versioning `pragma solidity ^0.5.2;`. With which of the following compilers will the contract run?  

- [ ]  Compiler version 0.5.1
- [ ]  Compiler version 0.4.1
- [x]  Compiler version 0.5.5
- [ ]  Compiler version 0.6.1
  
Hint: Think of what condition is applicable with `^` symbol in solidity versioning.
         
Explanation: A source file with the line above does not compile with a compiler earlier than version 0.5.2, and it also does not work on a compiler starting from version 0.6.0 (this second condition is added by using ^).

Sub Topics: solidity-compiler
 

---

##### Which of the following statements is incorrect regarding pragmas in solidity?  

- [x]  In Solidity `pragma` keyword is only used to specify the version of the compiler the code should compile with.
- [ ]  The `pragma` keyword is used to enable certain compiler features or checks.
- [ ]  The following code will only compile with compiler version 0.6.12, `pragma solidity 0.6.12;`.
- [x]  If you import another file, the pragma from that file will automatically apply to the importing file.
  
Hint: ABI coder pragma can be used to select between the two implementations of the ABI encoder and decoder and experimental pragma can be used to enable features of the compiler or language that are not yet enabled by default.
         
Explanation: The pragma keyword is used to enable certain compiler features or checks. A pragma directive is always local to a source file, so you have to add the pragma to all your files if you want to enable it in your whole project. If you import another file, the pragma from that file does not automatically apply to the importing file.
By using pragma abicoder v1 or pragma abicoder v2 you can select between the two implementations of the ABI encoder and decoder. It can be used to enable features of the compiler or language that are not yet enabled by default. The following experimental pragmas are currently supported: ABIEncoderV2 , SMTChecker.


Sub Topics: file-layout
 

---

##### Which of the following pragma declarations is incorrect?  

- [ ]  pragma experimental SMTChecker;
- [ ]  pragma abicoder v1;
- [ ]  pragma solidity ^0.5.2;
- [x]  pragma version 0.6.2;
  
Hint: noHint
         
Explanation: By using pragma abicoder v1 or pragma abicoder v2 you can select between the two implementations of the ABI encoder and decoder.
If you use pragma experimental SMTChecker;, then you get additional safety warnings which are obtained by querying an SMT solver.


Sub Topics: file-layout
 

---

##### If you want to import a sile in your solidity code which of the following will be a correct but inefficient way to do so?  

- [ ]  import * as symbolName from "filename";
- [ ]  import "filename" as symbolName;
- [ ]  import {symbol1 as alias, symbol2} from "filename";
- [x]  import "filename";
  
Hint: All import statements are correct.
         
Explanation: The statement `import "filename";` imports all global symbols from “filename” into the current global scope. This form is not recommended for use, because it unpredictably pollutes the namespace. If you add new top-level items inside “filename”, they automatically appear in all files that import like this from “filename”. It is better to import specific symbols explicitly.

Sub Topics: file-layout
 

---

##### In the context of the following comment `// SPDX-License-Identifier: MIT` which of the following statements is incorrect?  

- [x]  This comment gets validated by the solidity compiler and then supplies the string in the bytecode metadata.
- [ ]  The comment is recognized by the compiler anywhere in the file at the file level.
- [x]  Only MIT liscense should be used to validate smart contracts.
- [ ]  If you do not want to specify a license or if the source code is not open-source, you can use the special value UNLICENSED.
  
Hint: noHint
         
Explanation: The compiler does not validate that the license is part of the list allowed by SPDX, but it does include the supplied string in the bytecode metadata.
The comment is recognized by the compiler anywhere in the file at the file level, but it is recommended to put it at the top of the file.
The liscense should be one from the the list given in the SPDX. 


Sub Topics: file-layout
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: file-layout
 

---

##### Which of the following comments is invalid in a Solidity Code?  

- [x]  /This is a single line comment.
- [ ]  //This is a single line comment.
- [ ]  ///This is a single line comment.
- [x]  /*This is a single line comment.
  
Hint: noHint
         
Explanation: Single-line comments (//) and multi-line comments (/*...*/) are possible in Solidity. 
Additionally, there is another type of comment called a NatSpec comment, they are written with a triple slash (///) or a double asterisk block (/** ... */) and they should be used directly above function declarations or statements.


Sub Topics: file-layout
 

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


Sub Topics: file-layout
 

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


Sub Topics: contract-structure
 

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


Sub Topics: contract-structure
 

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


Sub Topics: contract-structure
 

---

##### Which of the following statements is correct regarding functions ?  

- [x]  Functions outside of a contract are also called 'free functions'.
- [ ]  Functions declared as view can modify the state variables.
- [x]  In Solidity the function is simply invoked by writing the name of the function where it has to be called.
- [x]  Functions can have multiple return values.
  
Hint: noHint
         
Explanation: Functions can be declared view in which case they promise not to modify the state, they can also be declared pure in which case they promise not to read from or modify the state.


Sub Topics: contract-structure
 

---

##### Which of the following options is correct regarding "free functions"?  

- [ ]  Free functions in solidity are functions declared inside a contract with public Visibility.
- [x]  Their code is included in all contracts that call them.
- [ ]  They can access state variables and internal functions directly.
- [x]  A free function behaves like an internal function of the contract that called it.
  
Hint: Free functions in Solidity are functions created outside of the scope of a contract.
         
Explanation: A free function behaves like an internal function of the contract that called it. 
The main difference is that a free function cannot directly access state variables and internal functions of contracts.


Sub Topics: contract-structure
 

---

##### What does the following syntax do? 
`import * as symbolName from "filename";`
  

- [x]  This statement imports all global symbols from “filename” into the current global scope.
- [ ]  This statement creates a new global symbol symbolName whose members are all the global symbols from "filename".
- [ ]  This statement imports symbolName member from "filename".
- [ ]  None of these.
  
Hint: noHint
         
Explanation: The following example creates a new global symbol symbolName whose members are all the global symbols from "filename":
`import * as symbolName from "filename";` which results in all global symbols being available in the format symbolName.symbol.


Sub Topics: file-layout
 

---

##### In which scenarios is a fallback function triggered?  

- [ ]  Contract received ether and no data.
- [ ]  Contract received data but no function matched the function called.
- [ ]  Contract sent insufficient gas.
- [x]  Both A & B
  
Hint: noHint
         
Explanation: A fallback function is called in two cases- A contract receives only Ether and no data,
or when no function calls matched even though the account received data.


Sub Topics: contract-structure
 

---

##### Remix IDE is used for the development of small contracts. What does IDE stand for?  

- [ ]  Integrated Development Engine
- [x]  Integrated Development Environment
- [ ]  Integrated DApp Engin
- [ ]  Internet Development Environment
  
Hint: noHint
         
Explanation: Remix IDE is part of the Remix Project which can be used for the development of small contracts and for quickly learning Solidity. IDE stands for Integrated Development Environment.

Sub Topics: solidity-compiler
 

---

##### What happens when an event is called ?  

- [ ]  When called, events flag an error to the caller.
- [ ]  They provide a condition under which event a function calling the event should be executed.
- [x]  They cause the arguments to be stored in the transactions log - a special data structure in the blockchain.
- [ ]  None of these.
  
Hint: noHint
         
Explanation: Events are inheritable members of contracts. When you call them, they cause the arguments to be stored in the transactions log - a special data structure in the blockchain.

Sub Topics: contract-structure
 

---

##### What are events used for?  

- [x]  Events can be used to communicate with external users about a transaction that happened on the blockchain.
- [ ]  They are used for error handling.
- [x]  They can be used to inform a user of any action that happened on the blockchain and can thus ease the development of outside systems in cooperation with smart contracts.
- [ ]  None of these.
  
Hint: When called, events cause the arguments to be stored in the transactions log - a special data structure in the blockchain.
         
Explanation: Events are used to inform external users that something happened on the blockchain. Smart contracts themselves cannot listen to any events.
All information in the blockchain is public and any actions can be found by looking into the transactions close enough but events are a shortcut to ease the development of outside systems in cooperation with smart contracts. 


Sub Topics: contract-structure
 

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

Sub Topics: contract-structure
 

---

##### Which of the following can be used to restrict access of a function?  

- [ ]  function
- [x]  function modifier
- [ ]  event
- [ ]  constructor
  
Hint: noHint
         
Explanation: Modifiers assist in the execution of a functions behavior. They can be used to restrict access of a function.


Sub Topics: contract-structure
 

---

##### Where is `_;` instruction used in Solidity?  

- [ ]  It is used in a function.
- [ ]  It is used in aconstructor.
- [x]  It is used in a modifier.
- [ ]  It can be used anywhere at the file level.
  
Hint: noHint
         
Explanation: In Solidity, `_;` is used inside a modifier to specify when the function should be executed.

Sub Topics: contract-structure
 

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

Sub Topics: contract-structure
 

---

##### Which of the following is a correct declaration of a function ?  

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


Sub Topics: contract-structure
 

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


Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 

---

##### question  

- [x]  option 1
- [ ]  option 2
- [ ]  option 3
- [ ]  option 4
  
Hint: noHint
         
Explanation: explanation

Sub Topics: variables
 
