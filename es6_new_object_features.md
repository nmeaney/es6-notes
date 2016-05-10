# ES6 New Object Features


### Object.assign()

> Object.assign() enables you to 'copy' Properties from one or more Objects to another.

Object.assign() implements a *Mixin Pattern* where the target Object gains new Properties and Methods without Inheritance.

```js
// Syntax: Object.assign(targetObject, sourceObject1, sourceObject2, ... );
```

Source Objects are assigned in sequence. Each successive source Object will overwrite any previously assigned Property with the same name.

Accessor Methods will be copied as a data Property. This is due to Object.assign using the `=` assignment operator.

Object.assign() operates in a similar fashion to the [`extend`](http://underscorejs.org/#extend) function in the underscore.js library.

```js
// targetObject can be a const which can be Object.assign-ed
// since you're not changing the data type of the variable
const targetObject = { };

let sourceObject1 = {

  name: 'Object2',
  hi() { return `hi ${this.name}`; }
};

let sourceObject2 = { name: 'Object2', list: ['data'] };

// Assign sourceObject1 to targetObject then
// assign sourceObject2 to targetObject, and so on
// Source Objects will overwrite previously assigned data
Object.assign(targetObject, sourceObject1, sourceObject2);

console.log('targetObject:', targetObject); // [object, object]
console.log('targetObject.hi():', targetObject.hi()); // Hi Object2
```


### Object.is()

> Object.is() performs an equality check on any pair of Objects.

```js
// Syntax: Object.is(objectA, objectB);
```

Object.is() operates in a similar fashion to the triple-equality operator `===`.

It returns true if objectA and objectB are of the same type and value.

It also returns true if:

- `NaN === NaN`
- `+0 === -0`

```js
const objectA = { name: 'Al' };
const objectB = objectA;
const objectC = { name: 'Al' }; // Note: objectC is 'identical' to objectA

// Referencing the same object
console.log('objectA IS equal to objectB:', Object.is(objectA, objectB)); // true

// Referencing different objects
console.log('objectA is NOT equal to objectC:', Object.is(objectA, objectC)); // false

console.log('NaN is NOT equal to NaN using ===:', NaN === NaN); // false
console.log('NaN IS equal to NaN with Object.is():', Object.is(NaN, NaN)); // true
```


### Object.setPrototyeOf()

> Object.setPrototypeOf() allows you to change an Object's Prototype after it has been created.

```js
// Syntax: Object.setPrototypeOf(targetObject, newPrototypeObject);
```

This is the reverse of `Object.getPrototypeOf()` method from ES5, which retrieves the Prototype of a given Object.

Object.setPrototypeOf() makes user of the "dunder" `__proto__` accessor for the Prototype Property.


##### __proto__

> `__proto__` is an accessor for the Prototype Property.

It can be specified *once* in an Object Literal. This is the only Property with such behaviour. It will throw an error if it is reassigned.

The computed form `[__proto__]` acts like a regular Property i.e. it does not get or set the Prototype Property.

```js
let parent = {

  type: 'parent',
  name: 'Bill'
};

let child = {

  __proto__: parent,
  type: 'child',
  name: 'Fred',
  // __proto__: {} // Error thrown on reassignment of __proto__
};

let otherParent = {

  type: 'parent',
  name: 'Jill'
};

console.log('child\'s parent name:', Object.getPrototypeOf(child).name);
console.log('Change child\'s Prototype to otherParent');
Object.setPrototypeOf(child, otherParent);
console.log('child\'s parent name:', Object.getPrototypeOf(child).name);
```


### super()

> The super() method references an Object's Prototype.

super() behaves like `Object.getPrototypeOf(this)`, but the `this` binding is setup automatically.

With `super()` you can call any method on an Object's Prototype e.g. `super.someMethod();`.

Super can only be used inside **Concise Methods** i.e. methods that are declared using the new ES6 Concise Method Syntax.


##### [[homeObject]]

In ES6, a method is a function that has an internal **[[homeObject]]** Property, which contains the Object to which the method belongs.

The [[homeObject]] value is only set when an Object is created.

[[homeObject]] is used by `super()` to decide what to do.

If [[homeObject]] is not found then an error is thrown.


### ES6 Object Types

1) **Ordinary** Objects
  - Has all default internal behaviour.

2) **Standard** Objects
  - Standard Objects are Built-In Objects.
  - Objects defined by ES6 e.g. Date, Array, String, etc.
  - But they can also be an Ordinary Object or an Exotic Object.

3) **Exotic** Objects
  - Internal behaviour is different to default behaviour e.g. by overriding a Symbol Property, etc.

4) **Built-In** Objects
  - These are Objects that are present in the JavaScript execution environment.
  - All Standard Objects are Built-In Objects.
