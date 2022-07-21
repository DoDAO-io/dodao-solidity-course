## Header

This is the course header. This will be added on top of every page. Do to [DoDAO.io](https://www.dodao.io) to know more.

---

## Types

**Value Types**  
The following types are called value types because variables of these types will always be passed by value, i.e. unlike reference types they are always copied when used in function arguments or asssignments.

- Booleans

  - They are declared using the keyword `bool`.
  - The possible values are constants true and false.

- Integers

  - They are declared using keywords `int` , `uint` for signed and unsigned integers.
  - Keywords `uint8` to `uint256` in steps of 8 are used to store unsigned integers with varying sizes in bits. Similarly , `int8` to `int256` for signed integers.
  - For Example, uint32 is a 32 bit unsigned integer having range from 0 to $2^{32}-1$ whearas int32 is a 32 bit signed integer having range from $-2^{31}$ to $2^{31}-1$.
  - For an integer type X, you can use `type(X).min` and `type(X).max` to access the minimum and maximum value representable by the type.
  - Integers allow the use of comparision (<=, <, ==, !=, >=, >) , bit (&, |, ^ , ~) , arithmetic (+, -, \*, /, %, \*\* ) and shift (<< , >>) operators.
  - `x << y` is equivalent to the mathematical expression $x * 2^y$. `x >> y` is equivalent to the mathematical expression $x / 2^y$.

- Fixed Point Numbers

  - They are declared using keywords `fixed` , `ufixed`.
  - Keywords ufixedMxN and fixedMxN, where M represents the number of bits taken by the type and N represents how many decimal points are available. M must be divisible by 8 and goes from 8 to 256 bits. N must be between 0 and 80, inclusive.
  - Fixed point numbers are not fully supported by Solidity yet. They can be declared, but cannot be assigned to or from.

- Addresses

  - They can be declared using keywords `address` and `address payable`.
  - address type hold a 20 byte value (size of an Ethereum address).
  - address payable is same as address, but with the additional members transfer and send.
  - address payable is an address you can send Ether to.
  - Implicit conversions from `address payable` to `address` are allowed, whereas conversions from address to address payable must be explicit via` payable(<address>)`.
  - It is possible to query the balance of an address using the property `balance` and to send Ether (in units of wei) to a payable address using the `transfer` function.
  - `send` is the low-level counterpart of `transfer`.

- Contract types

  - Every contract defines its own type.
  - You can implicitly convert contracts to contracts they inherit from.

- Enums

  - Enums are used create a user-defined type in Solidity.
  - Enums restrict the variable with one of a few predefined values, these values of the enumerated list are called enums.
  - Syntax to declare an enum is `enum <enumerator_name> {element 1, element 2,....,element n}`
  - Enums require at least one member, and its default value when declared is the first member.
  - Enums cannot have more than 256 members.
  - The options in an enum are represented by subsequent unsigned integer values starting from 0.
  - The default value of an enum when declared is its first member.

- User Defined Value Types

  - A user defined value type is defined using `type C is V`, where C is the name of the newly introduced type and V has to be a built-in value type (the “underlying type”).
  - The function C.wrap is used to convert from the underlying type to the custom type.
  - The function C.unwrap is used to convert from the custom type to the underlying type.
  - The type C does not have any operators or bound member functions.

- Function Types

  - Function types are the types of functions.
  - Function types are declared as `function (<parameter types>) {internal|external} [pure|view|payable] [returns (<return types>)]`.
  - Internal functions can only be called inside the current contract.
  - External functions consist of an address and a function signature and they can be passed via and returned from external function calls.
  - View functions are read only function and do not modify the state of the block chain (view data on the block chain).
  - Pure functions do not read and do not modify state of the block chain.

  **Reference Types**  
  In Solidity, unlike value types that stores it own data, reference types do not store the data directly to the variable, they contain a pointer to another memory location that holds the real data.
  Values of reference type can be modified through multiple different names in contrast to value types where an independent copy is maintained whenever a variable of value type is used.
  While using a reference type a data location(where the variable is stored) has to be provided explicitly. Currently, reference types comprise of structs, arrays and mappings.

- arrays

  - Arrays can have a compile-time fixed size, or they can have a dynamic size.
  - `type arrayName [ arraySize ];` declares an array of fixed size in Solidity.
  - `type[] arrayName;` declares an array of dynamic size in solidity.
  - Memory arrays with dynamic length can be created using the new operator eg `uint[] memory a = new uint[](7);` . As opposed to storage arrays, it is not possible to resize memory arrays.
  - Arrays inside a function can only be declared with memory data location and are always of fixed size, so `uint[] memory newArray = new uint[](10);` is a valid array declaration inside a function.

- bytes and strings as arrays

  - Variables of type bytes and string are special arrays.
  - The bytes type is similar to bytes1[], but it is packed tightly in calldata and memory.
  - string is equal to bytes but does not allow length or index access.
  - Solidity does not have string manipulation functions, but there are third-party string libraries.
  - You can compare two strings by their keccak256-hash using `keccak256(abi.encodePacked(s1)) == keccak256(abi.encodePacked(s2))` and concatenate two strings using `string.concat(s1, s2)`.

- structs

  - Structs in Solidity are used to create more complicated data types that have multiple properties.
  - They are useful for grouping together related data.
  - Syntax to declare a struct is -
    ```
      struct <structure_name> {
        <data type> variable_1;
        <data type> variable_2;
      }
    ```
  - For accessing any element of the structure the dot operator is used.
  - The below example shows how to initialize a struct in solidity.

  ```
  pragma solidity 0.8.15;
  contract test {
    // Declaring a structure
    struct Course {
        string title;
        string subTopic;
        uint id;
    }
    // Declaring a structure object
    Course course1;

    // declaring a struct and assigning values to the fields
    Course course2
      = Course("Solidity Course",
              "No topic",1);

    function setSubTopicopic() public{
        course2.subTopic="Reference Types";
    }
    function viewSubTopic() public view returns(string memory){
        return course2.subTopic;
    }
  }
  ```

  - In the above example the dot operator can be used inside the setTopic function to update the subtopic of Course struct.

**Data location**

- There are three data locations: memory, storage and calldata.
- When placed in storage, a variable is written on the blockchain. Every contract has its own storage, so these variables are persistent.
- If we want to store variables and later update or make changes to its state, we have to declare it using storage. We can update the variables declared with memory data location aswell inside a function but the data can be used only within the function and any modification will not persist outside the function execution.
- State variables and Local Variables of structs, array are always stored in storage by default.
- Variables stored in memory are declared inside a function. They are temporary and their lifetime is dependent on the runtime of the function they correspond to.
- Calldata is also a temporary data location in Solidity.
- Calldata acts like memory, in terms of its dependence on the functions execution however it is only available for external function call parameters.
- When we call a function which takes an array with memory keword, the array is copied. This leads to more gas fee. However with calldata, the array is not copied, but also the data cannot be modified when declared with keyword calldata.
- Variables declared with memory data location are mutable (i.e. they can be overwritten and changed) whearas variables declared with calldata location are immutable and cannot be overwritten or changed.
- The below example explains the differences between memory and calldata.

```
  pragma solidity 0.8.15;

  contract Test {
      function memoryTest(string memory _exampleString) public pure returns (string memory) {
          _exampleString = "example";  // You can modify memory
          string memory newString = _exampleString;  // You can use memory within a function's logic
          return newString;  // You can return memory
      }
      function calldataTest(string calldata _exampleString) external pure returns (string memory) {
          // cannot modify _exampleString
          return _exampleString; // but can return it
      }
  }
```

- Storage is the most expensive data location one can use. Then there is memory, with the cheapest being calldata.
  **Mapping Type**  
  Mapping in Solidity acts like a hash table or a dictionary. These are used to store the data in the form of key-value pairs.

* Mapping types use the syntax `mapping(KeyType => ValueType)` and variables of mapping type are declared using the syntax `mapping(KeyType => ValueType) VariableName`.
* The KeyType can be any built-in value type, bytes, string, or any contract or enum type. Other user-defined or complex types, such as mappings, structs or array types are not allowed.
* ValueType can be any type, including mappings, arrays and structs.
* Mappings can only have a data location of storage.
