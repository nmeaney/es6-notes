# ES6 WeakMaps

> A WeakMap is a data structure for mapping Objects to values.

WeakMaps are suitable for storing key/value pairs where the key may disappear sometime in the future (e.g. a Collection of DOM elements).

WeakMaps are good for attaching data to Objects.

WeakMaps can have any arbitrary values.


### WeakMap Rules

In a WeakMap, keys must be **Object References**.

You cannot iterate the contents of a WeakMap.

You cannot clear a WeakMap, but it does get garbage collected.


### Garbage Collection

Unlike a Map, a WeakMap doesn't prevent it's keys from being garbage collected, so there a no worries about memory leakage.

If a key is garbage collected, it's related value will be subsequently garbage collected, since it is no longer referenced.


### Examples

```js
// The 4 WeakMap methods (get, set, has, delete)
// operate the same as their equivalent Map methods
let someWeakMap = new WeakMap();
let objectOne = { name: 'Joe Bloggs' };
let objectTwo = { name: 'Bill Smith' };
let objectThree = { name: 'Jill Jones' };

// WeakMap.set() assigns a value to a key
// Keys must be referenced Objects
someWeakMap
.set(objectOne, 'first')
.set(objectTwo, 'second')
.set(objectThree, 'third');

// WeakMap.has(key) checks if an item exists
console.log('has ObjectOne:', someWeakMap.has(objectOne)); // true

// WeakMap.get(key) retrieves the value specified by a key Object
console.log('get ObjectTwo:', someWeakMap.get(objectTwo)); // second
console.log('get ObjectThree:', someWeakMap.get(objectThree)); // third

// WeakMap.delete(key) removes an item from the WeakMap
console.log('delete ObjectThree:', someWeakMap.delete(objectThree)); // true
console.log('has ObjectThree:', someWeakMap.has(objectThree)); // false

// Value 'second' will be garbage collected when objectTwo no longer exists
objectTwo = null; console.log('assign objectTwo to null');
console.log('get ObjectTwo:', someWeakMap.has(objectTwo)); // undefined

// Now only one item exists
console.log('get ObjectOne:', someWeakMap.get(objectOne)); // first
```
