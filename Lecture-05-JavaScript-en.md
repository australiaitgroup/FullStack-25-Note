# Lecture 05 JavaScript

## Description

> This note is based on the lecture ([link](https://jiangren.com.au/study/lesson?programId=672448ecea33cf003687af93&lessonId=673c41cb0022bb00124fe2ed&tab=content) by Ally Tang. The entire lecture is about CSS (**Cascading Style Sheets**). If doubts, please ask anyone or consult the documentation [W3School](https://www.w3schools.com/html/) and [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML). Happy Coding

## 目录

- [JavaScript Introduction](#javascript-introduction)
- [变量 variable](#变量-variable)
- [JS Data Types](#js-data-types)
- [Operators](#operators)
- [Conditional Statements](#conditional-statements)
- [Loops](#loops)
- [Arrays 的方法](#arrays的方法)
- [Functions](#functions)

## JavaScript Introduction

#### History of JavaScript

JavaScript was created at Netscape Communications by Brendan Eich in 1995. Netscape and Eich designed JavaScript as a scripting language for use with the company's flagship web browser, Netscape Navigator. Initially known as LiveScript, Netscape changed the name to JavaScript so they could position it as a companion for the Java language, a product of their partner, Sun Microsystems. Apart from some superficial syntactic similarities, though, JavaScript is in no way related to the Java programming language.

![350](https://i.imgur.com/mmPhRBk.png)

After its release, more and more browsers started adding JavaScript support. Still, for much of its history JavaScript was not regarded as a serious programming language. Its earliest releases suffered from notable performance and security issues, but developers had no alternatives. If they wanted to run programs in the browser, they had to use JavaScript.

In 2008, the creation of Google's open-source Chrome V8, a high-performance JavaScript engine, provided a crucial turning point for JavaScript. The subsequent proliferation of fast JavaScript engines made it possible for developers to build sophisticated browser-based applications with performance that competed with desktop and mobile applications.

Soon after, Ryan Dahl released an open-source, cross-platform environment called Node.js. It provided a way to run JavaScript code from outside a browser. It freed JavaScript from the browser's confines and led directly to JavaScript's current popularity. Today, you can use JavaScript to write all kinds of applications, including browser, server, mobile, and desktop applications. Most major online companies today, including Facebook, Twitter, Netflix, and Google, all use JavaScript in their products.

JavaScript has come a long way since its original implementation: it took a mere 10 days to write it. The JavaScript standard, proposed for the first time as ECMAScript 1 in 1997, is, as of late 2018, in its 9th iteration (ES 2018). The differences between the specifications described in ECMAScript 1 and ES 2018 are immense: they seem to describe different languages. In the intervening years, JavaScript has undergone massive changes. Not everyone agreed with every change, but, taken together, they made JavaScript a more robust, secure, and expressive language.

Morden JavaScript Frameworks and Libraries

- Complexity of Web Applications increased and the need for more efficient and scalable solutions emerged. Hence, we see the rise of many JavaScript frameworks and libraries, such as React, Angular, and Vue.


JavaScript Outside the Browser (How to use JavaScript in a runtime environment)

- With the emergence of Node.js, JavaScript began to be widely used in server-side applications. Node.js allows JavaScript to run on servers, making it a full-stack development language.

Single-threaded and Asynchronous Programming

- JavaScript is a single-threaded language, meaning it can only execute one task at a time. To handle asynchronous operations, JavaScript uses an event loop to process callback functions, Promises, and async/await mechanisms to ensure non-blocking execution.

#### Blocking vs Non-blocking

Think of it like a restaurant

Blocking (Synchronouse) Example
```
// This is like a waiter who can only serve one table at a time
console.log("Take order from Table 1");
// Waiter must wait 2 seconds doing nothing else
setTimeout(() => console.log("Food ready for Table 1"), 2000);
console.log("Take order from Table 2"); // Has to wait until Table 1 is complete
```
Non-blocking Execution Explained
```
// This is like a waiter who can handle multiple tables efficiently
console.log("Take order from Table 1");
// Waiter puts in order and immediately moves on
setTimeout(() => console.log("Food ready for Table 1"), 2000);
console.log("Take order from Table 2"); // Happens immediately
```

#### Event Loop

Event Loop is a mechanism that allows JavaScript to handle asynchronous operations efficiently. It manages the execution of tasks in a non-blocking manner, ensuring that the program remains responsive and efficient.

```
// JavaScript handles async tasks using the event loop
fetch('https://api.example.com/data')  // Start request
    .then(response => {                // Handle when ready
        console.log(response);
    });
console.log("This runs immediately");  // Doesn't wait for fetch
```

#### Callback Functions

- Callback functions are functions that are passed as arguments to other functions and executed when the function completes.

```
// Traditional callback approach
readFile('file.txt', (error, data) => {
    // This runs only when file is ready
    if (error) {
        console.error('Error reading file');
        return;
    }
    console.log(data);
});
console.log('Continuing with other tasks'); // Runs immediately
```

#### 3. Modern Async/Await:

Async/Await is a modern way to handle asynchronous operations in JavaScript. It provides a more readable and synchronous-like syntax for working with promises.

```
async function getData() {
    try {
        // Looks synchronous but doesn't block
        const response = await fetch('https://api.example.com/data');
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error('Error:', error);
    }
}
```

#####Why It's Important:
- User Experience:
  - UI remains responsive while processing
  - No freezing or hanging
- Performance:
  - Can handle multiple operations simultaneously
  - Better resource utilization
- Scalability:
  - Can handle many concurrent users
  - Better server resource management


- Web API and Web Platform Development

As the Web Platform continues to evolve, browsers are providing more and more Web APIs, allowing developers to access device hardware, geolocation, media streams, and other features. This has led to the development of innovative web applications that can now interact with the user's environment in ways that were previously unimaginable.



Scripting Language


JavaScript as a Scripting Language:
- JavaScript doesn't need to be compiled - it's interpreted and executed line by line by the JavaScript engine at runtime.

To expand on this:

1. **Compiled vs Interpreted Languages:**
   - Compiled languages (like C++):
     ```
     Source Code → Compiler → Machine Code → Execution
     ```
   - Interpreted languages (like JavaScript):
     ```
     Source Code → Direct Execution by Interpreter
     ```

2. **How JavaScript Works:**
   ```javascript
   // Each line is read and executed immediately
   console.log("First line");  // Read and executed
   console.log("Second line"); // Then this line
   // No separate compilation step needed
   ```

3. **Benefits:**
   - Faster development cycle (no compilation step)
   - Easier debugging (clear line-by-line execution)
   - Platform independence
   - Dynamic typing and evaluation

4. **Modern JavaScript:**
   - While technically interpreted, modern JavaScript engines (like V8) use Just-In-Time (JIT) compilation
   - This combines benefits of both interpreted and compiled languages
   - Still maintains the ease of development of an interpreted language



## Applications of JavaScript

JavaScript can be used for:

1. **Web Development**
   - Form validation
   - Interactive web effects and animations
   - Single Page Applications (SPAs)
   - Web APIs and AJAX interactions

2. **Server-side Development**
   - Backend services with Node.js
   - RESTful APIs
   - Real-time applications
   - Microservices

3. **Desktop Applications**
   - Cross-platform desktop apps using Electron
   - Examples: VS Code, Slack, Discord, WhatsApp Desktop

4. **Mobile Development**
   - Mobile apps using frameworks like:
     - React Native
     - Ionic
     - Cordova
     - NativeScript

5. **IoT (Internet of Things)**
   - Smart home devices
   - Embedded systems
   - Sensor networks
   - Using platforms like Johnny-Five

6. **Game Development**
   - Browser-based games
   - HTML5 games using frameworks like:
     - Phaser
     - Three.js
     - Babylon.js

7. **AI and Machine Learning**
   - TensorFlow.js for machine learning in browser
   - Natural language processing
   - Computer vision applications


## Components of JavaScript

JavaScript consists of three main components:

1. **ECMAScript Standard**
   - The core language specification
   - Defines basic syntax and features
   - Includes:
     - Variables and data types
     - Operators
     - Control structures
     - Functions
     - Object-oriented features

2. **DOM (Document Object Model)**
   - Interface provided by browsers to manipulate web pages
   - Represents HTML/XML documents as tree structures
   - Allows JavaScript to:
     - Access and modify page elements
     - Handle events
     - Change styles
     - Add/remove content dynamically
   ```javascript
   // DOM manipulation examples
   document.getElementById('myElement')
   document.querySelector('.myClass')
   element.addEventListener('click', handler)
   ```

3. **BOM (Browser Object Model)**
   - Interface for interacting with the browser window
   - Provides access to:
     - Window object
     - Navigation history
     - Location
     - Screen information
     - Browser information
   ```javascript
   // BOM examples
   window.innerHeight
   window.location.href
   window.history.back()
   window.localStorage
   ```

## JavaScript Code Placement

There are three ways to include JavaScript in HTML:

1. **Inline JavaScript**
   - Written directly in HTML element attributes
   - Rarely used due to poor maintainability and readability
   ```html
   <input type="button" onclick="alert('Button clicked')" />
   ```

2. **Internal JavaScript**
   - Embedded within HTML using script tags
   - Useful for page-specific scripts
   ```html
   <script>
     alert("Hello, World.");
   </script>
   ```

3. **External JavaScript Files**
   - Best practice for modern web development
   - Benefits:
     - Separation of concerns
     - Code reusability across pages
     - Browser caching
     - Easier maintenance
     - Better for team collaboration
   ```html
   <script src="index.js"></script>
   ```

Best Practices:
- Prefer external JavaScript files for larger applications
- Place script tags at the end of the body (for better page loading)
- Use async or defer attributes when appropriate
- Keep inline JavaScript to a minimum


## Variable

What is a variable?

- A variable is a named reference to a value.
- Variables must be declared before use, which essentially allocates memory space for them.
- The commonly used keywords for declaring variables are `let`, `const`, and `var` , which have some differences

In computer science,  a variable is simply a named area of a program's memory space where the program can store data. But simply put, a variable is a container for storing data that can be referenced and manipulated by the program.



![](https://i.imgur.com/k58h2H6.png)
  
### Comparison of Variable Declarations

| Feature | `let` | `const` | `var` |
|---------|-------|---------|-------|
| Scope | Block-scoped | Block-scoped | Function-scoped |
| Reassignment | ✅ Can be reassigned | ❌ Cannot be reassigned | ✅ Can be reassigned |
| Hoisting | ❌ No hoisting | ❌ No hoisting | ✅ Hoisted |
| Redeclaration | ❌ Cannot redeclare | ❌ Cannot redeclare | ✅ Can redeclare |
| Temporal Dead Zone | ✅ Has TDZ | ✅ Has TDZ | ❌ No TDZ |
| Global Object Property | ❌ No | ❌ No | ✅ Yes |

Example Usage:
```javascript
// let - for variables that need reassignment
let count = 1;
count = 2; // OK

// const - for constants and references that won't change
const API_KEY = "abc123";
API_KEY = "xyz"; // Error!

// var - older syntax, generally avoided in modern JavaScript
var message = "hello";
var message = "hi"; // OK but not recommended
```

- Variables declared with `var` are hoisted and initialized with `undefined`, while `let` variables are hoisted but not initialized, creating a Temporal Dead Zone.

> What is the Temporal Dead Zone (TDZ) in JavaScript?
> The Temporal Dead Zone is the period between entering a scope and the declaration of a variable, where accessing the variable results in a ReferenceError.


#### Use `var` to define a variable

Note:
- It is common to test your knowledge about var. e.g. disadvantages of using `var` to define a variable and why we should avoid using it.

##### 1. var hoisting


![](https://i.imgur.com/ekSRuh3.png)


`console.log(test);` is before the declaration of `test`, but it is not an error and it will return `undefined` if you console.log it. This is because `var` hoisting. In general, any variable used before it is declared will throw an error but `var` defines the variable in JavaScript, it will return `undefined`.

##### 2. `var` can be re-assigned
![](https://i.imgur.com/9horaRa.png)

##### 3. `var` has function scope before ES6

![](https://i.imgur.com/4UxpHrr.png)

Due to the local scope of the function, the variable `num1` is not defined outside the function. Hence , it will throw an error of `Uncaught ReferenceError: num1 is not defined` if you `console.log` it.

##### 4. `var` does not have block scope

```js
if (true) {
  var a = 1;
}
console.log(a); //-> a,1
```

In summary:
- `var` declared inside a function is function-scoped
- `var` declared outside any function becomes a global variable
- `var` ignores block scope (if, for, while blocks)



````js
  // for example, a variable defined with var in a function is not defined outside the function

  function fun() { // function scope
  var num1 = 20;
  console.log('num1', num1) //-> num1 20
  }
  console.log('num1', num1) //-> Error

           if (true) {
              var a = 1;
           }
           console('a',a) //-> a,1
           // this demonstrates that for var, if does not have a block scope, and the variable a can be accessed outside the if statement
           ```
          
```

- After ES6, let and const set block scope (as a way to fix the issue of `var` hoisting)

> What does a `variable scope` mean?
> - A variable scope refers to where a variable can be accessible by the variable's name (an identifier) in the program.

> What is a function scope in JavaScript?
> - Functions define a new scope for local variables
> - Variables defined inside a function are not accessible outside the function


> What is an inner scope in JavaScript?
> - An inner scope is a block of code that is enclosed within a function or a block of code.
> - Variables defined inside an inner scope are not accessible outside the inner scope.

> What is a block scope in JavaScript?
> - Block scope refers to segments of one or more statement and expressions grouped by a pair of curly brace.
> - Variables defined inside a block scope are not accessible outside the block scope.

> What is a variable shadowing?
> - Variables in inner scope can access variables from the outer scope.



#### Tips for Interview

- Be familiar with the difference between var, let, and const
- Make sure you understand the fundamental concepts of JavaScript before  the intervidew
- When dealing with the error, use try catch


Basic Syntax:
```javascript
try {
    // Code that might throw an error
} catch (error) {
    // Code to handle the error
} finally {
    // Code that runs regardless of error
}
```

Naming Conventions

![](https://i.imgur.com/iqTqCpc.png)

- Variable, property, function, parameter names cannot be keywords or reserved words

![](https://i.imgur.com/0PQ5Fyw.png)

- Camel Case is the most common naming convention in JavaScript

## JS Data Types

> JS is a weakly typed language

Data Types in JavaScript:

1.  Primitive Data Types (基本数据类型 )
    - Number, Boolean, String, Undefined, Null
      ![](https://i.imgur.com/1WouK2R.png)
2.  Reference Data Types (引用数据类型 )
    - Function, Array, Object
    - it stores the address, not the value

JS Type Conversion

- String + other types, the result is always a string type
   Dynamic data manipulation

```js
console.log("" + 12); //-> "12"
console.log("5" + 6); //-> "56"
```

- toString()
- String()
- parseInt() //this function can convert a string to a number type, the result is an integer
  ```js
  console.log(parseInt("3.14")); //-> 3
  console.log(parseInt("120px")); //-> 120
  console.log(parseInt("rem120px")); //-> NaN
  ```
- parseFloat() //this function can convert a string to a number type, the result is a float
  ```js
  console.log(parseFloat("3.14")); //-> 3.14
  console.log(parseFloat("120px")); //-> 120
  console.log(parseFloat("rem120px")); //-> NaN
  ```
- Number()
- Using - \* / to convert a string to a number type
  ```js
  console.log("12" - 0); //-> 12
  console.log("123" - "120"); //-> 3
  console.log("123" * 1); //-> 123
  ```
- Boolean()
  ```js
  console.log(Boolean("")); //-> false
  console.log(Boolean("0")); //-> false
  console.log(Boolean("NaN")); //-> false
  console.log(Boolean("null")); //-> false
  console.log(Boolean("undefined")); //-> false
  console.log(Boolean("123")); //-> true
  console.log(Boolean("hello")); //-> true
  ```

## Operators

How to check a variable's data type

1. You can use `typeof` to check the data type of a variable

![](https://i.imgur.com/SRuiuJs.png)



### Checking Data Types with `typeof`

```javascript
// Numbers
typeof 42;          // "number"
typeof 3.14;        // "number"
typeof NaN;         // "number" (interesting case!)

// Strings
typeof "hello";     // "string"
typeof '';          // "string"
typeof `template`;  // "string"

// Booleans
typeof true;        // "boolean"
typeof false;       // "boolean"

// Undefined
typeof undefined;   // "undefined"
let x;
typeof x;          // "undefined"

// Null (famous quirk!)
typeof null;        // "object" (this is a known JavaScript bug)

// Objects
typeof {};          // "object"
typeof [];          // "object" (arrays are objects!)
typeof new Date();  // "object"

// Functions
typeof function(){}; // "function"
typeof console.log;  // "function"

// Common Usage Examples
function checkType(value) {
    if (typeof value === "string") {
        return "It's a string!";
    } else if (typeof value === "number") {
        return "It's a number!";
    }
    return "It's something else!";
}

console.log(checkType("hello"));     // "It's a string!"
console.log(checkType(123));         // "It's a number!"
console.log(checkType(true));        // "It's something else!"
```

Important Notes:
- `typeof` always returns a string
- Arrays are considered "object"
- `null` is considered "object" (historical bug)
- Use `Array.isArray()` to specifically check for arrays



2. Use `instanceof` to check the data type of a variable for object mostly

![](https://i.imgur.com/sqHSL6g.png)



### Using `instanceof` for Type Checking

```javascript
// Basic Objects
const obj = {};
console.log(obj instanceof Object);      // true
console.log(obj instanceof Array);       // false

// Arrays
const arr = [1, 2, 3];
console.log(arr instanceof Array);       // true
console.log(arr instanceof Object);      // true (arrays inherit from Object)

// Custom Classes
class Car {
    constructor(brand) {
        this.brand = brand;
    }
}
const myCar = new Car('Toyota');
console.log(myCar instanceof Car);       // true
console.log(myCar instanceof Object);    // true

// Built-in Objects
const date = new Date();
console.log(date instanceof Date);       // true

const regex = /hello/;
console.log(regex instanceof RegExp);    // true

// Functions
function test() {}
console.log(test instanceof Function);   // true

// Primitive Types (important limitation!)
const str = "hello";
console.log(str instanceof String);      // false (primitive string)
console.log(new String("hello") instanceof String);  // true (String object)
```

Key Differences from `typeof`:
1. `instanceof` checks the prototype chain
2. Better for custom objects and classes
3. Doesn't work with primitive types
4. Can check inheritance relationships

Common Use Cases:
```javascript
// Error checking
try {
    // some code
} catch (error) {
    if (error instanceof TypeError) {
        // handle type error
    } else if (error instanceof ReferenceError) {
        // handle reference error
    }
}

// Array checking (though Array.isArray() is preferred)
function processArray(arr) {
    if (arr instanceof Array) {
        // process array
    } else {
        throw new Error('Input must be an array');
    }
}
```

Best Practices:
- Use `typeof` for primitive types
- Use `instanceof` for custom objects and inheritance checking
- Use `Array.isArray()` specifically for arrays
- Be aware of primitive vs object wrapper differences



##### The reason why we need to use `instanceof` to check the data type of a variable for object mostly

> **Important Note about `instanceof`:**
> - `instanceof` cannot check primitive types (like numbers, strings, booleans)
> - However, it works well with reference types (objects, arrays, functions)
> - Both `arr instanceof Object` and `obj instanceof Object` return `true` because Array inherits from Object in JavaScript's prototype chain

Example demonstrating this behavior:
```javascript
// Primitive types (doesn't work)
const str = "hello";
const num = 42;
const bool = true;

// Primitive types (doesn't work)
console.log(str instanceof String);   // false
console.log(num instanceof Number);   // false
console.log(bool instanceof Boolean); // false

// Reference types (works)
const arr = [1, 2, 3];
const obj = { x: 1 };

// we won't know the difference between an array and an object using instanceof Object
// you can't be 100% sure if it's an array or an object
// but we can use `Array.isArray()` to check if it's an array
console.log(arr instanceof Array);    // true
console.log(arr instanceof Object);   // true (inheritance!)
console.log(obj instanceof Object);   // true

```

This is why we often use:
- `typeof` for primitive types
- `instanceof` for custom objects and inheritance checking
- `Array.isArray()` specifically for arrays



3.  Use `Array.isArray()` to check if a variable is an array


`Array.isArray()` is a method introduced in HTML5 (supported in IE9 and above) that specifically checks if a value is an array.

```javascript
// Array.isArray() examples
const arr = [1, 2, 3];
const obj = { x: 1 };

console.log(Array.isArray(arr));  // true
console.log(Array.isArray(obj));  // false
```

Why use `Array.isArray()` instead of `instanceof`?
```javascript
// Problem with instanceof for arrays
const arr = [1, 2, 3];
console.log(arr instanceof Array);  // true
console.log(arr instanceof Object); // true - can be confusing!

// Array.isArray is more precise
console.log(Array.isArray(arr));    // true
console.log(Array.isArray({}));     // false
```

Browser Support:
- ✅ IE9+
- ✅ Modern browsers (Chrome, Firefox, Safari, Edge)
- ❌ IE8 and below

Polyfill for older browsers:
```javascript
if (!Array.isArray) {
    Array.isArray = function(arg) {
        return Object.prototype.toString.call(arg) === '[object Array]';
    };
}
```

Best Practice:
- Use `Array.isArray()` when you specifically need to check if something is an array
- It's more reliable than `instanceof` for array checking
- Consider browser support requirements



Note: how to check if a variable is a `null`?

```js
console.log(typeof null); //-> "object"
console.log(null === null); //-> true
console.log(null === undefined); //-> false
```

### Arithmetic Operators

- `+`, `-`, `*`, `/`, `%`
- You cannot directly use floating-point numbers for calculations, as there will be calculation errors
  - Solution:
    1. Convert to integer, then add, then convert back to decimal
    2. `toFixed(1);`

#### Increment and Decrement Operators

- Prefix increment operator `++a`
  - The rule: first add, then return the value
  ```js
  let a = 1;
  console.log(++a); //-> 2
  console.log(a); //-> 2
  ```
- Postfix increment operator `a++`
  - The rule: first return the value, then add
  ```js
  let a = 1;
  console.log(a++); //-> 1
  console.log(a); //-> 2
  ```

比较运算符

![](https://i.imgur.com/vzoLk2k.png)
![](https://i.imgur.com/vngcQM4.png)

- `==` and `===`
  -  `==` will convert the data type of the variable to the same type before comparison, while `===` will not
  - `==` is rarely used in work, and `===` is required

### Logical Operators

- `&&`
  - `console.log(3 > 5 && 3 > 2);`
  - both must be true to return true
- `||`
  - `console.log(3 > 5 || 3 > 2);`
  - only one must be true to return true
- `！`
  - `console.log(!(3 > 5));`
  - Logical NOT operator `!` the opposite of the value; `!true` return `false`

### Operator Precedence

![](https://i.imgur.com/qTiSqB0.png)

Spread Operator `...`

1. copy array
   ```js
   let arr = [1, 2, 3];
   let arr2 = [...arr];
   ```
2. concatenating array
   ```js
   let arr = [1, 2, 3];
   let arr2 = [4, 5, 6];
   let arr3 = [...arr, ...arr2];
   ```
3. output
   ```js
   // 工作中常用的方法
   let person = { name: "tom", age: 18 };
   let person2 = { ...person, name: "jack" };
   ```
   - Similar method: `person2 = Object.assign({}, person, { name: jack })`

### Destructuring Assignment

- Destructuring assignment is a method in JavaScript to assign values from arrays or objects to variables.
- There are two main forms of destructuring assignment: array destructuring and object destructuring.
- String can also be used for destructuring assignment
- Destructuring assignment can set default values

```js
// array
let numbers = [1, 2, 3, 4, 5];
let [a, b, ...rest] = numbers;

console.log(a); //-> 1
console.log(b); //-> 2
console.log(rest); //-> [3, 4, 5]

// object
let person = { name: "John", age: 30, city: "New York" };
let { name, age, ...rest } = person;

console.log(name); //-> John
console.log(age); //-> 30
console.log(rest); //-> { city: "New York" }

// string
let [a, b, ...rest] = "hello";

console.log(a); //-> h
console.log(b); //-> e
console.log(rest); //-> ["l", "l", "o"]

// 默认值
let user = { name: "John", age: 30};
let { name, age, gender: "male"} = user;

console.log(gender); //-> "male"
```

### Use Case: Destructuring Assignment 

```js
// 1. 交换变量
let num1 = 1;
let num2 = 2;
[num1, num2] = [num2, num1];
console.(num1, num2); //-> 2 1

// 2. 从函数返回多个值
// 返回一个数组
function example(){
   return [1, 2, 3];
}

let [a, b, c] = example();
// 返回一个对象
function example2(){
   return {
      sum1:1,
      sum2:2
   }
}

let {a, b} = example2();
```

```js
function sum(first, ...args) {
  console.log(first); //-> 10
  console.lof(args); //-> [20, 30]
}

sum(10, 20, 30);
```

## Conditional Statements

- Use Conditional Statements to make decisions
- `if else`
- `switch`
- Ternary Operator (三元表达式)
  - `expression ? expression1 : expression2`

Compound Ternary Operator (复合三元表达式)

- `(a > b) ? 1 : 0;`

## Loops

- `for` loop
- `while` loop
  ```js
  let sum = 0;
  let i = 1;
  while (i <= 100) {
    sum += i;
    i++;
  }
  ```
- `do...while`
  - Use `break` and `continue` to control the behavior of the loop
  - `continue`: Exit the current loop and proceed to the next iteration
  - `break`: Exit the entire loop

## Array Methods

- `push()`
- `shift()`
- `pop()`
- `unshift() `
  - Add a new element to the front of the array, return the new array length
- `indexOf`
  - Return the index of the first item that satisfies the condition, return `-1` if not found
- `lastIndexOf`
  - Return the index of the last item that satisfies the condition, return `-1` if not found
- `forEach() `
  - Use a callback function to operate on each element
- `filter()`
  - Does not change the original array, returns a new array, including items that satisfy the condition
- `reduce`
  - The main purpose is to execute a provided callback function on all elements of the array, reducing the array to a single value. This method is often used for cumulative, sum, find maximum or minimum, and various aggregation operations.

### Iterating over Objects (遍历对象)

- `for in`

  ```js
  for (变量 in 对象) {
  }
  ```

- `Object.keys(obj)`
  - Get all keys of an object and return an array
  ```js
  Object.keys(obj).forEach((key) => {
    console.log(obj[key]);
  });
  ```
- `Object.keys(value)`
  - Get all values of an object and return an array
- `Object.entries()`
  - Get all key:value pairs of an object and return an array
  ```js
  Object.entries(obj).forEach(([key, value]) => {
    console.log(value);
  });
  ```

> For some methods, be aware of whether the original array has changed and what the method is returned when called

> Some array methods consume a lot of resources, so avoid using them unnecessarily in work
> For example, `concat` is more resource-intensive than `push()`, so if you are allowed to change the original array, choose to change the original array
> If you are required not to change the original array, you can only copy it

## Functions

Difference between `function declaration` and `function expression`

- function declaration
  `js
function fun(a, b){
   console.log(a, b)
}
`
- function expression
  `js
const fun = function(a, b){
   console.log(a, b)
}
`
- Arrow Function (箭头函数)
  `js
  const fun = (a, b) => {
     console.log(a, b)
  }
  `
  > If you pass fewer arguments, the missing arguments are `undefined`

`return` statement 

- Terminate the function, the code after `return` will not be executed
- `return` can only return one value, if you write multiple values after `return`, it will return the last one. `return a, b, c; //-> c`
- If you do not write `return`, it will return `undefined`

#### Shallow Copy (浅拷贝)





##### Shallow Copy (浅拷贝) for Array

// ... existing content ...

### Array Shallow Copy Methods

1. **Using Lodash (Simplest)**
```javascript
const _ = require('lodash');
const original = [1, 2, {x: 3}];
const copy = _.clone(original);

copy[0] = 10;
console.log(original); // [1, 2, {x: 3}]
console.log(copy);    // [10, 2, {x: 3}]
```

2. **Spread Operator (Modern ES6)**
```javascript
const original = [1, 2, {x: 3}];
const copy = [...original];

copy[0] = 10;
console.log(original); // [1, 2, {x: 3}]
console.log(copy);    // [10, 2, {x: 3}]
```

3. **Array.from()**
```javascript
const original = [1, 2, {x: 3}];
const copy = Array.from(original);

copy[0] = 10;
console.log(original); // [1, 2, {x: 3}]
console.log(copy);    // [10, 2, {x: 3}]
```

4. **slice() Method**
```javascript
const original = [1, 2, {x: 3}];
const copy = original.slice();

copy[0] = 10;
console.log(original); // [1, 2, {x: 3}]
console.log(copy);    // [10, 2, {x: 3}]
```

Important Note About Shallow Copies:
```javascript
// Shallow copy limitation with nested objects
const original = [1, 2, {x: 3}];
const copy = [...original];

copy[2].x = 10;
console.log(original); // [1, 2, {x: 10}]  // Nested object is affected!
console.log(copy);    // [1, 2, {x: 10}]
```

Performance Comparison:
- Spread operator (`[...arr]`): Most readable, good performance
- `slice()`: Very good performance
- `Array.from()`: Slightly slower, but more versatile
- Lodash `_.clone()`: Good for complex cases, requires external library

Best Practices:
- Use spread operator for simple arrays
- Use `slice()` for performance-critical code
- Use Lodash when already in the project
- Consider deep copy methods for nested structures



### Object Shallow Copy Methods

1. **Spread Operator (Modern, Most Common)**
```javascript
// Basic usage
const original = { name: 'John', age: 30 };
const copy = { ...original };

// Commonly used for updating properties
const updatedUser = { ...original, age: 31 };
console.log(updatedUser); // { name: 'John', age: 31 }

// Merging objects
const defaults = { theme: 'dark', language: 'en' };
const userPrefs = { language: 'fr' };
const settings = { ...defaults, ...userPrefs };
console.log(settings); // { theme: 'dark', language: 'fr' }
```

2. **Object.assign() Method**
```javascript
// Basic copying
const original = { name: 'John', age: 30 };
const copy = Object.assign({}, original);

// Adding new properties while copying
const enhanced = Object.assign({}, original, { role: 'admin' });
console.log(enhanced); // { name: 'John', age: 30, role: 'admin' }

// Multiple source objects
const object1 = { a: 1 };
const object2 = { b: 2 };
const object3 = { c: 3 };
const combined = Object.assign({}, object1, object2, object3);
console.log(combined); // { a: 1, b: 2, c: 3 }
```

Important Note About Shallow Copies:
```javascript
// Limitation with nested objects
const original = {
    name: 'John',
    address: {
        city: 'New York',
        country: 'USA'
    }
};

// Both methods have the same limitation
const copy1 = { ...original };
const copy2 = Object.assign({}, original);

copy1.address.city = 'Boston';
console.log(original.address.city); // 'Boston' - nested object was modified!
console.log(copy1.address.city);    // 'Boston'
console.log(copy2.address.city);    // 'Boston'
```

Common Use Cases:
```javascript
// 1. Updating state in React
const newState = { ...oldState, updatedProperty: newValue };

// 2. Creating default options
const defaultOptions = { timeout: 1000, retry: 3 };
const userOptions = { timeout: 2000 };
const finalOptions = { ...defaultOptions, ...userOptions };

// 3. Cloning with additional properties
const user = { name: 'John', age: 30 };
const userWithRole = { ...user, role: 'admin' };
```

Best Practices:
- Use spread operator (`...`) for better readability
- Use `Object.assign()` when working with multiple sources
- Be aware of nested objects limitations
- Consider deep copy methods if you need to copy nested structures
- Use TypeScript for better type safety when copying objects



Summary:
- Array
  - The simplest method is the `_.clone` method of lodash
  - Spread Operator
  - `Array.from(arr)`
  - `arr.slice()`
- Object
  - Spread Operator
    > Often used in work
  - `Object.assign() `
    > Often used in work
- For nested objects, only the first layer is copied, and any changes to the deep layer will affect multiple arrays or objects, so you need to use deep copy

#### Deep Copy Methods  (深拷贝)

1. **Using Lodash's cloneDeep (Recommended)**
```javascript
const _ = require('lodash');

const original = {
    name: 'John',
    age: 30,
    address: {
        city: 'New York',
        country: 'USA'
    },
    hobbies: ['reading', { type: 'sports', name: 'basketball' }]
};

const deepCopy = _.cloneDeep(original);

// Modifying nested structures
deepCopy.address.city = 'Boston';
deepCopy.hobbies[1].name = 'football';

console.log(original.address.city);  // 'New York' - unchanged!
console.log(deepCopy.address.city);  // 'Boston'
console.log(original.hobbies[1].name);  // 'basketball' - unchanged!
console.log(deepCopy.hobbies[1].name);  // 'football'
```

2. **Using JSON methods (Simple but limited)**
```javascript
const deepCopy = JSON.parse(JSON.stringify(original));
```

3. **Using structuredClone (Modern browsers)**
```javascript
const deepCopy = structuredClone(original);
```

Comparison:

| Method | Pros | Cons |
|--------|------|------|
| `_.cloneDeep()` | ✅ Handles all types<br>✅ Well tested<br>✅ Reliable | ❌ Requires lodash library |
| `JSON.parse/stringify` | ✅ No dependencies<br>✅ Simple to use | ❌ Loses functions<br>❌ Can't handle circular references<br>❌ Loses undefined values |
| `structuredClone()` | ✅ Native solution<br>✅ Handles circular references | ❌ Limited browser support<br>❌ Can't clone functions |

Best Practices:
- Use `_.cloneDeep()` for production code when you already use Lodash
- Use `structuredClone()` for modern web applications
- Use JSON method only for simple objects with no special types

Example with Complex Data:
```javascript
const complexObject = {
    date: new Date(),
    regex: /hello/,
    nested: {
        array: [1, 2, { x: 3 }],
        func: function() { return 'hello'; }
    }
};

// Lodash handles all types correctly
const deepCopy = _.cloneDeep(complexObject);

// JSON method loses some data types
const jsonCopy = JSON.parse(JSON.stringify(complexObject));
// date becomes string, regex becomes {}, function is lost
```

Summary:
- `JSON.parse(JSON.stringify(object))`
Summary:
- `JSON.parse(JSON.stringify(object))`
- lodash 包 的 cloneDeep `_.cloneDeep`
  - The simplest
- `structuredClone()`



#### Reset parameter (重置参数) in side the `function foo(first, ...args){}`



The rest parameter (`...`) allows a function to accept an **indefinite number of arguments** as an array.

1. **Basic Usage**
```javascript
function sum(first, ...numbers) {
    console.log('First number:', first);    // First argument
    console.log('Rest of numbers:', numbers); // Array of remaining arguments
}

sum(10, 20, 30);
// First number: 10
// Rest of numbers: [20, 30]
```

2. **Adding Numbers Example**
```javascript
function addNumbers(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

console.log(addNumbers(1, 2, 3));      // 6
console.log(addNumbers(10, 20, 30, 40)); // 100
```

3. **Combining with Regular Parameters**
```javascript
function printUserData(username, ...hobbies) {
    console.log(`Username: ${username}`);
    console.log('Hobbies:', hobbies);
}

printUserData('John', 'reading', 'gaming', 'cooking');
// Username: John
// Hobbies: ['reading', 'gaming', 'cooking']
```

4. **Common Use Case: Function Arguments**
```javascript
function logInfo(action, ...details) {
    console.log(`Action: ${action}`);
    console.log('Details:', details);
}

logInfo('USER_LOGIN', 'John', '2024-01-20', 'Chrome');
// Action: USER_LOGIN
// Details: ['John', '2024-01-20', 'Chrome']
```

Important Rules:
1. Rest parameter must be the last parameter
2. Only one rest parameter is allowed per function
3. Rest parameter contains all remaining arguments

❌ Invalid Usage:
```javascript
// Error: Rest parameter must be last
function invalid(...numbers, last) {}

// Error: Only one rest parameter allowed
function invalid(...nums1, ...nums2) {}
```

✅ Valid Usage:
```javascript
function valid(first, second, ...rest) {}
```

Common Use Cases:
- Handling variable number of arguments
- Creating flexible function parameters
- Array operations
- Event handlers with multiple data points



#### Destructuring assignment

Array Destructuring

When discussing objects, you might hear:
```javascript
const person = { name: "John", age: 30 };

// Common phrases:
// - "name is a property of person"
// - "the object has a property called name"
// - "name is a key in the person object"
// - "accessing the name property"
```

In Object, the order of key (or property name) does not matter, the variable must be the same as the key name to get the correct value


```javascript
let obj = {
        bar: "asd",
        foo: 123,
      };

obj["bar"] // -> "asd"
obj.bar //-> "asd"
```


##### Accessing Object Properties

There are two ways to access object properties:

1. **Dot Notation**
```javascript
obj.bar
```

2. **Bracket Notation**
```javascript
obj["bar"]
```

**Important Limitations of Dot Notation:**

1. **Cannot use with property names that contain:**
```javascript
const obj = {};

// ❌ Cannot use dot notation with:
obj.123 = "invalid";      // Error: Invalid syntax
obj.my-property = "bad";  // Error: Interpreted as subtraction
obj.my space = "nope";    // Error: Invalid syntax

// ✅ Must use bracket notation instead:
obj["123"] = "valid";
obj["my-property"] = "good";
obj["my space"] = "works";
```

2. **Cannot use variables as property names:**
```javascript
const propertyName = "bar";

// ❌ Dot notation looks for literal property name "propertyName"
console.log(obj.propertyName);  // undefined

// ✅ Bracket notation can use variables
console.log(obj[propertyName]); // "asd"
```

3. **Cannot use with dynamic property names:**
```javascript
// ❌ Dot notation
obj.user.addresses.0    // Error: Invalid syntax

// ✅ Bracket notation
obj.user.addresses[0]   // Works
obj["user"]["addresses"][0]  // Also works
```

Best Practices:
- Use dot notation for simple, known property names (more readable)
- Use bracket notation when:
  - Property names contain special characters or spaces
  - Property names are stored in variables
  - Property names are dynamic or computed
  - Accessing numeric properties or array indices



##### Array Destructuring with Rest Pattern

The `...` in destructuring (called the "rest pattern") collects remaining elements into an array.

1. **Basic Array Destructuring with Rest**
```javascript
let [first, second, ...rest] = [1, 2, 3, 4, 5];

console.log(first);  // 1
console.log(second); // 2
console.log(rest);   // [3, 4, 5]
```

2. **Skipping Elements**
```javascript
let [, , ...remainingItems] = [1, 2, 3, 4, 5];
console.log(remainingItems); // [3, 4, 5]
```

3. **Function Parameters**
```javascript
function printScores(firstPlace, secondPlace, ...otherPlaces) {
    console.log('Winner:', firstPlace);
    console.log('Runner-up:', secondPlace);
    console.log('Others:', otherPlaces);
}

printScores('Alice', 'Bob', 'Charlie', 'David');
// Winner: Alice
// Runner-up: Bob
// Others: ['Charlie', 'David']
```

4. **Combining with Default Values**
```javascript
let [first = 'default', ...others] = [];
console.log(first);   // 'default'
console.log(others);  // []
```

Important Rules:
- The rest pattern must be the last element
- Can only use one rest pattern in destructuring
- Rest pattern collects all remaining elements

❌ Invalid Usage:
```javascript
// Error: Rest element must be last
let [...rest, last] = [1, 2, 3];

// Error: Cannot have multiple rest elements
let [...rest1, ...rest2] = [1, 2, 3];
```

✅ Valid Usage:
```javascript
let [first, ...rest] = [1, 2, 3];
```

Common Use Cases:
- Splitting arrays into parts
- Collecting function arguments
- Creating new arrays with some elements removed
- Handling variable-length lists

##### Nested Object Destructuring (嵌套解构)

1. **Basic Nested Destructuring**
```javascript
const user = {
    name: {
        first: "John",
        last: "Doe"
    },
    address: {
        city: "New York",
        country: "USA"
    }
};

// Destructuring nested objects
const { name: { first, last } } = user;
console.log(first);  // "John"
console.log(last);   // "Doe"
```

2. **Renaming Variables**
```javascript
const { 
    name: { 
        first: firstName, 
        last: lastName 
    } 
} = user;

console.log(firstName);  // "John"
console.log(lastName);   // "Doe"
```

3. **With Default Values**
```javascript
const user2 = {
    name: {
        first: "Jane"
    }
};

const { 
    name: { 
        first, 
        last = "Smith" // Default value
    } 
} = user2;

console.log(first);  // "Jane"
console.log(last);   // "Smith"
```

4. **Combining with Arrays**
```javascript
const data = {
    user: {
        contact: {
            phones: ["123", "456"]
        }
    }
};

const { 
    user: { 
        contact: { 
            phones: [primaryPhone, secondaryPhone] 
        } 
    } 
} = data;

console.log(primaryPhone);    // "123"
console.log(secondaryPhone);  // "456"
```

5. **Partial Destructuring**
```javascript
const { name, address: { city } } = user;
console.log(name);    // { first: "John", last: "Doe" }
console.log(city);    // "New York"
```

Common Use Cases:
```javascript
// API Response handling
const response = {
    data: {
        user: {
            profile: {
                name: "John",
                age: 30
            }
        }
    }
};

const { 
    data: { 
        user: { 
            profile: { name, age } 
        } 
    } 
} = response;

// React Props
const UserProfile = ({ 
    user: { 
        name: { first, last },
        settings: { theme = 'light' } // with default
    } 
}) => {
    // Component code
};
```

Best Practices:
- Keep nesting levels manageable (2-3 levels max)
- Use intermediate destructuring for complex objects
- Consider TypeScript for better type safety
- Add default values for optional nested properties


##### Failed Destructuring Assignment (解构失败)

When destructuring fails to find a matching property, the variable is assigned `undefined`:

1. **Basic Examples**
```javascript
// Array destructuring
const [a, b, c] = [1, 2];
console.log(a);  // 1
console.log(b);  // 2
console.log(c);  // undefined (no third element)

// Object destructuring
const { name, age, job } = { name: 'John', age: 30 };
console.log(name);  // 'John'
console.log(age);   // 30
console.log(job);   // undefined (property doesn't exist)
```

2. **Nested Destructuring**
```javascript
const user = {
    name: {
        first: 'John'
        // last name is missing
    }
};

const { name: { first, last } } = user;
console.log(first);  // 'John'
console.log(last);   // undefined
```

3. **Avoiding Undefined with Default Values**
```javascript
// With arrays
const [x = 'default', y = 'default'] = [1];
console.log(x);  // 1
console.log(y);  // 'default'

// With objects
const { name = 'Anonymous', age = 0 } = {};
console.log(name);  // 'Anonymous'
console.log(age);   // 0
```

Best Practices:
- Always provide default values for optional properties
- Check for undefined when working with destructured values
- Use TypeScript for better type safety
- Consider using the nullish coalescing operator (`??`)




##### Destructuring Default Assignment (解构默认赋值)

1. **Array Destructuring with Defaults**
```javascript
// Basic default values
const [a = 5, b = 7] = [1];
console.log(a);  // 1 (uses actual value)
console.log(b);  // 7 (uses default value)

// With undefined
const [x = 1, y = 2] = [undefined, undefined];
console.log(x);  // 1 (uses default)
console.log(y);  // 2 (uses default)

// Mixed values
const [first = 'guest', second = 'user'] = ['John'];
console.log(first);   // 'John'
console.log(second);  // 'user'
```

2. **Object Destructuring with Defaults**
```javascript
// Basic object defaults
const { name = 'Anonymous', age = 25 } = { name: 'John' };
console.log(name);  // 'John'
console.log(age);   // 25 (uses default)

// Nested defaults
const { 
    user = { name: 'Guest' },
    settings = { theme: 'light' }
} = { user: { name: 'John' } };

console.log(user.name);      // 'John'
console.log(settings.theme); // 'light'
```

3. **Function Parameters with Defaults**
```javascript
// Default parameters in destructuring
function createUser({ 
    name = 'Anonymous',
    age = 0,
    settings = { theme: 'dark' }
} = {}) {
    console.log(name, age, settings.theme);
}

createUser();  // 'Anonymous' 0 'dark'
createUser({ name: 'John' });  // 'John' 0 'dark'
createUser({ name: 'John', settings: { theme: 'light' } });  // 'John' 0 'light'
```

4. **Complex Defaults**
```javascript
// With computed defaults
const { 
    username = 'user_' + Math.random(),
    created = new Date()
} = {};

// With function calls as defaults
const { 
    id = generateId(),
    timestamp = getTimestamp()
} = {};

// Conditional defaults
const {
    status = (age >= 18 ? 'adult' : 'minor'),
    type = (role === 'admin' ? 'staff' : 'guest')
} = {};
```

Best Practices:
- Use meaningful default values
- Consider using null coalescing (`??`) for complex defaults
- Keep default values simple and predictable
- Document default values in comments for complex objects
- Use TypeScript for better type safety with defaults

Common Use Cases:
```javascript
// API configuration
function fetchData({
    url,
    method = 'GET',
    headers = {},
    timeout = 5000
} = {}) {
    // ... implementation
}

// Component props
function UserCard({
    name = 'Guest',
    avatar = 'default.png',
    role = 'user',
    isOnline = false
} = {}) {
    // ... component code
}
```

##### Use Case: Destructuring Assignment 

 1. Variable Swapping

Simple Variable Swapping
```js
let num1 = 1;
let num2 = 2;
[num1, num2] = [num2, num1];
console.log(num1, num2); //-> 2 1
```


```javascript
// Old way (needs temporary variable)
let x = 5;
let y = 10;
let temp = x;
x = y;
y = temp;

// Modern way with destructuring
let x = 5;
let y = 10;
[x, y] = [y, x];  // Clean and elegant!
```


Multiple Value Swaps
```javascript
// Swap multiple values at once
let [a, b, c] = [1, 2, 3];
[a, b, c] = [c, a, b];
console.log(a, b, c); // 3, 1, 2
```


2. Returning Multiple Values from Functions

Return as array  
```javascript
function example(){
   return [1, 2, 3];
}
let [a, b, c] = example();

// Return as object
function example2(){
   return {
      sum1: 1,
      sum2: 2
   }
}
let {sum1, sum2} = example2();
```



3. **Algorithm Implementation**
```javascript
// Common in sorting algorithms
function bubbleSort(arr) {
    for(let i = 0; i < arr.length; i++) {
        for(let j = 0; j < arr.length - 1; j++) {
            if(arr[j] > arr[j + 1]) {
                [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]]; // Swap!
            }
        }
    }
    return arr;
}
```

4. **State Management**
```javascript
// Common in React or state management
const [first, second] = useState(['old', 'new']);
const swapValues = () => {
    setValues([second, first]);
};
```

Benefits:
- No need for temporary variables
- More readable code
- Less prone to errors
- Single line solution


##### Use Case: Returning Multiple Values from Functions

1. **Using Array Return**
```javascript
// Function returning multiple values as array
function getCoordinates() {
    return [150, 300, 'pixel'];
}

// Destructure the returned values
const [x, y, unit] = getCoordinates();
console.log(x);    // 150
console.log(y);    // 300
console.log(unit); // 'pixel'
```

2. **Using Object Return**
```javascript
// Function returning multiple values as object
function getUserInfo() {
    return {
        name: 'John',
        age: 30,
        isAdmin: true
    };
}

// Destructure the returned values
const { name, age, isAdmin } = getUserInfo();
console.log(name);    // 'John'
console.log(age);     // 30
console.log(isAdmin); // true
```

3. **Common Real-World Examples**
```javascript
// React Hooks
function useWindowSize() {
    return [window.innerWidth, window.innerHeight];
}
const [width, height] = useWindowSize();

// Array methods with index
const entries = ['a', 'b', 'c'].entries();
for (const [index, value] of entries) {
    console.log(`${index}: ${value}`);
}

// API responses
function fetchUserData() {
    return {
        data: { /* ... */ },
        status: 200,
        timestamp: new Date()
    };
}
const { data, status } = fetchUserData();
```

4. **With Default Values**
```javascript
function getConfig() {
    return ['localhost', 3000];
}

// Using defaults for missing values
const [host = 'localhost', port = 8080, timeout = 5000] = getConfig();
```

Best Practices:
- Use arrays when order matters (coordinates, dimensions)
- Use objects when names matter (user properties, config settings)
- Consider TypeScript for better type safety
- Document the return structure

