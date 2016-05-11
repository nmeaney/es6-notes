# ES6 New String Methods

### String.startsWith(), String.endsWith() and String.includes()

> Check a String for the existence of a substring.

These functions can accept an optional start and end position.

These functions do not work with Regular Expressions.

```js
let someString = 'Hello there';

// Syntax: String.startsWith(subString, startPosition, endPosition);
console.log('starts with "He":', someString.startsWith('He')); // true
console.log('starts with "Ha":', someString.startsWith('Ha')); // false

// Syntax: String.startsWith(subString, startPosition, endPosition);
console.log('ends with "lo":', someString.endsWith('lo')); // true
console.log('ends with "hi":', someString.endsWith('hi')); // false

// Syntax: String.includes(subString, startPosition, endPosition);
console.log('includes "her":', someString.includes('her')); // true
console.log('includes "cat":', someString.includes('him')); // false
```

### String.repeat()

> Repeat a string a number of times.

```js
// Syntax: String.repeat(count);
console.log('ok '.repeat(3)); // ok ok ok
```


### String.raw()

> String.raw() is a Template Tag function that returns the unescaped content of a String.

```js
console.log(String.raw`My \t name is \n Joe.`); // 'My \t name is \n Joe.'
```


### Unicode Methods

> String.normalize() and String.fromCodePoint() convert numbers representing unicode code-points into a String.

> String.codePointAt() converts a code-point at a String index into a number.

```js
// Syntax: String.normalize('NFC')

// Syntax: String.fromCodePoint(codePoints)

// Syntax: String.codePointAt(index)
```
