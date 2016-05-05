# ES6 Generators

> Generators are functions that can suspend execution and resume it later.

Generators are indicated with an asterisk `*`:

- With a function declaration or expression by *postfixing* the asterisk to the function keyword: `function*`

- Inside an Object or Class by *prefixing* the asterisk to the method name: `*someMethod()`, `*[someComputedMethodName]`.

The code in a Generator starts executing the first time you call the Generator's `next()` method, and stops when a `yield` statement is encountered. Execution continues on the subsequent call to `next()`.

Generators are Iterables that can be traversed with `for...of`, which has implicit `next()` calls.

A `return` statement in a Generator indicates that all work is done and subsequent code will be unreachable. Note that `for...of` ignores `return` statements.


### Examples

```js
function* range(start, end, step) {

  while (start < end) {

    // output start variable
    yield start;

    // Continue execution on subsequent
    // next() call or for...of iteration
    start += step;
  }
}

let myGenerator = range(0, 10, 2);
console.log(myGenerator.next().value); // 0
console.log(myGenerator.next().value); // 2
console.log(myGenerator.next().value); // 4
console.log(myGenerator.next().value); // 6
console.log(myGenerator.next().value); // 8
console.log(myGenerator.next().value); // undefined

//
for (let i of range(0, 10, 2)) {

  console.log(i);
}
```


### yield

In Generator functions, execution will pause when a `yield` statement is encountered.

The `yield` statement is like a 'temporary' `return` statement.

The `yield` statement accepts data from `next()` and returns data to `next()`.
Generators can output a value with `yield` without finishing execution.


### yield Expressions With Assignments

In a `yield` expression with an assignment, the right-hand-side is evaluated on the first `next()` call, but the left-hand-side of the expression must wait for the ***subsequent*** call to `next()` before continuing execution.

```js
// Inside a Generator ...
let localVariable = yield outputData;

// The yield statement returns outputData to the calling code
// and pauses execution on the right-hand-side of the expression.

// Execution will resume on the left-hand-side of the expression when the
// subsequent next()  call is received i.e. localVariable will be
// assigned any data input to the subsequent next() call.
```


### next()

A Generator starts running the first time you call its `next()` method, and stops when a `yield` statement is encountered.

When an argument is passed to `next()`, it becomes the value of the `yield` statement.

The first call to `next()` is a special case where any argument passed is ignored.

The `next()` method returns a *Results* object with 2 properties:

- *done* - true || false - indicates whether the Generator has run to completion.

- *value* - data || `undefined` - the most recent value yielded or returned, or `undefined` if `done === true`.

```js
// Outside the Generator ...
let generatorOutput = someGenerator.next(someData);

// Inside the Generator ...
let localVariable = yield outputData;

// 1. outputData will be delivered as the return value of next(someData)
//    and will be assigned to the generatorOutput variable

// 2. someData is input via next(someData) and will be assigned
//    to the Generator's localVariable on the subsequent next()
```


### Yielding to Iterables and Generators

The `yield*` syntax can be used to nest any sort of Iterable, including those derived from Generators.

For example, `yield* "some string";` will call the String's default Iterator.

**Generator Delegation** means yielding to another Generator with the `yield*` syntax.


```js
function* splitString(someString) {

  yield* someString;
}

for (let character of splitString('Hello There')) {

  console.log(character);
}
```


### Notes

Generators don't need Consumer/calling/controller code; you can immediately invoke a Generator.

Generators can work with Promises to make asynchronous code appear synchronous (i.e. to provide the ES7 proposed async/await-style functionality).
