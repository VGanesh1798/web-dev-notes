# Javascript Data Types

Javascript has seven primitive data types in addition to some built-in objects. All of these data types have some associated methods.

## Primitive Methods
Objects are useful since they can have functions and other objects as properties, but this comes at the cost of complexity. Thankfully, the primitive data types have some methods of their own that can be accessed by special object wrappers. As an example, the `str.toUpperCase()` method is accessed by the primitive string, and then a new, special object is created with the property `toUpperCase`. This is executed, and then the special object is destroyed.

It is also possible to use the wrappers manually with statements like `new Number(2)`, but this is unrecommended as it has type problems. Using a wrapper without `new` is okay, though.

As you may have guessed, `null` and `undefined` have no methods.

## Number
When calling a method on a number literal, we will need to use two dots. The first dot is treated like a decimal point, while the second is the accessor operator. An alternative is to enclose the literal in parentheses.

Number literals are double precision floating point numbers. We can use e-notation with number literals as well, and the numbers can be decimal, hex, octal, or binary. To use a hex number, add a `0X` or `0x` to the front of the number. Octal uses `0O` and `0o`, and binary uses `0B` and `0b`. Other numeral systems will use `parseInt()`.

The `toString(base)` method for a number returns a string representation of a number in the specified base. The minimum base value is 2, and the highest is 36.

We can round by calling methods for the `Math` object: `Math.floor`, `Math.ceil`, `Math.round`, and `Math.trunc`. The last one is not supported by Internet Explorer. Another useful method for numbers is `toFixed(n)`, which fixes the floating point and returns a string. We can convert this string back into a number using the unary plus or the `Number()` wrapper.

If a number is too big, it will return as `Infinity`. Additionally, Javascript suffers from loss of precision for small values just like other languages. 0.1 + 0.2 evaluates to 0.30000000000000004 instead of 0.3, which will cause errors in conditionals. Luckily, the tiny loss of precision is often rounded away so we don't see it, but over time the losses add up. To avoid this outright, we can fix the floating point or multiply numbers to turn them into integers before dividing back; this second option won't remove error entirely but just makes it smaller. One more quirk is that `0` and `-0` are technically two different values since one has a sign bit. They are treated the same by operators.

We can use `isNaN(value)` to convert things into numbers and check if they are `NaN`. The comparison `value === NaN` is invalid because `NaN` is equivalent to nothing, not even itself. `isFinite(value)` returns a boolean value whether or not the value (when converted to a number) is finite or not. Compare these to the `Object.is()` method, which returns true for `NaN` and `NaN` but false for `0` and `-0`.

`parseInt()` and `parseFloat()` are less strict than the unary operator and the `Number()` constructor because they can extract numbers out of strings like `"15px"`. There are cases where these functions return `NaN`, such as when a non-numeric character terminates the parsing and no numbers have been read. The two functions also have a second, optional parameter to specify the **radix**, or base.

The `Math` object has some more useful methods like `Math.random()`, `Math.max(a, b, c...)`, etc.

## String
String literals are internally formatted in UTF-16 for Javascript, regardless of what the encoding is for the page. 

In addition to the benefits described earlier, backticks allow us to specify a template function before the string, with the syntax `` func`string` ``. The function receives the string and its embedded expressions and processes them.

Javascript has escape sequences.

An important string property is `length`, which is self-explanatory. Strings can be indexed using brackets or with the older `charAt(pos)` method. We can use `for...of` to iterate over characters.

Strings are immutable in Javascript, so one workaround is to create a whole new string and reassign that to the variable. We can change the case of a string with the `toUpperCase()` and `toLowerCase()` methods.

There are multiple methods to look for substrings, one of which is `indexOf(substr, pos)`. This will either return the position where the match was found, or a `-1` if no match was found. The `pos` parameter is optional and only specifies from what position to begin searching. To find *all* occurrences, we can use the method in a loop. The more modern method is `includes(substr, pos)`, which returns a boolean value. The methods `startsWith(substr)` and `endsWith(substr)` do just as they say.

We can use `slice` to get a substring. It slices from a start position up to, but not including, an end position. If no end position is specified, the slice travels through to the end of the string. We can also use negative values to index from the end to the beginning. The `substring` method is similar to `slice`, but it returns everything between the start and end, allowing the start to be greater than the end. Negative values are not supported. Lastly, the `substr` method takes a length parameter in addition to a start position. Negative values work.

String comparisons are made alphabetically, although lowercase letters are greater than uppercase letters and letters with accent marks will be "out of order". We can get the unicode code for a character at a position by using the `codePointAt(pos)` method. We can create a character from its code by using `String.fromCodePoint(code)`. Using `\u` followed by the hex code will allow us to add unicode characters too. To make a good comparison, we can use the `localeComparison(str2)` method, which returns `-1` if `str` is less than `str2`, `1` if `str` is greater than `str2`, and `0` if they are equal.

Most symbols have a 2-byte code, but this isn't enough to represent every Unicode character. Rare characters are encoded with a pair of 2-byte characters called a surrogate pair, but they are not processed correctly; for example, these rare characters will have a length of 2. The code methods above can deal with surrogate pairs correctly.

For diacritical marks, we can use hex codes to insert special mark characters on letters, but this can be ambiguous sometimes when two different character combinations have the same visual representation. To fix this, the `normalize()` method can being each string to its normal form.

## Array
Arrays can either be constructed using `new` or can be declared using an array literal. Elements of any type can be added on, and the `length` property can be used. Just like objects, arrays can have a trailing comma. Extra commas throughout will be considered `undefined` indices.

Arrays can be used as queues with the `push` and `shift` methods or as stacks with the `push` and `pop` methods. An additional method allows us to prepend elements: `unshift`.

Arrays are objects, so they are passed by reference. This means that we can break them if we try to use them like normal objects: If we make "gaps" in indices, if we try to fill them in reverse, or if we add non-numeric properties to arrays. Additionally, `for...in` loops aren't a good idea with arrays because this loop will iterate over other, non-numeric properties of the array. Stick to `for...of` loops with arrays.

We can clear arrays by resetting their length property to `0` (this can also truncate arrays if we use a different value), or we can set the variable equal to a `new Array()`. Doing so might accidentally create an array with `undefined` elements, so be careful using it.

Arrays can be multidimensional.

Arrays implement their own version of `toString`, but don't have a viable `Symbol.toPrimitive` or `valueOf`.

## Array Methods
Arrays can make use of the `delete` keyword for objects, but this won't shift the array. It only removes the key and sets the element to `undefined`. The `splice` method is much more powerful. It is structured like 