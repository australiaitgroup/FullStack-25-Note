---
created: 2025-02-20
updated: 2025-03-12
version: 1.0
---

本篇笔记是以 Mason 老师的 Lecture 14 Node.js (Part 1) 的课堂内容整理的随堂笔记。

[课程代码](https://github.com/LazeBear/jr-fullstack-notes-25)

## Table of Contents

1. [Course Structure](#1-course-structure)
2. [About Node.js](#2-about-nodejs)
   - 2.1 [Non-blocking and Asynchronous](#21-non-blocking-and-asynchronous)
   - 2.2 [Event-driven and Event Loop](#22-event-driven-and-event-loop)
3. [Node.js Architecture](#3-nodejs-architecture)
4. [Node Version](#4-node-version)
5. [Module Management](#5-module-management)
   - 5.1 [ES Module](#es-module)
   - 5.2 [CommonJS Module](#commonjs-module)
   - 5.3 [Private Variable & IIFE](#private-variable--iife)
6. [Built-in Module](#6-built-in-module)
   - 6.1 [File System - fs](#61-file-system---fs)
   - 6.2 [Http](#62-http)
7. [JSON](#7-json)

### 下节课必做

- [ ] 下载 Postman

### 0. 课程前导语

Mason 老师 ([LinkedIn](https://www.linkedin.com/in/mason-xiong/))，在 Canvas 就职，主要做前端（React），也会涉及后端(Java)；Node.js 是 Mason 老师上一份工作时候使用;

- Mason 老师不喜欢用 autocomplete，autocomplete 的不精准和不稳定，会给你带来负面影响；
- 在学习阶段不建议使用 Ai，使用 AI 的目的是为了将生产力提速，而非让你掌握一项技能。因为 AI 相当于 Assistant， 充当一个 pair programming 的角色。但是在学习阶段，使用 AI 去完成对概念的理解和思考，是导致自身学习能力以及技能掌握能力下降，因为过度使用导致过度依赖。（假设一下：在没有网络的情况下，你怎么去写代码？）
- 课后可以使用 AI 去提问和深度挖掘相关概念，甚至让 AI 和你讲一遍。
- 大多数 nodejs 后端课程是没有课后作业；
- 先过理论（ppt），再过实践

### 课后该怎么学习

- 把课上讲过的东西给弄明白，课上讲得是必备的
- 把课上提到关键词，必要知识点，全部理解通透
- 对流入信息中的一些名词，产生一点点印象，即便没有什么印象，也可以在相应的地方寻找，比如自己的笔记
- 做相关学习，通过 youtube 视频，可以找 ai，但是找 ai 不一定给你准确的答案，你要有判读版能力
- 其次可以读博客；
- 读文档是最好的学习材料，但不建议在没有任何前提下，把整个文档通读一遍，第一是读不过来，第二是没必要；在有 ai 的情况下，没有必要把文档给通读一遍，完全没有必要了解所有事情
- 只需要把核心知识点，核心概念的掌握了，提及一个知识的时候，你能知道哪一些是关键的，比如在 nodejs。需要明白什么是非阻塞，什么是异步，什么是 event loop，什么是 event driven
- 如果要调用一个具体 package，不知道怎么调用没关系，只是你要首先知道这个 package 的存在，知道怎么找相应的 package；等找到相应文件，为了能过代码实现，取再看下文档
- 这种是你必要掌握的技能
  - 关于 array 的用法
  - 关于时间用法
- 就需要多见几次，把这个案例记下来
- 比如我们这种需求
  - ![](https://i.imgur.com/m3MAMdG.png)
  - 登入页面，计入时间是有这种需求，那就需要掌握时间用法，array 用法

### 1. 后端系列课程大纲

后端课程总共有 11 节内容

- 第一节课：Node.js 基础 （Nodejs 的工作原理）
- 第二节课：API & RESTfulAPI （如何调用 API，如何搭建 server，API 的格式）
- 第三节课：NPM & Express.js （如何管理后端的项目，express 框架）
- 第四节课：MongoDB & Mongoose （怎么和数据库连接，怎么通过代码来和数据库连接）
- 第五节课：Authorization & Autheticaton （用户如何登陆，用户如何授权）
- 第六节课：Testing （测试）
- 第七节课：Deployment （部署）

## 本节课高亮

- nodejs 的特性
- nodejs 中 event loop 的工作机制
- nodejs 的架构

## Node.js 基础

### What is Nodejs

> Node.js is a **JavaScript runtime environment** built on Chrome's V8 engine. (Chrome's V8 engine is a high-performance JavaScript engine.)

- Node.js 不是语言，它本身还是 javascript
- Node.js 只是一个运行环境，也有其它的运行环境，如性能更高一些[Bun](https://bun.sh/)， 还有[Deno](https://deno.com/)；
  **在选择语言，工具和 library，要注意看生态环境。比如说 nodejs 的生态是其它两个运行环境没能匹配上的。**
- 目的是允许 JavaScript 可在浏览器之外运行

- Node.js 主要用来开发 含有 server-side logic 的 web application 和 APIs （本系列内容会提到如何通过 nodejs，从 0 开发这样的服务器，提供数据，从前端开始显示
- 我们也可以通过另外一个框架 Electron 开发桌面应用端。像 VSCode，Slack 就使用 Electron 来开发的。Documentation 传送门 [Electron](https://www.electronjs.org/)

#### Nodejs 两大特性

- 选择 nodejs 的原因是允许开发者建立一个 scalable 和 high-performance networked applications。这是基于两大特性: asynchronous （异步）和 non-blocking nature（非阻塞）

当我们提到“非阻塞”一词，我们是正在处理 I/O 操作 (input/output). Node.js 不会等待 I/O 请求的操作完成，而是继续执行其它任务。

异步是在我们把 I/O 操作完成了之后，我们通过一个回调(callback)的方式，另一种选择是通过事件方式来处理最终结果。

所以，asynchronous （异步）和 non-blocking nature（非阻塞）是合在一起的。

我们单独讲 I/O ，是因为 I/O 请求处理是普遍的，同时是很费时间的。因为很费时间，我们就绕过去，处理其它业务，再回来处理 I/O

#### Asynchronous

Asynchronous 操作好比现在我们去打电话到一家餐厅，进行订桌子。很多时候，餐厅太忙了，员工没办法接电话，这个时候你会在电话里留言，说你要订 4 人台，然后你可以继续做其它事情。等餐厅忙忘了，员工会打回电话给你确定是否还要来，什么时候有时间，这个台订成功了。总而言之，你可以把电话挂断，而非一直在电话里等着回应；

#### Synchronous

同步操作，指的是员工接了电话，但是因为餐厅太忙了，这个员工让你保持通话，在线等一等；单方面等待电话。

#### Non-blocking

在我们执行某一个操作的时候，我们不等待它的执行结果，跳过了这个执行结果的等待，而执行其它任务，这里考察到的概念是 JavaScript 什么时候执行下一行代码。我们得明白 JavaScript 代码是怎么执行的。

#### Blocking

就很好理解了，就是等待执行结果，然后执行下一行代码。

#### Single Threaded

JavaScript 是单线程，一次性只能处理一件事情。意味着当 JavaScript 被阻塞住了，意思是它在等待一个执行结果，即被阻塞的 JavaScript 不能干其它事情，它必须等待执行结果。

举例子：服务器监听，接受请求。

###### 阻塞的服务器

如果每个请求进来，都阻塞住，需要把第一个请求完全处理完之后，再能处理第二个请求。那么，同一时间只能处理一个请求。

###### 非阻塞服务器

服务器可以处理上百个请求。

##### 疑惑

- 但是这个有阻塞的时候，JavaScript 去哪了？我们阻塞的时候，我们需要等这么久，而非阻塞可以处理这么多请求？
- 阻塞，是因为我们要做 io 操作，如文件读写，数据库查询。这些操作我们是不需要通过阻塞来完成，所以采用非阻塞。等我们把这个数据调回来之后，我们再回过头来继续执行，是比较好的处理逻辑。从此，我们需要对 I/O 操作有一个分类处理的逻辑。我们会应用 event-loop 的方式去 distribute，等 I/O 的请求（事件处理）完成了之后，再回来继续处理。[[JR-lecture-14-nodejs-01#Nodejs是事件驱动机制 （event-driven model)]]
- 在 Nodejs 对事件分配出去的阶段，是处于 non-blocking 的；在 non-blocking 的情况下，我们可以继续接受其它请求，然后以此类推进行循环。

#### Nodejs 是事件驱动机制 （event-driven model)

- 后端是一个服务器，而服务器会接受各种各样的请求。然而，每一个请求就是一个事件。
- 当服务器运行中，一个请求进来之后，服务器需要根据这样的请求，触发相应的逻辑，从而应对这个请求。

##### 事件的循环(event loop)是用以实现 event-driven model

event loop 决定了

- 事件怎么循环
- 代码执行的顺序是如何

> [Event-Driven Programming in JavaScript](https://medium.com/@teamtechsis/event-driven-programming-in-javascript-c47ea5975005)

> [Event Loop simulator](http://latentflip.com/loupe/?code=JC5vbignYnV0dG9uJywgJ2NsaWNrJywgZnVuY3Rpb24gb25DbGljaygpIHsKICAgIHNldFRpbWVvdXQoZnVuY3Rpb24gdGltZXIoKSB7CiAgICAgICAgY29uc29sZS5sb2coJ1lvdSBjbGlja2VkIHRoZSBidXR0b24hJyk7ICAgIAogICAgfSwgMjAwMCk7Cn0pOwoKY29uc29sZS5sb2coIkhpISIpOwoKc2V0VGltZW91dChmdW5jdGlvbiB0aW1lb3V0KCkgewogICAgY29uc29sZS5sb2coIkNsaWNrIHRoZSBidXR0b24hIik7Cn0sIDUwMDApOwoKY29uc29sZS5sb2coIldlbGNvbWUgdG8gbG91cGUuIik7!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D)

![](https://i.imgur.com/zK1RhNf.png)

#### 用代码片段去理解 Nodejs 的机制

![](https://i.imgur.com/oyEhznd.png)

![](https://i.imgur.com/3XeHwl1.png)

- 为什么执行顺序是 ACB？

这里几行代码，只有一块是用了`setTimeout()` ;
`setTimeout()`，`fs.readFile()`, `fetch()` 属于异步函数

1. `console.log('A');` 开始执行（Call Stack)
2. 当`setTimeout()` 调用起来，这个函数的调用和以及所传入的参数会一同地进入到推到 WebAPI，这个时候在 C 里面会阻塞，但是在 JavaScript 不会阻塞。
   - 浏览器使用的是 Web API，和 Nodejs 使用的 API 是不一样的，但 WebAPI 和 Node APIs 的目的是相似的：在 JavaScript 的 execution thread 外，处理异步操作[[JR-lecture-14-nodejs-01#异步操作有哪一些]]。
   - 在 Web API(Thread Pool) 执行的情况下，倒计时 3000 milliseconds 开始启动
3. `console.log('C')` 开始执行(Call Stack)，因为 JavaScript 的引擎会继续执行后续的同步任务，直到调用 call stack(栈)为空值
4. 在 3000 milliseconds 之后，setTimeout 函数里的回调函数 （callback）`() => console.log("B")`, 会重新放回到 **Callback Queue （First In First Out**;
5. Event Loop 会把这个回调函数从 CallBack Queue 放回到 the **Call Stack**, 然后 JavaScript 执行

###### 即便我们设置成 0 - setTimeout( () => { console.log("B")}, 0);

- 加 0，或者不加 0（`setTimeout()`默认为 0)
- 我们的执行顺序是不变的, ACB
- JavaScript 把这个设计死了，所以我们不需要去猜，多线程是不知道的

###### 异步操作有哪一些

- **setTimeout / setInterval** → Timing functions
- ajax - **fetch / XMLHttpRequest** → HTTP requests
- **DOM APIs** → Handling UI updates
- **WebSockets** → Real-time communication
- **Geolocation API** → Getting user location

##### 多线程和单线程的对比

- 多线程的坏处是可能会出现冲突，为了解决冲突会导致代码变得复杂
- nodejs 单线程是不会出现冲突

#### How Event Loop Works?

- 代码在浏览器和不在浏览器执行顺序是一样的
- 课后学习 - [http://latentflip.com/loupe/](http://latentflip.com/loupe/ "http://latentflip.com/loupe/")

![](https://i.imgur.com/cDSOq8O.png)

> 先从代码出发，我们首先有一个 jQuery 的代码，这个代码是实现地下的`click me` button，这个会被推到 Web API，但我们整个代码来说，第 7 行代码 `connsole.log("Hi!");`会被先执行；接着，第 9 行的`setTimeout()` 被调用，因为 setTimeout 是异步函数，所以它被推到 Web API。然后，非阻塞操作下，JavaScript 会继续执行第 13 行的`console.log("Welcome to loupe");` 。接着，等到 Call Stack 为空之后，因为 Event Loop 遵行 First in First out，setTimeout()从 WebAPI 推到 CallBack Queue，再推到 Call Stack，接着里面封装的回调函数`console.log("Click the button!");` 将被 JavaScript 执行。

- Call Stack 是 javascript 的任务执行的工作台; 当代码出错时候，我们可以用 stacktrace 来查错
- Web API 可以被理解成外包，外包做的任务不是立马放回工作台，是会在 Callback Queue 等待 Call Stack 为空

![](https://i.imgur.com/LBKrDmU.png)

###### setTimeout 并不总是准确的，该如何修正？

- 在 Node.js 中，除了回调队列（Callback Queue），还有一个 Promise 队列（Promise Queue），用于处理基于 Promise 的异步操作。
- Promise 的处理方式类似于 setTimeout，但 Promise 的回调函数会被推入 Promise 队列，而不是回调队列。
- 事件循环（Event Loop）会优先处理微任务队列(microtask queue), 如 Promise 队列，然后再处理宏任务队列(macrotask queue), 如回调队列(Callback Queue）。

##### heavy computing - call stack 一直繁忙

###### 点击这个 button 会是怎么样的？

![](https://i.imgur.com/ZzHX993.png)

> 我发现，如果我们再执行整套代码时候，再我们 click 了这个 button。这一系列 click 的事件`[click , onClick()]` 其实需要发生在代码执行逻辑之后，因此会放到 Callback Queue, 而不是到 Web API ；
>
> 像之前一样，JavaScript 先将第 9 行推异步函数 setTimeoout 推到 Web API，等第 13 行的代码执行完，即 Call Stack 为空，Web API 将第 9 行的函数放到 Callback Queue 再到 Call Stack，因为 Call Stack 是空。接着，因为第 9 行代码有传入的回调函数，也会在 Call Stack 被调用。这个时候，我们才开始把`[click , onClick()]` 一一地 从 Callback Queue 推到 Call Stack，因为 Call Stack 为空。由于在这个`onClick`还嵌入 异步函数 `setTimeout()`, 即在`onClick()`被调用，立马在 call stack 上又调用了`setTimeout()`, 这个`setTimeout()` 会被推到 Web API (执行 timer)，然后被重新放到 Callback Queue，接着等待 Call Stack 为空，再放到 call stack

---

#### 另外一个例子

假设我们有两个 functions:

```
function foo() {
	console.log("foo");
}

//我们假设第二个function，需要执行1 sec
function runFor1Sec() {
	const start = Date.now();
	// 只要在一秒钟之内，这个condition都是true的
	while (Date.now() - start < 1000 ) {
		console.log("1");
	}
}
// 声明和定义好这两个functions
setTimeout(foo, 100);
runFor1Sec();
consoloe.log("hello");
```

我们的输出结构会是怎么样子的？

> hello -> 在第 1000ms，因为 runFor1Sec()会被执行 1000ms
> foo -> 因为 100ms，已经算在 1000ms 里面，所以 正确答案会在第 1001ms

第 0ms 时， 我们的 call stack, web api, callback queue 都是空的

![](https://i.imgur.com/ZFqPOmO.png)

第 1ms 时，由于 JavaScript 的运行机制，我们首先对函数进行 register，并且 JavaScript 会在 Call Stack 去调用`setTimeout(foo, 100);`
![](https://i.imgur.com/3ipDZuA.png)

当`setTimeout()`被执行完之后，假设执行时间为 1ms，那么我们在第 2ms 时候，我们有 100ms 的 timer，随即被 push 到 web api 里

![](https://i.imgur.com/Dtl2ayX.png)

第 3ms 时，我们的`runFor1Sec()`被放到 call stack 去调用，此时的 timer 变成 99ms

```
3ms
call stack : [runFor1Sec]
web api: [99ms timer]
callback queue: []
```

当我们的 timer 被执行完了 100ms 之后，我们来到了 103ms (其实，3ms 和 100ms 应该是同时进行的)

```
103ms
call stack : [runFor1Sec]
web api: []
callback queue: [100ms timer]
```

我们的 100ms timer 需要在 callback queue 等待，因为**call stack 不为空**
所以，我们需要等`runFor1Sec`被执行完，call stack 为空

我们来到 1003ms，此时`runFor1Sec()`已经结束了

```
1003ms
call stack : [console.log("hello")]
web api: []
callback queue: [100ms timer]
```

但是我们当前代码会去执行 `console.log("hello");`， 我也看到 hello 被打印出来

```
1004ms
call stack : [100ms timer]
web api: []
callback queue: []
```

那么 timer 就调用了`console.log('foo');`

```
1003 hello
1005 foo
```

- 所有同步代码被执行完之后，call stack 才会为空

- javascript 是单线程的，浏览器是多线程的，所以 web api

##### 面试题目-> event loop 可能会导致 timer 不准时，那么怎么让 timer 去准时

解决办法 ： 记录实际倒计时结束的时间，每次 timer 结束的时候，从时间距离来看，到底偏差了多少，做一个矫正。

##### Event Loop 的另外一个概念

- callbakk queue 的另一个更加专业名字叫做 macro task queue ()
  与之对应的是 micro task queue que
- 优先级：micro 先执行于 macro
- 先进先出

- 我们的 promise 是放在微任务里面的。
  ![](https://i.imgur.com/ZuUHntQ.png)

- 宏任务可能是 timer，requestAnimationFrame, i/o 的操作等事件属于 macro task

```
//p指的是promise
callstak: []
macro: [c1, c2, c3]
micro: [p1]
```

- 当 callstack 为空，会先执行微任务，不管宏任务执行多久，由于我们的 promise 的优先级是大于 macro task queue

```
callstak: [p1]
macro: [c1, c2, c3]
micro: []
```

- 如果我们这个`p1`里面嵌套另外一个 p2，即 p1 触发 p2, p2 会先到 micro

```
callstak: []
macro: [c1, c2, c3]
micro: [p2]
```

- 因为优先级这个情况， p2 会先执行

```
callstak: [p2]
macro: [c1, c2, c3]
micro: []
```

- 极端情况下， p1->p2->p3....p_n， 这样的话 callback queue 会一直等

- 要当 micro task queue 有 task 在等的时候，永远是优先执行微任务，不管宏任务等了多久

- micro task 还有 MutationObserver (前端用以监听 DOM）, queueMicrotask(手动添加一个 microtask)

#### 浏览器的 queue 和 nodejs 的 queue 是有区别的

- nodejs 的 queue 会加一个新的对象到这个 queue 里面 - nextTick,
- ⚠️ 注意一点： Nodejs 把 nextTick 的优先级设计得高于 promise

```
node.js -> nextTick -> micro task queue -> higher priority than promise
```

- 在 nodejs 里面，MutationObserver 是不存在的，因为后端是没有 DOM
- 在 nodejs 里面，Macro task（callback queue）有一个新的对象 setImmediate，即在这个事件下加了一个 timer 事件，只不过这个 timer 事件的优先级比较低，通常最后执行
- nextTick 和 setImmediate， 正常开发不需要用到 nextTick；
- 正常开发只需要用 callback 和 promise

---

### Node.js 架构

![](https://i.imgur.com/03TsYDP.png)

- 在 Nodejs 这一框架里头，70%左右的代码 由 C/C++构成的。
- Node.js Bindings 中间绑定层所做的任务是把你所写的 javascript，与 C/C++进行一个连接和沟通。
- 所写的代码主要是在 Application 一层，只需要学会调用 Node.js API 就好

#### Node version

![](https://i.imgur.com/vIgYbRx.png)

- 版本分单双号
- 单数版本 23，是当你想测试 node 的一些新鲜功能，你会使用单数版本
- 双数版本，稳定版，正常开发与商业开发，会使用双数版本

- Nodejs 每个版本分别三种阶段
  - Current, 目前正在开发阶段，包含了新的特性，导致 Current 阶段的 node version 不稳定
  - Active, 当所有新的特性都发布，确保版本不会出现差错，进入一个 active 版本
  - Maintenance，稳定之后，会进入维护阶段
- 完整的周期是 30 个月
- 我们去对版本做出一个选择时候，我们会选择 active
- 课程会使用 22 版本
- 入职之后，会在多个版本切换；不同项目使用的版本很可能不一样。版本不同会出现兼容问题
- 我们可以使用 node version manager，使用工具的好处是一个命令，直接切换；
- 任何一个版本，能达到 active 的时候，都可以使用

---

### 代码阶段 - 通过代码来熟悉 nodejs

- 在命令行执行 node，会进入 REPL 模式
  ![](https://i.imgur.com/a3IFX4k.png)

- 开发时候，我们建立一个`.js`文件去执行代码
- 在浏览器执行 js 代码，是有 window 这一个 object，但在 nodejs，我们没有 windows，取而代之的是 globalthis，这两者是等同的。只是我们在开发是不会用到它的

### Nodejs 核心概念之一：模块化 module

- 我们前端也有模块化 ，是通过 ES module 来实现的；导入和导出是用两个关键词 import 和 export
- 后端模块，nodejs 使用的是 commonJS module
- 两者实际的实现是不一样的
- 比如说，后端的导入是用 require，导出是用 module.exports/ export.xxx

### CommonJS Module 和 ES Module 差异

- 模块（Module）的概念：每一个文件是一个模块
- Commonjs 同步加载，意味着在加载一个模块时候，会阻塞后面模块的加载
- ES Module 异步， 非阻塞， 前端要考虑性能提升
- 这里的区别是因为使用场景的不同。
  - Nodejs 是在后端使用，即不需要考虑性能方面的问题，可以慢慢加载
  - 前端 ES module 采用异步是因为不希望有阻塞，从而提高性能

#### Node 模块的目的

- 第一个目的：模块提高代码可维护性
- 每一个模块，每一个文件负责一个特定的功能，从而相关的功能会在一个文件里面，方便管理开发修改
- 第二个目的：文件域-(scope) - 把变量私有化。我在一个文件（模块）声明的变量，我在另外一个文件可以复用这个变量

```
// index.js
const a = 12;

// index.js
const a = 13;
```

- IIFE (Immediately invoked function expression) 立即执行函数表达式
  - 正常声明一个函数是 `function foo(){}`
  - 如果再加一个`()`，我们有这样立即执行函数 `function foo(){}()`, 但是 javascript 是不理解的，所以 function foo(){}() -> 会报错 error
  - 但因为`()`有优先级，所以我们可以先把函数定义那部分给括器来 `(function foo(){})()`这样就不会报错了。
  - 因为是立即执行函数，所以函数变量名字就没有那么必要了，我们可以直接写成 `(function (){})()`
- 引入这个概念的意义是在执行对函数进行一个私有化，一旦私有化，外部文件是没办法访问它

```js
(function () {
  let count = 0;
  console.log(count);
})();
```

```
console.log(__filename, __dirname);

// Nodejs将 `__filename` 和 `__dirname` 注入进来的
```

![](https://i.imgur.com/RULS8lk.png)
如图所示，我们在外部调用了一个 `increment()`函数，此时这个会报错。

![](https://i.imgur.com/AJeAuja.png)

但是我们非要去调用这个`increment()`函数，我们会怎么办呢？

我们可以用 module 举例子，注意 module 只是一个 reserved keyword
如下图所示，现在外部声明一个 module 的对象，然后在声明函数中设置对象，接着我们可以用一般 object 的方式去赋值，我们这里把`module.increment = increment`,相当于这个 module 里的一个对象，把里面 incremennt 函数给对上，相当于函数指针. 在立即调用的时候，把这个 module 传入进去，
![](https://i.imgur.com/3rBhKEU.png)

之后我们能可以在外面去调用了，但是我们不能直接 access count 去 increment

另外一种性水，我们可以新建一个`counter.js`

![](https://i.imgur.com/sR75L7D.png)

用它的语法结构去导致，本质上是 IIFE

然后，我们去在另外一个文件导入`counter.js`，

![](https://i.imgur.com/Q3iNzZr.png)

另外一个导出的方法

```js
exports.increment = increment;
exports.getCount = getCount;
```

但不能这么写

```js
// ❌
// 这个相当于给 exports 赋一个对象
exports = {
  increment,
  getCount,
};
```

导出是通过 module 导出的。

exports 指向 module.exports 的一个 reference

---

### Nodejs 常用 Builtin Package

- 库 = package

- 如何导入 1️⃣ 个 package

```
const fs = require('fs');
```

之前通过相对路径导入一个 module，javascript 知道这是一个 js 环境，所以`.js`不需要写

```
const { getCount, increment } = require("./counter");
```

- 如何学会导入 package，看官网文档
  ![](https://i.imgur.com/acaAFMC.png)

#### 新的导入方式

#### 读文件

```
const fs require(`node:fs`):
```

![](https://i.imgur.com/pV0mN2E.png)

##### filesystem 的使用

```js
const fs = require("node:fs");

//常见的callback 函数写法，先传一个error
fs.readFile("./node.txt", (error, data) => {
  if (error) {
    console.log(error);
    return;
  }
  console.log(data);
});
```

![](https://i.imgur.com/UrmdX4K.png)

需要传入一个编码格式，才能够把`<Buffer>`给解读出来

```js
const fs = require("node:fs");

//常见的callback 函数写法，先传一个error
fs.readFile("./node.txt", { encoding: "utf-8" }, (error, data) => {
  if (error) {
    console.log(error);
    return;
  }
  console.log(data);
});
```

##### 写文件

`fs.writeFileSync('./test.txt', "hello from nodejs“);`

#### Node 包- path

我们可以用`path`去组装
`path.join(__dirname, './test.txt'`) can recognise the `./`

#### Node 包 http

##### 如何创建一个 http server

我们可以通过一个方法 `.createServer`, 而这个`.createServer()` 接受一个 callback function

```
http.createServer((req, res) => {

})
```

- 对于这个 callback function，我们能想到 Nodejs 的 server 工作原理，event-driven；

- 当有一个请求进来的时候，我们的 callback function 会被触发
- 再来看看这个 callback function，我们给了两个参数，一个是 res，另一个是 req

- 我们可以做一些边界检查，比如说对 `req.url` ，看是否是一个根路径 `/`
- 如果是的话，我们会返回一个`hello`. 注意我们用一个方法 `.end()`
-

![](https://i.imgur.com/Br43F5V.png)

- 为了能够让一个 server 去持续监听，我们需要声明一个变量
  ![](https://i.imgur.com/EsnTcZt.png)

- 我们所写的 server，只是用以处理请求，而做出一些相应逻辑
- 但是这个请求是怎么到达 server 的，

- 因为我们的请求连接，socket - 数据通信是通过端口和端口来实现的
- 而端口值不是随便取的，而是有范围的，上限 6 万 5 千 30 多
  - 0-1000 端口都是被 reserved
  - 1024 - 5 万之前
  - 四万之后会有其它用途
- express 后端常见的是 3000 端口

![](https://i.imgur.com/2ToATMi.png)

- 当你去执行这个命令 `node server.js`, 整个命令似乎卡住了，但并不是哟欧问题，相反是合理的反应。因为它证明我们的 server 正在执行持续监听
- 这时候我们需要回顾一下 event loop 的原理，我们的代码什么时候执行完？取决于 call back queue 是否为空，然后我们也没有 web api
- 因为我们的 server 在执行持续监听，那么这个 call back queue 永远不为空
- server.listen(3000) -> consistently listening

![](https://i.imgur.com/rmPEOT4.png)

`localhost:3000` -> `/` -> 根目录 -> hello

`localhost:3000/abc` -> 返回了一个 `hey`

##### server 返回什么值？

- JSON 是一个文本格式，是一个 text format

- JSON text format，它和 JavaScript 特别像

- 如果我们写成`res.end({a:1, b:2});`，我们是没办法返回的。因为 {a:1, b:2}不是一个字符串
- 因为必须返回 string，`res.end(JSON.stringify({a:1, b:2}));`

> 我一直以为 JSON 就是 javascript 的一个格式 但其实不是，它是一个标准文件格式

- 每次更新 server 的代码，我们需要手动更新
- 我们可以安装这个插件，使得返回 JSON 更加美观
  [https://chromewebstore.google.com/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh](https://chromewebstore.google.com/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh "https://chromewebstore.google.com/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh")

- 除了可以返回 手写字符串，还可以返回 JSON，又可以返回 一个文件`.html`

我们先建立一个`.html`

![](https://i.imgur.com/tBJq39T.png)

然后，再建立一个`about.html`
![](https://i.imgur.com/mWRywj1.png)

我们可以把之前学习的联系在一起，我们先导入 fs 包，和 path 包

```js
const fs = require("fs");

const homePage = fs.readFileSync(path.join(__direname, "home.html"));

const aboutPage = fs.readFileSync(path.join(__direname, "about.html"));
```

当我们声明和赋值之后，我们可以直接更换成 `res.end(homePage);`
![](https://i.imgur.com/JuprMRS.png)

#### 课堂一个小练习

![](https://i.imgur.com/mGHWxaa.png)

每次请求进来，我们都做一个日记录

![](https://i.imgur.com/ga4rZRg.png)

每一次请求进来，我们取当前的 URL，把当前的 URL 取出来`req.url`添加到的 logs 进去

![](https://i.imgur.com/F0s5ghK.png)

练习里面的一点 server 的重启，我们仍会有记录

因为我们已经写好了 log， 我们要利用读文件的方法来读取记录，

![](https://i.imgur.com/guZfCrZ.png)

我们需要保证 `logs.json`文件存在，

1. 我们自行创建一个文件
2. 我们可以写一个 try and catch 方式来避免文件不存在导致的错误

```js
const fs = require("fs");
const path = require("path");

let logsString = "";

try {
  logsString = fs.readFileSync(path.join(__dirname, "logs.json"), "utf-8");
} catch (error) {
  console.error("Error reading logs.json:", error.message);
  logsString = "{}"; // Default value to avoid breaking the program
}

console.log("Logs:", logsString);
```

#### 小知识点： `fs.readFileSync` (Synchronous)

- **Blocks execution** until the file is completely read.
- Code **stops** at this line until reading is done.
- Used when you need to ensure data is read before proceeding.

```js
const fs = require("fs");
const path = require("path");

console.log("Before reading file...");

const data = fs.readFileSync(path.join(__dirname, "logs.json"), "utf-8");

console.log("File content:", data);
console.log("After reading file...");
```

**Output (if the file is large, the program pauses):**

```bash
Before reading file...
File content: {...}  // File content appears
After reading file...
```

#### 小知识点： `fs.readFile` (Asynchronous)

- **Does not block execution**.
- Uses a **callback function** to handle the file content after reading.
- Code execution **continues** while reading happens in the background.

```js
const fs = require("fs");
const path = require("path");

console.log("Before reading file...");

fs.readFile(path.join(__dirname, "logs.json"), "utf-8", (err, data) => {
  if (err) {
    console.error("Error reading file:", err.message);
    return;
  }
  console.log("File content:", data);
});

console.log("After reading file...");
```

```bash
// output
Before reading file...
After reading file...
File content: {...}  // Appears later when reading is done
```
