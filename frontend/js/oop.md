# Javascript OOP
In Javascript, object oriented programming is oriented around objects. Who would've guessed. These objects can either be declared literally or with the `Object` constructor; note that classes weren't added until ES6 and are syntactic sugar for another feature, the constructor function.

## Objects
The basic data structure behind OOP in Javascript. Learning how to use objects is the first step to understanding how to use Javascript to its potential.

### Object Properties
- Objects have properties that can be accessed using either dot or bracket notation
  - Unassigned properties are left `undefined`
- For properties with usually invalid names, only bracket notation works
  - All keys are converted to strings in this notation, unless they're symbols
- Use `for...in` loops to loop over property names
  - `Object.keys(OBJECT)` returns an array of enumerable property names
  - `Object.getOwnPropertyNames(OBJECT)` returns an array of all property names
- Can refer to property either by name or by index, **but not both**. If you pick one you have to stick with it

### Object Construction
- Construct objects using object initializers or a call to the `Object` constructor
- A constructor function can also be used to make an object
  - Conventional to name capital letter
  - Pass parameters for object properties and use `this` to construct
  - A class is syntactic sugar for this constructor
- The `Object.create()` method allows us to choose prototype objects without writing constructor functions

## Classes
Javascript is **not** a class-based language like Java or C++. It is instead a prototype-based language. Classes, introduced in ES6, are just a fancy and more intuitive way of using constructor functions in Javascript.



## Inheritance
