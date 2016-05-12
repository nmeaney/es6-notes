# ES6 Arrow Functions

> Arrow Functions are a syntactic alternative to anonymous function expressions.

```js
// Arrow function example:
let square = [1, 2, 3].map(num => Math.pow(num, 2));

// is equivalent to:
let square = [1, 2, 3].map(function(num) { return Math.pow(num, 2) });
```

Arrow functions can be passed to other functions as input parameters.

Arrow functions can be used instead of anonymous function expressions.

Arrow functions are also know as *Lambda Expressions*.


### Arrow Function Scope

In arrow functions, the `this` keyword refers to the containing scope i.e. `this` is lexically-bound correctly; it is not dynamically bound.

This means that you don't need to use something like `var self = this;` in order to reference the outer scope from inside an arrow function.


### Empty Arrow Functions

An empty Arrow Function returns `undefined`.

```js
let empty = () => { };

console.log(empty()); // undefined
```

### Input Parentheses

Parentheses are required if there are no arguments.

Parentheses are required for multiple arguments.

Parentheses are *not* required for a single argument.

```js
// An empty arrow function returns undefined
// Parentheses are required if there are no arguments
let empty = () => { };
console.log(empty()); // undefined

// Parentheses are required for multiple arguments
let add = (a, b) => a + b;
console.log(sum(4, 4)); // 8

// Parentheses are not required for a single parameter
let doubler = x => x * 2;
console.log(add(44)); // 88
```


### Single Expression Syntax

Curly braces `{ }` are not required for single expression functions.

The `return` keyword is implied in single expression statements.

```js
// Curly braces are not required for single expression functions
// return is implied in single expression statements
let square = x => x * x;
// is equivalent to:
// let square = function(x) { return x * x; }

console.log(square(12)); // 144
```


### Multi-Expression Syntax

A `return` statement is required in multi-expression arrow functions.

```js
// A return statement is required in multi-expression arrow functions
let addMore = (a, b, c) => {

  let result = a + b + c;
  return result;
}

console.log(addMore(1 ,3, 4)); // 8
```
