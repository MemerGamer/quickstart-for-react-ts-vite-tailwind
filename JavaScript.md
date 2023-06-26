# Getting started with Javascript

## Table of Contents

1. [Data Types](#data-types)
2. [Functions](#functions)
3. [Conditional statements](#conditional-statements)
4. [Loops](#loops)
5. [`this` keyword](#this-keyword)
6. [Object oriented programming](#object-oriented-programming)
7. [Asynchronous programming](#asynchronous-programming)

## Data Types

### Primitive data types

1. Number
2. String
3. Boolean
4. undefined (Non initialized variables have this value by default)
5. null

In JavaScript, all variables are declared using the `let` and `const` keywords. There is a difference between them, but for now, we will use `let` for all variables.
(There is also a `var` keyword, but it is not recommended to use it)

The variables data type is determined by the value assigned to it, and can be changed at any time.
This means that JavaScript is dynamically typed.

```javascript
let myNumber = 5;
console.log(typeof myNumber); // number
```

Type of an undefined variable is also undefined and the value is also undefined.

Type of a null-assigned variable is an object.

```javascript
let myAge;
console.log(myAge); // undefined
console.log(typeof myAge); // undefined

let myName = null;
console.log(myName); // null
console.log(typeof myName); // object
```

### Template Strings

Template strings are used to create strings that include variables using substitution.

```javascript
`string text ${expression} string text`;
```

### Reference data types

JavaScript has three reference data types: Array, Object, Function
They are all objects under the hood.

The syntax of reference types called object literal syntax.

```javascript
let car = {
  name: "BMW",
  model: "X5",
  year: 2019,
  isUsed: true,
};
```

You can access the object properties using the dot notation or the bracket notation.

```javascript
console.log(car.name); // BMW
console.log(car["model"]); // X5
```

### Arrays

Arrays are used to store multiple values in a single variable.

```javascript
let fruits = ["apple", "banana", "orange"];

console.log(fruits[0]); // apple
console.log(fruits[1]); // banana

fruits[2] = "grape";
console.log(fruits[2]); // grape
```

### Functions

#### Method vs Function

A **method** is a function that is a property of an object.

```javascript
let car = {
  name: "BMW",
  model: "X5",
  year: 2019,
  isUsed: true,
  drive: function () {
    console.log("Driving...");
  },
};
```

A **function** is a piece of code that is called by name. It can be passed data to operate on (i.e. the parameters) and can optionally return data (the return value).

```javascript
function sum(a, b) {
  return a + b;
}
```

#### Function declaration vs Function expression

```javascript
// Function declaration
function sum(a, b) {
  return a + b;
}

// Function expression
let sum = function (a, b) {
  return a + b;
};
```

#### Arrow functions

Arrow functions are a short syntax for writing function expressions.

```javascript
let sum = (a, b) => {
  return a + b;
};
```

If the function has only one statement, and the statement returns a value, you can remove the brackets and the return keyword.

```javascript
let sum = (a, b) => a + b;
```

#### Anonymous functions

Anonymous functions are functions that are dynamically declared at runtime.

```javascript
let sum = function (a, b) {
  return a + b;
};
```

#### Immediately Invoked Function Expression (IIFE)

An IIFE is a JavaScript function that runs as soon as it is defined.

```javascript
(function () {
  console.log("Hello World!");
})();
```

### Conditional statements

#### if...else

```javascript
let age = 18;

if (age >= 18) {
  console.log("You can drive");
} else if (age >= 16 && age < 18) {
  console.log("You can drive with supervision");
} else {
  console.log("You can't drive");
}
```

#### switch

```javascript
let day = 3;

switch (day) {
  case 1:
    console.log("Monday");
    break;
  case 2:
    console.log("Tuesday");
    break;
  case 3:
    console.log("Wednesday");
    break;
  case 4:
    console.log("Thursday");
    break;
  case 5:
    console.log("Friday");
    break;
  case 6:
    console.log("Saturday");
    break;
  case 7:
    console.log("Sunday");
    break;
  default:
    console.log("Invalid day");
}
```

#### ternary operator

```javascript
let age = 18;

age >= 18 ? console.log("You can drive") : console.log("You can't drive");
```

#### truthy and falsy values

In JavaScript values evaluate to true or false when evaluated in a boolean context.

Falsy values:

- false
- 0
- null
- undefined

All other values are truthy.

### Loops

#### for loop

```javascript
for (let i = 0; i < 10; i++) {
  console.log(i);
}
```

#### for...in loop

```javascript
let car = {
  name: "BMW",
  model: "X5",
  year: 2019,
  isUsed: true,
};

for (let key in car) {
  console.log(key, car[key]);
}
```

#### for...of loop

```javascript
let fruits = ["apple", "banana", "orange"];

for (let fruit of fruits) {
  console.log(fruit);
}
```

#### while loop

```javascript
let i = 0;

while (i < 10) {
  console.log(i);
  i++;
}
```

#### do...while loop

```javascript
let i = 0;

do {
  console.log(i);
  i++;
} while (i < 10);
```

### this keyword

- In a method, `this` refers to the **owner object**.
- Alone, `this` refers to the **global object**.
- In a function, `this` refers to the **global object**.
- In a function, in strict mode, `this` is **undefined**.
- In an event `this` refers to the **element** that received the event.
- Methods like **call()**, and **apply()** can refer `this` to **any object**.
- In arrow functions, there is no `this` binding.

### Object Oriented Programming

Objects are used to model real-world objects that we want to represent inside our programs, and/or provide a simple way to access functionality that would otherwise be hard or impossible to make use of.

Objects are mutable, and they are manipulated by reference, and not by value.

If a `car` is an object, then `x` and `car` are pointing to the same object, and any changes to `x` will also change `car`. This will not create a copy of `car`.

```javascript
const x = car; // will not create a copy of car
```

#### Getters and Setters

```javascript
let car = {
  name: "BMW",
  model: "X5",
  year: 2019,
  isUsed: true,
  get fullName() {
    return `${this.name} ${this.model}`;
  },
  set fullName(value) {
    const parts = value.split(" ");
    this.name = parts[0];
    this.model = parts[1];
  },
};

car.fullName = "Mercedes Benz C200";

console.log(car.fullName); // Mercedes Benz
```

#### Constructor function

```javascript
function Car(name, model, year, isUsed) {
  this.name = name;
  this.model = model;
  this.year = year;
  this.isUsed = isUsed;
  this.drive = function () {
    console.log("Driving...");
  };
}

let car = new Car("BMW", "X5", 2019, true);
```

#### Prototype

The JavaScript prototype property allows you to add new properties to object constructors:

```javascript
function Car(name, model, year, isUsed) {
  this.name = name;
  this.model = model;
  this.year = year;
  this.isUsed = isUsed;
}

Car.prototype.drive = function () {
  console.log("Driving...");
};
```

#### Classes

```javascript
class Car {
  constructor(name, model, year, isUsed) {
    this.name = name;
    this.model = model;
    this.year = year;
    this.isUsed = isUsed;
  }

  drive() {
    console.log("Driving...");
  }
}
```

### Asynchronous programming

#### Promises

A promise is an object that may produce a single value some time in the future: either a resolved value, or a reason that it’s not resolved (e.g., a network error occurred). A promise may be in one of 3 possible states: fulfilled, rejected, or pending.

```javascript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Success");
    // reject(new Error("Error"));
  }, 2000);
});

promise
  .then((result) => console.log(result))
  .catch((err) => console.log(err.message));
```

If the job is finished successfully, `resolve(value)` is called with `value` being the result of the job.

If an error occurs, `reject(error)` is called with `error` being the error object.

#### Async/Await

The `async` keyword is added to functions to tell them to return a promise rather than directly returning the value.

The `await` keyword is added before a function call to tell the program to wait for the promise to resolve before continuing.

```javascript
function getUser(id) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log("Reading a user from a database...");
      resolve({ id: id, username: "john" });
    }, 2000);
  });
}

function getRepositories(username) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log("Calling GitHub API...");
      resolve(["repo1", "repo2", "repo3"]);
    }, 2000);
  });
}

function getCommits(repo) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log("Calling GitHub API...");
      resolve(["commit1", "commit2", "commit3"]);
    }, 2000);
  });
}

async function displayCommits() {
  try {
    const user = await getUser(1);
    const repos = await getRepositories(user.username);
    const commits = await getCommits(repos[0]);
    console.log(commits);
  } catch (err) {
    console.log(err.message);
  }
}

displayCommits();
```

#### Try...Catch

The `try...catch` statement marks a block of statements to try and specifies a response should an exception be thrown.

```javascript
try {
  // code to try
} catch (err) {
  // code to handle errors
}
```

You can use `finally` to execute code, after try and catch, regardless of the result:

```javascript
try {
  // code to try
} catch (err) {
  // code to handle errors
} finally {
  // code to be executed regardless of the try / catch result
}
```

You can use `throw` to create custom errors:

```javascript
try {
  // code to try
  throw new Error("Error message");
} catch (err) {
  // code to handle errors
}
```

Combined with async/await:

```javascript
async function displayCommits() {
  try {
    const user = await getUser(1);
    const repos = await getRepositories(user.username);
    const commits = await getCommits(repos[0]);
    console.log(commits);
  } catch (err) {
    console.log(err.message);
  }
}
```

#### Callbacks

A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.

```javascript
function getUser(id, callback) {
  setTimeout(() => {
    console.log("Reading a user from a database...");
    callback({ id: id, username: "john" });
  }, 2000);
}

function getRepositories(username, callback) {
  setTimeout(() => {
    console.log("Calling GitHub API...");
    callback(["repo1", "repo2", "repo3"]);
  }, 2000);
}

function getCommits(repo, callback) {
  setTimeout(() => {
    console.log("Calling GitHub API...");
    callback(["commit1", "commit2", "commit3"]);
  }, 2000);
}

getUser(1, (user) => {
  console.log(user);
  getRepositories(user.username, (repos) => {
    console.log(repos);
    getCommits(repos[0], (commits) => {
      console.log(commits);
    });
  });
});
```

#### Strict mode

Strict mode is a way to introduce better error-checking into your code.

```javascript
// Whole-script strict mode syntax

"use strict";

// Function-level strict mode syntax

function strict() {
  "use strict";
  // function body
}
```
