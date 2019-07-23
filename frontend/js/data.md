# Javascript Data Types
Javascript has seven primitive data types, an `Object`, and some built-in objects and data structures. Each of these has its own methods and properties that can be used for various functionality.

## Numbers
- Numbers in Javascript can represent integers or floating point numbers
- Numbers can also be positive/negative `Infinity` or `NaN`
- The `BingInt` data type does have have access to the `Math` object

### Number Literals
- Number literals can be expressed in four numeral systems:
  - Decimal, like `42`
  - Binary, like `0b11` or `0B11011`
  - Octal, like `057`
    - If in ES6, octal numbers are formed like `0o10` or `0O473`
  - Hexadecimal, like `0x132` or `0X3AF5`
- Additionally, number literals can be wirrten using exponent notation like `1E3` or `2e5`

### `Number` Object
The `Number` object has some built-in properties like `Number.MAX_VALUE` and some built-in methods like `Number.isNaN()`. There are also some methods for `Number.prototype` to retrieve information from `Number` objects in various formats.

### Math and Dates
The `Math` object has many methods for mathematical constants and functions, and it cannot be used to create our own `Math` object.

The `Date` object can be used to manipulate dates since there is no data type for dates in Javascript.

## Strings
- Can use either single or double quotes
- Has all the usual escape sequences
  - The `\x` escape sequence can be used for hexadecimals
  - The `\u` escape sequence can be used for Unicode characters
    - ES6 added Unicode code point escapes
- The `String` object is a wrapper for the primitive data type and has some properties and methods for string manipulation
  - These can be accessed by string literals
- Multiline template strings use backticks

### Internationalization
The `Intl` object is a namespace for the Internationalization API and provides three main objects:
- `DateTimeFormat` for formatting date and time
- `NumberFormat` for formatting numbers like currencies
- `Collator` for comparing and sorting strings

## Regular Expressions
Regular expressions can either be declared literally by placing the pattern between slashes, like `/ab+c/`, or using the `RegExp` object constructor.

There are a lot of unique regex characters for pattern matching in addition to the main ones, and the `RegExp` and `String` objects have some methods for dealing with regular expressions.

## Boolean
The `Boolean` object constructor takes truthy and falsy values. When performing boolean comparisons, falsy values are all evaluated to false:
- `false`
- `undefined`
- `null`
- `0`
- `NaN`
- `""`

All other values, including objects, evaluate to true. Note that `"0"` and `" "` are **not** falsy.

Oddly, `null` and `undefined` are considered equal to each other but not to other falsy values. In numeric contexts they are converted to `0` and `NaN` respectively.

## Indexed Collections
Javascript has two indexed collections, one of which was introduced fairly recently.

### Array
- Arrays can either be constructed using `Array` or declared literally
  - Trailing commas in an array literal are ignored (only the last one)
    - Empty commas create indices with `undefined` elements
