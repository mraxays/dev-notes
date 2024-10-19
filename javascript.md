### JavaScript: Key Concepts and Notes

JavaScript is a high-level, interpreted programming language commonly used to create interactive effects within web browsers. Below are some important concepts and notes to help you understand JavaScript better:

---

### 1. **Basics**
- **Variables**:
  - `var`: function-scoped (legacy, avoid using).
  - `let`: block-scoped, can be reassigned.
  - `const`: block-scoped, cannot be reassigned.

  ```javascript
  let x = 10;      // Mutable
  const y = 20;    // Immutable
  ```

- **Data Types**:
  - **Primitive Types**: `Number`, `String`, `Boolean`, `Null`, `Undefined`, `Symbol`, `BigInt`.
  - **Objects**: Complex data types (Arrays, Functions, Date, etc.).

  ```javascript
  let name = "John";  // String
  let age = 30;       // Number
  let isAdult = true; // Boolean
  ```

- **Operators**:
  - Arithmetic: `+`, `-`, `*`, `/`, `%`, `++`, `--`.
  - Assignment: `=`, `+=`, `-=`, `*=`, `/=`, `%=`.
  - Comparison: `==`, `===`, `!=`, `!==`, `>`, `<`, `>=`, `<=`.
  - Logical: `&&`, `||`, `!`.

  ```javascript
  let result = 5 + 3;      // 8
  let isEqual = 5 === '5'; // false (strict equality)
  ```

---

### 2. **Control Structures**
- **Conditional Statements**: `if`, `else if`, `else`, `switch`.
  ```javascript
  let score = 85;

  if (score > 90) {
      console.log('A');
  } else if (score > 75) {
      console.log('B');
  } else {
      console.log('C');
  }
  ```

- **Loops**: `for`, `while`, `do...while`, `for...of`, `for...in`.
  ```javascript
  for (let i = 0; i < 5; i++) {
      console.log(i);  // Outputs 0 to 4
  }

  let arr = [1, 2, 3];
  for (let item of arr) {
      console.log(item);  // Outputs each item in array
  }
  ```

---

### 3. **Functions**
- **Function Declaration**:
  ```javascript
  function greet(name) {
      return `Hello, ${name}`;
  }
  ```

- **Function Expression**:
  ```javascript
  const greet = function(name) {
      return `Hello, ${name}`;
  };
  ```

- **Arrow Functions**: Shorter syntax, `this` is lexically bound.
  ```javascript
  const greet = (name) => `Hello, ${name}`;
  ```

- **Default Parameters**:
  ```javascript
  function greet(name = 'Guest') {
      return `Hello, ${name}`;
  }
  ```

---

### 4. **Objects and Arrays**
- **Objects**: Key-value pairs.
  ```javascript
  let person = {
      name: 'John',
      age: 30,
      greet: function() {
          console.log(`Hello, I am ${this.name}`);
      }
  };
  person.greet();  // Access object method
  ```

- **Arrays**: List-like objects.
  ```javascript
  let arr = [10, 20, 30];
  console.log(arr[0]);  // Access element at index 0
  ```

- **Common Array Methods**:
  - `push()`, `pop()`, `shift()`, `unshift()`: Add/remove elements.
  - `map()`, `filter()`, `forEach()`, `reduce()`: Iterate and manipulate arrays.
  ```javascript
  let numbers = [1, 2, 3, 4];
  let doubled = numbers.map(num => num * 2); // [2, 4, 6, 8]
  ```

---

### 5. **ES6 Features (ECMAScript 2015)**
- **Template Literals**: Use backticks (\`\`) for string interpolation.
  ```javascript
  let name = 'John';
  console.log(`Hello, ${name}!`); // Outputs: Hello, John!
  ```

- **Destructuring**:
  ```javascript
  let person = {name: 'John', age: 30};
  let {name, age} = person;  // Extracts name and age from the object
  ```

- **Spread Operator**: Expands elements of arrays or objects.
  ```javascript
  let arr = [1, 2, 3];
  let arr2 = [...arr, 4, 5];  // [1, 2, 3, 4, 5]
  ```

---

### 6. **Asynchronous JavaScript**
- **Callbacks**:
  ```javascript
  function fetchData(callback) {
      setTimeout(() => {
          callback('Data loaded');
      }, 1000);
  }
  fetchData(data => console.log(data));  // Outputs after 1 sec
  ```

- **Promises**: Represents a future value.
  ```javascript
  const promise = new Promise((resolve, reject) => {
      let success = true;
      if (success) {
          resolve('Data loaded');
      } else {
          reject('Error occurred');
      }
  });

  promise.then(data => console.log(data)).catch(err => console.log(err));
  ```

- **Async/Await**: Cleaner syntax for handling promises.
  ```javascript
  async function fetchData() {
      let result = await fetch('https://api.example.com');
      let data = await result.json();
      console.log(data);
  }
  ```

---

### 7. **DOM Manipulation**
- **Selecting Elements**: Use `getElementById`, `querySelector`, `getElementsByClassName`, etc.
  ```javascript
  let element = document.getElementById('myElement');
  let elements = document.querySelectorAll('.myClass');
  ```

- **Modifying Content**:
  ```javascript
  element.textContent = 'New Content';
  element.style.color = 'blue';
  ```

- **Event Listeners**: Listen for user actions like clicks or key presses.
  ```javascript
  element.addEventListener('click', function() {
      console.log('Element clicked');
  });
  ```

---

### 8. **Error Handling**
- **Try/Catch**: Handle exceptions in JavaScript.
  ```javascript
  try {
      let result = riskyOperation();
  } catch (error) {
      console.log('Error:', error);
  } finally {
      console.log('Finally block executed');
  }
  ```

---

### 9. **Modules** (ES6+)
- Export and import functions, objects, or primitives from/to other files.
  - **Export**:
    ```javascript
    export const name = 'John';
    export function greet() {
        return 'Hello';
    }
    ```

  - **Import**:
    ```javascript
    import { name, greet } from './module.js';
    ```

---

### 10. **Object-Oriented JavaScript**
- **Classes**: Blueprints for creating objects.
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

- **Inheritance**: Subclasses can inherit properties and methods.
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

  let emp = new Employee('Jane', 28, 'Developer');
  emp.work();  // Outputs: Jane is working as a Developer
  ```

---

### 11. **Miscellaneous**
- **Truthy and Falsy Values**: In JavaScript, some values evaluate to `false` in conditional checks (e.g., `0`, `null`, `undefined`, `NaN`, `false`, `""`). Everything else is "truthy".
  
  ```javascript
  if (0) {
      console.log('This will not run'); // 0 is falsy
  }
  ```

- **Short-Circuit Evaluation**:
  ```javascript
  let name = userName || 'Guest';  // Uses 'Guest' if userName is falsy
  ```

- **Strict Mode**: Makes JavaScript execute in a more secure manner. Declare it at the top of your script.
  ```javascript
  'use strict';
  ```

--- 
