# ES6 Tagged Templates

> A Tagged Template is a special type of function that can be called with compiled Template Literal data.

A Tagged Template function can be used to perform a transformation on a Template Literal.

The Tagged Template syntax places a function name directly before the Template Literal with no parentheses e.g.

```js
someTagFunction`Some template ${literal}.`;
```

Tagged Templates receives the two parts of the Template Literal (`literals` and `substitutions`) as input arguments.


### literals

`literals` is an Array of the Template Literal text split on each `${}` substitution.

If the Template Literal begins with a `${}` substitution, then the first item in `literals` will be an empty string. This ensures that `literals[0]` is always the start of a string.


##### literals.raw

`literals` has a property called `raw` where backslashes are not interpreted.

The `literals.raw` property is an Array of raw characters e.g. `\n` as opposed to an actual newline.


### substitutions

`substitutions` is the interpreted substitution values.

There is always one less substitution then literal i.e. `substitutions.length === literals.length - 1;`


### Example

```js
// Simple Tagged Template example that uppercases the substitutions
function uppercasePartial(literals, ...substitutions) {

  console.log('literals:', literals);
  console.log('substitutions:', substitutions);

  let output = literals[0];

  substitutions.forEach((item, index) => {

    output += substitutions[index].toUpperCase() + literals[index + 1];
  });

  console.log('Tagged Template output:');
  return output;  
}

let quick = 'quick';
let lazy = 'lazy';

console.log(uppercasePartial`The ${quick} brown fox jumps over the ${lazy} dog.`);
```


### Notes

Possible use cases for Tags include formatting, auto-escaping and localisation.

Tags also enable domain specific languages on strings.
