# ES6 Maps

> A Map is an data structure for mapping values to values.

A Map is an Iterable Collection of key-value pairs.

Any arbitrary data can be used as a key or a value (for example, an Array, an Object or even NaN).


### Iterating Maps

You can retrieve an Iterator for a Map by calling one of 3 special functions:

- `keys()` - returns an Iterator whose values are the Map's keys.
- `values()` - returns an Iterator whose values are the Map's values.
- `entries()` - returns an Iterator whose values are the Maps's keys and values as 2-item arrays `[key, value]`.

Use the `for...of` construct with these functions to enumerate Map data.

You can also use `forEach` for functional iteration of Maps.

The order of insertion is preserved when iterating Maps.

The default Iterator for Maps is `entries()`.


### Map Examples

```js
// Create a Map and set a value to a key
let someMap = new Map([[1, 'won']]);

// Map.set() will update the value if the key exists
let data = [[1, 'one'], [2, 'two'], [3, 'three'], [4, 'four']];
for (let item of data) { someMap.set(...item); }

// Map.set() is chainable
someMap.set(0, 'ZERO') // This will be inserted after other values
  .set(1, 'ONE')
  .set(2, 'TWO')
  .set(3, 'THREE')
  .set(4, 'FOUR');

// Iterating Maps - Insertion order is preserved
// Note we use the ... spread operator to provide
// individual Set items for display by console.log
console.log('keys:', ...someMap.keys());
console.log('values:', ...someMap.values());
console.log('entries:', ...someMap.entries());

// entries() is the default Map Iterator
someMap.forEach((value, key, map) => console.log('item:', key, value, map));

// The size property is number of items in a Map
console.log('Size:', someMap.size); // 4

// Map.has(key) checks if an item exists in a Map
console.log('has 2:', someMap.has(2)); // true
console.log('has 5:', someMap.has(5)); // false

// Map.get(key) return the matching value
console.log('value of key 3:', someMap.get(3)); // three

// trying to get a non-existant key returns undefined
console.log('value of key 5:', someMap.get(5)); // undefined

// Map.delete(key) removes an item from the Map
console.log('delete key 3:', someMap.delete(3));
console.log('size:', someMap.size); // 3

// Map.clear() empties the Map
console.log('clear:', someMap.clear());
console.log('size:', someMap.size); // 0
```


### Key Comparison Rules

Key comparison uses the internal operator `sameValueZero`.

This works the same as the triple-equality operator `===`, ***EXCEPT***:

- `(NaN === NaN)` is true
- `(+0 === -0)` is true

Different Objects are not considered equal, even if they "look" the same.
