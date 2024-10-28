## Comprehensive JavaScript Notes

### Table of Contents

1. [Introduction to JavaScript](#1-introduction-to-javascript)
2. [JavaScript Basics](#2-javascript-basics)
3. [Control Structures](#3-control-structures)
4. [Functions](#4-functions)
5. [Objects and Arrays](#5-objects-and-arrays)
6. [ES6 Features](#6-es6-features)
7. [Asynchronous JavaScript](#7-asynchronous-javascript)
8. [DOM Manipulation](#8-dom-manipulation)
9. [Error Handling](#9-error-handling)
10. [JavaScript Modules](#10-javascript-modules)
11. [Object-Oriented Programming in JavaScript](#11-object-oriented-programming-in-javascript)
12. [Regular Expressions](#12-regular-expressions)
13. [Miscellaneous Concepts](#13-miscellaneous-concepts)

---

### 1. Introduction to JavaScript

- **Definition**: JavaScript is a high-level, interpreted programming language primarily used for web development to create interactive effects and dynamic content on websites.
- **History**: Developed by Brendan Eich in 1995, JavaScript has evolved to become a versatile language used on both the client-side and server-side (via Node.js).
- **Execution**: JavaScript code can be executed in web browsers (like Chrome, Firefox) and on servers (using Node.js).

### 2. JavaScript Basics

#### Variables

- **Declaring Variables**:

  - `var`: Function-scoped, hoisted to the top of its scope, can be redeclared.
  - `let`: Block-scoped, not hoisted, can be reassigned but not redeclared in the same scope.
  - `const`: Block-scoped, must be initialized at declaration, cannot be reassigned.

  ```javascript
  var name = "John"; // Function-scoped
  let age = 30; // Block-scoped
  const birthYear = 1990; // Immutable
  ```

#### Data Types

- **Primitive Data Types**:

  - **String**: Text data (e.g., `"Hello, World!"`).
  - **Number**: Numeric data, can be integers or floats (e.g., `42`, `3.14`).
  - **Boolean**: Represents `true` or `false`.
  - **Null**: Represents intentional absence of any value.
  - **Undefined**: Variable declared but not initialized.
  - **Symbol**: Unique and immutable primitive value (used mainly for object property keys).
  - **BigInt**: Represents integers with arbitrary precision (e.g., `1234567890123456789012345678901234567890n`).

- **Composite Data Types**:
  - **Object**: Collection of key-value pairs (e.g., `{name: "John", age: 30}`).
  - **Array**: Ordered collection of values (e.g., `[1, 2, 3, 4]`).

#### Operators

- **Arithmetic Operators**: `+`, `-`, `*`, `/`, `%`, `++`, `--`.
- **Assignment Operators**: `=`, `+=`, `-=`, `*=`, `/=`, `%=`.
- **Comparison Operators**:
  - `==` (loose equality), `===` (strict equality), `!=` (loose inequality), `!==` (strict inequality), `>`, `<`, `>=`, `<=`.
- **Logical Operators**: `&&` (and), `||` (or), `!` (not).

```javascript
let sum = 5 + 3; // 8
let isEqual = 5 === "5"; // false (strict comparison)
let isAdult = age >= 18; // true if age is 18 or more
```

### 3. Control Structures

#### Conditional Statements

- **if statement**: Executes a block of code if the condition is true.

```javascript
if (age >= 18) {
  console.log("You are an adult.");
} else {
  console.log("You are not an adult.");
}
```

- **switch statement**: A cleaner way to handle multiple conditions.

```javascript
let fruit = "apple";

switch (fruit) {
  case "banana":
    console.log("Banana is yellow.");
    break;
  case "apple":
    console.log("Apple is red.");
    break;
  default:
    console.log("Unknown fruit.");
}
```

#### Loops

- **for loop**: Runs a block of code a specific number of times.

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i); // Outputs 0 to 4
}
```

- **while loop**: Continues until the condition is false.

```javascript
let count = 0;
while (count < 5) {
  console.log(count);
  count++;
}
```

- **do...while loop**: Executes the block at least once, then checks the condition.

```javascript
let number = 0;
do {
  console.log(number);
  number++;
} while (number < 5);
```

- **for...of loop**: Iterates over iterable objects (like arrays).

```javascript
let numbers = [1, 2, 3];

for (let num of numbers) {
  console.log(num); // Outputs 1, 2, 3
}
```

- **for...in loop**: Iterates over enumerable properties of an object.

```javascript
let person = { name: "John", age: 30 };

for (let key in person) {
  console.log(key + ": " + person[key]); // Outputs each key-value pair
}
```

### 4. Functions

#### Function Declaration

Defines a function that can be called anywhere in the scope.

```javascript
function greet(name) {
  return `Hello, ${name}!`;
}

console.log(greet("Alice")); // Outputs: Hello, Alice!
```

#### Function Expression

Creates a function that can be assigned to a variable.

```javascript
const greet = function (name) {
  return `Hello, ${name}!`;
};

console.log(greet("Bob")); // Outputs: Hello, Bob!
```

#### Arrow Functions

A shorter syntax for writing functions, with lexical `this`.

```javascript
const greet = (name) => `Hello, ${name}!`;
console.log(greet("Charlie")); // Outputs: Hello, Charlie!
```

#### Default Parameters

Sets default values for parameters if not provided.

```javascript
function greet(name = "Guest") {
  return `Hello, ${name}!`;
}

console.log(greet()); // Outputs: Hello, Guest!
```

#### Higher-Order Functions

Functions that can take other functions as arguments or return functions.

```javascript
function createMultiplier(multiplier) {
  return function (x) {
    return x * multiplier;
  };
}

const double = createMultiplier(2);
console.log(double(5)); // Outputs: 10
```

### 5. Objects and Arrays

#### Objects

Objects are collections of properties.

```javascript
let person = {
  name: "John",
  age: 30,
  greet: function () {
    console.log(`Hello, I am ${this.name}`);
  },
};

person.greet(); // Outputs: Hello, I am John
```

#### Accessing Object Properties

- Dot notation: `object.property`
- Bracket notation: `object["property"]`

```javascript
console.log(person.name); // Outputs: John
console.log(person["age"]); // Outputs: 30
```

#### Arrays

Arrays are list-like objects.

```javascript
let fruits = ["apple", "banana", "cherry"];
console.log(fruits[0]); // Outputs: apple
```

#### Array Methods

- `push()`: Adds an item to the end of an array.
- `pop()`: Removes the last item from an array.
- `shift()`: Removes the first item from an array.
- `unshift()`: Adds an item to the beginning of an array.
- `map()`: Creates a new array with the results of calling a function on every element.
- `filter()`: Creates a new array with elements that pass a test.
- **Advanced Array Methods**:
  - `reduce()`: Accumulates values in an array to a single result.
  - `some()`: Tests if at least one element in the array passes a test.
  - `every()`: Tests if all elements in the array pass a test.

```javascript
fruits.push("date"); // Adds "date" to the end
let newFruits = fruits.map((fruit) => fruit.toUpperCase()); // ["APPLE", "BANANA", "CHERRY", "DATE"]
```

### 6. ES6 Features

#### Template Literals

Allow for string interpolation and multi-line strings.

```javascript
let name = "Alice";
console.log(`Hello, ${name}!`); // Outputs: Hello, Alice!
```

#### Destructuring

Easily extract values from arrays or properties from objects.

```javascript
let person = { name: "John", age: 30 };
let { name, age } = person;

let numbers = [1, 2, 3];
let [first, second] = numbers;
```

#### Spread Operator

Expands elements in arrays or properties in objects.

```javascript
let arr1 = [1, 2];
let arr2 = [...arr1, 3, 4]; // [1, 2, 3, 4]

let person1 = { name: "Alice" };
let person2 = { ...person1, age: 25 }; // {name: "Alice", age: 25}
```

#### Optional Chaining (`?.`)

Safely access deeply nested properties.

```javascript
let user = { name: "Alice", address: { city: "Wonderland" } };
console.log(user.address?.city); // Outputs: Wonderland
console.log(user.contact?.phone); // Outputs: undefined (no error)
```

#### Nullish Coalescing Operator (`??`)

Assign a fallback value if the variable is `null` or `undefined`.

```javascript
let greeting = null;
console.log(greeting ?? "Hello"); // Outputs: Hello
```

### 7. Asynchronous JavaScript

#### Callbacks

Functions passed as arguments and called later.

```javascript
function fetchData(callback) {
  setTimeout(() => {
    callback("Data received");
  }, 1000);
}

fetchData(console.log); // Outputs: Data received after 1 second
```

#### Promises

Handle asynchronous operations with `then()` and `catch()` for chaining.

```javascript
let fetchData = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Data received"), 1000);
});

fetchData.then(console.log).catch(console.error);
```

#### Async/Await

A cleaner way to work with promises, allowing for sequential async code.

```javascript
async function fetchData() {
  try {
    let data = await fetch("https://api.example.com/data");
    let json = await data.json();
    return json;
  } catch (error) {
    console.error("Error fetching data", error);
  }
}

fetchData();
```

### 8. DOM Manipulation

- **Selecting Elements**:

  - `document.getElementById("id")`
  - `document.querySelector(".class")`
  - `document.querySelectorAll(".class")`

- **Modifying Content**:
  - `.textContent`: Updates the text inside an element.
  - `.innerHTML`: Updates the HTML inside an element.

```javascript
document.querySelector("#title").textContent = "Hello World";
```

### 9. Error Handling

#### Try/Catch

Handle errors gracefully.

```javascript
try {
  let result = riskyOperation();
  console.log(result);
} catch (error) {
  console.error("An error occurred", error);
}
```

#### Custom Error Classes

Creating custom error classes for specific error types.

```javascript
class ValidationError extends Error {
  constructor(message) {
    super(message);
    this.name = "ValidationError";
  }
}

function validateInput(input) {
  if (!input) throw new ValidationError("Input cannot be empty");
}
```

### 10. JavaScript Modules

#### Export and Import

Use `export` to share code across files and `import` to bring it in.

```javascript
// module.js
export const greeting = "Hello";
export function greet() {
  console.log(greeting);
}

// main.js
import { greeting, greet } from "./module.js";
```

#### Dynamic Imports with `import()`

Load modules only when needed, often to improve performance.

```javascript
async function loadModule() {
  const module = await import("./module.js");
  module.greet();
}
loadModule();
```

### 11. Object-Oriented Programming in JavaScript

#### Classes

JavaScript classes enable creating reusable objects.

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hello, my name is ${this.name}`);
  }
}

const alice = new Person("Alice", 30);
alice.greet();
```

### 12. Regular Expressions

Used for matching patterns in strings.

```javascript
let emailPattern = /^[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,4}$/;
console.log(emailPattern.test("example@example.com")); // Outputs: true
```

### 13. Miscellaneous Concepts

#### Symbols

Unique values mainly used as object property keys.

```javascript
let uniqueKey = Symbol("uniqueKey");
let obj = { [uniqueKey]: "value" };
```

#### WeakMap and WeakSet

Memory-efficient collections for storing weak references to objects.

```javascript
let weakMap = new WeakMap();
let obj = {};
weakMap.set(obj, "data");
```

---
### Happy coding!
