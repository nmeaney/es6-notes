# ES6 `let`, `const` and Block Scope

> Variables declared with `let` or `const` are scoped to the block in which they were defined.

This means they can only be accessed in that block. They are not hoisted.

Variables declared with `let` can be redefined (i.e. their value can be changed).

Variables declared with `const` *cannot* be redefined (i.e. they are immutable).


### let

Variables assigned with `let` can have their value changed.

```js
let myVariable = 'I can be changed';
console.log(myVariable);

myVariable = 'I have changed';
console.log(myVariable);
```


### const

Variables assigned with `const` are immutable; they cannot be changed.

```js
const someCalculation = a => {

  // bumpValue cannot be modified in someCalculation
  const bumpValue = 10;

  // Functions are scoped to the block in which they were defined
  // multiplier cannot be used outside of someCalculation
  // Note: variable 'a' is internal to multiplier function
  const multiplier = a => a * a;

  // Note: variable 'a' refers to argument input to someCalculation
  return multiplier(a) + bumpValue;
};

console.log(someCalculation(2)); // 14
console.log(multiplier(2)); // Uncaught ReferenceError: multiplier is not defined
```


### Block-Scoped Functions

```js
// Outer block
{
  const funky = () => 1;
  console.log(funky()); // 1

  // Inner block
  {
    const funky = () => 2;

    // Uses inner funky()
    console.log(funky()); // 2
  }

  // Uses outer funky()
  console.log(funky()); // 1
}
```


### Temporal Dead Zone

Since `let` and `const` variables are not hoisted, they cannot be used in a block until after they are declared.

The 'space' between the start of a block and the declaration of a variable with `let` and `const`, is known as the Temporal Dead Zone (TDZ).
