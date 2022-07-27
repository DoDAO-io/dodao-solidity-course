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
  * Use the command `npm install -g solc` , to install the Solidity compiler.
  * Using `solcjs --help` provides you with an explanation of all available options.
  * To compile a contract that imports other contracts via relative paths:      
    `solcjs --bin --include-path node_modules/ --base-path . MainContract.sol`
    Use the `--base-path` and `--include-path` options to describe the layout of your project. `--base-path` represents the root of your own source tree while `--include-path` allows you to specify extra locations containing external code (e.g. libraries installed with a package manager).
 
 **Layout of a Source File**        
- SPDX License Identifier
  * Trust in smart contracts is better established if their source code is available and open source. Since making it available always touches on legal problems with regards to copyright, the Solidity compiler encourages the use of machine-readable SPDX license identifiers.
  * Every solidity source file should start with a comment indicating its license. eg. `// SPDX-License-Identifier: MIT` .
  * The Software Package Data Exchange (SPDX) is an open standard used for communicating licenses , copyrights and security references.

- Pragmas
  * pragma is a directive used to configure compiler features and checks.
  * A pragma directive is always local to a source file, so you have to add the pragma to all your files if you want to enable it in your whole project.
  * If you import another file, the pragma from that file does not automatically apply to the importing file.
  * A Version pragma is a directive that specifies the compiler version to be used for current Solidity file.
  * For example, `pragma solidity ^0.4.0;`,  the pragma for a file using the above statement will not compile earlier than version 0.4.0 and it will also not work on a compiler starting from version 0.5.0, this condition is taken care off by ^. 
  * Another example is, `pragma solidity >=0.6.0 <0.8.0;` where the pragma directive instructs the compiler to compile code for Solidity version greater than equal to 0.6.0 till up to but not including 0.8.0.
  * #TODO - ABI encoder pragma
- Single-line comments (//) and multi-line comments (/*...*/) are possible. Any text after // or between /* and */ is ignored by the compiler.
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
  * State variables can be declared as `constant` or `immutable`. In both cases, the variables cannot be modified after the contract has been constructed.
  * For constant variables, the value has to be fixed at compile-time, while for immutable, it can still be assigned at construction time. Constant variables can also be declared at the file level.
  * Not all types for constants and immutables are implemented at this time. The only supported types are strings (only for constants) and value types.
  * The example below shows the use of constant and immutable state variables.
    ```
    // SPDX-License-Identifier: GPL-3.0
    pragma solidity >=0.7.4;

    uint constant X = 32**22 + 8;

    contract C {
        string constant TEXT = "abc";
        bytes32 constant MY_HASH = keccak256("abc");
        uint immutable decimals;
        uint immutable maxBalance;
        address immutable owner = msg.sender;

        constructor(uint decimals_, address ref) {
            decimals = decimals_;
            maxBalance = ref.balance;
        }
    }
    ```

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

- Constructors 
  * A constructor is an optional function declared with the constructor keyword which is executed upon contract creation, and where you can run contract initialisation code.
  * Before the constructor code is executed, state variables are initialised to their specified value if you initialise them inline, or their default value if you do not.
  * If there is no constructor, the contract will assume the default constructor, which is equivalent to constructor() {}.
  * The code snippet below explains the use of a constructor, 
    ```
      uint public x;
      uint public y;
      address public owner;
      uint public createdAt;
      Constructor (uint _x, uint _y) public {
                  x=_x;
                  y=_y;
                  owner = msg.sender;
                  createdAt = block.timestamp;
    ```
  * Constructors are very useful in Solidity , if you do not implement a function to change the state variable it will remain as long as the block chain is running. So using a constructor is a way to set a state variable that you do not want to change.

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
- Solidity uses state-reverting exceptions to handle errors. Such an exception undoes all changes made to the state in the current call (and all its sub-calls) and flags an error to the caller.
- Solidity has many functions for error handling. Errors can occur at compile time or runtime.
  Solidity is compiled to byte code and there a syntax error check happens at compile-time, while runtime errors occur mainly while executing the contracts. Some of the runtime errors are out-of-gas error, data type overflow error, divide by zero error, array-out-of-index error, etc.
- Error handling in solidity is done using revert, require, assert and try/catch.
- Solidity has built-in errors `Error(string)` and `Panic(uint256)` which are handled by functions `require` and `assert`.
  Error is used for “regular” error conditions while Panic is used for errors that should not be present in bug-free code.

- Panic via `assert`
  * The assert function creates an error of type Panic(uint256).
  * Assert should only be used to test for internal errors, and to check invariants. Properly functioning code should never create a Panic, not even on invalid external input. If this happens, then there is a bug in your contract which you should fix.
  * A Panic exception is generated in the following situations.
    * If you call assert with an argument that evaluates to false.
    * If an arithmetic operation results in underflow or overflow.
    * If you divide or modulo by zero.
    * If you convert a value that is too big or negative into an enum type.
    * If you call .pop() on an empty array.
    * If you access an array or an array slice at an out-of-bounds or negative index.
    * If you allocate too much memory or create an array that is too large.
    * If you call a zero-initialized variable of internal function type.
  * In the code snippet below , For large vaues of variables a and b , a+b might give an overflow and hence make the statement `c<=a` false resulting in a Panic generated by the assert statement.
   ```
   contract Assert {
        function add(uint256 a, uint256 b) internal pure returns (uint256) {
            uint256 c = a + b;
            assert(c >= a);
            
            return c;
        }
    }
   ```

- Error via require
  * The require function is used to guarantee valid conditions that cannot be detected before execution. It checks conditions on input, contract state variables or return values from calls to external contracts.
  * It accepts a single argument and returns a boolean value after evaluation, it also has a custom string message option. If false then exception is raised and execution is terminated. The unused gas is returned back to the caller and the state is reversed to its original state.
  * An Error exception is generated by the compiler in the following cases-
    * Calling require(x) where x evaluates to false.
    * If you perform an external function call targeting a contract that contains no code.
    * If you use revert() or revert("description").
    * If your contract receives Ether via a public function without payable modifier.
    * If your contract receives Ether via a public getter function.
  * For the following cases, the error data from the external call (if provided) is forwarded. This means that it can either cause an Error or a Panic (or whatever else was given):
    * If a .transfer() fails.
    * If you call a function via a message call but it does not finish properly (i.e., it runs out of gas, has no matching function, or throws an exception itself).
    * f you create a contract using the new keyword but the contract creation does not finish properly.
  * In the code snippet below , the account that invokes the function `idGenerator` must be an owner otherwise, require statement creates an error 'Only owner!'.
    ```
    function idGenerator() external view returns (uint) {
    
        require(msg.sender == lawyer, 'Only owner!');
        
        return uint(keccak256(abi.encode(block.timestamp, block.difficulty)));
    }
    ```

- revert 
  * This statement is similar to the require statement. It does not evaluate any condition and does not depends on any state or statement. It is used to generate exceptions, display errors, and revert the function call.
  * Calling a revert statement implies an exception is thrown, the unused gas is returned and the state reverts to its original state.  Revert is used to handle the same exception types as require handles, but with little bit more complex logic.
  * In the code snippet below, the function checkOverflow throws an error exception with the string "Overflow Exist" in case the sum variable is out of bounds.
    ```
    function checkOverflow(uint _num1, uint _num2) public view returns(string memory, uint){
        uint sum = _num1 + _num2;
        if(sum < 0 || sum > 255){
            revert(" Overflow Exist");
        }
        else{
            return ("No Overflow", sum);
        }
          
    }
    ```

- try/catch
  * A failure in an external call can be caught using a try/catch statement.
  * The try/ catch feature is only available for external calls.
  * The try keyword has to be followed by an expression representing an external function call or a contract creation (new ContractName()).
  * Code shown belows shows an example usage of a try/catch block.
    ```
      // SPDX-License-Identifier: GPL-3.0
      pragma solidity >=0.8.1;

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
                  // This is executed in case
                  // revert was called inside getData
                  // and a reason string was provided.
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
  * Solidity supports different kinds of catch blocks depending on the type of errors.
  * `catch Error(string memory reason) { ... }`, This catch clause is executed if the error was caused by `revert("reasonString")` or `require(false, "reasonString")` (or an internal error that causes such an exception).
  * `catch Panic(uint errorCode) { ... }`, If the error was caused by a panic, i.e. by a failing assert, division by zero, invalid array access, arithmetic overflow and others, this catch clause will be run.
  * `catch (bytes memory lowLevelData) { ... }`, This clause is executed if the error signature does not match any other clause, if there was an error while decoding the error message, or if no error data was provided with the exception. The declared variable provides access to the low-level error data in that case.
  * We can just use catch { … } if we are not interested in error data.

- custom errors
  * Starting from Solidity v0.8.4, there is a convenient and gas-efficient way to explain to users why an operation failed through the use of custom errors.
  * You can already use strings to give more information about failures (e.g., revert("Insufficient funds.");), but they are rather expensive, especially when it comes to deploy cost, and it is difficult to use dynamic information in them.
  * Custom errors are defined using the `error` statement, which can be used inside and outside of contracts (including interfaces and libraries).
  * They have to be used together with the revert statement which causes all changes in the current call to be reverted and passes the error data back to the caller.
  * The example below shows use of error with the revert statement.
    ```
      // SPDX-License-Identifier: GPL-3.0
      pragma solidity ^0.8.4;

      error InsufficientBalance(uint256 available, uint256 required);

      contract TestToken {
          mapping(address => uint) balance;
          function transfer(address to, uint256 amount) public {
              if (amount > balance[msg.sender])
                  revert InsufficientBalance({
                      available: balance[msg.sender],
                      required: amount
                  });
              balance[msg.sender] -= amount;
              balance[to] += amount;
          }
      }
    ```




  
 
 