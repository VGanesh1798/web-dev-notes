# Javascript Operators, Data Types, and Data Structures
Javascript has all of the operators you would expect a language to have, including some unique ones. 

## Operators
Javascript's operators follow the basic format of most languages, but there are a few quirks here and there.

### Assignment Operators and Destructuring
- The assignment operator `=` and its arithmetic and bitwise variants existarthm

ES6 introduced destructuring to extract information from arrays and objects in a more concise way:
```
var foo = ['one', 'two', 'three'];

// without destructuring
var one   = foo[0];
var two   = foo[1];
var three = foo[2];

// with destructuring
var [one, two, three] = foo;
```

### Comparison Operators
Javascript has all of the usual comparison operators and also has two additional ones:
- `===` is the strict equality operator. It returns true if the operands are equal *and* of the same type.
- `!==` is the strict inequality operator. It returns true if the operands are not equal and of the same type, *or* if they are of different type.

### Arithmetic Operators
- The standard arithmetic operators, remainder, and increment/decrement
- The unary negation operator `-` returns the negation of the operand
- The unary plus operator `+` attempts to convert the value to a number
- Exponentiation with `**`

### Bitwise Operators
- The standard bitwise operators
- Bitwise shift operators

### Logical Operators
- The three standard logical operators
- The ternary conditional operator

### String Concatenation
- Accomplished using `+`
  - Can also use `+=`

### Comma Operator
- Evaluates both operands and returns the value of the last operand

### Unary Operators
- `delete` deletes an object, an object property, or an element at a specified array index
  - Changes the value to `undefined`, meaning array length is not changed but the index returns `undefined`. It is still addressable but not in the array.
    - Use the `undefined` keyword instead to keep the index in the array
- `typeof` returns the type of the operand as a string
  - Parentheses are optional
- `void` indicates an expression should return nothing
  - Parentheses are again optional

### Relational Operators
- `in` returns true if the specified property is in the specified object
- `instanceof` returns true if the specified object is of the specified type

## Expressions
Most expressions in Javascript involve the use of arthmetic, string, or logical operators. Others are as follows.

### Primary Expressions
- `this` refers to the current object and can be ambiguous at times
  - Use bracket or dot notation to access the properties of `this`
- `( )` is the grouping operator and allows us to do PEMDAS
  
### Left-Hand-Side Expressions
- `new` is used to create a new instance of an object
- `super` calls the object's parent; more useful with classes
- `...` is the spread operator and allows for expressions to be expanded in places where multiple argments or elements are expected.
  - In a function, this operator is used to make rest parameters