## HTML&CSS的奥秘 - 01

## 网页开发基础

现代网页开发的三大核心技术：

1. HTML (HyperText Markup Language): 负责网页的内容结构
2. CSS (Cascading Style Sheets): 负责网页的样式表现
3. JavaScript: 负责网页的交互行为，现代前端开发中的重要角色

### 学习资源推荐

推荐的学习网站：

- W3Schools: 适合查询语法和基础知识
- MDN (Mozilla Developer Network): 全面的开发者文档
- CSS-Tricks: 专注于CSS相关问题和解决方案

* 可以尝试练5-6个掌握扎实dom技能
* https://github.com/bradtraversy/50projects50days
  推荐学习网站

推荐的开发工具：

- Visual Studio Code（推荐）
- WebStorm（付费）
- Sublime Text

VS Code 推荐插件：

- Git History Diff: Git历史比较
- Color Highlight: 颜色高亮
- CSS Peek: CSS快速查看
- Live Server: 实时预览
- ESLint: 代码规范检查
- Prettier: 代码格式化

## HTML基础

### HTML5 文档规范

编写HTML5文档需要注意：

1. 遵守W3C标准
2. 内容和样式分离
3. 保持语义化结构，原因如下：
   - 提高代码可读性和可维护性
   - 有利于无障碍访问（accessibility）
   - 有利于搜索引擎优化（SEO）

### 基本文档结构

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="页面描述">
    <meta name="keywords" content="关键词">
    <title>网页标题</title>
</head>
<body>
    <!-- 页面内容 -->
</body>
</html>
```

### 常用语义化标签

页面布局相关：

```html
<header>页头</header>
<nav>导航</nav>
<main>主要内容</main>
<article>文章</article>
<section>区块</section>
<aside>侧边栏</aside>
<footer>页脚</footer>
```

文本相关：

```html
<h1>一级标题</h1> <!-- 到 <h6> -->
<p>段落</p>
<strong>重要文本</strong> <!-- 比<b>更语义化 -->
<em>强调文本</em> <!-- 比<i>更语义化 -->
<del>删除文本</del> <!-- 比<s>更语义化 -->
<ins>插入文本</ins> <!-- 比<u>更语义化 -->
```

### 列表

无序列表：

```html
<ul>
    <li>项目1</li>
    <li>项目2</li>
</ul>
```

有序列表：

```html
<ol>
    <li>第一项</li>
    <li>第二项</li>
</ol>
```

描述列表：

```html
<dl>
    <dt>术语</dt>
    <dd>描述</dd>
</dl>
```

### 表格

基本表格结构：

```html
<table>
    <tr>
        <th>表头1</th>
        <th>表头2</th>
    </tr>
    <tr>
        <td>数据1</td>
        <td>数据2</td>
    </tr>
</table>
```

### 表单

基本表单结构：

```html
<form method="post" action="/submit">
    <label for="username">用户名：</label>
    <input type="text" id="username" name="username" required>
    
    <label for="password">密码：</label>
    <input type="password" id="password" name="password" required>
    
    <label>性别：</label>
    <input type="radio" name="gender" value="male" id="male">
    <label for="male">男</label>
    <input type="radio" name="gender" value="female" id="female">
    <label for="female">女</label>
    
    <button type="submit">提交</button>
</form>
```

常用的input类型：

- text: 文本输入
- password: 密码输入
- radio: 单选按钮
- checkbox: 复选框
- file: 文件上传
- submit: 提交按钮
- button: 普通按钮
- email: 邮箱输入
- number: 数字输入
- date: 日期选择

### 块级元素和内联元素

块级元素特点：

- 独占一行
- 可设置宽高
- 可设置margin和padding
- 例如：div, p, h1-h6, ul, ol, table

内联元素特点：

- 在同一行显示
- 宽高由内容决定
- 只能设置水平方向的margin和padding
- 例如：span, a, img, input, strong, em

### 特殊字符

常用HTML字符实体：

- 空格：`&nbsp;`
- 小于号：`&lt;`
- 大于号：`&gt;`
- 引号：`&quot;`
- 版权符号：`&copy;`

### 文件路径

- 相对路径：相对于当前文件的位置
- 绝对路径：完整的URL地址
- 根路径：以 / 开始的路径

### SEO基础

提高SEO的关键要素：

1. 使用适当的语义化标签
2. 设置合适的title和meta标签
3. 使用适当的heading层级
4. 图片添加alt属性
5. 使用有意义的URL结构

以上内容是HTML基础的主要部分，建议结合实践来加深理解。在实际开发中，这些知识点会经常使用到。