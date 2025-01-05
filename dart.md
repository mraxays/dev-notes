## Comprehensive Dart Notes

### Table of Contents

1. [Introduction to Dart](#1-introduction-to-dart)
2. [Dart Basics](#2-dart-basics)
3. [Control Structures](#3-control-structures)
4. [Functions](#4-functions)
5. [Classes and Objects](#5-classes-and-objects)
6. [Collections (Lists, Sets, and Maps)](#6-collections-lists-sets-and-maps)
7. [Asynchronous Programming](#7-asynchronous-programming)
8. [Error Handling](#8-error-handling)
9. [Null Safety](#9-null-safety)
10. [Dart Packages and Libraries](#10-dart-packages-and-libraries)
11. [File I/O and HTTP Requests](#11-file-io-and-http-requests)
12. [Regular Expressions](#12-regular-expressions)
13. [Miscellaneous Concepts](#13-miscellaneous-concepts)

---

### 1. Introduction to Dart

- **Definition**: Dart is an open-source, general-purpose programming language developed by Google. It is optimized for building user interfaces and powers frameworks like **Flutter** for mobile, web, and desktop applications.
- **History**: First released in 2011, Dart has grown significantly and is now used to build fast and scalable apps.
- **Execution**: Dart code can be compiled to native machine code or JavaScript for web applications.

### 2. Dart Basics

#### Variables

- **Declaring Variables**:
  - `var`: Type inference, can hold any type.
  - `dynamic`: Allows a variable to change its type during runtime.
  - `final`: Variable can be set only once.
  - `const`: Compile-time constant.

```dart
var name = 'John'; // Type inferred as String
dynamic age = 30; // Can change type later
final city = 'New York'; // Immutable after assignment
const pi = 3.14; // Compile-time constant
```

#### Data Types

- **Primitive Data Types**:
  - **int**: Integer numbers (e.g., `42`)
  - **double**: Floating-point numbers (e.g., `3.14`)
  - **String**: Text data (e.g., `'Hello'`)
  - **bool**: Boolean values (`true` or `false`)
  - **List**: Ordered collection of items (array)
  - **Map**: Key-value pairs

```dart
int age = 25;
double height = 5.9;
String greeting = 'Hello, World!';
bool isAdult = true;
List<int> numbers = [1, 2, 3];
Map<String, String> user = {'name': 'Alice', 'city': 'London'};
```

#### Operators

- **Arithmetic Operators**: `+`, `-`, `*`, `/`, `%`
- **Assignment Operators**: `=`, `+=`, `-=`, `*=`, `/=`, `%=`
- **Comparison Operators**: `==`, `!=`, `>`, `<`, `>=`, `<=`
- **Logical Operators**: `&&` (and), `||` (or), `!` (not)

```dart
int sum = 5 + 3;
bool isEqual = (5 == 5); // true
bool isAdult = (age >= 18) && (isStudent == false);
```

---

### 3. Control Structures

#### Conditional Statements

- **if/else**

```dart
if (age >= 18) {
  print('You are an adult.');
} else {
  print('You are not an adult.');
}
```

- **switch/case**

```dart
String fruit = 'apple';

switch (fruit) {
  case 'banana':
    print('Banana is yellow.');
    break;
  case 'apple':
    print('Apple is red.');
    break;
  default:
    print('Unknown fruit.');
}
```

#### Loops

- **for loop**

```dart
for (int i = 0; i < 5; i++) {
  print(i);
}
```

- **while loop**

```dart
int count = 0;
while (count < 5) {
  print(count);
  count++;
}
```

- **do...while loop**

```dart
int number = 0;
do {
  print(number);
  number++;
} while (number < 5);
```

- **for...in loop**

```dart
List<int> numbers = [1, 2, 3];
for (int num in numbers) {
  print(num);
}
```

---

### 4. Functions

#### Function Declaration

```dart
void greet(String name) {
  print('Hello, $name!');
}

greet('Alice'); // Outputs: Hello, Alice!
```

#### Function Expression (Anonymous Functions)

```dart
var greet = (String name) => 'Hello, $name!';
print(greet('Bob')); // Outputs: Hello, Bob!
```

#### Optional Parameters

```dart
void greet(String name, [String? title]) {
  print('Hello, ${title ?? ''} $name!');
}

greet('Alice');
greet('Alice', 'Dr.');
```

#### Named Parameters

```dart
void greet({required String name, String? title}) {
  print('Hello, ${title ?? ''} $name!');
}

greet(name: 'Alice', title: 'Dr.');
```

---

### 5. Classes and Objects

#### Defining a Class

```dart
class Person {
  String name;
  int age;

  Person(this.name, this.age);

  void greet() {
    print('Hello, my name is $name and I am $age years old.');
  }
}

Person alice = Person('Alice', 30);
alice.greet(); // Outputs: Hello, my name is Alice and I am 30 years old.
```

#### Inheritance

```dart
class Animal {
  void sound() {
    print('Animal makes a sound');
  }
}

class Dog extends Animal {
  @override
  void sound() {
    print('Dog barks');
  }
}

Dog dog = Dog();
dog.sound(); // Outputs: Dog barks
```

---

### 6. Collections (Lists, Sets, and Maps)

#### Lists

```dart
List<String> fruits = ['apple', 'banana', 'cherry'];
fruits.add('date');
print(fruits);
```

#### Sets

```dart
Set<int> numbers = {1, 2, 3, 4};
numbers.add(5);
print(numbers);
```

#### Maps

```dart
Map<String, String> user = {'name': 'Alice', 'city': 'Wonderland'};
user['country'] = 'Wonderland';
print(user);
```

---

### 7. Asynchronous Programming

#### Futures

```dart
Future<String> fetchData() async {
  await Future.delayed(Duration(seconds: 2));
  return 'Data received';
}

fetchData().then((data) => print(data));
```

#### Async/Await

```dart
Future<void> fetchData() async {
  try {
    String data = await Future.delayed(Duration(seconds: 2), () => 'Data received');
    print(data);
  } catch (e) {
    print('Error: $e');
  }
}

fetchData();
```

---

### 8. Error Handling

```dart
try {
  int result = 100 ~/ 0;
  print(result);
} catch (e) {
  print('Error: $e');
} finally {
  print('Execution completed.');
}
```

---

### 9. Null Safety

Dart introduced **null safety** to eliminate null reference errors, a common source of bugs. Null safety ensures that variables cannot be null unless explicitly declared as nullable.

#### Non-Nullable and Nullable Types

```dart
int a = 10; // Non-nullable
int? b; // Nullable
```

#### Null Assertion Operator

Use `!` to assert that a nullable variable is not null.

```dart
int? a;
int b = a!; // Throws error if a is null
```

#### Null Aware Operators

- **`??`**: Provides a default value if a variable is null.
- **`?.`**: Calls a method or accesses a property only if the variable is not null.

```dart
int? age;
print(age ?? 18); // Outputs: 18

String? name;
print(name?.toUpperCase()); // Outputs: null
```

---

### 10. Dart Packages and Libraries

Dart has a rich ecosystem of packages and libraries that can be used to enhance your projects. The main package manager is **pub.dev**.

#### Using Packages

1. Find a package on [pub.dev](https://pub.dev/).
2. Add the package to your `pubspec.yaml` file.
3. Run `dart pub get` to install the package.
4. Import the package into your Dart file.

```yaml
# pubspec.yaml
name: my_app
dependencies:
  http: ^0.13.4
```

```dart
// main.dart
import 'package:http/http.dart' as http;
```

#### Creating Your Own Package

```shell
dart create my_package
```

---

### 11. File I/O and HTTP Requests

#### Reading and Writing Files

```dart
import 'dart:io';

void writeFile() {
  File file = File('example.txt');
  file.writeAsStringSync('Hello, Dart!');
}

void readFile() {
  File file = File('example.txt');
  String content = file.readAsStringSync();
  print(content);
}
```

#### Making HTTP Requests

```dart
import 'package:http/http.dart' as http;

Future<void> fetchData() async {
  var url = Uri.parse('https://jsonplaceholder.typicode.com/posts/1');
  var response = await http.get(url);

  if (response.statusCode == 200) {
    print(response.body);
  } else {
    print('Request failed with status: ${response.statusCode}.');
  }
}
```

---

### 12. Regular Expressions

Dart provides robust support for regular expressions through the **RegExp** class.

#### Creating a Regular Expression

```dart
RegExp regExp = RegExp(r'^[a-zA-Z0-9]+$');
String input = 'Dart123';
print(regExp.hasMatch(input)); // true
```

#### Matching and Replacing

```dart
RegExp regExp = RegExp(r'Dart');
String input = 'I love Dart programming.';
print(input.replaceAll(regExp, 'Flutter')); // I love Flutter programming.
```

---

### 13. Miscellaneous Concepts

#### Generics

```dart
List<int> numbers = [1, 2, 3];

Map<String, int> nameAgeMap = {'Alice': 30, 'Bob': 25};
```

#### Type Casting

```dart
dynamic value = 'Hello';
String message = value as String;
print(message);
```

#### Enums

```dart
enum Color { red, green, blue }

void main() {
  Color favoriteColor = Color.blue;
  print(favoriteColor);
}
```
---
### Happy coding!
