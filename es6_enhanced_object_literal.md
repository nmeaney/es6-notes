# ES6 Enhanced Object Literals

In ES6 the Object Literal syntax has been enhanced and simplified.


### Concise Property Syntax

A Property name can be inferred from it's associated variable name.

```js
let someProperty = 'Hello';

// The following two lines are equivalent
var someObject = { someProperty: someProperty };
var someObject = { someProperty };

console.log(someObject.someProperty); // 'Hello'
```


### Computed Property Names

Property names can be dynamically generated in Object Literals using square bracket notation.

```js
let someObject = {

  foo: 'bar',
  ['prop_' + foo()]: 42,
  ['year' + new Date().getYear()]: true

}

console.log(someObject.prop_bar); // 42
console.log(someObject.year2016); // true
```


### More on Property Names

For duplicate Property names, the last one defined in the Object Literal is used.

Property names can be **Symbols**.


### Concise Method Syntax

The `function` keyword is no longer required for methods.

A colon `:` is no longer required between a Property name and value.

Methods can be Generators which are indicated by a prefix asterisk: `*someMethod(x)`.

Arrow functions are *NOT* allowed in Object Literals.

Comma separators are still required.

```js
let name = 'Joe';

let someObject = {

  // The 'function' keyword is no longer required for methods
  // A colon ':' is no longer required between a Property name and value
  multiply(x) {

    return x * x;
  }, // Comma separator is still required

  // Methods can be Generator Functions
  // specified with a prefixed asterisk
  *double(x) {

    yield x + x;
    return;
  }

  // Arrow functions are NOT allowed in Object Literals
  // pi() => 3.1415;
};

// Using someObject's 'double' Generator function
let doubler = someObject.double(4);

console.log(someObject.multiply(4)); // 16
console.dir(doubler.next().value);   // 8
console.dir(doubler.next().value);   // undefined - Generator has completed
```
