### JavaScript: Comprehensive Notes

JavaScript is a versatile, high-level programming language commonly used to create dynamic web pages, handle asynchronous events, and manage client-side data processing. These notes will cover everything from basic syntax to advanced concepts.

---

### 1. **JavaScript Basics**

#### **Variables**

Variables in JavaScript can be declared using `var`, `let`, or `const`. Each has different scoping rules:
- `var`: Function-scoped and can be redeclared. Avoid using `var` due to potential scoping issues.
- `let`: Block-scoped and can be updated but not redeclared within the same scope.
- `const`: Block-scoped but cannot be updated or redeclared.

```javascript
let name = "Alice";  // Block-scoped, mutable
const age = 25;      // Block-scoped, immutable
```

#### **Data Types**

JavaScript has dynamic typing, meaning a variable can hold any type of value.

1. **Primitive Types**:  
   - `Number`: Integer or floating-point.
   - `String`: A sequence of characters enclosed in quotes.
   - `Boolean`: `true` or `false`.
   - `Undefined`: A variable that has been declared but not yet assigned a value.
   - `Null`: Represents the intentional absence of a value.
   - `Symbol`: Unique and immutable primitive used as object property keys.
   - `BigInt`: Used for representing numbers larger than the `Number` type can safely handle.

2. **Non-Primitive (Reference) Types**:  
   - **Objects**: Key-value pairs.
   - **Arrays**: Ordered collections of data.
   - **Functions**: Blocks of reusable code.

```javascript
let myNumber = 42;                // Number
let myString = "Hello, world";     // String
let isJavaScriptFun = true;        // Boolean
let myUndefinedVar;                // Undefined
let myNullVar = null;              // Null
let mySymbol = Symbol("id");       // Symbol
let myBigInt = 12345678901234567890n; // BigInt
```

#### **Operators**
- **Arithmetic**: `+`, `-`, `*`, `/`, `%`, `++`, `--`.
- **Comparison**: `==` (loose equality), `===` (strict equality), `!=`, `!==`, `<`, `>`, `<=`, `>=`.
- **Logical**: `&&` (AND), `||` (OR), `!` (NOT).
- **Assignment**: `=`, `+=`, `-=`, `*=`, `/=`, `%=`.
  
```javascript
let sum = 5 + 3;         // 8
let isEqual = 5 === '5'; // false (strict equality)
```

---

### 2. **Control Structures**

#### **Conditionals**: `if`, `else if`, `else`, `switch`
```javascript
let score = 85;

if (score > 90) {
    console.log('A');
} else if (score > 75) {
    console.log('B');
} else {
    console.log('C');
}

// Switch statement
let grade = 'B';

switch(grade) {
  case 'A':
    console.log("Excellent");
    break;
  case 'B':
    console.log("Good");
    break;
  default:
    console.log("Try again");
}
```

#### **Loops**: `for`, `while`, `do...while`, `for...in`, `for...of`
```javascript
for (let i = 0; i < 5; i++) {
    console.log(i); // Outputs 0, 1, 2, 3, 4
}

let arr = [10, 20, 30];
for (let item of arr) {
    console.log(item);  // Outputs each item in the array
}

// While loop
let i = 0;
while (i < 5) {
    console.log(i);
    i++;
}
```

---

### 3. **Functions**

#### **Function Declaration**
```javascript
function add(a, b) {
    return a + b;
}
console.log(add(2, 3));  // 5
```

#### **Function Expression**
```javascript
const subtract = function(a, b) {
    return a - b;
};
console.log(subtract(5, 2));  // 3
```

#### **Arrow Functions**
Arrow functions provide a shorter syntax and lexically bind the `this` keyword.

```javascript
const multiply = (a, b) => a * b;
console.log(multiply(2, 3));  // 6
```

#### **Default Parameters**
```javascript
function greet(name = 'Guest') {
    return `Hello, ${name}`;
}
console.log(greet());  // "Hello, Guest"
```

#### **Rest and Spread Operators**
- **Rest Operator** (`...`): Collects all remaining arguments into an array.
- **Spread Operator** (`...`): Expands an array or object into its elements.

```javascript
// Rest operator
function sum(...numbers) {
    return numbers.reduce((acc, curr) => acc + curr, 0);
}
console.log(sum(1, 2, 3, 4));  // 10

// Spread operator
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];  // [1, 2, 3, 4, 5]
```

---

### 4. **Objects and Arrays**

#### **Objects**
Objects are collections of key-value pairs.

```javascript
let person = {
    name: 'John',
    age: 30,
    greet() {
        console.log(`Hello, I am ${this.name}`);
    }
};
console.log(person.name);  // Access property
person.greet();  // Call method
```

#### **Arrays**
Arrays are ordered collections of values.

```javascript
let arr = [10, 20, 30];
console.log(arr[0]);  // Access first element

// Common array methods
arr.push(40);        // Adds an element
arr.pop();           // Removes the last element
arr.shift();         // Removes the first element
arr.unshift(5);      // Adds an element to the front

arr.forEach(element => console.log(element));  // Iterates over the array
```

---

### 5. **ES6 Features**

#### **Template Literals**
Use backticks for embedding expressions and variables inside strings.

```javascript
let name = 'John';
console.log(`Hello, ${name}!`);  // Outputs: Hello, John!
```

#### **Destructuring**
Allows extraction of data from arrays or objects into distinct variables.

```javascript
// Array destructuring
let [x, y] = [10, 20];
console.log(x, y);  // 10, 20

// Object destructuring
let person = { name: 'Alice', age: 25 };
let { name, age } = person;
console.log(name, age);  // Alice, 25
```

#### **Classes**
Classes are syntactic sugar over JavaScript's prototype-based inheritance model.

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
let john = new Person('John', 30);
john.greet();  // Outputs: Hello, I am John
```

#### **Inheritance**
Use `extends` to create a subclass.

```javascript
class Employee extends Person {
    constructor(name, age, jobTitle) {
        super(name, age);  // Call the parent constructor
        this.jobTitle = jobTitle;
    }
    work() {
        console.log(`${this.name} is working as a ${this.jobTitle}`);
    }
}
let emp = new Employee('Jane', 28, 'Developer');
emp.work();  // Outputs: Jane is working as a Developer
```

---

### 6. **Asynchronous JavaScript**

#### **Callbacks**
A callback is a function passed as an argument to another function.

```javascript
function fetchData(callback) {
    setTimeout(() => {
        callback('Data loaded');
    }, 1000);
}
fetchData(data => console.log(data));  // Outputs: Data loaded (after 1 second)
```

#### **Promises**
A `Promise` is an object that represents a value which may be available now, later, or never.

```javascript
const promise = new Promise((resolve, reject) => {
    let success = true;
    if (success) {
        resolve('Data loaded');
    } else {
        reject('Error occurred');
    }
});

promise
  .then(data => console.log(data))    // If resolved: Outputs 'Data loaded'
  .catch(err => console.log(err));    // If rejected: Outputs 'Error occurred'
```

#### **Async/Await**
Async/await provides a cleaner way to handle asynchronous operations.

```javascript
async function fetchData() {
    let result = await fetch('https://api.example.com');
    let data = await result.json();
    console.log(data);
}
fetchData();
```

---

### 7. **Error Handling**

Use `try`, `catch`, and `finally` to handle errors.

```javascript
try {
    let result = riskyOperation();
} catch (error) {
    console.log('Error:', error);
} finally {
    console.log('Cleanup code runs here');
}
```

---

### 8. **DOM Manipulation**



JavaScript can interact with and modify the HTML structure of a webpage using the DOM (Document Object Model).

#### **Selecting Elements**
```javascript
let element = document.getElementById('myElement');
let elements = document.querySelectorAll('.myClass');
```

#### **Modifying Elements**
```javascript
element.textContent = 'New Content';  // Change text
element.style.color = 'blue';         // Change CSS style
```

#### **Event Listeners**
```javascript
element.addEventListener('click', function() {
    console.log('Element clicked');
});
```

---

### 9. **Modules (ES6)**

JavaScript modules allow you to divide your code into multiple files for better organization.

- **Export**: Share code from a module.
  ```javascript
  export const name = 'John';
  export function greet() {
      return 'Hello';
  }
  ```

- **Import**: Import code from a module.
  ```javascript
  import { name, greet } from './module.js';
  ```

---

### 10. **Miscellaneous Concepts**

#### **Truthy and Falsy Values**
In JavaScript, certain values are inherently "truthy" or "falsy".

- **Falsy**: `false`, `0`, `''` (empty string), `null`, `undefined`, `NaN`.
- **Truthy**: Anything that is not falsy.

```javascript
if (0) {
    console.log('This will not run'); // 0 is falsy
}
```

#### **Short-Circuit Evaluation**
JavaScript uses short-circuit evaluation with logical operators (`&&`, `||`).

```javascript
let name = userName || 'Guest';  // If userName is falsy, 'Guest' will be used
```

#### **Strict Mode**
JavaScript's "strict mode" enforces stricter parsing and error handling in your code.

```javascript
'use strict';
```

---

### 11. **Higher-Order Functions**

JavaScript allows the use of higher-order functions — functions that take other functions as arguments or return functions.

#### **Example: `map`, `filter`, `reduce`**

```javascript
let numbers = [1, 2, 3, 4, 5];

// map: applies a function to each element
let squares = numbers.map(x => x * 2);  // [2, 4, 6, 8, 10]

// filter: filters elements based on a condition
let even = numbers.filter(x => x % 2 === 0);  // [2, 4]

// reduce: reduces an array to a single value
let sum = numbers.reduce((acc, curr) => acc + curr, 0);  // 15
```

