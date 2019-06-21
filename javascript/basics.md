# Javascript Basics

## Grammar
Javascript is case-sensitive and uses Unicode.

It is best to end all statements with a semicolon.

Comments are C++ style.

There are three variable declarations: `var`, `let`, and `const`. Variable identifiers must begin with an alphabet character, an underscore, or a dollar sign. Subsequent characters can additionally be numeric.

Variables declared with `var` or `let` without an initial value are `undefined`, which is a falsy value. In a numeric context, `undefined` becomes `NaN`. We can also declare a variable's value as `null`, which is also falsy.

`var` is old and thus does not have a concept of "local" scope. Its scope is the function in which it was declared, which means it can have a global scope. In contrast, `let` and `const` are only scoped in the block in which they are declared. 

Javascript also allows us to **hoist** variables; this means that we can use them before declaring them, although the evaluated value will be `undefined`. `let` and `const` will not be hoisted. Functions can also be hoisted, but only the function declaration is hoisted, not the expression.

Global variables are properties of the global object, which is `window` in web pages. We can also refer to global variables declared in one window/frame from another by specifying the window name.

## Types
There are seven primitive data types in Javascript: Boolean, null, undefined, Number, BigInt, String, and Symbol. Since Javascript is dynamically typed, we don't need to specify the type of our variables in the declaration. When concatenating strings and numbers, the number is converted into a string. We can convert a string to a number with either `parseInt()` or `parseFloat()`.

Array literals that have extra commas will make those indices `undefined`, but the last extra comma at the end is always ignored. 

Boolean literals have two values of `true` and `false`, which should not be confused with the primitive Boolean type values.

Numeric literals can be expressed in decimal, hexadecimal, octal, or binary. A leading `0`, `0O`, or `0o` indicates octal, a `0X` or `0x` indicates hex, and a `0B` or `0b` indicates binary.

Floating-point literals can have a sign, a decimal point, a fraction, or an exponent. We use E-notation for the exponent.

Do not use object literals at the beginning of a statement; the braces will cause an error. Object values can either be literals, other variables, or functions. Property names can be numeric or string literals. Unusual property names will have to be enclosed in quotes and cannot be accessed by the dot operator, only by the bracket operator. ES6 enhanced object literals by allowing us to prototype.

Regex literals are enclosed in forward slashes.

String literals can use either double or single quotes and have a `length` property. Template literals use back-ticks instead of quotes and can be multi-line or allow us to insert variables into strings, much like Python. Don't forget to use escape sequences where necessary.

## Control Flow