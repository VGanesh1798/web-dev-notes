# Javascript Objects

Javascript supports OOP in the form of the `Object` data type, which can really be anything you want it to be. Objects consist of key:value pairs much like Python's dictionary. 

## Basics
Objects can either be declared using the constructor, like `let foo = new Object()`, or more often as object literals. Either the dot operator or brackets can be used to access the property values of an object. The last property can have a hanging comma, but hanging/empty commas do not come without some quirks.

We can add new key:value pairs to an object at any time simply by declaring them, and we can delete them by using `delete`. Multiword property names have to be encased in quotes, but the dot operator won't work when trying to access the value. Brackets also allow us to obtain property names of objects as expressions as opposed to literals.

Reserved words like `for` and `if` can be used as property names, but again, the dot operator won't work. The only reserved word that doesn't work is `__proto__`. 

ES6 introduced the property value shorthand, where we don't have to write delcarations like `name: name,` and can instead just declare `name,` to accomplish the same result.

Trying to access properties that don't exist returns `undefined`. We can check for properties in an object through this kind of validation, or we can use the `in` keyword like we would use in `for...in` loops. Integer properties are ordered in ascending order, while other properties are ordered by creation.

Again, primitive types are passed by value, while objects are passed by reference. When making comparisons, two variables will only be equal if they are referencing the exact same object. Two variables each referencing a `{}` are thus not equal unless the object's reference is copied.

Although primitive `const` variables are immutable, that does not apply to object properties. If we tried to reassign a constant variable to another object, then we'd get an error, but we can change the original object's properties all we want.

To clone an object, we can either use an empty object and assign it key:value pairs in a for loop, or we can use the `Object.assign` method. If the object being assigned already has a same named property, the assignment will overwrite the old property.

## Garbage Collection
The garbage collector is a background process in a Javascript engine that monitors objects and removes those which have become unreachable. As an example, if we have a global variable referencing an object, that object's properties are reachable. If we were to reassign the variable to `null`, the object is no longer reachable and thus it is removed from memory.

If we assign two variables to the same object but only nullify one, the object will still be reachable. Interlinking objects can make them reachable even if we delete a bunch of references. However, we can end up with unreachable islands if we remove the "root", which is the initial reachable variable.

## Symbols
Object keys can either be strings or symbols. Symbols can be constructed using `Symbol()` and can have a description, or symbol name, specified in the parentheses. Two symbols can share the same name but will be unique.

If we want to convert a symbol to a string, we'd have to use the `toString()` method or use the `description` property of the symbol.

Symbols let us create hidden properties for objects. Say we `let id = Symbol("id")`. Now for some object `foo`, we can use `foo[id] = "Our ID"` and we have a unique identifier for the object that is inaccessible by other parts of the code.

Like the assignment above, if we want to use a symbol in an object literal we will have to enclose the name in brackets. Symbols also do not participate in `for...in` loops, and `Object.keys` will also ignore them. We can still use `Object.assign` with symbols, though.

If we want multiple objects to access the same symbol, we can use the *global symbol registry*. The syntax is `Symbol.for(key)`, which will either read the global symbol with that particular key or will create the symbol if needed. This method returns a symbol by name, but to return a name by symbol, we can use `Symbol.keyFor(sym)`.

There are a lot of other important symbols in Javascript, such as `Symbol.hasInstance` and `Symbol.iterator`.

## Object Methods
A method is a function which is a property of an object. This is the foundation of OOP. We can either use an expression or declaration when adding methods to an object literal, but outside of the literal we can only use function expressions.

The `this` keyword is another important part of OOP. It refers to the object itself, such as when a method needs access to another property of the same object. We can also refer to the property by referring to the outside variable, but this can be unreliable and break things if we aren't careful when copying objects.

Unlike most languages, `this` is not bound. This means that it can be used in any function, and its value is evaluated on run-time and is gathered depending on context. Usually, an unbound `this` will work in functions that take objects as parameters; `this` will just become the object itself. In scenarios with multiple objects, `this` will pick one of the objects. However, if we don't have an object, `this` evaulates to `undefined`, at least in strict mode. If we don't use strict mode, a hanging `this` refers to the global object, which is `window` in the browser. If we attempt to access properties of such a `this`, we will be met with an error, or we will end up altering the global object and screw things up.

How does `obj.method()` actually work? First, the dot operator gets the property called `method`, and then the parentheses execute the method. If we were to assign a variable to an object method, and then try to call that variable, we would be met with an error if the method referred to `this` because we have lost `this`. There is no longer an object being referred to by the method, so it causes an error. Dot operators return a special **Reference Type** value which allows for `this` to work. If we assign the method to a variable, we will have lost that Reference Type. 

Arrow functions do not have their own `this` and instead inherit it directly from the outer context.

## Object to Primitive Conversion
All objects are considered truthy values, which covers any boolean conversion. Numeric conversion usually happen when an arithmetic operator is applied to objects, such as when `Date` objects are subtracted. String conversions usually happen when an object is printed using `alert()` or something.

The `toPrimitive` method allows us to fine-tune our object conversions, and it can take three hints. The first is `"string"`, which is useful for when we use a statement that expects a string (like `alert()`). The second is `"number"`, which is used when doing math. The last hint is `"default"`, which occurs in rare cases where operators aren't sure what type to expect. For all built-in objects except `Date`, the default hint is implemented the same as the number hint.

There are three methods to consider when performing an object conversion. The first is `Symbol.toPrimitive`, which is used like `obj[Symbol.toPrimitive] = function(hint) {}`. Within the hint function, we can then return a primtive value, and whenever the object needs to be converted it will look at the hint function to figure out what to return.

The next two methods are `toString` and `valueOf`. If no `Symbol.toPrimitive` is found, Javascript looks for `toString`, then `valueOf` for the "string" hint, and `valueOf`, then `toString` for a "number" hint. `toString` functions as a catch-all, so we can use it by itself to handle all primitive conversions.

These methods are only guaranteed to return a primitive; they don't have to return the hinted value.

## Constructor
If we want to create a lot of similar objects, we can use function constructors. These are essentially regular functions that are named with capital letters (like classes) and are always executed with the `new` operator. 

Implicitly, a function constructor creates an empty `this` object, which can have properties like `this.foo` and stuff applied to it in the function body. At the end, `this` is implicitly returned. This way, we don't need to keep making object literals and can reuse the function constructor to make multiple objects with the same properties.

We can also use `new` in a function expression, especially if we have complex code that will only be executed once to make a single object.

We can use `new.target` in a constructor to test if the function was called with the `new` keyword or not. If it wasn't, the property will equal `undefined`; otherwise, it equals the function.

Constructors usually don't have return statements because their only purpose is to, well, construct `this`. If a return is called with an object, that object is returned instead of `this`. If it is empty or called with a primitive, it is ignored.

We can even include methods in the constructor, and these methods can refer to `this`.