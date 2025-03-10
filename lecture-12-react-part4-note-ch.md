## Lecture 12 Component & Props

### 本节课高亮点

- 学习方式
- 组件
- child props

> 不是为了学好 React，而是为了能把任意一个前端项目做好，做好的标准是代码质量（可读，可维护，可复用），React 是我们实现这个标准的工具，学 React 是为了利用好这个工具，实现这个标准。”学会 react 就能找到工作“是一个错误的思维，要不然人人都是软件工程师，只需要三个小时。真正决定你是否是一个 job ready 的状况，不是你是否掌握好工具，而是是否能够利用工具来实现高质量代码的标准。

### 课程前导语

- 关于是否学习 nextjs 的问题，龙哥的回答是[学海无涯，回头是岸]
- 想学一个东西之前，问自己为什么要学
- nextjs - 因为你要前后端不分离，所以学习 nextjs 是有必要的

- 上节课我们花了很多时间去搞明白编译器的概念，即利用 babel 把不合法的 javascript 转化为合法合规的 javascript

- JSX 只是为了声明式编程，而为什么坚持声明式写代码？因为我们最终关注的是结果，所见即所得的概念。最重要的一点是为了代码质量，不需要 JSX 也是可以完成一样的功能。那么，坚持写 JSX 的目标是为了可读，可维护，可复用-三大代码标准。

- 按需学习，按业务学习。有人问了 typescript 需不需要学，龙哥再次对填鸭式学习养成，和必须对学习动机进行详细分析。如，“在做出”我要学 typsript“的动作之前，问问自己是否可以把 typscript 学会？”，再次强调[学海无涯，回头是岸]，因为所要学习的东西实在太多了，这很容易把自己导入一个死胡同。

- 学习速度，跟不上技术更新速度。真正要学习的东西是**思维转变到关注代码质量**，保证代码质量是 IT 行业里万年不变真理。

- 将自己知识提高广度，不求深度。不要求你变成专家。

### React 组件化 - 核心之一

- 组件，作为 React 里构建和组织应用程序的基本单位。

#### 组件的本质

- 在 JavaScript 中，能够承担起最小责任，且符合可复用的整块代码块的一个 construct 是 JavaScript 的函数（function）。
- 从这个角度去思考，那么可以把 React 里的组件，理解成一个函数。一个组件，一个函数。所以，组件的本质是 JavaScript 的函数 function，组件不是一个复杂的概念。
  ![](https://i.imgur.com/ZAws7Ij.png)

#### 如何把组件写好

##### 组件的封装

- 如何把组件写好，那就是如何把 JavaScript 中的函数（function）写好；从这个角度去思考的话，我们就是如何把任何语言的函数去写好。

- 组件封装了特定的 UI 功能和逻辑，而每个组件(component)，即每个函数（function），需要有明确的职责（single responsibility), 并且是要封闭的(open/close)，因为一个组件（函数）的内部逻辑对外部是不可见的。

##### 组件的可复用

- 可复用的代码块，具体指能够在不同情景中和项目的不同部分重复使用。比如说一个 button，把这个 button 从颜色和形状搭建好，那么可以在任何一个页面（home page， about page）中重复利用。

##### 组件的组合

- 组件（function）和其它组件（function）可以相互嵌套和合并，从而产出新的功能组件。比如说一个 navigation 的组件下，可以嵌套已做好的 button。如下图

#### 组件类型

- 我们注重关注函数组件(Function Component),即简单的 JavaScript 函数（function），通常返回值是一段 JSX

![](https://i.imgur.com/UqB2BnF.png)

- 一个小点需要注意，如果你把返回值写成`console.log()` ，那就是一个简单的 JavaScript 函数。如果返回 JSX，那就是一个组件。

#### 组件的调用

- 假设我们把组件搭建好了，我们需要去调用这个已写好的组件。

![](https://i.imgur.com/YBP7Aqk.png)

- 1 和 2 表达的是一个意思，即我们要去调用这个函数，名为`MyComponent`的函数。

  > 由于自己刚完成一项目，我理解到，创建一个编程语言考虑如何通过对传入进来的东西做一个解析(parse), 你像`{}` 就会被视为一组 tokens, 而`{}` 也会被视为一组 tokens ，所以 Babel 会转译成 JSX。

- 至于为什么我们采取第二种方式去调用我们的组件。我们去阅读一个代码，希望从整体性出发，用`<MyComponent />` 更容易读，而且可能大脑识别起来容易些。前面我们提到[声明式编程]的概念，我们只关注结果，而非具体的`MyComponent()`是怎么实现的。当然了，这个 function 的名字取得不好。

- 龙哥抛出一个字节的面试问题：
  ![](https://i.imgur.com/m8x8QcV.png)
- 首先，我们的文件格式是`.jsx`，编译器语法会将`<>`的所有内容识别为`jsx`， 即我们的`<>` 会被识别为`jsx`语言，但`<img>`是原生 html。那么，本来在 html 的`<img>` 会被错认为一个组件，所以我们需要注意这个区分。

#### 组件的命名

- TitleCase
- camelCase
- snake_case
- kebabe-case
- PASCAL_CASE

- 在 JavaScript 的命名范式是 camelCase + PASCAL_CASE, 但是 React 前期，组件的命名方式是 TitleCase，但是现在不强制要求，只落为行业约定俗成的习惯。

- 至于为什么使用 TitleCase, 如果我们有一个组件(component)，命名为`Button = () => { return <button className="xx"}`，一个普通的 button，附上设计好的样式，变成了我们复杂的 Button。那么，以 TitleCase 起名的 Button，可以让我们对普通 html 里的`<button>`进行一个明显的区分。

- React 早期强制要求，是因为功能不够完善，算法不够好，通过人为规范来保证编译器的正常运行，让我们知道哪些部分是用了 `React.createElement('div');`，这种方式可以区分 HTML tag 和 component，毕竟 html tag 的首字母都是 lowercase
  ![](https://i.imgur.com/wF8cQ7c.png)

- Fiber Node 是现有 react 优化算法后的方法，所以再也不用以上的简单算法来调用`React.createElement()`

![](https://i.imgur.com/pfdgn3R.png)

### React 项目结构

![](https://i.imgur.com/BULtNYo.png)

##### 这个叫做 Fractal - 分型 - recursion

1. 任何一个片段拿出来，都是可以自成一体的。即`HomePage`下的组件，不能命名为`HomePageHeroMessage`； 如我桌子上的水杯，不会被写成一种无限随机套娃的“我我桌子上的我桌子上的水杯”
   -> 组件由组件责任确定，不应该耦合副组件的概念 (S, O, D)

- 文件夹名字和组件文件名字保持一致 - (`HomePage` as the folder name, `Homepage.jsx` as the component name)

- 一个组件下面，会通过实际业务情况，含有很多支持性组件，如`HomaPage`下面有`HeroMessage`, 这个时候，我们在 Hompage 创建一个文件夹 components，循环利用相同风格； 子组件也有可能有其组件支持

- 龙哥再次考察写代码的小细节： 从以下的代码片段，有什么可以改进的方式？

![](https://i.imgur.com/KgbsPYZ.png)

- 以上代码片段，我们发现项目结构的构建导致我们有 `./components/HeroMessage/HeroMessage` 重复。
- 实际上，当我们把`./components/HeroMessage`，系统默认去取 当前文件夹下的`index.js`， 这样以来，我们理解了为什么需要一个入口文件 `index.js`

- 从这个思路去思考，我们可以把`index.js`作为 api 的调用的主入口.

![](https://i.imgur.com/LBOYwqj.png)

![](https://i.imgur.com/OLpE3zZ.png)

- 当我们用 import 语句调用这个组件 HeroMessage，我们从`./components/HeroMessage`，即`index.js`，而`index.js`，我们有 export default HeroMessage， 等于`import HeroMessage from `./HeroMessage`

- `index.js` 可以从两句变成一句 `export { default } from `./HeroMessage``

新的版本以下

![](https://i.imgur.com/ULRxxrL.png)

- 在新的版本中，为什么要在`index.js`上给 `default` 中加入`{}` ？因为在组件文件，我们已经有 default.

![](https://i.imgur.com/xppZLai.png)

- 以下代码段，我一开始觉得没什么必要，但可能为了可读性而做出的引入。
  ![](https://i.imgur.com/Xpkbk0e.png)

- 但是后面龙哥提到直接引入一个文件路径，实际上是不会工作的。

![](https://i.imgur.com/mlugnIW.png)

- 原因是 javascript 不知道这个路径指的是谁

- 龙哥继续提出另一个小细节，因为我们有 webpack，我们才能够把代码写成 `import HeroMessage from `'./components/HereMessage'`

- 作为打包器的 webpack 的简单工作原理，是去找入口文件，和出口地址

- webpack 就是一层层去剥开来的。先看到`import`， webpack 列出 HomePage, HeroMessage, getAddress，接着从 HeroMessage
- 不需要打包的东西，放在 public 里

- 我们写的所有代码都是基于最基本的 HTML + CSS + JavaScript ， 在此之上，我们加上了 编译器，和打包器。
- 真正在运行的代码是(HTML, CSS, JavaScript)

### 已经淘汰的组件范式

#### 类组件 (Class Component)

龙哥跳过了

![](https://i.imgur.com/gzRH0tj.png)

#### 高阶组件 (higher order component, high order function)

龙哥跳过了

![](https://i.imgur.com/KdOeS2o.png)

#### lifecycle

##### componentDidMount

##### componentWillUpdate

##### componentWillUnmount

### Props （属性） - 核心之一

> `Props` 是 properties 的缩写，可被视为用以传给函数的参数。但是`Props` 指的是从父组件传递给子组件的数据

- 我们怎么去把组件写死呢？

![](https://i.imgur.com/Fm9UfHn.png)

- 我们去写一个方法，就像写一个名为`sum`的 JavaScript 函数。
- 然后第一个组件写法，只能是返回 `<div> {1 + 1} </div>`
- 我们要把这个组件写灵活一些，就必须要考虑怎么传参数

- 此时，我们意识到在 JSX 语法下，我们似乎无法传参数，因为我们得写成 html 的形式 - `<Sum />`

- 在 javascript 函数定义上来说，我们的参数名字是没有特殊指向的，但在首字母大写的组件来说，为了避免参数的名字指向是有歧义的。我们需要专注于顺序。

![](https://i.imgur.com/PKaM4Eu.png)

- 为了符合只关注结果的声明式编程和符合 html 的写法，我们写成了 `<Sum />`；
- 如果我们写成了 `<Sum {1} {2} />`, 我们也不会去写成。因为这不是 HTML 的写法，只要不符合，我们不考虑。
- 我们先看下 html 下，怎么导入 javascript，我们有一个 `<button className="" onclick="" />`， 当我们看到 html 的属性（如 onclickl=""), 是 key-value 的格式，key-value 是 object 的结构。

- 把以下的的代码
  ![](https://i.imgur.com/PKaM4Eu.png)

改成 key-value 的结构

![](https://i.imgur.com/eDeaDKA.png)

当我们改成这种结构之后，我们就可以像 object 那样去传了

![](https://i.imgur.com/ZOXcXiu.png)

从此，我们可以叫任何名字。多亏 ES6 的特性！

由于这个是基于 HTML 的属性，所以我们称它为 Props
![](https://i.imgur.com/rli4ogN.png)

可是呢，我们也要考虑到可读性，所以我们在这个理解之上，进行逻辑具象，而不是进行逻辑抽象。

因为 ES6 特性，我们可以直接在组件申明中，加上花括号作进一步的解构

![](https://i.imgur.com/MnmbfvB.png)

#### Props 的行业命名规范

##### Props 命名遵循一般参数命名

- props 的命名靠近 HTML attribute 的命名方式

- 可以直接用 html 的命名来命名，所以我们可以让 JSX 更好地使用成 html

##### props 是只读，而不是去改一个值

```
const sum = (a, b) => {
a = 1;
return (a + b);
}
```

- 如果要去改一个值的话，我们需要通过返回值来改变，而不是在封装里面来改变一个值

#### Props 使用场景

- 任何数据类型都可以成为 props，如基本数据类型(string, number, boolan, etc), 对象、数组和函数，自顶向下地传

![](https://i.imgur.com/omNBC5D.png)

![](https://i.imgur.com/jo1qFEa.png)

![](https://i.imgur.com/YEkI7N8.png)

当你声明了这个组件，是有参数的 props，而你没有传，那么这个值是`undefined` -> falsy value

![](https://i.imgur.com/Ah2lRzA.png)

#### `Child` 是一个特殊 `props`

- 任何一个组件的调用是有开标签(`open tag`) 和闭标签 (`close tag`) ; 那么，Child props 可以使我们能够在 之间插入内容
  ![](https://i.imgur.com/U5m9DT9.png)

- 这个是 escape to Javascript using `{}`

- 当我们的产品不断地增进复杂的需求时候，我们通过用简单的 object 去结构，勉为其难地满足了产品提出的要求，但是在代码质量上似乎没办法满足

![](https://i.imgur.com/aYjcrid.png)

- 原生 html 上，我们只用一个 tag，并且在这个 tag 可以传值

![](https://i.imgur.com/GxSmAwy.png)

- 上面的代码是可工作的，但是这个代码总是和原生的代码。 比如我们有 `<button> Submit </button>`

- 理想状态上来说，我们需要写成
  ![](https://i.imgur.com/4IW1Fjv.png)

- 但我们这么写的话，原来声明的组件，似乎无法把参数传进去

![](https://i.imgur.com/ThKnfAk.png)

- React 也考虑到这个特性，所以给我们预留了 children

- Children 是一个 reserved keyword，我们把在组件的情景下，所有在开标签和闭标签之间的内容归为 children
- 从而这个特性，我们可以把代码改成

![](https://i.imgur.com/cNgnGHV.png)

![](https://i.imgur.com/k6ch66d.png)

#### 面试题目

- 我们要调用 Compoonent, 这个 component 会 返回 Hello world, Alice!
- 假设 name 的传值是 Alice, `<Component name="Alice"> `, 请你完成代码，使输出结构为 Hello world, Alice!

```
const Component = ( {name, children }) => {
return (
	<div>{children(name)}</div>
)
}
```

```
const Component = ( ) => {}
```

```
<Component name="Alice"> { (name) = > `Hello world, ${name}` } </Component>
```

这里直接传入一个 arrow function 了

另外一个写法， 传值可以传 html element

![](https://i.imgur.com/GqkAokH.png)

#### Spread Attributes 的方式去传 所有 props

![](https://i.imgur.com/hRxEX6T.png)

首先，我们有一个变量声明和变量定义 表达式

```
const student = { id: 0, name: 'Alice', age: 23 }
```

之后，用与不用`...` Spread Attribute 的区别

```
const studentWithResult = { id: student.id, name: student.name, age: student.age, result: 'pass'}

// 不推荐以下这个写法，因为并不接近html
const studentWithResult= { ...student, result: 'pass'}
// 偷懒行为
```

以上是 JavaScript 的 ES6 写法，以下是 React 情景下的真对 props 的 Spread Attribute 写法

![](https://i.imgur.com/DPpVEKy.png)

![](https://i.imgur.com/AAc6tHr.png)

Props 不是一个高级复杂的特性
组件不是一个高级复杂的特性
![](https://i.imgur.com/p1Wx3KB.png)

要脱离 react 去学习 react，专门学习 react 的话可能会被套牢

什么时候写 component？
当你想把原来代码拆出去做一个方法。
为什么要拆？根据代码质量来拆，
为什么拆？为了符合人类思考方式去拆

quality of code，javascript 语言
