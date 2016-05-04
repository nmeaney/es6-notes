# ES6 Sets

> A Set is an Iterable Collection of *unique* values.

A Set is a data structure for storing unique values.


### Iterating Sets

You can retrieve an Iterator for a Set by calling one of 3 special functions:

- `values()` - returns an Iterator whose data is the Sets's values.
- `keys()` - returns an Iterator whose data is the Set's values (i.e. the same as `values()`).
- `entries()` - returns an Iterator whose values are the Sets's values as 2-item arrays `[value, value]`.

Use a `for...of` loop with these functions to enumerate Set data.

You can also use `forEach` for functional iteration of Sets.

The order of insertion is preserved when iterating Sets.

The default Iterator for Sets is `values()`.


### Set Examples

```js
// Create a set using an Iterable e.g. an Array
let data = ['first' , 'second', 'third', 'fourth'];
let someSet = new Set(data);

// Adding an item a second time has no effect
// Note also that Set.add(value) is chainable
for (let item of data) { someSet.add(item); }

// Iterating Sets
console.log('keys:', ...someSet.keys());
console.log('values:', ...someSet.values());
console.log('entries:', ...someSet.entries());

// entries() is the default Set Iterator
someSet.forEach((value, key, set) => console.log('item:', value, key, set));

// The size property is number of items in a Set
console.log('Size:', someSet.size); // 4

// Set.has(value) checks if an item exists in a Set
console.log('has 2:', someSet.has('second')); // true
console.log('has 5:', someSet.has('fifth')); // false

// Set.delete(value) removes an item from the Set
console.log('delete 3:', someSet.delete('third'));
console.log('size:', someSet.size); // 3

// Set.clear() empties the Set
console.log('clear:', someSet.clear()); // undefined
console.log('size:', someSet.size); // 0
```


### Key Comparison Rules

Key comparison uses the internal operator `sameValueZero`.

This works the same as the triple-equality operator `===`, ***EXCEPT***:

- `(NaN === NaN)` is true
- `(+0 === -0)` is true

Different Objects are not considered equal, even if they "look" the same.


### Notes

Unlike Maps, Sets do not have a `get()` method.

The spread `...` operator converts a Set to an Array and vice versa.

Converting an array to a Set and back again will remove all duplicates:

```js
var someArray = [1, 2, 3];
var someSet = new Set(someArray);

someArray = [...someSet];
someArray.push(3);

console.log('someArray:', someArray); // 1,2,3,3
console.log('Spread to someSet', [...new Set(someArray)]); // 1,2,3
```
