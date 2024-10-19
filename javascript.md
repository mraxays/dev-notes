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
12. [Miscellaneous Concepts](#12-miscellaneous-concepts)

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
  var name = "John";  // Function-scoped
  let age = 30;       // Block-scoped
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
let sum = 5 + 3;               // 8
let isEqual = (5 === '5');     // false (strict comparison)
let isAdult = (age >= 18);     // true if age is 18 or more
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
    console.log(i);  // Outputs 0 to 4
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
    console.log(num);  // Outputs 1, 2, 3
}
```

- **for...in loop**: Iterates over enumerable properties of an object.

```javascript
let person = {name: "John", age: 30};

for (let key in person) {
    console.log(key + ": " + person[key]);  // Outputs each key-value pair
}
```

### 4. Functions
#### Function Declaration
Defines a function that can be called anywhere in the scope.

```javascript
function greet(name) {
    return `Hello, ${name}!`;
}

console.log(greet("Alice"));  // Outputs: Hello, Alice!
```

#### Function Expression
Creates a function that can be assigned to a variable.

```javascript
const greet = function(name) {
    return `Hello, ${name}!`;
};

console.log(greet("Bob"));  // Outputs: Hello, Bob!
```

#### Arrow Functions
A shorter syntax for writing functions, with lexical `this`.

```javascript
const greet = (name) => `Hello, ${name}!`;
console.log(greet("Charlie"));  // Outputs: Hello, Charlie!
```

#### Default Parameters
Sets default values for parameters if not provided.

```javascript
function greet(name = "Guest") {
    return `Hello, ${name}!`;
}

console.log(greet());  // Outputs: Hello, Guest!
```

#### Higher-Order Functions
Functions that can take other functions as arguments or return functions.

```javascript
function createMultiplier(multiplier) {
    return function(x) {
        return x * multiplier;
    };
}

const double = createMultiplier(2);
console.log(double(5));  // Outputs: 10
```

### 5. Objects and Arrays
#### Objects
Objects are collections of properties.

```javascript
let person = {
    name: "John",
    age: 30,
    greet: function() {
        console.log(`Hello, I am ${this.name}`);
    }
};

person.greet();  // Outputs: Hello, I am John
```

#### Accessing Object Properties
- Dot notation: `object.property`
- Bracket notation: `object["property"]`

```javascript
console.log(person.name);         // Outputs: John
console.log(person["age"]);       // Outputs: 30
```

#### Arrays
Arrays are list-like objects.

```javascript
let fruits = ["apple", "banana", "cherry"];
console.log(fruits[0]);  // Outputs: apple
```

#### Array Methods
- `push()`: Adds an item to the end of an array.
- `pop()`: Removes the last item from an array.
- `shift()`: Removes the first item from an array.
- `unshift()`: Adds an item to the beginning of an array.
- `map()`: Creates a new array with the results of calling a function on every element.
- `filter()`: Creates a new array with elements that pass a test.

```javascript
fruits.push("date");  // Adds "date" to the end
let newFruits = fruits.map(fruit => fruit.toUpperCase());  // ["APPLE", "BANANA", "CHERRY", "DATE"]
```

### 6. ES6 Features
#### Template Literals
Allow for string interpolation and multi-line strings.

```javascript
let name = "Alice";
console.log(`Hello, ${name}!`);  // Outputs: Hello, Alice!
```

#### Destructuring
Easily extract values from arrays or properties from objects.

```javascript
let person = {name: "John", age: 30};
let {name, age} = person;

let numbers = [1, 2, 3];
let [first, second] = numbers;
```

#### Spread Operator
Expands elements in arrays or properties in objects.

```javascript
let arr1 = [1, 2, 3];
let arr2 = [...arr1, 4, 5];  // [1, 2, 3, 4, 5]

let obj1 = {a: 1, b: 2};
let obj2 = {...obj1, c: 3};

  // {a: 1, b: 2, c: 3}
```

#### Rest Parameters
Represents an indefinite number of arguments as an array.

```javascript
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3, 4));  // Outputs: 10
```

### 7. Asynchronous JavaScript
#### Callbacks
Functions passed as arguments to be executed later.

```javascript
function fetchData(callback) {
    setTimeout(() => {
        callback("Data loaded");
    }, 1000);
}

fetchData(data => console.log(data));  // Outputs: Data loaded after 1 second
```

#### Promises
Objects representing the eventual completion (or failure) of an asynchronous operation.

```javascript
const promise = new Promise((resolve, reject) => {
    let success = true;
    if (success) {
        resolve("Data loaded");
    } else {
        reject("Error occurred");
    }
});

promise
    .then(data => console.log(data))  // Outputs: Data loaded
    .catch(err => console.log(err));
```

#### Async/Await
Syntactic sugar built on promises that allows writing asynchronous code in a more synchronous manner.

```javascript
async function fetchData() {
    let response = await fetch('https://api.example.com/data');
    let data = await response.json();
    console.log(data);
}

fetchData();  // Calls the async function
```

### 8. DOM Manipulation
#### Selecting Elements
- **By ID**: `document.getElementById()`
- **By Class**: `document.getElementsByClassName()`
- **By Tag Name**: `document.getElementsByTagName()`
- **Using Query Selector**: `document.querySelector()`, `document.querySelectorAll()`

```javascript
let header = document.getElementById("header");
let items = document.querySelectorAll(".item");
```

#### Modifying Content
- Change text content: `element.textContent`
- Change HTML content: `element.innerHTML`
- Change styles: `element.style.property`

```javascript
header.textContent = "Welcome!";
header.style.color = "blue";
```

#### Adding Event Listeners
Attach events to elements.

```javascript
header.addEventListener("click", function() {
    console.log("Header clicked!");
});
```

### 9. Error Handling
Use `try...catch` to handle exceptions.

```javascript
try {
    let result = riskyOperation();
} catch (error) {
    console.log("Error:", error);
} finally {
    console.log("Finally block executed");
}
```

### 10. JavaScript Modules
JavaScript modules allow for organizing code into reusable pieces.

#### Exporting
- **Named Exports**: Export multiple values from a module.

```javascript
// module.js
export const name = "John";
export function greet() {
    return "Hello!";
}
```

- **Default Exports**: Export a single value from a module.

```javascript
// module.js
const name = "John";
export default name;
```

#### Importing
Import values from other modules.

```javascript
// main.js
import { name, greet } from './module.js';
import defaultName from './module.js';
```

### 11. Object-Oriented Programming in JavaScript
JavaScript supports object-oriented programming through prototypes and classes.

#### Classes
- Define classes using the `class` keyword.

```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    greet() {
        console.log(`Hello, I am ${this.name}`);
    }
}

let john = new Person("John", 30);
john.greet();  // Outputs: Hello, I am John
```

#### Inheritance
Classes can inherit properties and methods from other classes.

```javascript
class Employee extends Person {
    constructor(name, age, jobTitle) {
        super(name, age);
        this.jobTitle = jobTitle;
    }

    work() {
        console.log(`${this.name} is working as a ${this.jobTitle}`);
    }
}

let emp = new Employee("Jane", 28, "Developer");
emp.work();  // Outputs: Jane is working as a Developer
```

### 12. Miscellaneous Concepts
#### Scope
- **Global Scope**: Variables declared outside functions are globally accessible.
- **Function Scope**: Variables declared within a function are only accessible inside that function.
- **Block Scope**: Variables declared with `let` and `const` are only accessible within the block they are defined.

#### `this` Keyword
Refers to the context in which a function is executed.
- In a method, `this` refers to the owner object.
- In a function, `this` refers to the global object (or `undefined` in strict mode).
- In an arrow function, `this` is lexically inherited from the outer function.

```javascript
let person = {
    name: "John",
    greet: function() {
        console.log(`Hello, I am ${this.name}`);
    }
};

person.greet();  // Outputs: Hello, I am John
```

#### Higher-Order Functions
Functions that can take other functions as arguments or return them.

```javascript
function filterArray(arr, callback) {
    let filtered = [];
    for (let item of arr) {
        if (callback(item)) {
            filtered.push(item);
        }
    }
    return filtered;
}

let result = filterArray([1, 2, 3, 4], item => item > 2);
console.log(result);  // Outputs: [3, 4]
```

---

### Happy coding!
