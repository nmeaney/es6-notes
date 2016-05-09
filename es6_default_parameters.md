# ES6 Default Function Parameters

> Default function parameters can be specified in function definitions using the  `=` assignment operator.

Default values can be functions.


### Examples

```js
// Example 1
function sayMsg(msg = 'This is the default message.') {

	console.log(msg);
}

sayMsg(); // This is the default message.
sayMsg('This is a different message!');


function toUpperCase(someString = '') {

  return someString.toUpperCase();
}
```

```js
// Example 2
function logger(message, level = toUpperCase('debug')) {

  // `${level}:` is an ES6 Template Literal
  console.log(`${level}:`, message);
}

logger('I\'m debugging');
logger('I\'m warning you ', toUpperCase('warn'));
```
