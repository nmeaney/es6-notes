# ES6 Template Literals

> Template Literals enable the interpolation of any JavaScript expression in a string.

- Template Literals are declared with the gravé accent **`** character.

- Variables and expressions can be inserted in Template Literals using a `${}` syntax.

- Template Literals support whitespace characters.

- Template Literals support multiple lines.

- Template Literals were previously called "Template Strings".


### Examples

```js
// Simple variable
let name = 'John';
let message = `My name is ${name}.`;
console.log(message);

// Object reference
let person = { name: 'John Smith' };
message = `My name is ${person.name}.`;
console.log(message);

// Embedded expression
message = `The sum of 4 plus 5 is ${4 + 5}`;
console.log(message);

// Multi-line
message = `
  I can be
  wrapped \t over
  many lines
  too`;
console.log(message);
```
