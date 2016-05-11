# ES6 WeakSets

> A WeakSet is a data structure for storing unique values.

There are not many use-cases for WeakSets - maybe they could be used to flag Objects as edited/dirty.


### WeakSet Rules

You cannot iterate the contents of a WeakSet.

You cannot clear a WeakSet, but it does get garbage collected.


### Garbage Collection

Unlike Sets, a WeakSet doesn't prevent it's values being garbage collected, so there are no worries regarding Memory Leaks.


### Examples

```js
// The 3 WeakSet methods (add, has, delete)
// operate like their equivalent Set methods
let editedObjects = new WeakSet();
let objectOne = { name: 'Joe Bloggs' };
let objectTwo = { name: 'Bill Smith' };
let objectThree = { name: 'Jill Jones' };

// Add a value as a referenced Object
editedObjects
.add(objectOne)
.add(objectTwo)
.add(objectThree);

// WeakSet.has(value) checks if a value exists in the Set
console.log('has ObjectOne:', editedObjects.has(objectOne)); // true

// WeakSet.delete(value) removes a value from the Set
console.log('delete ObjectThree:', editedObjects.delete(objectThree)); // true
console.log('has ObjectThree:', editedObjects.has(objectThree)); // false

console.log('has ObjectTwo:', editedObjects.has(objectTwo)); // true
objectTwo = null; console.log('assign objectTwo to null');
console.log('has ObjectTwo:', editedObjects.has(objectTwo)); // false
```
