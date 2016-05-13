# ES6 Rest & Spread Operators

> **Rest** combines multiple function parameters into a single Array.

> **Spread** inserts Iterator values into Arrays or function calls.

Rest and Spread both use the `...` syntax.

The context determines which functionality is performed.


### Rest Parameters in Functions

*Think of it as "the rest of the parameters in a function call become an Array"*.

Rest can be used to replace the `arguments` pseudo-Array with a real Array.

```js
let [x, y, ...z] = [1, 2, 3, 4, 5];

console.log(x); // 1
console.log(y); // 2
console.log(z); // [3, 4, 5]
```


### Spread Operator

*Think of it as "spreading out the values of an Iterable into individual values e.g. like fanning a deck of cards"*.

Spread can operate on all Iterables - Maps, Sets, Arrays, Strings, etc.

Spread can convert an Iterable into the elements of an Array.

Spread can convert an Iterable into the arguments of a function call.

Spread can be used to expand an Array in places where multiple values are expected.

Spread can be used to replace `function.prototype.apply`.

```js
let someData = new Set();

someData.add(1);
someData.add(2);
someData.add(3);

// Spread values from the Set
// into the items of an Array
let someArray = [...someData];

console.log(someArray); // [1, 2, 3]
```
