# ES6 Symbols

> A Symbol is a unique and immutable data type and may be used as an identifier for Object Properties.

Symbols are a new **Primitive Type** (joining `String`, `Number`, `Boolean`, `null` and `undefined`).

Symbols do not have a literal form.

Symbols can be used for non-string Property names.

Symbols are represented with an `@@` prefix in documentation.

Symbols can have a descriptive name.

Symbol Properties are:

- Non-enumerable by default
- Discoverable (not private)


### Use of Symbols

Symbols can be used anywhere you can use a **Computed Property Name**, for example:

- Classes
- Object Literals
- Square bracket notation
- `Object.defineProperty()`
- `Object.defineProperties()`

Symbols *cannot* be used with dot.notation.


### Examples

```js
// Create a Symbol
// No need for 'new' keyword since Symbols are primitive
// Using 'new' would throw an error
const usernameSymbol = Symbol('User Name');

// Use a Symbol
let myObject = {

  // Computed property syntax
  [usernameSymbol]: 'Joe Bloggs'
};

// Square bracket property syntax
console.log(myObject[usernameSymbol]);

// typeof returns 'symbol'
console.log(typeof usernameSymbol);
```


### Accessing Symbol Properties

All Objects start off with zero own-Symbol properties (though they may have inherited Symbol Properties).

You can access Symbol properties using `object.getOwnPropertySymbols()` which returns an array of Symbols.

The `object.getOwnProperties()` method does not return Symbols, since Symbols are technically not property names.


### Global Symbol Registry

The **Global Symbol Registry** is a sharable registry of Symbols.

It exists in a shared environment (such as the global object).

It is best practice to namespace your App's Symbols to avoid name collisions.

The `for()` method writes a Symbol to the Registry if it doesn't exist OR returns the existing Symbol.

The `keyFor()` method returns the key associated with a Symbol, OR `undefined` if it doesn't exist.

```js
// 'user_id' is the key in the Global Symbol Registry
let uid = Symbol.for('user_id');

console.log(Symbol.keyFor(uid)); // user_id
console.log(Symbol.keyFor(cid)); // ReferenceError: cid is not defined
```


### Well Known Symbols

**Well Known Symbols** are predefined Symbols that expose common internal-only operations that can be used in application Objects.

They are represented by Prototype Properties on the Symbol e.g. `Symbol.create` for the `@@Create` Symbol.

For example, the `@@toStringTag` Symbol determines what to return when you run `toString` on an Object:

```js
let userObject = {

  [Symbol.toStringTag]: 'Hello There'
}

console.log(userObject.toString()); // [object Hello There]
```
