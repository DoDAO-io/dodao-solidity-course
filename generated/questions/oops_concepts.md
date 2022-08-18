## Header
This is the course header. This will be added on top of every page. Do to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Object-Oriented Programming (OOP) Concepts in Solidity
 
 
---

##### The feature in object-oriented programming that allows the same operation to be carried out differently, depending on the object, is  

- [ ]  Inheritance
- [x]  Polymorphism
- [ ]  Overriding
- [ ]  Overloading
  
Hint: noHint
         
Explanation: Polymorphism is an ability to process data in more than one form.

Sub Topics: polymorphism
 

---

##### Consider the following two statements related to inheritance * (a)A publicly derived class is a subtype of its base class. * (b)Inheritance provides for code reuse.  

- [x]  Both the statements (a) and (b) are correct.
- [ ]  Statements (a) is correct and statement (b) is incorrect.
- [ ]  Statements (a) is incorrect and statement (b) is correct.
- [ ]  Both the statements (a) and (b) are incorrect.
  
Hint: noHint
         
Explanation: A publicly derived class is a subtype of its base class and Inheritance provides for code reuse.

Sub Topics: inheritance
 

---

##### Abstraction and encapsulation are fundamental principles that underlie the object oriented approach to software development. What can you say about the following two statements ? * I. Abstraction talks about bundling data and methods together in one contract. * II. Encapsulation allows us to consider complex ideas while ignoring irrelevant detail that would confuse us.  

- [x]  Neither I nor II is correct.
- [ ]  Both I and II are correct.
- [ ]  Only I is correct.
- [ ]  Only II is correct.
  
Hint: noHint
         
Explanation: Encapsulation allows us to focus on what something does without considering the complexities of how it works. Abstraction allows us to consider complex ideas while ignoring irrelevant detail that would confuse us. So, option (A) is correct.

Sub Topics: inheritance, encapsulation
 

---

##### Which one of the following are essential features of object oriented language? * A. Abstraction and encapsulation * B. Strictly-typed * C. Type-safe property coupled with sub-type rule * D. Polymorphism in the presence of inheritance  

- [ ]  A and B only
- [ ]  A, D and B only
- [x]  A and D only
- [ ]  A, C and B only
  
Hint: noHint
         
Explanation: Abstraction, Encapsulation, Polymorphism and Inheritance are the essential features of a OOP Language.

Sub Topics: inheritance, encapsulation, polymorphism
 

---

##### Which objects can only be accessed internally from the current contract instances?  

- [ ]  public
- [x]  private
- [ ]  internal
- [ ]  external
  
Hint: noHint
         
Explanation: - Private properties can only be accessed internally from the current contract instances.
- Internal properties can be accessed from child contracts, but not from external contracts.
- Private properties can't be accessed even from child contracts.


Sub Topics: encapsulation
 

---

##### Which of the following does not belong to state visibility?  

- [ ]  Public
- [ ]  Internal
- [ ]  Private
- [x]  External
  
Hint: noHint
         
Explanation: - Values of state variables are permanently stored in the contract storage. Each function has its own scope, and state variables should always be defined outside of that scope.
- Only functions can be marked external. External functions are part of the contract interface and can be called from other contracts and transactions. They can't be called internally. This leads to external functions being cheaper to execute.


Sub Topics: encapsulation
 

---

##### The process of defining multiple contracts related to each other through parent-child relationships is called?  

- [ ]  Abstraction
- [ ]  Encapsulation
- [x]  Inheritance
- [ ]  None
  
Hint: noHint
         
Explanation: TODO

Sub Topics: inheritance
 

---

##### Solidity uses to force a specific order in graphs of base contracts is known as  

- [ ]  C1 Linearization
- [ ]  Method Revolution Order
- [x]  C3 Linearization
- [ ]  None
  
Hint: noHint
         
Explanation: - C3 linearization is consistent with three properties: a consistent extended precedence graph, preservation of local precedence order, and. fitting a monotonicity criterion
- Solidity follows C3 Linearization.


Sub Topics: inheritance
 

---

##### Which of the following inheritance does not belongs to solidity?  

- [ ]  Single Inheritance
- [x]  Hybrid Inheritance: A combination of single, multiple inheritance and hierarchical inheritance.
- [ ]  Hierarchical Inheritance: A parent has more than one child class/contract
- [ ]  Multiple Inheritance
  
Hint: noHint
         
Explanation: TODO

Sub Topics: inheritance
 

---

##### Which of the following explain about Multi-level Inheritance?  

- [ ]  A single contract can be inherited from one or more contracts.
- [ ]  Single contract acts as a base contract for multiple derived contracts.
- [x]  Multiple levels of the parent-child relationship.
- [ ]  None
  
Hint: noHint
         
Explanation: Multi-level inheritance is similar to single inheritance, but it has levels of the relationship between the parent and the child.

Sub Topics: inheritance
 

---

##### Which of the following is a inbuilt library of solidity?  

- [x]  Dapp-bin
- [ ]  Matplotlib
- [ ]  Seaborn
- [ ]  None
  
Hint: noHint
         
Explanation: Dapp-bin was created by Ethereum includes interesting and useful libraries like DoublyLinkedList, StringUtils, IterableMapping, etc.

Sub Topics: library
 

---

##### Which of the below solidity keyword is used while importing library.  

- [ ]  of
- [x]  for
- [ ]  apply
- [ ]  match
  
Hint: noHint
         
Explanation: - `for` keyword is used to attach library functions to any type
-  `<libraryName> for <dataType>: libraryName is the name of the desired library to import, dataType is the variable type for which we want to access the library`


Sub Topics: library
 

---

##### Which of the below property is incorrect about libraries in solidity?  

- [ ]  It does not have state variables.
- [ ]  It can not inherit any element.
- [ ]  It can not be inherited
- [x]  None
  
Hint: noHint
         
Explanation: All the properties are correct regarding library in solidity.

Sub Topics: library
 

---

##### Choose the correct description about the popular solidity library OpenZeppelin.  

- [ ]  Includes many modular libraries that are very useful for implementation like ArrayUtils, Token, CrowdSale, Vesting, StringUtils, LinkedList, Wallet, etc.
- [ ]  Includes interesting and useful libraries like DoublyLinkedList, StringUtils, IterableMapping, etc.
- [x]  Includes other supporting libraries are Roles, MerkleProof, ECDSA, Math, Address, SafeERC20, ERC165Checker, SafeMath, Arrays, etc which protects from overflow.
- [ ]  None
  
Hint: noHint
         
Explanation: OpenZeppelin Contracts helps you minimize risk by using battle-tested libraries of smart contracts for Ethereum and other blockchains.

Sub Topics: library
 

---

##### Choose the data type that can not be used in solidity library.  

- [ ]  struct
- [ ]  enums
- [ ]  constant variables
- [x]  None
  
Hint: noHint
         
Explanation: Library in solidity can implement some data types like struct and enums which are user-defined, and constant variables that are stored in a stack of Ethereum, not in storage.

Sub Topics: encapsulation
 

---

##### Which of the following can not be declared inside a library in solidity?  

- [ ]  state variable
- [ ]  fallback
- [ ]  None
- [x]  Both A and B
  
Hint: noHint
         
Explanation: Libraries do not have any storage thus it cannot hold state variables, fallback or payable functions also cannot be created inside the library as it cannot store ethers.

Sub Topics: encapsulation
 

---

##### Which type of functions can be called directly from outside of the library.  

- [ ]  pure
- [ ]  view
- [x]  Both A and B
- [ ]  None
  
Hint: noHint
         
Explanation: Functions of the library can be called directly when they do not modify the state variables i.e. only pure and view functions can be called from outside of the library.

Sub Topics: library
 

---

##### Find the incorrect property about Interface.  

- [ ]  Interface can not have any function with implementation.
- [ ]  Functions of an interface can be only of type external.
- [ ]  Interface can not have constructor.
- [x]  Interface can have state variables.
  
Hint: noHint
         
Explanation: You can't put any state variables inside Interfaces, because interfaces define contracts which can be implemented in various ways. T

Sub Topics: inheritance
 

---

##### Functions of Interface can be only of type  

- [ ]  public
- [x]  external
- [ ]  private
- [ ]  None
  
Hint: noHint
         
Explanation: Functions of Interface can be only of type external.

Sub Topics: inheritance
 

---

##### From where an interface can inherit?  

- [x]  other interface
- [ ]  other contract
- [ ]  Both A and B
- [ ]  None
  
Hint: noHint
         
Explanation: An interface can inherit from other interfaces, but they can’t inherit from other contracts.

Sub Topics: inheritance
 

---

##### Which of the following data type can be used in an interface?  

- [ ]  enum
- [ ]  struct
- [x]  Both A and B
- [ ]  None
  
Hint: noHint
         
Explanation: An interface can have enum, structs which can be accessed using interface name dot notation.

Sub Topics: inheritance
 

---

##### Select the correct property regarding abstract contracts.  

- [ ]  Abstract contracts are contracts that have at least one function without its implementation.
- [ ]  When we don’t intend to create a contract directly we can consider the contract to be abstract.
- [ ]  An instance of an abstract cannot be created.
- [x]  All of these
  
Hint: noHint
         
Explanation: explanation

Sub Topics: inheritance
 

---

##### If the derived contract of an abstract contract is also not implementing the incomplete functions then that derived contract will also be marked as  

- [ ]  interface
- [x]  abstract
- [ ]  library
- [ ]  None
  
Hint: noHint
         
Explanation: TODO

Sub Topics: inheritance
 

---

##### Which of the following keyword is used to declare an abstract contract?  

- [ ]  interface
- [ ]  library
- [x]  abstract
- [ ]  None
  
Hint: noHint
         
Explanation: An abstract contract is declared using the abstract keyword.

Sub Topics: inheritance
 

---

##### Which of the below statement is correct regarding constructor in solidity?  

- [ ]  A constructor can be called multiple times.
- [ ]  A constructor can not accept arguments.
- [x]  A constructor can be invoked only once.
- [ ]  None
  
Hint: noHint
         
Explanation: Solidity provides a constructor declaration inside the smart contract and it invokes only once when the contract is deployed and is used to initialize the contract state.

Sub Topics: constructor
 

---

##### Which of the following key word is used to declare a constructor?  

- [ ]  pragma
- [ ]  abstract
- [ ]  interface
- [x]  constructor
  
Hint: noHint
         
Explanation: A Constructor is defined using a constructor keyword without any function name followed by an access modifier.

Sub Topics: constructor
 

---

##### Choose the correct statement from below options about constructor in solidity.  

- [ ]  A parameter value can be defined at the run time in a constructor.
- [ ]  A constructor can also restrict method call.
- [x]  Both A and B
- [ ]  None
  
Hint: noHint
         
Explanation: - A parameter value can be defined at the run time in a constructor.
- Constructor can also restrict the method call.


Sub Topics: constructor
 

---

##### Ways of calling parent contract's constructor  

- [ ]  Direct Initialization: This method is used to initialize the constructor of the parent class.
- [ ]  Indirect Initialization: By using Base(string(abi.encodePacked(_info, _info))) is done to initialize the constructor of the base class.
- [x]  Both A and B
- [ ]  None
  
Hint: noHint
         
Explanation: There are two ways of calling a parent contract’s constructor i.e. Direct Initialization and Indirect Initialization.

Sub Topics: constructor, inheritance
 

---

##### If the child contract is not passing any parameter to the parent’s constructor the child contract will become  

- [ ]  library
- [ ]  interface
- [x]  abstract contract
- [ ]  None
  
Hint: noHint
         
Explanation: If the child contract is not passing any parameter to the parent’s constructor the child contract will become an abstract contract.

Sub Topics: inheritance, constructor
 

---

##### Solidity keyword to declare a constructor is  

- [ ]  const
- [x]  constructor
- [ ]  construct
- [ ]  None
  
Hint: noHint
         
Explanation: 'constructor' keyword is used to declare a constructor

Sub Topics: constructor
 

---

##### How to call a constructor in contract.  

- [ ]  Constructor are called from other functions in the solidity.
- [x]  It get invoked only once when the contract is deployed.
- [ ]  Constructor can't restrict the method call.
- [ ]  None
  
Hint: noHint
         
Explanation: Constructor invokes only once when the contract is deployed and is used to initialize the contract state.

Sub Topics: constructor
 

---

##### Which of the following is not belongs to polymorphism in solidity?  

- [ ]  Function Polymorphism
- [x]  Variable Polymorphism
- [ ]  Contract Polymorphism
- [ ]  None
  
Hint: noHint
         
Explanation: Solidity supports two types of polymorphism, Function Polymorphism, and Contract Polymorphism.

Sub Topics: polymorphism
 

---

##### Function Polymorphism is also known as  

- [ ]  method calling
- [ ]  method overriding
- [x]  method overloading
- [ ]  None
  
Hint: noHint
         
Explanation: Function Polymorphism is also known as method overloading.

Sub Topics: polymorphism
 

---

##### In function polymorphism, functions are differ by  

- [x]  number of parameters
- [ ]  function name
- [ ]  access modifier
- [ ]  None
  
Hint: noHint
         
Explanation: In function polymorphism, multiple functions are declared having the same name within the same contract or inheriting contract. Functions differ on the basis of the number of parameters or parameter datatypes.

Sub Topics: polymorphism
 

---

##### "Declaration of function cannot be overload by functions that differ only in return type in solidity." The statement is  

- [x]  True
- [ ]  False
  
Hint: noHint
         
Explanation: - We can have multiple definitions for the same function name in the same scope. The definition of the function must differ from each other by the types and/or the number of arguments in the argument list. 
- We cannot overload function declarations that differ only by return type.


Sub Topics: polymorphism
 

---

##### Using multiple contract instances interchangeably when they are related to each other by using inheritance is known as  

- [ ]  Method overloading
- [x]  Contract Polymorphism
- [ ]  Both A and B
- [ ]  None
  
Hint: noHint
         
Explanation: Contract polymorphism means using multiple contract instances interchangeably when they are related to each other by using inheritance.

Sub Topics: polymorphism
 

---

##### Which of the following explains polymorphism  

- [x]  An ability to process data in more than one form.
- [ ]  The mechanism of manipulation of the scope of variables.
- [ ]  Way of extending the functionality of a program, used to separate the code, reduces the dependency, and increases the re-usability of the existing code.
- [ ]  None
  
Hint: noHint
         
Explanation: Polymorphism is an ability to process data in more than one form. Like any other programming language Solidity also supports polymorphism.

Sub Topics: polymorphism
 

---

##### Is it accurate that private variables are truly private?  

- [ ]  Yes
- [x]  No
  
Hint: noHint
         
Explanation: No, Only the EVM has access to private information (Ethereum Virtual Machine, the part of Ethereum that executes smart contracts). On the other hand, smart contract data is stored on the Ethereum blockchain, which is open to the world. Anyone can read secret variables of smart contracts using a particular tool for analyzing blockchain data.

Sub Topics: encapsulation
 

---

##### Which of types belongs to libraries avialable in solidity  

- [ ]  Deployed
- [ ]  Embedded
- [x]  Both A and B
- [ ]  None
  
Hint: noHint
         
Explanation: There are 2 types of libraries
- Deployed- They have their own address, and several other smart contracts can use them.
- Embedded- They don’t have their own address and are deployed as part of the code of the smart contract that uses them.


Sub Topics: library
 
