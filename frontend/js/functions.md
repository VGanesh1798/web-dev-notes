# Javascript Functions
Functions in Javascript can either be declared or expressed. There is an additional way to create a function using the `Function` object constructor, but it has some flaws. It works similarly to `eval()`, which is one of many predefined functions in Javascript.

## Function Structure
- Functions can access variables in their same scope
  - Functions also have their own scope
- A function can have parameters passed to it
  - These parameters can have default values set
  - Primitive parameters are passed by value, while objects are passed by reference
- Functions can return values at the end
  - A function with no `return` or an empty one return `undefined`
- Functions can only be called in scope and can call themselves for recursion

## Function Declaration
```
function myFunction() {
    alert("Hello, World!");
}
```
- Function declarations can be hoisted

## Function Expression
```
let func = function(number) {
    return number * 2;
}
```
- Function expressions can be anonymous (don't need a name)
- Function expressions cannot be hoisted
- Allow for functions to be defined based on conditions

## Closure
- Functions can be nested within other functions
  - The inner function has access to everything in the outer function
- A closure is formed when the inner function is made available to scopes outside of the outer function

## Arguments and Parameters
- The arguments passed to a function can be accessed with the `arguments` object
  - Total number of arguments is `arguments.length`
- Rest parameter syntax allows us to represent an indefinite number of arguments as an array
  - Uses the spread operator

## Arrow Function
```
let func = (arg1, arg2) => arg1 + arg2;

let newFunc = arg => {
    arg += "Text";
    return arg;
}
```
- Modified function expression that is more concise
- Arrow functions do not have their own `this`
  - They are already bound to the `this` from the outer context
- If there is only one argument, we can omit the parentheses
  - If there are no arguments, use empty parentheses
- If we have a multiline arrow function, use braces