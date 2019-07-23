# Javascript Basics
This section goes over the basics of Javascript. The content here should be very familiar to people who have used another programming language before.

## Syntax
- Case sensitive and uses Unicode
- Semicolons are optional but should probably always be used
- C++ style comments
- Variable identifiers can be alphanumeric and contain underscores or dollar signs
  - Cannot begin with a number, however

## Variables
- `var` is the old way to declare a variable and has no concept of block scope
- `let` is the new way to declare a variable and has block scope
- `const` is block-scoped and is used to denote a constant

### Declarations
- Without an initial value, `var` or `let` variables are `undefined`
  - This is a falsy value
- In a numeric context, `undefined` becomes `NaN`
- Variables can be declared as `null` which is also falsy

### Hoisting
- `var` variables can be "hoisted" above their declaration, allowing us to use them before they are even declared
  - The variable's value will be `undefined` if it is hoisted
- `let` and `const` cannot be hoisted
- Function declarations can be hoisted, but function expressions cannot

### Global Variables
- Properties of the global `window` object are global variables
- Refer to global variables from one window/frame in another by specifying the window name

## Data Types
There are seven primitive data types and an `Object`:
```
Number      # For decimal, binary, octal, and hex numbers
Boolean     # For true/false
BigInt      # For large numbers with arbitrary precision
null        # For null values
undefined   # For undefined values
String      # For strings
Symbol      # Useful for working with objects

Object      # A very broad data structure
```
- Javascript is dynamically typed, so type conversion happens automatically
- The `parseInt()` and `parseFloat()` functions can extract numbers from strings
  - `parseInt()` can take a radix argument to specify the numeral system

There are also a bunch of literals in Javascript:
```
Array            # Arrays
Boolean          # Boolean values
Numeric          # Includes both integer and big integer
Floating-point   # For floats
Object           # For objects
RegExp           # Regular expressions
String           # Strings, complete with escape sequences
```

## Block Statements
Javascript has pretty much all of the common block statements in most languages.

### Control Flow
- `if` and `else` statements
- `switch` statements

### Error Handling
- `try`, `catch`, and `throw`
- Error objects constructed using `Error`

### Looping
- `while` and `do...while` loops
- `for` loops
- `break` and `continue` for loop control
- `for...in` loops over property names of an object or array
- `for...of` loops over property values of an object or array