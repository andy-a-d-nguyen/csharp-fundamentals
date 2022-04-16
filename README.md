# "C#"

- ["C#"](#c)
  - [Static Methods](#static-methods)
  - [Decimal Types](#decimal-types)
  - [Integer Types (Signed)](#integer-types-signed)
  - [Integer Types (Unsigned)](#integer-types-unsigned)
  - [Integer Types (Native)](#integer-types-native)
  - [Other Builtin Types](#other-builtin-types)
  - [Classes](#classes)
  - [Structs](#structs)
  - [Records](#records)
  - [Record Structs](#record-structs)
  - [Record Classes](#record-classes)
  - [Statements](#statements)
  - [Expressions](#expressions)
  - [Using Data Types in "C#"](#using-data-types-in-c)
  - [Data Types in "C#"](#data-types-in-c)
  - [Value Types](#value-types)
  - [Type Hierarchy in "C#"](#type-hierarchy-in-c)
  - [Backing Types](#backing-types)
  - [Strings](#strings)
  - [Methods in "C#"](#methods-in-c)
    - ["C#" Method Syntax](#c-method-syntax)
  - [Passing Parameters](#passing-parameters)
  - [The out Keyword](#the-out-keyword)
  - [The params Keyword](#the-params-keyword)
  - [Optional Parameters](#optional-parameters)
  - [Named arguments](#named-arguments)
  - [Expression-bodied Methods](#expression-bodied-methods)
  - [The Common Type System (CTS)](#the-common-type-system-cts)
    - [Types in the CTS](#types-in-the-cts)
  - [Custom Types](#custom-types)
    - [Organizing Types in Namespaces](#organizing-types-in-namespaces)
  - [The using Keyword](#the-using-keyword)
  - [Enumerations in "C#"](#enumerations-in-c)
  - [Struct in "C#"](#struct-in-c)
  - [Classes in C](#classes-in-c)
    - [Contents of a Class](#contents-of-a-class)
    - [Access Modifiers](#access-modifiers)
    - [Constructors](#constructors)
    - [Properties](#properties)

## Static Methods

- Instead of functions, C# has static methods

## Decimal Types

- float
  - 32 bits
  - Floating point
  - 6-9 digits precision
  - Based on .NET's System.Single type
- double
  - 64 bits
  - Floating point
  - 15-17 digits precision
  - Based on .NET's System.Double type'
- decimal
  - 128 bits
  - Fixed point
  - From ±1.0 x 10^-28 to ±7.9228 x 10^28

## Integer Types (Signed)

- sbyte: 8 bits (-128 to 127)
- short: 16 bits (-32,768 to 32,767)
- int: 32 bits (-2,147,483,648 to 2,147,483,647)
- long: 64 bits (-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807)

## Integer Types (Unsigned)

- byte: 8 bits (0 to 255)
- ushort: 16 bits (0 to 63,535)
- uint: 32 bits (0 to 4,294,967,295)
- ulong: 64 bits (0 to 18,446,744,073,709,551,615)

## Integer Types (Native)

- nint: Size depends on the platform
- nuint: Size depends on the platform

## Other Builtin Types

- string: Sequence of characters
- char: Unicode UTF-16 characters
- bool: Booleans (either true or false)

## Classes

- Classes are reference types

## Structs

- Structs are value types
- A struct cannot inherit another struct

## Records

- Classes that are meant to be immutable

## Record Structs

- Combine record and struct behaviors

## Record Classes

- Combine record and class behaviors

## Statements

- A basic instruction a C# program executes to take action
- They are written using a combination of C# keywords and expressions

## Expressions

- A sequence of operands and operators
- An operator performs an action on an operand

## Using Data Types in "C#"

- Size and location in memory
- Data range
- Supported operations
- Return value of an expression

## Data Types in "C#"

- Predefined types
- User-defined types

## Value Types

- Data Types:
  - Value Data Types (Data stored on the stack/variables directly contain values):
    - Predefined Data Types:
      - Integer
      - Boolean
    - User Defined Types:
      - Enumeration
      - Struct
  - Reference Data Types (Data stored on the heap):
    - Predefined Data Types:
      - String
      - Array
    - User Defined Types:
      - Class
      - Interface

## Type Hierarchy in "C#"

- Object:
  - String
  - Array
  - Exception
  - File
  - ValueType:
    - Double
    - Float
    - Int32
    - Byte
    - Decimal
    - Boolean

## Backing Types

|Primitive type|Backing type|
|--------------|------------|
|int           |Int32       |
|float         |Float       |
|decimal       |Decimal     |
|bool          |Boolean     |
|byte          |Byte        |

## Strings

- Contains text stored as collection of char objects (array of characters)
- Reference type but still primitive type
- Strings are immutable. String operations result in new strings being created
- If multiple string concatenation and copying operations are needed, StringBuilder class provides more performance

## Methods in "C#"

- Code block
- Receives parameters and optionally returns a value
- Readable code and code reuse
- Declared within a class or struct

### "C#" Method Syntax

```csharp
<access modifier> <return type> Method_Name (Parameters)
{
  // method statements
}
```

## Passing Parameters

- By value:
  - Default if nothing else is specified
  - A copy is created for the method
  - Value in caller stays the same
- By reference:
  - Require use of `ref` keyword on parameters
  - A reference to the value is passed
  - No copy is made
  - Changes made in method affect original values
  - All `ref` parameters must be initialized
  - Ex:

  ```csharp
  int a = 33;
  int b = 44;
  AddTwoNumbers(a, ref b);

  public int AddTwoNumbers(int a, ref int b)
  {
    b += 10; // modifies b
    int sum = a + b;
    return sum;
  }
  ```

## The out Keyword

- `out` values are passed by reference
- `out` values don't need to be initialized (they are passed in to a method uninitialized)
- Multiple values can be returned
- Before the method that takes in `out` values exits, they must be initialized

Ex:

```csharp
int a = 33;
int b;
AddTwoNumbers(a, out b);

public int AddTwoNumbers(int a, out int b)
{
  b = 10; // modifies b
  int sum = a + b;
  return sum;
}
```

## The params Keyword

- Represents array to capture multiple parameters
- Are available through array in the method body
- The `params` must be the last parameter in the method signature
- Does not require special keywords when the method is invoked

Ex:

```csharp
public int AddNumbers(params int[] values)
{
  for (int i = 0; i < values.length; i++)
  {
    // Add values to calculate total
  }
}
```

## Optional Parameters

- Specify default value for one or more parameters
- Caller can omit the optional ones

Ex:

```csharp
public int AddNumbers(int a, int b, int c = 100)
{
  int sum = a + b + c
  return sum
}

AddNumbers(10, 20);
AddNumbers(10, 20, 30);
```

## Named arguments

- Not required to follow order of parameters
- One or more parameters can have a name defined when invoking the method

Ex:

```csharp
public static int AddNumbers(int a, int b)
{
  ...
}

AddNumbers(b: 10, a: 20);
```

## Expression-bodied Methods

- Methods with one line can use the arrow syntax instead of curly braces

Ex:

```csharp
public static int AddNumbers(int a, int b) => a + b;
```

## The Common Type System (CTS)

- .NET specific
- Defines how type definitions and values are handled in memory
- Standard across all languages in .NET

### Types in the CTS

- Enumeration
- Struct
- Class
- Interface
- Delegate

## Custom Types

- Class: Reference type
- Struct: Value type
- Contain data
- Have defined functionality

### Organizing Types in Namespaces

- System
  - System.Web
  - System.IO
  - System.Windows
  - System.Data
    - System.Data.Common
    - System.Data.SqlTypes

## The using Keyword

- A `using` statement only brings the types within the specified namespace, not the ones in nested namespaces

## Enumerations in "C#"

- Named constants for improved readability
- Value type

```csharp
enum EmployeeType
{
  Sales, // default value: 0
  Manager, // default value: 1
  Research, // default value: 2
  StoreManager // default value: 3
}

enum StoreType
{
  PieCorner = 10,
  Seating = 20,
  FullPieRestaurant = 100,
  Undefined = 99
}
```

## Struct in "C#"

- Represents a custom data structure
- Value type
- Can be new'ed
- Can contain methods and other members

```csharp
struct Employee
{
  public string Name;
  public string Department;
  public void GetPaid()
  {
    // code to pay out wage
  }
}
```

## Classes in C #

- Blueprint of an object
- Define data and functionality to work on those data
- Reference types

### Contents of a Class

- Fields
- Methods
- Properties
- Events

### Access Modifiers

- `public`: Accessible from outside the class
- `private`: Accessible from only inside the class
- `protected`: Accessible from the class and its inheritance

### Constructors

- If no constructors are defined, C# will generate a default constructor

### Properties

- Accessors(getters/setters) for fields
- Wraps data (fields) of a class
- Hides implementation
- Define get and set implementation

```csharp
pubic class Employee
{
  private string firstName;
  public string FirstName
  {
    get
    {
      return firstName;
    }
    set
    {
      firstName = value;
    }
  }
}
```
