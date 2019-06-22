# Javascript Basics
Javascript is the programming language of the Internet. If HTML is the skeleton and CSS is the clothing, Javascript is all of the organs that make up a fully functioning (and good-looking) person.

## Javascript in the Browser
Javascript allows us to interact with the DOM, which is a slightly modified version of our HTML/CSS structure. The DOM API is a useful tool with its own set of predefined functions for interacting with the page.

To use Javascript in HTML, we can use a  `<script>` tag and specify the `src` attribute to import the code, or we can write directly inside the tags. It is best to put this tag at the end of the body because otherwise it could cause weird problems when rendering. 

Using the `src` attribute will cause the `<script>` to ignore anything written directly in.

## Structure
Javascript is case-sensitive and uses Unicode.

It is best to end all statements with a semicolon.

Comments are C++ style.

ES5 introduced `"use strict"`, which goes at the top of a script and makes the code run in a less-sloppy, stricter mode. It can cause some problems with older browsers but is generally a good idea to use since it can catch confusing syntax errors and other horrible stuff from old Javascript, while letting modern Javascript work much better.

## Variables

There are three variable declarations: `var`, `let`, and `const`. Variable identifiers can be alphanumeric and have underscores, or dollar signs, but cannot begin with a number.

Variables declared with `var` or `let` without an initial value are `undefined`, which is a falsy value. In a numeric context, `undefined` becomes `NaN`. We can also declare a variable's value as `null`, which is also falsy.

`var` is old and thus does not have a concept of "local" scope. Its scope is the function in which it was declared, which means it can have a global scope. In contrast, `let` and `const` are only scoped in the block in which they are declared. 

Javascript also allows us to **hoist** variables; this means that we can use them before declaring them, although the evaluated value will be `undefined`. `let` and `const` will not be hoisted. Functions can also be hoisted, but only function declarations are hoisted, not expressions. Strict mode disables hoisting entirely.

Global variables are properties of the global object, which is `window` in web pages. We can also refer to global variables declared in one window/frame from another by specifying the window name.

## Types
There are seven primitive data types in Javascript: Boolean, null, undefined, Number, BigInt, String, and Symbol.

Numbers can also be `Infinity`, `-Infinity`, or `NaN`. The `NaN` value is sticky.

Strings normally use single or double quotes, but using back-ticks allows us to make multi-line strings that can have variables inserted into them, like Python.

When concatenating a number to a string, the number is converted into a string. We can convert a string to a number with either `parseInt()` or `parseFloat()`.

We can use the `typeof` operator to get the type of a variable. It can be used with or without parentheses.

## Type Conversion
When a number is concatenated to a string, it is automatically converted. The `parseInt()` and `parseFloat()` functions are a formal way of converting strings into numbers.

The `String()` and `Number()` constructors can also be used to convert variables to strings or numbers. Strings which aren't valid numbers become `NaN`.

The `Boolean()` constructor uses truthy and falsy values. Note that since `"0"` and `" "` are not empty strings, they are **not** falsy!

## Operators
As a binary operator, `+` can either perform addition or concatenate strings. Since operations travel left to right, consecutive numbers before a string will be added before being converted into strings. When prefixed to a variable as a uanry operator, `+` converts that value into a number.

Javascript includes arithmetic operators like `-`, `*`, `/`, `%`, and `**`, the assignment operator `=`, prefix and postfix `++` and `--`, bitwise operators, and operators like `+=` and `*=`.

The comma operator allows us to evaluate multiple expressions. Only the last expression's output is returned.

## Comparisons
Javascript also has the boolean operators `<`, `>`, `>=`, `<=`, `==`, and `!=`.

Strings are compared alphabetically, but by Unicode and not an actual dictionary. Thus, lowercase lettes have greater value than uppercase letters. Again, since `"0"` is not empty, `Boolean("0")` is `true` and `Boolean(0)` is `false`, but if compared like `0 == "0"` the result will actually be true since strings and numbers convert.

Th `==` operator takes falsy values like `0`, `""`, `NaN`, `null`, and `undefined` and converts them all to `false`. If we want to be stricter in our comparison and check for equality in type as well, we can use the operator `===` (and `!==`) to differentiate between an actual `false` and another falsy value.

Oddly, `null` and `undefined` aren't considered equal to other falsy values but are equal to each other. When doing math or other comparisons they are converted into `0` and `NaN` respectively.

## Interaction
In the browser, Javascript has some useful built-in functions. `alert()` sends a popup on the screen displaying a message. `prompt()` takes two parameters, a title and/or a default input value for the text field. If input is cancelled, the field returns `null`. Lastly, `confirm()` asks a boolean question.

## Conditionals
Javascript has `if...else` statements like a lot of other languages. The comparisons made in the conditional operate on falsy/truthy value.

Javascript also has the ternary comparison operator, `foo ? bar : baz;`. Try not to overuse this and don't try to replace `if..else` with it.

## Logical Operators
The logical operators in Javascript are `&&`, `||`, and `!`.

## Loops
Javascript has `while`, `do...while`, and `for` loops. Loops can be exited using `break` and `continue` moves on to the next iteration.

Loops can be labelled, which aids in control flow when multiple loops are nested inside of each other and we want to break/continue an outer loop.

ES6 introduced `for...of`, which allows us to iterate over property values in an object like an array or map. `for...in` can be used to iterate over property names.

## Switch
Javascript has switch-case statements.

## Functions
Function declarations are designed like `function foo() {}`. Primitive types are passed by value, while objects are passed by reference. Functions have access to variables that are in their same scope, while variables local to a function's scope are inaccessible anywhere else. 

Parameters can have default values if specified; otherwise, the default value will be `undefined`. Older versions of Javascript required us to perform checks to see if default values were provided.

Functions without returns or with empty returns just return `undefined`.

## Function Expressions
Function expressions can be **anonymous**, meaning that they don't need a name. We use them like `var foo = function() {};`. They are useful when we want to pass functions as parameters to other functions.

Unlike a function declaration, a function expression is not hoisted.

Arrow functions came with ES6 are a more concise way of writing function expressions. They are structured like `let func = (a1, a2, ...an) => expression` and the result of the expression is returned. If there is only one argument, we can omit the parentheses. If we have no arguments, we should use empty parantheses. If we have a multi-line arrow function, we should use curly braces.