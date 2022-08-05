## Header
This is the course header. This will be added on top of every page. Do to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Object Oriented Programming (OOP) Concepts in Solidity
 
 **Understanding Encapsulation in Solidity**        
It refers to the bundling of data, along with the methods that operate on that data, into a single unit.
It refers to the mechanism of manipulating the scope of variables, i.e., restricting the variable's access outside the scope.

Syntax
  ```solidity
  // Unlike in Java,
  // the data type comes before the visibility modifier in Solidity
  uint public num;
  // <data type> <visibility> <variale name>;
  ```

- Public
  * These objects can be accessed internally and externally as well as via messages also.
  * External methods can inherit public elements.
  * A getter function is generated automatically when a public variable is created.
  * However, no setter function is created, implying that the external function can not modify the variable.

- Internal
  * As the name suggests, Internal objects can be accessed by internal or derived methods but cannot be accessed by external.
  * Only a base contract and a derived contract have their access.

- Private
  * Private objects can only be accessed internally from the current contract instances.
  * They cannot be accessed by derived methods also.

- External
  * These objects can be accessed externally but not internally, i.e., current contract instances cannot access it.
  * They cannot be inherited.

State Variable visibility
  - Public
  - Internal
  - Private

Function visibility
  - External
  - Public
  - Internal
  - Private

One should always use the principle of least privilege when determining which level of visibility to use.
 
 **Understanding Inheritance in Solidity**        
Inheritance is the process of defining multiple contracts related to each other through parent-child relationships.

Solidity supports inheritance between smart contracts.
  * Base contract: The contract from which other contracts inherit features.
  * Derived contract: The contract which inherits the features.
  * Simply, they are referred to as parent-child contracts.

Syntax
  ```solidity
    contract <Derived Contract Name> is <Base Contract Name>{
  }
  ```

Solidity provides different types of inheritance.
  - Single Inheritance
    * In Single or single-level inheritance, the functions, and variables of one base contract are inherited to only one derived contract.
    
  - Multi-level Inheritance
    * Very similar to single inheritance.
    * Instead of just a single parent-child relationship, there are multiple levels of the parent-child relationship.

  - Hierarchical Inheritance
    * Here, a single contract acts as a base contract for multiple derived contracts.
    * It is mostly used when a common functionality is used in different places.

  - Multiple Inheritance
    * Here, a single contract can be inherited from one or more contracts.
  
Note : Solidity follows the path of Python and uses C3 Linearization, also known as Method Resolution Order (MRO), to force a specific order in graphs of base contracts. The order of execution is determined by order of the declaration at the contract level. It has nothing to do with the order you call/pass arguments up from the constructor's signature.
 
 **Polymorphism in Solidity**        
It is an ability to process data in more than one form.

Solidity supports two types of polymorphism.
  - Note
    - Function overriding
      * When the base class and derived class have member functions with exactly the same name, same return-type, and same arguments list.
    
    - Function overloading
      * A set of different functions that happen to have the same name differ by their parameters.

  - Function polymorphism
    * It is also known as method overloading.
    * Multiple functions are declared to have the same name within the same contract or inheriting the contract.
    * Functions differ based on the number of parameters or parameter datatypes.
    * Declaration of function cannot be overloaded by functions that differ only in return type.
  
    ```solidity
      // Solidity program to demonstrate
      // Function Polymorphism
      pragma solidity ^0.5.0;
        
      // Contract definition
      contract methodOverloading {
        
          // function to get value of 
          // the unsigned integer variable 
          function getData(uint _n) public pure returns(uint){
              return _n;
          }
            
          // Function to get value 
          // of the string variable
          function getData(string memory _str) public pure returns(string memory){
              return _str;
          }
      }
    ```
  - Contract polymorphism
    * Using multiple contract instances interchangeably when they are related to each other by using inheritance.

    ```solidity
    // Solidity program to demonstrate Contract Polymorphism
    pragma solidity >=0.4.22 <0.6.0;

    contract parent{  
      uint internal sum;
      
      // Function to set the value of
      // internal state variable sum
      function setValue(uint _num1, uint _num2) public {
        sum = _num1 + _num2;
      }

      // Function to return a value 10
      function getValue() public view returns(uint) {
        return 10;
      }
    }

    // Defining child contract
    contract child is parent{
      
      // Function getValue overloaded
      // to return internal state
      // variable sum defined in the
      // parent contract
      function getValue() public view returns(uint) {
        return sum;
      }
    }

    // Defining calling contract
    contract ContractPolymorphism {
      
      // Creating object
      parent pc = new child();
        
      // Function to set values
      // of 2 unsigned integers
      function getInput(uint _num1, uint _num2) public {
        pc.setValue(_num1, _num2);
      }

      // Function to get value of
      // internal state variable sum
      function getSum() public view returns(uint){
        return pc.getValue();
      }
    }
    ```
 
 **Constructor for Solidity**        
It is a special method in any object-oriented programming language that gets called whenever an object of a class is initialized.
Solidity provides a constructor declaration inside the smart contract, and it invokes only once when the contract is deployed and is used to initialize the contract state.
The compiler creates a default constructor if there is no explicitly defined constructor.

Syntax
  ```solidity
  constructor() <Access Modifier> {         
  }
  ```

Note
  * It is very useful in a smart contract, a parameter value can be defined at the run time and can also restrict the method call.
  * Constructor overloading is not supported in Solidity; it only allows one constructor at a time.
 
 **Abstraction in Solidity**        
Hiding the implementation details and showing only important/useful parts to the user.

  - Abstract Contract
    * These are contracts that have partial function definitions. One cannot create an instance of an abstract contract.
    * It must be inherited by a child contract for utilizing its functions.
    * Abstract contracts help define a contract's structure, and any class inheriting from it must ensure to provide an implementation for them.
    * If the child contract does not provide the implementation for incomplete functions, even its instance cannot be created.
    * A contract becomes an abstract class if it has functioned without implementation.
    * There is no Solidity-provided keyword to mark a contract as abstract.
  
  - Interface
    * These are like abstract contracts, but there are differences.
    * Interfaces cannot contain any definition.
    * They can only contain function declarations, which means functions in interfaces cannot contain any code.
    * An interface can contain only the signature of functions.

    ```solidity
    // Solidity program to
    // demonstrate the working
    // of the interface

    pragma solidity ^0.5.0;
    interface InterfaceExample{
      function getStr() public view returns(string memory);
    }

    // Contract that implements interface
    contract thisContract is InterfaceExample{

      // Function definitions of functions
      // declared inside an interface
      function getStr() public view returns(string memory){
        return "GeeksForGeeks";
      }
    }
    ```
 
 **Libraries in Solidity**        
- Highlights
  * A library has functions that can be called by other contracts. 
  * Deploying a common code by creating a library reduces the gas cost. 
  * Functions of the library can be called directly when they do not modify the state variables i.e. only pure and view   functions can be called from outside of the library. 
  * It cannot be destroyed because it is assumed as stateless. 
  * The library does not have state variables, it cannot inherit any element and cannot be inherited.

- Creating library
  ```solidity
  library <libraryName> {
      // block of code
  }
  ```

- Deploying library

  ```solidity
  // import <libraryName> from “./library-file.sol”;

  // Solidity program to demonstrate 
  // how to deploy a library
  pragma solidity ^0.5.0;

  // Defining Library
  library LibraryExample {
      function pow(uint a, uint b) public view returns (uint, address) {
          return (a ** b, address(this));
      }
  }

  // library deployed with for keyword

  contract LibExample {
      
    // Deploying library using 
    // "for" keyword
    using LibraryExample for unit;
    address owner = address(this);
      
    function getPow(uint num1, uint num2) public view returns (uint, address) {
        return num1.pow(num2);
    }
  }

  // library can be used without for keyword

  contract LibExample2{

    // Deploying library without using 
    // "for" keyword
    
    function getPow(uint num1, uint num2) public view returns (uint, address) {
          return LibraryExample.pow(num1, num2);
    }
  }
  ```
 
 
