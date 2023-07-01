# Getting started with TypeScript

TypeScript is a **statically typed superset** of JavaScript that adds optional static types to the language. It provides enhanced tooling, better code organization, and improved error detection. This guide will cover the basics of TypeScript and how to get started with it.

## Table of Contents

- [Getting started with TypeScript](#getting-started-with-typescript)
  - [Table of Contents](#table-of-contents)
  - [TypeScript Introduction](#typescript-introduction)
  - [Data Types](#data-types)
  - [Functions](#functions)
  - [Conditional Statements](#conditional-statements)
  - [Loops](#loops)
  - [Classes and Interfaces](#classes-and-interfaces)
  - [Modules](#modules)
  - [Asynchronous Programming](#asynchronous-programming)
  - [Optional Chaining Operator](#optional-chaining-operator)
  - [Non-null Assertion Operator](#non-null-assertion-operator)

## TypeScript Introduction

TypeScript is a programming language that builds on top of JavaScript by adding static types. It allows you to define the types of variables, function parameters, and return values, which enables the TypeScript compiler to catch type-related errors at compile-time.

To use TypeScript, you need to have the TypeScript compiler (`tsc`) installed globally or locally in your project. You can install it using [npm](https://www.npmjs.com/):

```bash
npm install -g typescript
```

Once installed, you can create TypeScript files with the `.ts` extension and compile them to JavaScript using the `tsc` command.

## Data Types

TypeScript includes all the data types available in JavaScript, such as `number`, `string`, `boolean`, `undefined`, and `null`. However, TypeScript also introduces additional static types, such as `array`, `tuple`, `enum`, `any`, and more.

```typescript
let myNumber: number = 5;
let myString: string = "Hello, TypeScript";
let myBoolean: boolean = true;
let myUndefined: undefined = undefined;
let myNull: null = null;

let myArray: number[] = [1, 2, 3];
let myTuple: [string, number] = ["TypeScript", 2021];
let myEnum: Color = Color.Red;

let myAny: any = "Any type can hold any value";

enum Color {
  Red,
  Green,
  Blue,
}
```

TypeScript's static typing allows for better code validation and helps catch errors early in the development process.

## Functions

TypeScript supports the same function syntax as JavaScript and allows you to specify parameter types and return types.

```typescript
function sum(a: number, b: number): number {
  return a + b;
}

function greet(name: string): void {
  console.log("Hello, " + name);
}
```

In the above examples, `sum` takes two `number` parameters and returns a `number`. `greet` takes a `string` parameter but does not return a value (`void`).

## Conditional Statements

Conditional statements in TypeScript work similarly to JavaScript. You can use `if...else` statements and the ternary operator to control the program flow based on conditions.

```typescript
let age: number = 18;

if (age >= 18) {
  console.log("You can drive");
} else {
  console.log("You can't drive");
}

let message: string = age >= 18 ? "You can drive" : "You can't drive";
console.log(message);
```

## Loops

TypeScript supports the same loop constructs as JavaScript, such as `for`, `while`, and `do...while` loops.

```typescript
for (let i: number = 0; i < 5; i++) {
  console.log(i);
}

let fruits: string[] = ["apple", "banana", "orange"];

for (let fruit of fruits) {
  console.log(fruit);
}

let count: number = 0;
while (count < 5) {
  console.log(count);
  count++;
}
```

## Classes and Interfaces

TypeScript provides support for classes and interfaces, enabling you to write object-oriented code with static types.

```typescript
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  sayHello(): void {
    console.log(
      `Hello, my name is ${this.name} and I'm ${this.age} years old.`
    );
  }
}

interface Animal {
  name: string;
  age: number;
  makeSound(): void;
}

class Dog implements Animal {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  makeSound(): void {
    console.log("Woof!");
  }
}

let person = new Person("John", 30);
person.sayHello();

let dog = new Dog("Buddy", 5);
dog.makeSound();
```

## Modules

TypeScript provides a module system that allows you to organize your code into reusable modules. You can use the `export` and `import` keywords to define and import modules.

```typescript
// math.ts
export function add(a: number, b: number): number {
  return a + b;
}

// app.ts
import { add } from "./math";

console.log(add(3, 5)); // Output: 8
```

## Asynchronous Programming

TypeScript provides excellent support for asynchronous programming using promises, async/await syntax, and the `async` modifier.

```typescript
function delay(ms: number): Promise<void> {
  return new Promise((resolve) => {
    setTimeout(resolve, ms);
  });
}

async function greetAsync(name: string): Promise<void> {
  await delay(1000);
  console.log("Hello, " + name);
}

greetAsync("Alice");
```

In the above example, the `greetAsync` function is asynchronous and waits for 1 second using the `delay` function before printing the greeting.

## Optional Chaining Operator

TypeScript introduces the optional chaining operator (`?`), which allows you to safely access properties or call methods on potentially undefined or null values. If the value is undefined or null, the expression short-circuits and returns `undefined`.

```typescript
interface Person {
  name: string;
  address?: {
    street: string;
    city: string;
  };
}

const person: Person = {
  name: "John",
};

console.log(person.address?.city); // Output: undefined
```

In the above example, the `address` property of `person` is optional. By using the optional chaining operator (`?.`), accessing the `city` property does not throw an error when `address` is not defined.

## Non-null Assertion Operator

TypeScript provides the non-null assertion operator (`!`) to tell the compiler that a value will not be null or undefined at runtime, even if the type declaration allows it. It asserts that the value is non-null and non-undefined, allowing you to access properties or call methods without a compiler error.

```typescript
const element = document.getElementById("myElement")!;

element.classList.add("active");
```

In the above example, the `getElementById` method returns a potentially nullable value (`HTMLElement | null`). By using the non-null assertion operator (`!`), we assert that the returned value is not null, allowing us to safely call the `classList.add` method.
