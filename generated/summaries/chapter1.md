## Header
This is the course header. This will be added on top of every page. Do to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Your First Solidity Smart Contract
 
 **Installing Solidity Compiler**        
- Versoning 
  * Solidity versions follow 'Semantic Versioning' which is essential to avoid 'dependency hell' while programming in Solidity.
    'Dependency hell' in software management occurs when version specifications are made too tight or too loose due to which releasing new versions becomes a nightmare as it becomes difficult to resolve conflicts. To avoid this solidity 
    releases its versions with version number MAJOR.MINOR.PATCH .eg Solidity compiler version 0.8.15 indicates major release 0 with 8th minor release and 15th patch fix.
  * Patch level releases with major release 0 (i.e. 0.x.y) does not contain breaking changes. That means code that compiles with version 0.x.y can be expected to compile with 0.x.z where z > y.
- Remix IDE is part of the Remix Project which can be used for the development of small contracts and for quickly learning Solidity. [Access Remix Online](https://remix.ethereum.org) .
- npm/Node.js
 * npm can be used for a convenient and portable way to install solcjs, a Solidity compiler. 
  #TODO - elaborate on solcjs , installation , use
 
 **Layout of a Source File**        
- SPDX License Identifier
  * Trust in smart contracts is better established if their source code is available and open source. Since making it available always touches on legal problems with regards to copyright, the Solidity compiler encourages the use of machine-readable SPDX license identifiers.
  * Every solidity source file should start with a comment indicating its license. eg. `// SPDX-License-Identifier: MIT` .
  * The Software Package Data Exchange (SPDX) is an open standard used for communicating licenses , copyrights and security references.
  #TODO bytecode-metadata
- Pragmas
  * pragma is a directive used to configure compiler features and checks.
  * A pragma directive is always local to a source file, so you have to add the pragma to all your files if you want to enable it in your whole project.
  * If you import another file, the pragma from that file does not automatically apply to the importing file.
  * A Version pragma is a directive that specifies the compiler version to be used for current Solidity file.
  * For example, `pragma solidity ^0.4.0;`,  the pragma for a file using the above statement will not compile earlier than version 0.4.0 and it will also not work on a compiler starting from version 0.5.0, this condition is taken care off by ^. 
  * Another example is, `pragma solidity >=0.6.0 <0.8.0;` where the pragma directive instructs the compiler to compile code for Solidity version greater than equal to 0.6.0 till up to but not including 0.8.0.
  * #TODO - ABI encoder pragma
- Single-line comments (//) and multi-line comments (/*...*/) are possible.
    ```
    // This is a single-line comment.

    /*
    This is a
    multi-line comment.
    */
    ```
- Imports
  * Solidity supports import statements to modularise code similar to those available in JavaScript (from ES6 on).
  * At a global level, you can use import statements of the following form: `import "filename";`. This statement imports all global symbols from “filename” into the current global scope. This form is not recommended for use, because it unpredictably pollutes the namespace. If you add new top-level items inside “filename”, they automatically appear in all files that import like this from “filename”. 
  * The following example creates a new global symbol symbolName whose members are all the global symbols from "filename": `import * as symbolName from "filename";`
    which results in all global symbols being available in the format symbolName.symbol.
  * If there is a naming collision, you can rename symbols while importing. `import {symbol1 as alias, symbol2} from "filename";`. 
 
 **Structure of a Smart Contract**        
Contracts in Solidity are similar to classes in object-oriented languages. 
Each contract can contain declarations of State Variables, Functions, Function Modifiers, Events, Errors, Struct Types and Enum Types.

- State Variables
  * State variables are variables whose values are permanently stored in contract storage.
  * In the following code snippet `storedData` is an example of a state variable.
  ```
  // SPDX-License-Identifier: GPL-3.0
  pragma solidity >=0.4.0 <0.9.0;

  contract SimpleStorage {
      uint storedData; // State variable
      // ...
  }
  ```
  * 

- Functions 
  * Functions are the executable units of code. 
    Functions are usually defined inside a contract, but they can also be defined outside of contracts.
  * In the code below helper function is defined outside the contract whearas arithmetic function is declared inside the contract.
    ```
    // SPDX-License-Identifier: GPL-3.0
    pragma solidity >=0.7.1 <0.9.0;

    contract Simple {
        function arithmetic(uint a, uint b)
            public
            pure
            returns (uint sum, uint product)
        {
            return (a + b, a * b);
        }
    }

    // Helper function defined outside of a contract
    function helper(uint x) pure returns (uint) {
        return x * 2;
    }
    ```
  * Functions outside of a contract are also called 'free function' and their code is included in all contracts that call them.
  * The main difference to functions defined inside a contract is that free functions do not have direct access to storage variables and functions not in their scope.
  * Functions take typed parameters as input and can also return an arbitrary number of values as output.
  * In the code snippet above , the contract `Simple` has a function arithmetic which takes two input parameters `uint a` and `uint b`.
  * The function arithmetic also returns two values `uint sum` and `uint product`.
  * the return values in a function can also be explicitly assigned to return variables instead of a return statememnt like in the code below.
    ```
    function arithmetic(uint a, uint b)
        public
        pure
        returns (uint sum, uint product)
    {
        sum = a + b;
        product = a * b;
    }
    ```
  * Functions can be declared view in which case they promise not to modify the state, they can also be declared pure in which case they promise not to read from or modify the state.
    ```
    contract ViewAndPure {
        uint public x = 1;

        // Promise not to modify the state.
        function addToX(uint y) public view returns (uint) {
            return x + y;
        }

        // Promise not to modify or read from the state.
        function add(uint i, uint j) public pure returns (uint) {
            return i + j;
        }
    }
    ```
    The above view function `addToX` can read the state variable x but cannot update its state whearas the pure function `add` can neither read nor update the state.
  # TODO: fallback function.

- Events
  * Events are inheritable members of contracts. When you call them, they cause the arguments to be stored in the transactions log - a special data structure in the blockchain.
  * Events are defined within the contracts as global and called within their functions. Events are declared by using the event keyword as follows , `event <eventName>(parameters) ;`.
  * The example below shows the declaration of an event and its use in its function. In this example, the Deposit event is emitted when a user sends Ether to the smart contract with the deposit function.

   ```
    event Deposit(
    address indexed from,
    bytes32 indexed id,
    uint value
    );

    function deposit(bytes32 id) public payable {
        emit Deposit(msg.sender, id, msg.value);
    }
  ```
  * Events are ways to communicate with a client application or front-end website that something has happened on the blockchain. The above event Deposit can be detected from
    the JavaScript API by filtering for `Deposit`.
  #TODO: indexed keyword

- Function Modifiers
  * Function modifiers can be used to change the behaviour of functions in a declarative way.
  * A modifier can be used automatically to check a condition prior to execution of the function.
  * In the code snippet below constructor sets the creator of the contract to the owner variable . The `onlyOwner` modifier checks that the caller of the function is the owner. 
    the function `setName` uses the modifier `onlyOwner`. If the caller of the function is not the owner then the function does not execute.
    ```
    pragma solidity ^0.7.0;
    contract C {
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
    }
    ```

  * “_;” is a special code only used in the function modifier. It instructs solidity to run the code in the function. It' indicates where “the rest” of the function code should go by merging the function source with the modifier code.
  * "_;" can be used to execute the function modifier and then the function or execute the function and then the function modifier by placing "_;" before or after the modifier code;
 
 **Error Handling**        
Solidity has many functions for error handling. Errors can occur at compile time or runtime.
Solidity is compiled to byte code and there a syntax error check happens at compile-time, while runtime errors occur mainly while executing the contracts. Some of the runtime errors are out-of-gas error, data type overflow error, divide by zero error, array-out-of-index error, etc.
Error handling in solidity is done using revert, require, assert and try/catch to undoes all changes made to the state in the current call.
Currently, Solidity supports two error signatures: Error(string) and Panic(uint256). Error(string) is used for regular error conditions while Panic(uint256) is used for errors that should not be present in bug-free code.
- Panic via assert
  * 
  
 
 
