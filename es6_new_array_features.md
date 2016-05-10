# ES6 New Array Features


### Iterating Arrays

You can retrieve an Iterator for an Array by calling one of 3 special functions:

- `keys()` - returns an Iterator whose data is the Array's indexes.
- `values()` - returns an Iterator whose data is the Array's values.
- `entries()` - returns an Iterator whose data is the Array's indexes and values as 2-item arrays e.g. `[index, value]`.

The default Iterator for Arrays is `values()`.

You can use the `for of` construct to enumerate the output of these Iterators.

You can use the Spread operator `...` to convert the Iterator output to an Array.

```js
let someArray = ['AAA', 'BBB', 'CCC'];

// [0, "AAA"] [1, "BBB"] [2, "CCC"]
// Use spread `...` operator to output each [index, value] entry
console.log('someArray.entries():', ...someArray.entries());

// Using for-of
for (let item of someArray.entries()) { console.log(item); }
```


### Array.fill()

> Array.fill() populates an Array with data.

The `startIndex` and `endIndex` parameters are optional. If they are not supplied, the whole Array will be filled with `data`.

```js
// Syntax: Array.fill(data, startIndex, endIndex);

let someArray = new Array(5);

// ['Hello', 'Hello', 'World', 'World', 'World']
console.log(someArray.fill('Hello', 0, 2).fill('World', 2, 5));

// ['ok', 'ok', 'ok', 'ok', 'ok']
console.log(someArray.fill('ok'));
```


### Array.find()

> Array.find() returns the first Array item that satisfies the callback function, or `undefined` if not found.

Array.find() ignores 'holes' in Arrays  (i.e. `undefined` values).

```js
// Syntax: Array.findIndex(callback(item, index, array), thisArgument);

let someArray = ['first', 'second', 'third'];
let longerThenFive = someArray.find((el, i, arr) => el.length > 5);

console.log('find first element longer then 5 characters:', longerThenFive); // 'second'
```


### Array.findIndex()

> Array.findIndex() returns the index of the first Array item that satisfies the callback function, or` -1` if not found.

Array.findIndex() ignores 'holes' in Arrays.

```js
// Syntax: Array.findIndex(callback(item, index, array), thisArgument);

let someArray = ['one', 'two', 'three', 'four', 'five'];
let firstEven = someArray.findIndex((el, i, arr) => (el.length % 2) === 0);
let notFound = someArray.findIndex((el, i, arr) => el === 100);

console.log('firstEven:', firstEven); // 3 i.e. element 'four'
console.log('notFound:', notFound); // -1
```

### Array.from()

> Array.from() converts an array-like Object to a real Array.

An array-like Object is an Object with a length Property and indexed elements e.g. the `arguments` Object in every `function`.

Array.from() ignores 'holes' in Arrays, which means that you can use it to create and populate an Array.

Array.from() can be considered an alternative to Array.map().

```js
// Syntax: Array.from(arrayLikeObject, callback(item, index, array), thisArgument);

let arrayLikeObject = {

  0: 10,
  1: 20,
  2: 30,
  length: 3
};

// The callback function squares each value before it's assigned to realArray
let realArray = Array.from(arrayLikeObject, (item) => item * item);
console.log('Array.from an Array-like Object:', realArray); // [100, 400, 900]

// Create an array with values from start to end (uses an array-like object as a 'seed')
const range = (start, end) => Array.from({ length: end + 1 - start }, (v, k) => start + k);
console.log(range(5, 10)); // [5, 6, 7, 8, 9, 10]
```


### Array.of()

> Array.of() creates an Array with the given values as elements.

Array.of() takes the type and amount of arguments and created an Array from them.

For example, `Array.of(5)` creates an Array with one item - the number 5 - `[5]`.

This is not the same as an Array seeded with a number (e.g. `new Array(3)`), which will create an array of length 3 comprised of `undefined` items `[,,]`.

```js
// Syntax: Array.of(data);

// Returns Array with 5 empty items i.e. 'holes' [,,,,]
console.log('using new Array(5):', new Array(5));

// Returns Array with 1 item: [5]
console.log('using Array.of(5):', Array.of(5));

// Returns Array with 3 items: [5, 'five', Object]
console.log('using Array.of(5, \'five\', { \'FIVE\': 5 }):', Array.of(5, 'five', { 'FIVE': 5 }));
```
