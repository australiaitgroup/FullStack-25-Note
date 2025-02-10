# Lecture 10 React Part 2

本篇笔记以 Long Zhao 老师的 Lecture 10 React (Part 2) 的课堂内容整理的随堂笔记

简单地回顾一下第一节课内容
![](https://i.imgur.com/m27LaSZ.png)

Q：What is the difference between Senior and Junior?
- Senior 和junior的体现不会再代码层面上
- 区别在于senior会对一个变动的需求，复杂的情况，进行一个不同分解；
相反，junior因经验少不会对其应变，或者解决方案不够稳定，甚至可能没有解决方案，或者花的时间太长，才能把问题解决。

一个需求过来，principle,senior, mid, junior 的反应
- junior会说这个需求我从来没做过，做不了
- mid会说，这个需求我没有做过，但是给我一点时间，可以做过来
- senior，这个需求简单，我以前做过，很快的。Senior甚至会反哺（mentor）junior
- principle/staff engineer 不仅会解答出来，而且会很系统地告诉你，具体考量是什么，然后具体风险会是什么，需要留意的错误是什么.


简单地回顾了下 getStops 题目
![](https://i.imgur.com/7rlb6FD.png)

这个有点炫技的成分，会被视为risky candidate。因为ta没有考虑到可读性，或者想象到了一点可维护性（for example he or she would say "hash table can be good for maintaining code"


## 正课

### 1. 前端工程化与 React

>面试技巧1：首先，直接了当地回答， 直切重点。许多同学的第一句话直接扣到细节上。因为他们可能会铺垫了好多句，可能第六句才是重点。现在面试的远程面试，如果你回答到面试官的前几句不是ta想要的，ta不开心不耐烦，马上切出去做其他事情了。(md，我遇到过这样的面试官,也不能拿人家怎么样)

>面试技巧2：说话永远说两边，回答从两面性回答，而不是一面,"React虽好，但是没有angular“。如果面试官问你"你为什么用react而不用angular？",而你天真地回答一大堆react的好，但是有没有可能万一面试你的人最近上手项目就是用angular的。当ta问你css和sass的好，说了一堆sass的好，但是要写css也行，也有补救的方法。看项目需求。如果这个项目要求我去写css，我也会用可读性，可复用，可维护来写css

>面试技巧3: 不要从技术的角度去回答面试官的问题 “你为什么用X？”这个题目，实际上考的不是技术，而是编程思维。


#### JavaScript(Vanilla JS | Node.js)

- Vanilla JavaScript 是指原生 JavaScript，未经任何库或者框架修改的纯粹的 JavaScript。它不依赖于任何外部库，如 jQuery 或 React。
- 使用 Vanilla JavaScript 操作前端页面，引入了 DOM

#### DOM（Document Object Model，文档对象模型）

DOM 是一个编程接口，它允许 JavaScript 动态地访问和更新文档内容、结构和样式。当浏览器加载页面时，他会创建页面的文档对象模型。DOM API 就是让开发者可以通过变成方式与 DOM 交互的一组方法和属性。参考 MDN: [Document Object Model (DOM)](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)

* DOM API 是框架和库操作浏览器的唯一方法
* 由于 Vanilla JavaScript 自身存在的问题（语法复杂、可读性差等），jQurey 被引入。



写了P1的同学就知道，HTML， CSS， JAVASCRIPT 具有天生得不可读，不可维护，不可复用。这也是为什么前端之前很难工程化。原生的JavaScript和DOM-API绑起来了，看如图下
![](https://i.imgur.com/c4TQXqk.png)

DOM又长又臭，可读性很差。

#### JQuery

* 跨浏览器的兼容性
* 简化的语法
* 易用的 AJAX 语法
* 强大的选择器引擎


jQuery的出现推动了前端的发展，但是没有解决核心的问题，其在处理大型、复杂应用时的局限性导致了现代框架和库的出现。
虽然把那些又长又臭的代码给遮掩了，但是没有解决核心问题


![](https://i.imgur.com/4CTH2Mj.png)

以上的图，4代码本质上在做同样的事情，但是不同写法。1是原生js，2，3是jQurey，4是await (async await的写法)


#### IT行业的发展规律

整个IT发展，是一个消除神秘化的过程，最终目的就是每个人都可以写代码，每个人都可以开发。
jQuery 之前，javascript还没有人愿意当javascript developer，因为太难了。
早期没有人愿意做前端， jQuery出来之后，网页应用的概念出来了。jquery出来之前，你还没办法在网页看到网页应用。
在python出来之前，数据分析师，数据工程师；之后，se和de是平级，da和de跟着python走进了平常百姓的家。

代码不需要写太复杂，只需要越来越普及

deepseek 打平了ai的门槛，普通老百姓都可以训练自己的ai了。之前，现在新的岗位 十几万ai engineer岗位已经出现了
所有工具最终目的是大家都能用。

这里的讲了一个规律，有以前的高高在上，到现在的普及化。



### 2. React 的特性

#### 命令式与声明式简单粗暴的区别

命令式编程和声明式编程是两种不同的编程范式，它们在解决问题和描述程序行为的方式上有所不同。

命令式的概念重点在于把握过程的每一个小细节。比如说一个华人家庭餐馆，这个餐馆的老板会全程监控，从客人进门到客人出门，全程监控。有的餐馆可以做大做强，有的餐馆就做不大。
而做大做强取决于发号施令的这个人，如果这个人天生就是干餐饮的这个料，那上限是没有上限的。

声明式概念-你要想赚钱，先定一个小目标，告诉所有人先赚ta一个亿。声明式是从结果出发，从结果倒退，需要什么，然后调用什么。

回到餐馆例子，我们熟悉麦当劳连锁店概念。麦当劳的每个员工都是事先培训好的，他们只需要按照流程操作即可。像肯德基麦当劳这种大型连锁店，标准化，流程化，所以做大做强是一个大概率事情。

声明式-> 由于不是每个人都会有天赋，所以需要流程化，标准化。

至于声明式的发展，特典在于把风险变得可控，把成本变得可控，这样公司也会愿意去招junior去培养。因为大家写的代码最终实现的是差不多的，那么就没有关系了。
另外，注意jQuery是命令式的。


#### 命令式编程(Imperative Programming)
![](https://i.imgur.com/1GHwupw.png)

这里龙哥插播了一下，一开始你会写for loop，但有没有反思一下，如果你的数据由上亿级别呢？

##### 命令式：（注重过程而不是结果）

- 命令式编程强调编写详细的指令，告诉计算机如何执行任务。
- 开发者需要显式地指定每个步骤和每个操作的执行顺序。
- 代码通常包含大量的控制结构（如循环和条件语句）和副作用（直接修改状态）。


```
const db = sql.connect(str);
const table = db.readTable("student");
const result = [];

for (let i = 0; i < table.data.length; i++) {
  if (table.data[i].score < 50) {
    result.push(table.data[i]);
  }
}

result.slice(0, 10);
```

#### 声明式编程(Declarative Programming)

声明式的代码，在意的是最终结果

![](https://i.imgur.com/fY6ufrF.png)


##### 声明式：（注重结果而不是过程）


- 声明式编程更关注描述问题的解决方案，而不是具体的实现细节。
- 开发者描述所需的结果，而不是详细说明如何达到这个结果。
- 代码更加简洁、易读和易维护，因为它们通常更抽象，不涉及具体的操作步骤。

```
SELECT name, score, id FROM student WHERE score < 50
```


>总的来说，随着前端应用的复杂性不断增加，从命令式到声明式的转变已经成为了一种必然。这种转变为前端开发带来了更高的效率，可读性和可维护性，从而支持了大规模项目的持续发展和创新。


Example
```javascript
<button id="alertButton">Show Alert</button>

<script>
  document.getElementById('alertButton').addEventListener('click', function()) {
    alert('Button was clicked!');
  }
</script>
```

```jsx
import React from "react";

function AlertButton() {
  return (
    <button onClick={() => alert("Button was clicked!")}>Show Alert</button>
  );
}

export default AlertButton;
```


上面的两个例子都达到了同样的效果，但是方法不同：

- Vanilla JS，使用了命令式，明确描述了如何操作 DOM
- React，使用了声明式，只描述了界面应该如何呈现。实际的 DOM 操作是 react 库在背后处理的。



规范化后，我们可以请junior developer了，因为大家写的代码几乎是一样的


你要学习的不是这个高深的语法，高级的程序，牛逼的实现，都不是。
而是作为一个junior developer，你是学习能力好的junior developer，是能够写好声明式的编程

产品过来提需求的时候，不可能是a，b，c这种单一的，而是多个复杂的内容，可以提取出来，细化出来，senior dev 。
junior可能就不知道从哪里开始下手

落实到代码上，junior和senior是高度一致


#### Component-Based 组件化，像玩乐高积木一样地写代码

组件化是为解决以下前端项目问题而产生的：

- 复杂性增加
- 代码重复与冗余
- 难以维护
- 团队协作困难
- 缺乏 UI 和功能的一致性


而组件化就像乐高积木一样：

- 模块化与可重用性
- 简单与清晰的结构
- 易于维护
- 团队协作


声明式的风格转变 - 组件化的提倡 - 导致前端再一次大规模发展

我们了解一下组件化是什么意思，比如说下面一个项目，怎么练习组件，如果我要分割成组件，我们该怎么去进行一个复用

![](https://i.imgur.com/3ZvLTNi.png)

![](https://i.imgur.com/nzKGn99.png)

复用一个东西的时候，可以开始考虑用function去打包
![](https://i.imgur.com/QTxWbrv.png)


在写react的时候，不断考虑组件化本身就是一种练习


初学者先把react学好，再学习其他框架；先别学next js，先学react，再学next js

#### 脚手架 -vite

[https://vite.dev/guide/](https://vite.dev/guide/)

![](https://i.imgur.com/fVHJPht.png)

```
npm create vite@latest my-react-app --template
```


很多同学看到`npm create vite@latest my-react-app --template`, 马上跳入到深入细节环节。
但是不要转牛角尖，直接声明式，只关心结果不关心过程，只关注能够改变结果的那部分。

学习的时候，关注声明式，关注结果。不要说关心着项目结构和细节，比如这一些文件是干什么的是太细节了，暂时不需要考虑的东西先放着，而是只需要关注现在要干什么。
比如说现在我要写个hello world，那么去哪里改可能马上得到这个结果？找到了，改动更行，运行。然后再不断反思，为什么是这样，为什么不是那样。
一开始有不懂的地方，没有关系，就让它不懂。根据产品需求，在代码中所需要的结果，来改动那一块代码是影响结果的，改掉

![](https://i.imgur.com/Gplp5b6.png)

最好是什么都没学，还找到了工作
毕竟把什么都学了，还是没找到工作，就很打击人












