## Header
This is the course header. This will be added on top of every page. Do to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Object-Oriented Programming (OOP) Concepts in Solidity
 
 **OOPS Intro**        
A programming paradigm called OOP (object-oriented programming) is based on the idea that objects can contain data 
and code. Data can be found in the form of attributes or properties, and code can be found in the form of methods.

Solidity is used as an object-oriented programming language to implement smart contracts on different blockchain 
platforms, most notably Ethereum. Here in this section, we will discuss various concepts, i.e., belonging to OOPs 
in contex of Solidity and vice versa.
 
 **Understanding Encapsulation in Solidity**        
Encapsulation is the mechanism of manipulating the scope of variables and functions, i.e.; it prevents the variable from being 
accessed outside the scope.

Syntax
```solidity
// Unlike in Java,
// the data type comes before the visibility modifier in Solidity
uint public num;
// <data type> <visibility> <variale name>;
```

State variables only have three possible visibility modifiers; public, internal, or private, whereas a function's 
visibility can be set to external, public, internal, or private. State variables are not covered by the keyword 
external.

```solidity
  pragma solidity ^0.5.0;

  contract Parent {
    uint num = 10;
    uint public public_num = 100;
    uint internal internal_num = 200;

    // uint external external_num = 300;
    // ParserError: Expected identifier but got 'external'
    // uint external external_num = 300;
    //      ^------^

    // Remark: We can't declare external variable/state in solidty.

    uint private private_num = 400;

    function get_public() public view returns(uint){
        return public_num;
    }

    function get_private() private view returns(uint){
        return private_num;
    }

    function get_internal() internal view returns(uint){
        return internal_num;
    }

    function get_external() external view returns(uint){
        uint num1 = get_private();
        return num1;
    }
  }
```
### Visibility Modifiers
- Public objects can be accessed from outside, inside of the contract, as well as via message also. One need to 
  declare a method as public during declaration. While creation of public variable getter function are created. As 
  setter function is not created for the same external functions can't modify the variable.     
- Internal objects can only be accessed by internal or derived methods. External methods can't access the same. 
- External objects can be accessed by external contract but not inside the same contract instance. These can not 
  be inherited. 
- Private is most restricted object scope. It can only be accessed internally from the current contract instance. One
  can not access the same by derived methods. A function or variable that has its visibility set to private is not 
  rendered invisible on the blockchain. It merely limits its access to function covered by the contract.

```solidity
  contract Child is Parent{

  // uint c = get_private();
  // DeclarationError: Undeclared identifier.
  // uint c = get_private();
  //          ^---------^

  // Remark: From the above error, it is understood that the private functions are 
  //         not accessible in the child class. 


  // uint d = get_external();
  // DeclarationError: Undeclared identifier. Did you mean "get_internal"?
  // uint d = get_external();
  //          ^----------^

  // Remark: From the above error, we learned that the external functions could be 
  //         accessed after deployment, not even in the child class.

    function add_private() private view returns(uint){
        uint a = get_public();
        uint b = get_internal();
        return a+b;
    }

    function add_public() public view returns(uint){
        uint c = add_private();
        // accessing the function within the contract Child
        return c;
    }

    function square_internal() internal view returns(uint){
        return num**2;
    }

  }
```
```solidity
  contract Caller { 

    Child ch = new Child();
  // creating Child contract object

  // uint e = ch.add_private();
  // TypeError: Member "add_private" not found or not visible after argument-dependent lookup in contract Child.
  //     uint e = ch.add_private();
  //             ^------------^

  // uint f = ch.square_internal();
  // TypeError: Member "square_internal" not found or not visible after argument-dependent lookup in contract Child.
  // uint f = ch.square_internal();
  //         ^----------------^

  // Remark: i. From the above two errors, we learned that the private function is not visible outside of the
  //              contract through object call also.
  //         ii. Internal functions are not accessible out side the contract inheritance hierarchy.   

    function get_external() public view returns(uint){
        return ch.get_external();
        // external function can be accessed outside of the contract i.e., here we access the same through ch object. 
    }// returns 400

    function add_public() public view returns(uint){
        return ch.add_public();
        // public functions can be accessed every where. 
    }// returns 300  
  }
```
 
 **Inheritance in Solidity**        
Inheritance is a way to expand usefulness of a contract by defining multiple related contracts through parent-child 
relationship.  

The contract having no incoming inheritance or from which other contrcats inherit features is known as Base contract. 
While the contract having atleast one incoming inheritance or which inherits features are known as Derived contract. 

Syntax
```solidity
  contract <Derived Contract Name> is <Base Contract Name>{
  }
```
All non-private members, including state variables and internal methods, are accessible to derived contracts. However, 
using this is prohibited. Function calls made with super give preference to the majority of derived contracts when 
there are multiple inheritances. Function overriding is permitted as long as the function signature is maintained. 

The compilation will fail if the output parameters are different. The super keyword or the super contract name can 
be used to invoke a super contract's function. 

Soility supports four types of Inheritance. 

#### Single Inheritance
In Single or single-level inheritance, the functions, and variables of one base contract are inherited to only one 
derived contract.

```solidity
  pragma solidity ^0.5.0;
  /* Graph of inheritance
      Parent
        |
      Child
  */


  contract Parent{
      uint internal num;

      function addition(uint a, uint b) external {
          num = a+b;
      }
  }

  contract Child is Parent{
      // inheriting from parent contract i.e., Parent.
      function get_sum() public view returns(uint){
          return num;
      }
  }

  contract Caller{
      Child ch = new Child();

      function setNum(uint a, uint b) public returns(uint){
          //setting num value
          ch.addition(a,b);
          return ch.get_sum();
      }
  }
```

#### Multi-level Inheritance
The multi-level inheritance includes the involvement of at least two or more than two contracts. One contract inherits 
the features from a parent contract and the newly created sub-contract becomes the base contract for another new contract.
```solidity
  pragma solidity ^0.5.0;

  /* Graph of inheritance
      SuperParent
          | 
      Parent
          | 
      SubParent 
          |
      Child
  */
  contract SuperParent{
      uint internal num;
      uint internal b = 20;
      uint internal a = 10;

      function add(uint n, uint m) external {
          num = n+m;
      }
  }

  contract Parent is SuperParent{
      // inheriting from parent contract i.e., SuperParent.
      function multiply() external {
          num = num*b; // num = num*20
      }
  }

  contract SubParent is Parent{
      // inheriting from parent contract i.e., Parent.
      function subtract() external {
          num = num-a; // num = num-10
      }
  }

  contract Child is SubParent{
      // inheriting from parent contract i.e., SubParent.
      function get_num() public view returns(uint){
          return num;
      }
  }

  contract Caller{
      Child ch = new Child();
      function setNum(uint a, uint b) public returns(uint){
          //setting num value
          // for input of a=100, b=200
          ch.add(a,b);//num=300
          ch.subtract();//num=290
          ch.multiply();//num=5800
          return ch.get_num();
      }//returns 5800 for input of (100,200)
  }

```

#### Hierarchical Inheritance
In Hierarchical Inheritance single contract acts as a base contract for multiple derived contracts. It is mostly 
used when a common functionality is used in different places.

```solidity
  pragma solidity ^0.8.0;

  /* Graph of inheritance
      SuperParent
      /           \
    Parent1       Parent2
  /       \        /
  Child1  Child2  Child3

  */

  contract SuperParent {
      function find() public pure virtual returns (string memory) {
          return "SuperParent";
      }
  }

  contract Parent1 is SuperParent {
      // Override SuperParent.find()
      function find() public pure virtual override returns (string memory) {
          return "Parent1";
      }
  }

  contract Parent2 is SuperParent {
      // Override SuperParent.find()
      function find() public pure virtual override returns (string memory) {
          return "Parent2";
      }
  }

  // When a function defined multiple times in different contracts is called, parent contracts 
  // are searched from right to left and in depth-first order.

  contract Child3 is Parent2, Parent1 {
      // Child3.find() returns "Parent1"
      // since Parent1 is the right most parent contract with function find()
      function find() public pure override(Parent2, Parent1) returns (string memory) {
          return super.find();
      }
  }

  contract Child2 is Parent1, Parent2 {
      // Child2.find() returns "Parent2"
      // since Parent2 is the right most parent contract with function find()
      function find() public pure override(Parent1, Parent2) returns (string memory) {
          return super.find();
      }
  }

  // Inheritance must be sorted from "most base-like" to "most derived."
  // Changing the order of SuperParent and Parent1 will result in a compilation error.
  contract Child1 is SuperParent, Parent1 {
      function find() public pure override(SuperParent, Parent1) returns (string memory) {
          return super.find();
      }

  }

```    
#### Multiple Inheritance
In Multiple Inheritance a single contract can be inherited from one or more contracts.

```solidity
  pragma solidity ^0.8.0;

  /* Graph of inheritance
    Parent1   Parent2
          \  /
          Child
  */

  contract Parent1{
      uint internal num;
      function sum(uint n, uint m) external{
          num = n+m;
      }
  }

  contract Parent2{
      string name;
      function assignName(string memory nm) external{
          name = nm;
      }
  }

  contract Child is Parent1, Parent2{
      // inheriting from both parent contracts i.e., Parent1 & Parent2.
      function getNum() public view returns(uint){
          return num;
      }
      function getName() public view returns(string memory){
          return name;
      }
  }

  contract Caller{
      Child ch = new Child();
      function getNumName(uint n, uint m) public returns(uint, string memory){
          // For n=100, m=200
          ch.sum(n,m);// num=300
          ch.assignName("DoDAO");// name="DoDAO"
          return (ch.getNum(),ch.getName());
      }// returns (300,"DoDAO")
  }
```
C3 Linearization, also known as Method Resolution Order (MRO), is a technique that Solidity uses to enforce a 
particular order in graphs of base contracts. The contract level declaration order determines the order of 
execution. The order in which you call/pass arguments up from the constructor's signature has no bearing on it.
 
 **Polymorphism in Solidity**        
Polymorphism describes the concept of being able to access objects of different types through the same interface. This interface can be implemented independently by each type.

### Function polymorphism
Function polymorphism refers to expressing multiple functions within the same contract or inheriting contracts with 
the same name. The parameter data types differ between functions. They also alter the number of parameters. Return 
types are not considered in a meeting to define valid function signatures for polymorphism; function declaration 
cannot be overloaded by functions that differ only in return type. Method overloading is another term for function 
polymorphism.

```solidity
  pragma solidity ^0.5.0;

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
### Contract polymorphism
Contract polymorphism refers to using multiple contract instances interchangeably when the contracts are related by 
inheritance. Contract polymorphism allows using parent contract instances to call the child contract function.

```solidity
  pragma solidity ^0.5.0;

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
 
 **Abstraction in Solidity**        
Abstraction allows the user to build more complex logic on top of the provided abstraction(abstract contracts) without having to understand 
or even consider all the hidden complexity.

### Abstract Contracts
In Solidity the contracts having at least one function that do not have its implementation or not provided arguments 
for all the base contract constructors. One can also consider a contract to be abstract if we do not intend to 
create one directly. An abstract contract can be declared using the abstract keyword. 

```solidity
  pragma solidity ^0.4.19;

  abstract contract Parent {
      function sum(uint256 a, uint256 b) public returns (uint256);
  }

  contract Child is Parent {
      function sum(uint256 a, uint256 b) public returns (uint256) { return a+b; }
  }
``` 
Abstract contracts are used as base contracts, allowing child contracts to inherit and use their functions. The abstract 
contract defines the structure of the contract, and any derived contract inherited from it should provide an 
implementation for the incomplete functions; if the derived contract does not provide an implementation for the 
incomplete functions, it will be marked as abstract as well. One cannot create an instance of an abstract contract.

```solidity
  // SPDX-License-Identifier: GPL-3.0
  pragma solidity ^0.8.0;

  // Creating an abstract contract
  abstract contract AbstractContract {
      uint256 public num;
      constructor(uint256 n ){
          num = n;
      }

      function getNum() public virtual view returns (uint256){
          return num;
      }
      function setNum(uint256 n) public virtual {}
  }

  // Child contract inheriting an abstract parent contract 'AbstractContract'
  contract DerivedContract is AbstractContract {
      string public name;
      constructor(string memory nm  ,uint256  n) AbstractContract(n) {
        name = nm;
      }
      function getName() public view returns (string memory){
          return name;
      }
      // Calling functions inherited
    // from abstract contract
      function getNum() public override virtual view returns (uint256){
          return 67;
      }
    // Defining functions inherited from abstract parent contract
      function setNum(uint256 n ) public override virtual {
          num = n;
      }
  }

  contract Caller{
      DerivedContract dc = new DerivedContract("DoDAO",70);
      function getData() public view returns(string memory, uint){
          return (dc.getName(), dc.getNum());
      }// returns ("DoDAO", 67)

  }
```
### Interfaces
Interfaces are similar to abstract contracts, which are created by using an interface keyword. It does not have any 
definitions, state variables, constructors, or functions with implementations; instead, they only contain function 
declarations, implying that functions in interfaces do not have any statements. They can inherit from other interfaces 
but not from other contracts. An interface may contain enums and structs that can be accessed using the interface 
name dot notation.Interface functions can only be of the external type.    

```solidity
  // SPDX-License-Identifier: GPL-3.0
  pragma solidity 0.4.19;

  // Creating an interface contract
  interface interfaceContract {
    function getName(string name) public view returns(string memory);
    function mul(uint n,uint m) public view returns(uint);
  }

  // Child contract inheriting
  // an interface parent
  // contract 'interfaceContract'
  contract derivedContract is interfaceContract{
    // Defining functions inherited from interface parent contract
    function mul(uint n,uint m) public view returns(uint){
      return n*m;
    }
    function getName(string name) public view returns(string memory){
      return "DoDAO";
    }

  }

  contract Caller{
    // Creating an instance of
    // an interface contract
    interfaceContract obj;

    // Creating an object of
    // child contract
    function call() public{
      obj = new derivedContract();
    }

    // Calling functions inherited
    // from interface contract
    function getValues() public view returns(uint){
      uint n = obj.mul(10, 20);
      obj.getName("Interface");
      return n;
    }// returns 200
  }
```
 
 **Libraries in Solidity**        
Libraries are similar to Contracts in that they are intended to be reused. A Library is a collection of functions 
that other contracts can use.

### Creating library**

```solidity
library <libraryName> {
    // block of code
}
```

In Solidity, a library is a stateless entity. Unlike smart contracts, state variables cannot be defined in a library; 
library functions are not permitted to alter or modify the state of a smart contract. It does not change the state of 
the contract; calling a library function consumes no gas. Hence it can only implement pure or view functions. An 
external scope cannot access a library. The other contracts can call them, but they are not accessible from outside 
the deployment.

Let have a look upon how to use libraries in solidity. 

### Deploying library

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

The library is an independent entity that can not inherit any other library or contract. No other entity/library/contract 
can inherit a library. A library is unable to provide fallback or payable functions.
 
 
