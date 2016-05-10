# ES6 New Number Features

In ES6 some global Number functions have been moved under the Number Object namespace.

In JavaScript numbers are either 64-bit Floats or 32-bit Integers.


### New Constants

> There are two new constants to define JavaScript's safe Integer boundaries.

JavaScript's safe Integer range is 2^-53 to 2^+53.

```js
// Values are from Google's V8 JavaScript engine as used in Node.js
console.log('Number.MAX_SAFE_INTEGER:', Number.MAX_SAFE_INTEGER); // 9007199254740991
console.log('Number.MIN_SAFE_INTEGER:', Number.MIN_SAFE_INTEGER); // -9007199254740991
```


### Number.isInteger()

> Number.isInteger() checks if a value is an Integer.

Number.isInteger() always returns `false` for non-numbers.

Note: `25.0` is stored as `25` in JavaScript and is treated as an Integer.

```js
console.log('Is 24.0 is an Integer?', Number.isInteger(24.0));  // true
console.log('Is 24.01 is an Integer?', Number.isInteger(24.01)); // false
```


### Number.isSafeInteger()

>  Number.isSafeInteger() checks if a value is an Integer within JavaScripts safe Integer range.

Number.isSafeInteger() identifies Integers that can be accurately represented by JavaScript.


### Number.isFinite() and Number.isNaN()

> Number.isFinite() checks if a value is a finite number i.e. not =/- INFINITY.

> Number.isNaN() checks if a value is not a number.

The existing global version of these two functions pass the input value through `Number()` before the comparison is performed. This can lead to confusing results. Number.isFinite() and Number.isNaN() improve on their global equivalents by not passing the input value through `Number()`.

Number.isFinite() and Number.isNaN() return false when passed a non-number.

Note: NaN is the only Primitive value not equal to itself i.e. `isNaN(NaN)` is true. HOWEVER, in ES6 `Object.is(NaN) === NaN` is false.

```js
console.log('Is Math.PI a number?', !Number.isNaN(Math.PI)); // true (3.141592653589793)
console.log('Is Math.INFINITY finite?', Number.isFinite(Math.INFINITY)); // false
```


### Number.parseInt() and Number.parseFloat()

> Number.parseInt() and Number.parseFloat() convert Strings to Numbers.

The global functions `parseInt` and `parseFloat` have been moved to the Number Object with no change in functionality.
