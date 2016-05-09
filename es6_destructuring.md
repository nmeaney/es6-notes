# ES6 Destructuring

> Destructuring lets you extract data from an Array, Object or String and assign it to multiple variables in a single operation.

Destructuring is *fail-soft* - it produces `undefined` when a value is not found. It does not throw an error.

Destructuring is also known as **Destructured Assignment**.


### Array Destructuring

Array destructuring provides a shorthand for assigning values from elements in a Array to variables.

```js
let someArray = ['Hello', 'there', 'World'];

// Syntax: let [some, variables] = values in Array;
// Note: skipped second element
let [firstElementValue, , thirdElementValue] = someArray;

console.log(firstElementValue, thirdElementValue);  // 'Hello World'
console.log(secondElementValue); // undefined
```


### Object Destructuring

Object destructuring provides a shorthand for assigning values from Properties in an Object to variables.

```js
// EXAMPLE 1
let numbers = { one: 1, two: 2, three: 3, four: 4 };

// Syntax: let { fromProperty: toVariable } = Object;
let { three: third, four: fourth } = numbers;

console.log(third, fourth); // 3 4

// EXAMPLE 2
// Shorthand Syntax: { x, y } is the same as { x: x, y: y }
let person = {

  firstName: 'Joe',
  middleInitial: 'W',
  lastName: 'Bloggs'
};
let { firstName, lastName } = person;

console.log(firstName, lastName); Joe Bloggs
```


### Function Parameter Destructuring

Function Parameter Destructuring maps from a single function argument (e.g. an Object) into multiple variables in the function.

```js
// Map from input Object Properties to individual variables
// i.e. map from Object.firstName to variable first with a
// default value of 'Bill' if Object.firstName is not supplied
function sayHello({ firstName: first, lastName: second }) {

  console.log(first, second);
}

console.log(sayHello({ firstName: 'Joe', lastName: 'Bloggs' })); // Joe Bloggs
```


##### Destructuring & Default Values

Destructuring can provide default values to function arguments.

```js
// The first variable has a default value of 'Bill'
// which is used if firstName is not supplied to function
function sayHello({ firstName: first = 'Bill', lastName: second }) {

  console.log(first, second);
}

console.log(sayHello({ lastName: 'Bloggs' })); // Bill Bloggs
```


### String Destructuring

Strings Destructuring can be achieved using a square-bracket syntax.

```js
let [first, second, , , fifth] = 'hello';
console.log(first, fifth); // ho

// Destructuring fails softly and returns undefined for a missing value
let [one, two, three] = 'ab'; // No third character
console.log(three); // undefined

// Unicode strings can also be destructured
let [alpha, space, coffee] = 'a ☕';
console.log('2 coffees please', coffee, coffee);
```
