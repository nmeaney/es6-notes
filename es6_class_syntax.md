# ES6 Class Syntax

> The ES6 Class syntax is syntactic sugar for Prototypal Inheritance.


### Class Syntax

See comments: 

```js
class User {

  // Constructor
  constructor(name) {

    // Class properties
    this.name = name;
    this.type = 'standard';
  }

  // Class methods
  // The function keyword is not required
  // Comma separators are not required
  sayName() {

    return `Hi, I am ${this.name}`;
  }

  isAdmin() {

    return 'I am not an administrator.';
  }
}

let standardUser = new User('Joe');

console.log(standardUser.sayName());
console.log(standardUser.isAdmin());
```


### Inheritance with `extends`

Class declarations are not hoisted since `extends` needs to know which Object to extend.

```js
// Use the extends keyword for inheritance
class Admin extends User {

  constructor(name) {

    // super() calls the Constructor in the parent 'class'
    // In derived 'classes' you must call super() before using 'this'
    super(name);
    this.type = 'admin';
  }

  isAdmin() {

    return 'I am an administrator.';
  }
}

let adminUser = new Admin('Fred');

console.log(adminUser.sayName());
console.log(adminUser.isAdmin());
```


### Static Properties & Methods - TODO

Static properties and methods are inherited.

When calling a static method, you must specify the 'class' name.

