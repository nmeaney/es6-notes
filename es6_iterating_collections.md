### ES6 Iterating Collections

> Collections are Iterable data structures that can be enumerated with an Iterator.

For example:
- Strings
- Arrays
- Maps
- Sets
- `arguments` pseudo-array
- Array-like Objects (e.g. DOM Objects)

You can retrieve an Iterator for a Collection by calling one of 3 special Iterator functions:

- `keys()` - returns an Iterator whose data is the collections's keys.
- `values()` - returns an Iterator whose data is the collections's values.
- `entries()` - returns an Iterator whose data is the collections's keys and values as 2-item arrays `[key, value]`.

You can use the spread operator `...` to convert an the output of these functions into an Array.


### Default Iterators

The default Iterator for Arrays and Sets is `values()`.

The default Iterator for Maps is `entries()`.

The default Iterator for Strings operates on characters (and not *code-units* i.e. bytes).


### values()

Returns an Iterator whose values are the Collection's data values.

Returns the exact data container in the *value* Property of the *Results* Object (as returned by `next()`).


### entries()

Returns an Iterator whose values are the Collection's key-value pairs as a 2-item array.

- Arrays return `[index, value]`
- Sets return `[value, value]`
- Maps return `[key, value]`


### keys()

Returns an Iterator whose values are the Collection's keys.

- Arrays - returns numeric indexes only.
- Sets - In Sets, keys contain values, so values are returned.
- Maps - Keys are returned.
