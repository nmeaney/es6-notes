# ES6 Iterables and Iterators

> An Iterable is a data structure whose elements can be enumerated one at a time.

An Iterable is an Object that returns a default Iterator.

An Iterator is an Object with a special Iterable interface.

All JavaScript collection Objects are Iterables i.e. they have a default ```@@Iterator``` Object:

- Strings
- Arrays
- Maps
- Sets
- `arguments` pseudo-array
- Array-like Objects (e.g. DOM Objects)

Generators are also Iterables.


### Iterables

An Iterable returns a default Iterator Object, which implements a `next()` method.

The `next()` method returns a *Results* Object on each call, until all data in the Collection has been traversed.


### Iterators

> Iterators are Objects with a special default Iterable interface.

An Iterable interface is comprised of:

- A `next()` method that returns a *Results* Object
- A *Results* Object containing *value* and *done* roperties:
  - done can be `false` or `true`.
  - value can contain actual data or `undefined`
  - When done is true, there is no more data to return and value is either `undefined` *OR* the `return` value of the Iterator if one exists.

An Iterator manages an internal pointer into a collection of data, which is used for enumeration.


### @@Iterator Symbol

An Iterable is specified with the `@@Iterator` Symbol.

The `@@Iterator` Symbol contains a function that returns an Iterator Object.

The `@@Iterator` Symbol is used to define default Iterators in Objects. It is used to provide a method that returns an Iterator.

The `Symbol.Iterable` Symbol can be used to access the default Iterator, or check if an Object is Iterable:

```js
const isIterable = (someObject) => (typeof someObject[Symbol.Iterable] === 'function') ? true : false;
```


### Iterables and `for...of`

Iterables are designed for use with `for...of`, which automatically enumerates all objects in a Collection.

- `for...of` ignores `return` values in Iterators.

- `for...of` throws an error if run on a non-Iterator.

- `for...of` calls `next()` behind the scenes and exits when `done === true` in the *Results* Object.
