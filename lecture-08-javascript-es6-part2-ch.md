# JavaScript ES6 Part 2

## Description

- 本篇笔记是根据大漠老师 Lecture 08 JavaScript ES6 的课堂内容整理的随堂笔记
- 参考资料：
  - 课程代码：https://github.com/damoqiongqiu/es6-webpack-quickstart
  - 知识结构脑图：https://naotu.baidu.com/file/547762325c74dabadcc476262298814c?token=7a621251020a7fa1

> 无法使用百度的同学，请看PPT

## Table of Contents

1. [Spread 展开](#1-spread-展开)
2. [Rest](#2-rest)
3. [内置对象特性的更新 Build in Object](#3-内置对象特性的更新-build-in-object)
   - 3.1. [模版字符串 Template String](#31-模版字符串-template-string)
   - 3.2. [Object](#32-object)
     - 3.2.1 [构造 Object 字面值的方法有改变](#321-构造-object-字面值的方法有改变)
     - 3.2.2 [关于 Object 的重点 API](#322-关于-object-的重点-api)
   - 3.3. [数组 Array](#33-数组-array)
     - 3.3.1 [Array.from()](#331-arrayfrom)
     - 3.3.2 [Array.of()](#332-arrayof)
   - 3.4. [函数 Function](#34-函数-function)
     - 3.4.1 [箭头函数 Arrow Function](#341-箭头函数-arrow-function)
   - 3.5. [其他内置对象](#35-其他内置对象)
4. [面向对象相关特性](#4-面向对象相关特性)
   - 4.1. [类和构造函数](#41-类和构造函数)
   - 4.2. [继承](#42-继承)
   - 4.3. [super 关键字](#43-super-关键字)
   - 4.4. [静态方法](#44-静态方法)
   - 4.5. [getter 和 setter](#45-getter-和-setter)
5. [模块化](#5-模块化)
6. [新增数据结构](#6-新增数据结构)
   - 6.1. [set 集合](#61-set-集合)
   - 6.2. [map 映射](#62-map-映射)
7. [迭代器](#7-迭代器)
8. [新增 promise](#8-新增-promise)
9. [async/await](#9-asyncawait)
10. [装饰器 decorator)](#10-装饰器-decorator)

## 1. spread 展开

Spread 操作符（也称为展开操作符）是 JavaScript 中的一个语法特性，用于在数组和对象字面量中展开（拆分）可迭代对象的元素或属性。同样也是一个语法糖。

常见操作：

1. 拷贝数组

```js
const arr1 = [1, 2, 3, 4];

const arr2 = [...arr1];
// 使用[]（数组字面值）快速创建了一个数组实例，并将 arr1 中的值拷贝到了 arr2 中
console.log(arr2); // [1, 2, 3, 4]
```

2. 合并数组

```js
const numbers = [1, 2, 3];
const moreNumbers = [4, 5, 6];

// 使用 Spread 操作符将一个数组的元素展开到另一个数组中
const mergedNumbers = [...numbers, ...moreNumbers];

console.log(mergedNumbers); // 输出: [1, 2, 3, 4, 5, 6]
```

3. 展开字符串（特定业务中可能用到）

```js
let str = "Hello, 匠人学员";
console.log(...str); // H e l l o ,   匠 人 学 员
```

4. 展开集合

```js
const numSet = new Set([1, 2, 3, 4]);
console.log(...numSet); // 1 2 3 4
```

5. Object 的展开

```js
const person = {
  name: "Alice",
  age: 30,
};

// 使用 Spread 操作符将一个对象的属性展开到另一个对象中
const newPerson = {
  ...person,
  city: "New York",
};

console.log(newPerson); // 输出: { name: 'Alice', age: 30, city: 'New York' }
```

## 2. rest

在 JavaScript 中，rest 参数允许你将不定数量的函数参数表示为一个数组。Rest 参数语法使用三个点号（...）来表示，通常用于**函数声明**中，以便将多余的（剩余的）参数收集到一个数组中。

```js
// 使用 rest 参数来接收不定数量的参数
function sum(...numbers) {
  let result = 0;
  for (let i of numbers) {
    result += i;
  }

  return result;
}

// 调用 sum 函数，传递不定数量的参数
console.log(sum(1, 2, 3)); // 输出: 6
console.log(sum(1, 2, 3, 4, 5)); // 输出: 15
```

**在数组的解构赋值中使用 rest**

```js
const numbers = [1, 2, 3, 4, 5];

// 使用数组解构赋值将数组的前两个元素赋值给变量，并将剩余的元素收集到一个新数组中
const [first, second, ...rest] = numbers;

console.log(first); // 输出: 1
console.log(second); // 输出: 2
console.log(rest); // 输出: [3, 4, 5]
```

## 3. 内置对象特性的更新 Build in Object

ES6（ECMAScript 2015）引入了许多新的内置对象特性，包括新的模版字符串、数据结构、方法、迭代器等。

### 3.1. 模版字符串 Template String

模板字符串（Template Strings），又称为模板字面量（Template Literals），是 ES6 中新增的一种字符串表示方式，使用反引号 ` （grave accents）来表示字符串。与传统的字符串表示方式不同，模板字符串允许在字符串中插入变量或表达式，并支持多行字符串的书写。

引入模版字符串之前：

```js
// 使用字符串拼接来构建字符串
const name = "Alice";
const greeting = "Hello, " + name + "!";

console.log(greeting); // 输出: Hello, Alice!
```

缺点：

- 写法繁琐麻烦
- 不安全

**引入模版字符串之后**：

```js
// 基本语法：使用反引号 `` 表示字符串
const name = "Alice";
const greeting = `Hello, ${name}!`;

console.log(greeting); // 输出: Hello, Alice!
```

在上面的例子中，${name} 是模板字符串中的插值表达式，它会被变量 name 的值替换。模板字符串中的插值表达式可以包含任意 JavaScript 表达式。

其他例子：

Example1:

```js
let userInfo = {
  username: "Damo",
  age: 18,
  sayHello: function () {
    return this.username;
  },
};

let userDetail = `username: ${userInfo.username}, age: ${
  userInfo.age
}, say hello: ${userInfo.sayHello()}`;
console.log(userDetail); // 输出: username: Damo, age: 18, say hello: Damo
```

> 在上面的例子中，关键字 this 是一个指向当前执行上下文的引用。它通常用在对象方法中，用于引用调用该方法的对象。因此 this.username 引用了 userInfo 对象的 username 属性，等同于 userInfo.username。直接引用对象属性（`return username`）会导致错误。

Example 2:

```js
const userList = [
  { username: "Damo", age: "18", address: "China" },
  { username: "Damo", age: "18", address: "China" },
  { username: "Damo", age: "18", address: "China" },
  { username: "Damo", age: "18", address: "China" },
  { username: "Damo", age: "18", address: "China" },
];

let tempHTML = `
  <ul>
    ${userList
      .map((item, index) => {
        return `<li>username: ${item.username}-age: ${item.age}-address: ${item.address}</li>`;
      })
      .join("")}
  </ul>
`;

document.body.innerHTML = tempHTML;
```

上面是一个实际开发中可能遇到的例子，使用模板字符串构建了一个 HTML 列表，其中使用了 ${} 插值语法来动态地插入用户信息。在模板字符串中，使用了 map 方法对 userList 数组进行遍历，对每个用户信息生成一个 `<li>` 元素，并将其插入到 `<ul>` 列表中。最后，使用 join('') 方法将生成的所有 `<li>` 元素拼接成一个字符串。最后，使用 `document.body.innerHTML` 将构建好的 HTML 列表插入到页面的 `<body>` 元素中，完成了页面的渲染。

> String 还有很多工具函数非常实用，请参考 MDN 文档进行学习：https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String

### 3.2. Object

#### 3.2.1 构造 Object 字面值的方法有改变

ES6 之前，构造 Object 必须严格遵循 key-value 的写法

```js
const userInfo = {
  username: "Damo",
  age: 18,
  address: "China",
};
```

ES6 之后：

```js
let username = "Damo";
let age = 18;
let address = "China";
const userInfo = { username, age, address }; // 这是一个语法糖（syntax sugar）
```

#### 3.2.2 关于 Object 的重点 API

- `Object.keys()`
- `Object.values()`
- `Object.entries()`
- `Object.fromEntries()` - 构建对象字面值有用的方法
- `Object.is()`
- `Object.assign()`
- ...

> 以上详细内容，请参考 MDN: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object

### 3.3. 数组 Array

ES6 中给数组新增了 2 个工具函数

#### 3.3.1 Array.from()

Array.from() 是 ES6 中的一个静态方法，用于将类数组对象或可迭代对象（iterable）转换为一个新的数组。是一种构造数组的新方式。

```js
// Example1:
const arr1 = Array.from("Hello World");
console.log(arr1); // ['H', 'e', 'l', 'l', 'o', ' ', 'W', 'o', 'r', 'l', 'd']

// Example2:
const arr2 = Array.from({
  0: "a",
  1: "b",
  2: "c",
  length: 3,
});
console.log(arr2); // ['a', 'b', 'c']
```

#### 3.3.2. Array.of()

Array.of() 是 ES6 中的一个静态方法，用于创建一个新的数组实例，该数组实例包含传入的参数作为其元素。与 Array() 构造函数不同的是，Array.of() 会保留传入参数的数量和类型，而不会对参数进行任何特殊处理。

```js
const arr3 = Array.of(1, 2, 3);
console.log(arr3); // [1, 2, 3]
```

还有一些重要的工具函数需要了解：

- `Array.concat()`
- `Array.includes()`
- ...

> 请参考 MDN: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array

### 3.4. 函数 Function

#### 3.4.1. 箭头函数 Arrow Function

箭头函数（Arrow Function）是 ES6 中引入的一种新的函数语法，它提供了一种更简洁的方式来定义函数。也是一种语法糖。

**Syntax**

```js
(parameters) => {
  statements;
};
```

**Examples**

```js
// 给定一个数组，将该数组中的每个元素乘以 2，生成一个新的数组。

// 使用传统的函数表达式
const arr = [1, 2, 3];
const newArr = arr.map(function (item, index) {
  return item * 2;
});
console.log(arr);
console.log(newArr);

// 使用箭头函数
const arr = [1, 2, 3];
const newArr = arr.map((item, index) => item * 2);
console.log(arr);
console.log(newArr);
```

在上面的例子中，使用 map 方法对 arr 数组进行遍历，对每个元素执行回调函数，将每个元素乘以 2。map 方法会返回一个新数组，该数组包含了对原数组每个元素执行回调函数后的结果。

> map 方法不会改变原数组，而是返回一个新数组。因此，arr 数组不会被修改，而是保持不变。

**箭头函数作用域**

箭头函数的作用域是词法作用域：

1.  **词法作用域（Lexical Scope）**：箭头函数的作用域是由它定义时所在的作用域决定的，而不是调用时所在的作用域。这意味着箭头函数内部的 this、arguments、super 和 new.target 等变量的值都是继承自外层最近一层非箭头函数的作用域。

2.  **没有自己的 `this`**：箭头函数内部没有自己的 `this`，它会捕获所在的执行上下文中的 `this` 值，并且无法通过 call()、apply()、bind() 等方法改变 `this` 的值。因此，在箭头函数内部使用 `this`，它指向的是定义时所在的对象，而不是调用时所在的对象。

3.  **没有自己的 arguments 对象**：箭头函数内部也没有自己的 arguments 对象，它会继承所在的执行上下文中的 arguments 对象。

4.  **没有 prototype 属性**：箭头函数没有 prototype 属性，因此无法通过 new 关键字来创建对象。

> 参考 MDN: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions

### 3.5. 其他内置对象

本次课程中没有涉及，请大家自行参考 MDN 学习

- `Number`: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number
- `Math`: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math
- `RegExp`: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp

## 4. 面向对象相关特性

ES6（ECMAScript 2015）引入了一些新的面向对象编程的特性，使得 JavaScript 中的对象更加强大和灵活。以下是 ES6 中面向对象编程方面的一些主要特性：

### 4.1. 类和构造函数

ES6 引入了 `class` 关键字，使得 JavaScript 可以更方便地使用类来定义对象。类可以用来创建对象的模板，并且可以包含构造函数、属性和方法。

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  sayHello() {
    console.log(`Hello, my name is ${this.name}`);
  }
}

const person = new Person("Alice", 25); // 使用 new 关键字创建实例
person.sayHello(); // 输出: Hello, my name is Alice
```

### 4.2. 继承

ES6 中的类支持继承，可以使用 `extends` 关键字来实现类的继承关系。子类可以继承父类的属性和方法，并且可以重写父类的方法。

```js
class Student extends Person {
  constructor(name, age, grade) {
    super(name, age);
    this.grade = grade;
  }

  study() {
    console.log(`${this.name} is studying in grade ${this.grade}`);
  }
}

const student = new Student("Bob", 18, 12); // 使用 new 关键字创建实例
student.sayHello(); // 输出: Hello, my name is Bob
student.study(); // 输出: Bob is studying in grade 12
```

### 4.3. super 关键字

super 关键字可以在子类的构造函数中调用父类的构造函数，并且在子类中访问父类的方法。

```js
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name); // 调用父类的构造函数
    this.breed = breed;
  }

  speak() {
    super.speak(); // 调用父类的方法
    console.log(`${this.name} is a ${this.breed}.`);
  }
}

const dog = new Dog("Buddy", "Golden Retriever");
dog.speak();
```

在这个例子中，Animal 类表示动物，有一个 name 属性和一个 speak 方法。Dog 类继承自 Animal 类，表示狗，有一个额外的 breed 属性。在 Dog 类的构造函数中，我们使用 super(name) 调用了父类 Animal 的构造函数，确保了 name 属性被正确初始化。在 Dog 类的 speak 方法中，我们使用 super.speak() 调用了父类 Animal 的 speak 方法，然后输出了狗的品种信息。

### 4.4. 静态方法

使用 static 关键字来定义类的静态方法，静态方法不会被实例继承，而是直接通过类来调用。

```js
class MathUtil {
  static add(a, b) {
    return a + b;
  }
}

console.log(MathUtil.add(2, 3)); // 输出: 5
```

### 4.5. getter 和 settet

ES6 中的类支持使用 get 和 set 关键字定义属性的 getter 和 setter 方法

```js
class Rectangle {
  constructor(width, height) {
    this._width = width;
    this._height = height;
  }

  get area() {
    return this._width * this._height;
  }

  set width(value) {
    if (value > 0) {
      this._width = value;
    }
  }
}

const rectangle = new Rectangle(3, 4);
console.log(rectangle.area); // 输出: 12
rectangle.width = 5;
console.log(rectangle.area); // 输出: 20
```

> 更多特性请参考 MDN: https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object-oriented_programming

## 5. 模块化

JavaScript 模块化指的是将 JavaScript 代码分割成独立的模块，以便于组织、管理和重用代码。ES6 模块系统使用 `import` 和 `export` 关键字来定义模块的导入和导出。

Example:

当前程序有两个文件 Animal.js 和 Monkey.js

```js
// Animal.js
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}

export default Animal;
```

```js
// Monkey.js
import { Animal } from "./Animal.js";

export class Monkey extends Animal {
  constructor(name, type) {
    super(name);
    this.type = type;
  }

  swing() {
    console.log(`${this.name} is swinging from tree to tree.`);
  }
}
```

在上面的示例中，Animal.js 定义了一个名为 Animal 的类，并将其导出。Monkey.js 导入了 Animal.js 中导出的 Animal 类，并使用 `extends` 关键字扩展了它，创建了一个名为 Monkey 的子类。

> 更多可参考 MDN: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

## 6. 新增数据结构

### 6.1. Set 集合

Set 是一种值的无序集合，其中每个值都是唯一的，不允许重复。与数组不同，Set 中的值是唯一的，不会存在相同的值。可以使用 Set 构造函数创建一个空的 Set 对象，然后使用 add() 方法添加值，使用 has() 方法检查值是否存在，以及使用 delete() 方法删除值。

```js
let set = new Set();
set.add("value1");
set.add("value2");
console.log(set.has("value1")); // 输出: true
set.delete("value1");
```

> 常用方法请参考 MDN: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set

### 6.2. Map 映射

Map 是一种键值对的集合，其中每个键都唯一，可以是任意值（包括对象或原始值）。与对象不同，Map 中的键值对保持插入顺序。可以使用 Map 构造函数创建一个空的 Map 对象，然后使用 set() 方法添加键值对，使用 get() 方法获取值，使用 has() 方法检查键是否存在，以及使用 delete() 方法删除键值对。

```js
let map = new Map();
map.set("key1", "value1");
map.set("key2", "value2");
console.log(map.get("key1")); // 输出: value1
console.log(map.has("key2")); // 输出: true
map.delete("key2");
```

> 常用方法请参考 MDN: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map

## 7. 迭代器

ES6 引入了迭代器（Iterator）和可迭代对象（Iterable）的概念，这是一种更灵活、更统一的数据访问方式。迭代器是一种对象，它定义了一个序列的访问方式，使得我们可以按需获取序列中的元素。可迭代对象是一种具有迭代器的对象，它可以被迭代（遍历）。

**隐式调用**

```js
// 新语法 for...of，也是一个语法糖
let arr1 = [1, 2, 3];
for (let item of arr1) {
  console.log(item);
}
```

**显式调用**

该方式不常用

```js
let arr2 = [3, 4, 5];
let iterator = arr2[Symbol.iterator]();

while (iterator.hasNext()) {
  console.log(iterator.next());
}
```

## 8. 新增 promise

ES6 引入了 Promise 对象，它是一种用于异步编程的标准化方式，旨在解决 JavaScript 中回调地狱（callback hell）的问题，使得异步代码更加清晰、可读和可维护。

用法：

创建 Promise：Promise 是一个表示异步操作最终完成或失败的对象。你可以通过 new Promise() 构造函数来创建一个 Promise 对象，并传入一个执行器函数作为参数，该执行器函数会立即执行，并在异步操作完成时调用 resolve 函数来表示成功，或调用 reject 函数来表示失败。

```js
let promise = new Promise((resolve, reject) => {
  // 异步操作
  setTimeout(() => {
    // 成功时调用 resolve
    resolve("成功");
    // 或者失败时调用 reject
    // reject('失败');
  }, 1000);
});
```

处理 Promise 结果：可以使用 then() 方法来处理 Promise 对象的结果。then() 方法接受两个回调函数作为参数，第一个参数用于处理成功的情况，第二个参数用于处理失败的情况。

```js
promise.then(
  (result) => {
    console.log("成功:", result);
  },
  (error) => {
    console.error("失败:", error);
  }
);
```

Promise.all()：Promise.all() 方法接受一个 Promise 对象的数组作为参数，当所有 Promise 对象都成功时，返回一个新的 Promise 对象，其结果为所有 Promise 对象的结果组成的数组。如果任意一个 Promise 对象失败，则返回的 Promise 对象也失败。

```js
let promise1 = Promise.resolve("成功1");
let promise2 = Promise.resolve("成功2");

Promise.all([promise1, promise2]).then((results) => {
  console.log(results); // 输出: ['成功1', '成功2']
});
```

> 更多例子请参考 MDN: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise

## 9. async/await

async/await 是 ES8（也称为 ES2017）引入的异步编程语法糖，它提供了一种更简洁、更直观的方式来处理异步操作。async 函数用于定义一个异步函数，而 await 关键字用于等待一个 Promise 对象的解析，并将其结果返回。

> 可以直接参考老师 github 中的例子：https://github.com/damoqiongqiu/es6-webpack-quickstart/blob/master/src/es8/async-await.js

## 10. 装饰器 Decorator

装饰器是一种用于修改类、方法、属性或参数的行为的特殊语法。它们可以应用于类、类方法、类属性以及方法参数。

装饰器以 `@`符号紧跟着函数或类名，并且可以传递参数。

> 参考老师代码: https://github.com/damoqiongqiu/es6-webpack-quickstart/blob/master/src/es7/Decotrator.js
