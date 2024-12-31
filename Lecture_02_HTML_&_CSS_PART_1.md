# Lecture02 HTML & CSS - Part 1



> This note is based on the lecture ([link](https://jiangren.com.au/study/lesson?programId=672448ecea33cf003687af93&lessonId=673c41cb0022bb00124fe2ea)) by Ally Tang. The entire lecture was about HTML (**Hypertext Markup Language**) and a preview knowledge about CSS (**Cascading Style Sheets**) from the Part 2. 



**Homework: Registration form using HTML and CSS**

[TOC]



### HTML - Hypertext Markup Language



#### 1. Introduction

> **Addition Background Knowledge**
>
> in 1989 something really big was born and I actually Googled earlier, big things that happened in 1989, three of the top five results were Kendrick Lamar and Taylor Swift, fortunately we're not gonna be talking about Taylor Swift but I can talk about K.dot all day. Yet what we are talking about in 1989 was the world wide web, which was invented by this guy on the left here, Tim Berners-Lee, who was working as an engineer at CERN, so it's the big sort of science place in Geneva as just an engineer and he wanted to come up with a way for them to share all the research and information, that's been gathered at CERN with people, who weren't just physically located there.
>
> <img src="/Users/david/Documents/1.-project/craftman-web/notes/asset/01-html/html-intro.002.png" alt="500" style="zoom:33%;" />
>
> http://info.cern.ch/hypertext/WWW/TheProject.html
>
> So a lot of the time, scientists would come, do their research projects, gather all this data and research and stuff, go back to their home countries or wherever they're from and they wouldn't have access to it, so Tim proposed this concept of the web, which is an open platform to be able to share information easily and locate it from anywhere.



As a developer, it is necessary to cultivate a good habit: Check offical documentation as frequent as you can, especially when you are at the learning phase. The go-to reference documents are  [W3School](https://www.w3schools.com/html/) and [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML).[^1] .

**Note:**

- Follow **World Wide Web Consortium (W3C)** standards - [link](https://www.w3.org/standards/)
- The World Wide Web Consortium (W3C) advocates for the **separation of content and presentation** in web development. This principle emphasizes that the **content** (the information and structure of a webpage) should be kept distinct from its **presentation** (the visual styling and layout). 
- Following the last point - what W3c promotes, we need to have two key distinct points: Content (Structure) and **Presentation (Style**). Content is defined by semantic HTML elements that convey the meaning and organisation of the information for users. For example, using `<h1>` for main headings, `<p>` for paragraphs, and `<nav>` for navigation sections. See more later, whereas Presentation(Style) is managed via **CSS (Cascading Style Sheets)** that controls the visual aspects such as  colours, fonts, and layouts
- Therefore, we need to ensure HTML is semantic. And we need to maintain a clear and organised HTML structure for readability and maintainability, facilitating team development and maintenance .
- Another thing to do is the accessibility to all users. Poor web accessibility occurs when websites are designed without considering the diverse needs of all users, particularly those with disabilities. For example, some of my British friends are dyslexia and it will be difficult for them to focus if the font is too dense. To understand more by reading this article about [accessibility-friendly](https://www.whoisaccessible.com/guidelines/inspection-of-a-few-ada-compliant-websites-and-some-that-are-not/);
- Thinking of **Search Engine Optimisation (SEO)** more. For example, the heading tag `<h1>` is the most important tag and you wouldn't find more than two `<h1>` tags in all famous websites. Search Engine will have its own algorithms to crawl web pages so it could determine the weights and factors by how you structure your contents for your website.



Although Ally mentioned there wouldn't be high chance for interviewers to test your knowledge about HTML and CSS, mostly JavaScript DOM (Document Object Model) is a high frequent concept to test for. She also mentioned that she was asked for what `<!DOCTYPE html>` (remember where there is space exactly.[^2])



#### HTML, CSS and JavaScript

What consists of modern web is 3 bodies - HTML, CSS, JavaScript.

<img src="/Users/david/Documents/1.-project/craftman-web/notes/asset/01-html/html-css-js.001.png" style="zoom:33%;" />

- As you know, HTML is for content - the structure of web page.
- CSS is for styling the webpage
- JavaScript is to make webpage more dynamic and interactive. 



#### IDE (**Integrated Development Environment**)

The easiest way to crack on your code is to use Visual Studio Code (i.e. **VScode**) by Microsoft which is what Ally is using and she shared this common popular extension list. ([link](https://hackr.io/blog/best-vscode-extensions)).

you are welcome to use other editors such as Sublime Text 3,  IntelliJ IDEA, Atom By GitHub, NetBeans , Eclipse, PyCharm(mostly Python projects), WebStorm, Brackets;[^3]

**What to consider for IDE**

- **Code Editor**: allow you to write and edit source code at ease with features such as syntax highlighting and code completion for clean code and efficient code
- **Compiler/Interpreter**: IDEs often include a compiler or interpreter to convert source code into machine code, enabling real-time testing and error checking. 
- **Debugger**: A crucial tool for identifying and fixing bugs, allowing developers to step through their programs and inspect variables during runtime.
- **Build Automation Tools**: These tools automate repetitive tasks such as code compilation and testing, streamlining the development workflow.



#### 2. HTML Basic Structure and Elements

##### 2.1. HTML Basic Structure 

```html
<!DOCTYPE html>
<!-- Document Declaration for telling browser this is a HTML5 file -->
<html>
  <head>
    <title>My Web Page</title>
    <!-- title as shown in tab inside the browser，mostly for SEO -->
  </head>

  <body>
    <h1>My first heading</h1>
    <p>paragraph about how amazing the web page is</p>
  </body>
</html>

<!-- <head> <title> <body> these are html structural tags meaning they can be only one in a document -->
```



##### 2.2 HTML Elements

A HTML element consists of a html tag and content. see below

```HTML
<!-- the whole thing below is called a HTML element -->
<tagname> Content goes here... </tagname> 
```

When it comes to HTML elements, we need to know there will be different types of HTML elements such as block level element and incline element. However, I think the reason why we need to know about them is that how they work/stack with other elements. 

- block level element will occupy the entire line. So two block elements will occupy two lines on the web page. because a block-level element always takes up the full width available (stretches out to the left and right as far as it can)

**Common block-level tags**

```html
<address> <article> <aside> <blockquote> <canvas> <dd> <div> <dl> <dt> <fieldset> <figcaption> <figure> <footer> <form> <h1>-<h6> <header> <hr> <li> <main> <nav> <noscript> <ol> <p> <pre> <section> <table> <tfoot> <ul> <video>
```



- inline element will occupy a typical slot in a line. So two incline elements will squeze together in a line and they only take up as much width as necessary



```html
<a> <abbr> <b> <bdo> <br> <button> <cite> <code> <dfn> <em> <i> <img> <input> <kbd> <label> <map> <object> <output> <q> <samp> <script> <select> <small> <span> <strong> <sub> <sup> <textarea> <time> <tt> <var>
```



Since we know that the key to differentiate block and incline level elements is to better control how each elements should present on the web page, we can also use CSS to change their default types ( from block level to incline , vice versa)



Note:

- you can not put block-level elements inside inline-level elements. due to **layout and display Issues**,  Inline elements are designed to fit within the flow of text and don't have the necessary space to contain block-level elements, which require more space and typically force new lines. For example, placing a block element like a `<div>` inside a `<span>` can cause layout issues because `<span>` is an inline element and doesn't have enough space or the necessary properties to accommodate block elements.



Here is an example to  cause unexpected layout behavior.

```html
<span>
  <div>This is a block element inside an inline element.</div>
</span>

```



Correct usage:
```html
<div>
  <span>This is an inline element inside a block element.</span>
</div>

```





###### HTML Tags



html tags usually come in a pair.  `opening tag (start tag) + content + closing tag (end tag)`  as shown below. 

<img src="/Users/david/Documents/1.-project/craftman-web/notes/asset/01-html/html-elements.webp" style="zoom:50%;" />



Yet there are also self-closing tags such as `<img>`, `<input>`, `<br>` 

There are common HTML tags as follows. [^4]

<img src="/Users/david/Documents/1.-project/craftman-web/notes/asset/01-html/html-common-ags.webp" style="zoom:80%;" />



###### All HTML Elements Can Have Attributes

> Note:
>
> - Attributes provide additional information about an element.
> - Attributes are always specified in the **start tag**.
> - Attributes are typically written in **name/value pairs**, such as `name="value"`, though there are exceptions.
> - Attribute names are usually presented in **lowercase**.
> - Attribute values are generally enclosed in **double quotation marks**.



**Example**

```html
<html lang="en">
  <!-- html tag has an attribute:lang,we specify the value of en wrapped with double quotes -->

  <p style="color:red;">This is a red paragraph.</p>
  <!-- you can do inlince styling (css) via the attribute style with CSS rules -->

  <img src="img_girl.jpg" alt="Girl with a jacket" />
  <!-- img tag has been sepcified two attributes: src, alt -->
</html>
```

You don't need to memroise these details. I doubt it will be tested but you will remember them because you will write lots of tags as well as their common attributes such as `<img src="happy_new_year_2025.jpg"/>`  for your projects.

###### - HTML tag: `<head>`

>  In a sentence, everything in `<head></head>` can't be visible for web visitors

During the lecture we talked about `<head>`  and it contains lots of  usually are 

```html
<head>
  <meta charset="UTF-8" />
  <!-- This is a Comment: (Unicode Transformation Format - 8-bit) is a variable-length character encoding used to represent the Unicode character set. -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <!-- Comment: Setting the viewport to ensure your website looks good on all devices. -->
  <meta name="keywords" content="test keywords" />
  <!-- Comment: Defines keywords for search engines. -->
  <meta name="description" content="test keywords" />
  <!-- Comment: Defines a description of your web page. -->
  <title>Document</title>
</head>

```

###### -  HTML tag: `<meta>`

HTML meta tags provide information about a web page to search engines and browsers. They are placed in the section of an HTML document and are not displayed on the page itself.

<img src="/Users/david/Documents/1.-project/craftman-web/notes/asset/01-html/meta.png" style="zoom:55%;" />

<img src="/Users/david/Documents/1.-project/craftman-web/notes/asset/01-html/meta-02.png" style="zoom:50%;" />

###### Common Meta Tags

There are several types of meta tags, each with its own purpose. Here are some common meta tags:

- `meta charset`: This tag specifies the character encoding used in the document, which affects how text is displayed. The recommended value is UTF-8.
- `meta name="viewport"`: This tag specifies the viewport properties for responsive design. It includes attributes such as width, initial-scale, and minimum-scale.
- `meta name="description"`: This tag provides a brief summary of the page content and is used by search engines when displaying search results.
- `meta name="keywords"`: This tag specifies keywords related to the page content and was used in the past by search engines for indexing, but is now less important.
- `meta name="author"`: This tag specifies the author of the page.
- `meta name="robots"`: This tag specifies instructions for web crawlers, such as whether to index or follow links on the page.



###### Platform-Specific Meta Tags

There are also platform-specific tags for social media sites such as Facebook and Twitter. These tags are used to provide more information about the page when it is shared on these platforms. Here are some examples:

- `meta property="og:title"`: This tag specifies the title of the page when it is shared on Facebook and several other sites.
- `meta property="og:description"`: This tag specifies the description of the page when it is shared on Facebook and several other sites.
- `meta property="og:image"`: This tag is used to specify the image that should be displayed when a page is shared on social media platforms, such as Facebook or Twitter.
- `meta name="twitter:title"`: This tag specifies the title of the page when it is shared on Twitter.
- `meta name="twitter:description"`: This tag specifies the description of the page when it is shared on Twitter.
- `meta name="twitter:card"`: This is used to display the preview of the web page as a card on Twitter.



###### - HTML tag: `<title>`

**Title and Favicon**

The `title` tag and favicon `link` tag are also related to meta tags.

- The `title` tag specifies the title of the page, which appears in the browser's title bar and is also used by search engines.
- The favicon `link` tag specifies the icon that appears in the browser's address bar and bookmark menu.

Let's add proper meta tags to our web page:

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Learn about job openings at Jiangren and submit your application now">
    <meta name="keywords" content="data science, software development, jobs">
    <meta name="author" content="Jiangren">
    <meta name="robots" content="index, follow">
    <meta property="og:title" content="Jiangewn Careers">
    <meta property="og:description" content="Learn about job openings at Jiangren and submit your application now">
    <meta property="og:image" content="/jjiangren_meta.png">
    <meta name="twitter:title" content="Jiangren Careers">
    <meta name="twitter:description" content="Learn about job openings at Jiangren and submit your application now">
    <meta name="twitter:image" content="/jiangren_meta.png">
    <title>Jovian Careers</title>
    <link rel="icon" href="/jiangren_favicon.png" type="image/x-icon">
```

###### - HTML tag: `<body>`

>  everything in <body></body> can be visible for web visitors.



The basic layout is as follows:

![](/Users/david/Documents/1.-project/craftman-web/notes/asset/01-html/html-common-structure.png)



**Example**

```html
<body>
  <header>
    <!-- Defines a header for a document or a section -->
    <nav>
      <!-- Defines a set of navigation links -->
    </nav>
  </header>

  <section>
    <!-- Defines a section in a document -->
    <article>
      <!-- Defines an independent, self-contained content -->
      <aside>
        <!-- Defines content aside from the content (like a sidebar) -->
      </aside>
    </article>
  </section>

  
    <!-- another section with <details> and <summary> -->
  <section>
    <details>
      <!-- Defines additional details that the user can open and close on demand -->
      <summary>More Information</summary>
      <p>This is extra content that can be toggled open or closed.</p>
    </details>
   </section>
  
  <footer>
    <!-- Defines a footer for a document or a section -->
    <p>© 2024 Your Website. All rights reserved.</p>
    <p>Contact us: info@yourwebsite.com</p>
  </footer>

</body>

```

Note:

- `<summary>` tag is the heading or clickable summary that allows the user to toggle the visibility of the content within the `<details>` tag.
- `<detail>` tag is more commonly used in content sections (like an article, sidebar, or a section)  where extra content can be hidden or revealed. like toggle list in Notion
- `<footer>` tag is usually meant to contain footer information related to the document, like copyright, contact details, or links to privacy policies. 



###### Other Examples with common tags



```html
<h1>...</h1>
Level 1 Heading
<h2>...</h2>
Level 2 Heading
<h3>...</h3>
...
<h4>...</h4>
...
<h5>...</h5>
...
<h6>...</h6>
Level 6 Heading

<br />
Self-closing tag, used for line breaks
<hr />
Self-closing tag, horizontal line

<b></b> Bold <strong></strong> Bold, more semantic

<i></i> Italics <em></em> Italics, more semantic

<s></s> Strikethrough <del></del> Strikethrough, more semantic

<u></u> Underline <ins></ins> Underline, more semantic

<div></div>
No semantic meaning, just a box <span></span> No semantic meaning, just a box

<img
  src="path"
  alt="Alternative text for the image"
  title="Text displayed when hovering over the image"
  width="Image width"
  height="Image height, often set to 'auto' to automatically match the image width"
/>
Image
<!-- It's better practice to set the height and width of images using CSS -->

<a href="path" target="target window position">Insert link text or image</a>
<!-- Comment
     - The <a> tag's purpose:
        1. Hyperlinks between pages
        2. Anchor links, used for quick navigation to a specific point on the page, using target="#elementId" with the element's id
        3. Functional links, like email links

     - alt attribute: Image description, used when the img fails to load to describe what the image is for


     - target attribute:
        _self: Opens the link in the same window (default behaviour).
        _blank: Opens the link in a new window.
        _parent: Opens the link in the parent frame.
        _top: Opens the link in the full window, ignoring any frames.


     - The <a> tag can also be used for downloading
    -->
<a href="path/to/your/file.zip">Download File</a>

```



Please learn more about other tags via  [W3School](https://www.w3schools.com/html/) and [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML) if you are not clear

##### 2.3 Sematic HTML Tags

###### What is it?

- A semantic element clearly describes its meaning to both the browser and the developer.



**Examples of non-semantic elements**

```html
<div>and <span> - Tells nothing about its content.</span></div>
```

**Examples of semantic elements**

```html
<form>
  ,
  <table>
    , and
    <article>- Clearly defines its content.</article>
  </table>
</form>
```



<img src="/Users/david/Documents/1.-project/craftman-web/notes/asset/01-html/html-semantic-non-semantic.png" style="zoom:80%;" />





#### 3. Comments and HTML Character Entities

##### 3.1 Comments

```html
<!-- this is a comment -->
```



In VSCode, you can use shortcut via [^5]

- `Ctrl + /` on Windows
- `Command + /` on MacOS



##### 3.2 HTML Character Entities

In HTML, reserved characters must be replaced with character entities. 

Here are some commonly used character entities:

| HTML Entity        | Character | Description                        |
| ------------------ | --------- | ---------------------------------- |
| `<`                | `<`       | less than                          |
| `>`                | `>`       | greater than                       |
| `&`                | `&`       | Ampersand                          |
| `"`                | `"`       | Double quotation mark              |
| `'`                | `'`       | Single quotation mark (apostrophe) |
| Non-breaking space | ` `       | Non-breaking space                 |
| ©                  | `©`       | Copyright symbol                   |
| ®                  | `®`       | Registered trademark symbol        |
| ™                  | `™`       | Trademark symbol                   |
| ¢                  | `¢`       | Cent symbol                        |
| £                  | `£`       | Pound sterling symbol              |
| ¥                  | `¥`       | Yen symbol                         |
| €                  | `€`       | Euro symbol                        |
| §                  | `§`       | Section symbol                     |
| °                  | `°`       | Degree symbol                      |



#### 4. Lists

##### 4.1 ul (unordered list)

**Features:**

- No ordeal number, each `<li>` occupies **its own line, block element.**
- By default, the `<li>` tag has a solid bullet point before it, which can be removed using CSS. `list-style: none;`
- Commonly used for unordered lists such as navigation, sidebars, and regular image-text combinations.



**Example**

```html
<ul>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ul>
```



##### 4.2. ol (ordered list)

**Features:**

- Has orderial number, each `<li>` occupies its own line, block element.
- By default, the `<li>` tag has an ordered marker (like numbers) before it, which can be removed using CSS.`list-style: none;`
- Commonly used for ordered lists, such as lists that require a specific sequence or ranking



```html
<ol>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ol>
```



##### 4.3 dl (Description list)

**Features:**

- No order, each `<dt>` and `<dd>` occupies its own line, block element.
- By default, there are no markers.



```html
<dl>
  <dt>Coffee</dt>
  <dd>Black hot drink</dd>
  <dt>Milk</dt>
  <dd>White cold drink</dd>
</dl>
```





#### 5. Table in HTML

Basic table structure in html as follows:

```
<table>
  <tr>
    <td>Row 1, Column 1</td>
    <td>Row 1, Column 2</td>
  </tr>
  <tr>
    <td>Row 2, Column 1</td>
    <td>Row 3, Column 2</td>
  </tr>
</table>
```

Tables are a fundamental component of HTML used for displaying data in a structured manner. Tables are versatile and can be used to organize a variety of data types, including text, images, and other HTML elements.

- Tables are created using a combination of `<table>`, `<tr>`, `<td>`, and `<th>` tags.
- Tables can be styled using CSS to add borders, backgrounds, and other visual elements.
- Tables can be manipulated to merge cells or adjust the size of columns and rows.
- Tables should be used appropriately and sparingly to avoid cluttering a web page or application.

<img src="/Users/david/Documents/1.-project/craftman-web/notes/asset/01-html/html-table.png" style="zoom:50%;" />

##### `table`, `tr` and `td` Tags

The following tags are used to create tables, rows, and cells:

- The `<table>` tag is used to create a table in HTML. All other table-related tags are nested inside this tag.
- The `<tr>` tag is used to create a table row. Each row contains one or more table cells (`<td>` or `<th>` tags).
- The `<th>` tag is used to create a table header cell in HTML, and is typically used to denote column or row headings within a table.
- The `<td>` tag is used to create a standard table cell. This tag is typically used to hold data such as text, images, or other HTML elements.



Basic example

```html

<table border="1">
  <tr>
    <th>Heading 1</th>
    <th>Heading 2</th>
  </tr>
  <tr>
    <td>Data 1</td>
    <td>Data 2</td>
  </tr>
  <tr>
    <td>Data 3</td>
    <td>Data 4</td>
  </tr>
</table>
```



The `border` attribute is used to provide a border width for the table and individual cells.

![](/Users/david/Documents/1.-project/craftman-web/notes/asset/01-html/html-table-02.png)

using CSS to control the styling is recommended. Also, Ally mentioned at her work she rarely needed to use HTML table. Unless some webpage requires a specific granular details and flex box model doesn't work. She suggested it is good to test the solution of using HTML table. On other hand, if your work deals with lots of data (i.e. financial institution), HTML table may be common in use. 



#### 6. HTML Form and input tags

HTML **`form`**  element is a block-level element primarily used for collecting and submitting user information. In actual web development, the **POST** method is commonly used to submit form data.

HTML forms are an essential part of creating dynamic web pages. They allow users to input and submit data to the web server, which can then be processed and stored.

- Use the `<form>` tag to start a form and the `</form>` tag to end it.
- Use the `<input>`, `<select>` and `<textarea>` tag to create form fields for the user to input data. There are various types of input fields, such as text, password, email, radio buttons, checkboxes, dropdowns and more.
- Use the `<label>` tag to create a label for each input field to provide more context and improve accessibility.
- Add a button at the end to trigger form submission and set the `action` and `method` attributes to configure where the results are sent (more on this later).

###### Form Action and Submission

Form submission is an important aspect of HTML forms. It involves sending the form data to a server for processing.

Two Attributes

- **method:** Specifies the HTTP method (GET or POST) to be used when submitting the form. **POST** is commonly used for submitting data securely, while **GET** is typically used for retrieving data. The `method` attribute specifies the HTTP method used to submit the form data. The most common methods are `GET` and `POST`. `GET` submits the form data as URL parameters, while `POST` submits the form data in the HTTP request body.
- **action:** Defines the URL where the form data will be sent for processing. It specifies the endpoint or script that will handle the submitted form data. The `action` attribute specifies the URL of the server-side script or service that will process the form data. This URL can be an absolute or relative URL.

- **target**: attribute specifies the location where the server response should be displayed. The most common values for this attribute are `_self` (default) and `_blank`. `_self` opens the response in the same window, while `_blank` opens the response in a new window.

In addition to these attributes, the `submit` input `type` is used to show a button to submit the form data. When a user clicks on a `submit` button, the form data is sent to the server for processing.

###### Common form attributes

- **name** - Used to identify a form element so that its data can be associated with the field name when the form is submitted.
- **value**- Sets the initial value of the form element. For radio buttons, this value must be specified.
- **size** - Specifies the initial width of the form element. When `type="text"` or `type="password"`, the size is defined by the number of characters. For other types, the width is defined in pixels.
- **maxlength**- Defines the maximum number of characters that can be entered into the field when `type="text"` or `type="password"`.
- **checked** - Used for `type="radio"` or `type="checkbox"` to pre-select the checkbox or radio button.
- **autocomplete** - Specifies whether the browser should attempt to automatically complete the form field based on previous inputs.
- **disabled**- Prevents the user from interacting with the form element, making it non-functional.
- **readonly**- Makes the form element read-only, meaning the user cannot modify its value, but the value will still be sent when the form is submitted.
- **placeholder** - Provides a short hint that describes the expected value of the input field, displayed inside the input field before the user enters a value.
- **required**-  Specifies that the user must fill out the field before submitting the form.



Here is an example

```html
<form method="post" action="result.html">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required />

  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required />

  <label for="password">Password:</label>
  <input type="password" id="password" name="password" required />

  <label for="gender">Gender:</label>
  <input type="radio" id="male" name="gender" value="male" />
  <label for="male">Male</label>
  <input type="radio" id="female" name="gender" value="female" />
  <label for="female">Female</label>

  <label for="country">Country:</label>
  <select id="country" name="country">
    <option value="china" selected="selected">China</option>
    <option value="usa">USA</option>
    <option value="uk">UK</option>
  </select>

  <label for="message">Message:</label>
  <textarea id="message" name="message" rows="4"></textarea>

  <label for="subscribe">Subscribe to newsletter:</label>
  <input type="checkbox" id="subscribe" name="subscribe" value="yes" />

  <input type="reset" id="reset" name="reset" value="Reset" />

  <button type="submit">Submit</button>
</form>

```



The `<input>` tags have various attributes, such as "type" to specify the type of input, "id" for unique identification, "name" for server-side processing, and "required" to indicate that the field is mandatory.



###### HTML Form and Input types

Here are the different types of inputs in HTML, most of which are created using the `input` tag:

1. **Text Input**: It allows users to enter text, such as name, address, email, etc. The `type` attribute for text input is text.
2. **Checkbox Input**: It is used to select one or more options from a list of options. The `type` attribute for checkbox input is `checkbox`.
3. **Radio Input**: It is used to select only one option from a list of options. The `type` attribute for radio input is `radio`. Radio buttons are grouped using the name attribute.
4. **Dropdown**: It is used to create a dropdown list of options. Dropdowns are created using the `select` and `options` tags.
5. **Textarea**: It allows users to input a larger amount of text, such as comments or messages. Text areas are created using the `textarea` tag.
6. **Date Input**: It is used to input date values, such as birthdays, deadlines, etc. The type attribute for date input is date.
7. **Password Input**: It is similar to the text input, but it masks the entered text with asterisks or dots for privacy and security purposes. The `type` attribute for password input is `password`.
8. **Email Input**: It is used to input an email address, which can be validated using HTML5. The `type` attribute for email input is `email`.
9. **Number Input**: It is used to input numerical values and has additional attributes such as `min`, `max`, and `step`. The `type` attribute for number input is `number`.

There are several other less commonly used input types that you can learn about here: [https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input](https://jovian.com/outlink?url=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FHTML%2FElement%2Finput)



Here's a form demonstrating usage of the above input types:

```html
<div id="application">
    <h2>Submit Your Application</h2>

    <form id="application-form">
        <div class="form-group">
            <label for="name">Name</label><br>
            <input type="text" id="name" name="name" required placeholder="John Doe">
        </div>

        <div class="form-group">
            <label for="email">Email</label><br>
            <input type="email" id="email" name="email" required placeholder="jdoe@example.com">
        </div>
        <div class="form-group">

            <label for="phone">Phone</label><br>
            <input type="tel" id="phone" name="phone" required placeholder="+919898989898">
        </div>

        <div class="form-group">
            <label for="dob">Date of Birth</label><br>
            <input type="date" id="dob" name="dob" required>
        </div>

        <div class="form-group">
            <label for="position">Position Applied for</label><br>
            <select id="position" name="position" required>
                <option value="">Select an option</option>
                <option value="Frontend Developer">Frontend Developer</option>
                <option value="Full Stack Developer">Full Stack Developer</option>
                <option value="Data Scientist">Data Scientist</option>
                <option value="ML Engineer">ML Engineer</option>
            </select>
        </div>

        <div class="form-group">
            <label for="resume">Upload Resume</label><br>
            <input type="file" id="resume" name="resume" accept=".pdf,.doc,.docx" required>
        </div>

        <div class="form-group">
            <label for="coverletter">Cover Letter</label><br>
            <textarea id="coverletter" name="coverletter" rows="5" required placeholder="Explain what makes you suitable for the job.."></textarea>
        </div>

        <div class="form-group">
            <label for="terms">
                <input type="checkbox" id="terms" name="terms" required>
                I agree to the terms and conditions
            </label>
        </div>

        <div class="form-group">
            <input type="submit" value="Submit">
        </div>
    </form>


</div>
```



###### Another example

```html
<input type="button" />
<input type="checkbox" />
<input type="color" />
<input type="date" />
<input type="datetime-local" />
<input type="email" />
<input type="file" />
<input type="hidden" />
<input type="image" />
<input type="month" />
<input type="number" />
<input type="password" />
<input type="radio" />
<input type="range" />
<input type="reset" />
<input type="search" />
<input type="submit" />
<input type="tel" />
<input type="text" />
<input type="time" />
<input type="url" />
<input type="week" />
```



###### To enhance User Experience 



the `for` in `<label>` tag will work with the `id` from `<input>` tag

```html
<label for="click-label-to-input"></label>
<input id="click-label-to-input" [more..other..tags]/>
```



###### Common HTML Elements to work with HTML form:

```html
<input>
<label>
<select>
<textarea>
<button>
<fieldset>
<legend>
<datalist>
<output>
<option>
<optgroup>
```



**example for using multiple choice/single choice**



```html
<input
  type="text"
  id="username"
  name="username"
  value="username"
  size="30"
  maxlength="20"
  required
/>
<textarea></textarea>

multiple choice 
single choice

<form action="" method="post" enctype="multipart/form-data">
  <p>
    <input type="file" name="files" />
    <input type="submit" name="upload" value="upload" />
  </p>
</form>
```



###### HTML Form Submission

Form submission is typically handled by writing a JavaScript function in the `onsubmit` attribute of `<form>` tag, which makes an API call to send the form data to the backend.





```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Simple Form Example</title>
</head>
<body>

  <h1>Contact Form</h1>

  <form action="result.html" method="get">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" required />
    <br />
    
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required />
    <br />

    <label for="message">Message:</label>
    <textarea id="message" name="message" rows="4" required></textarea>
    <br />

    <button type="submit">Submit</button>
  </form>

</body>
</html>

```







----

## Footnotes

[^1]: Miss Tang said she likes W3Schhol but my personal choice will be always MDN, as I heard W3School might not be always correct for some other concepts. 
[^2]: My personal take is that the kind of interviewer mostly tests if you pay attention to this details since everyone use shortcut nowadays
[^3]: I use NeoVim by the way
[^4]: This is from my previous career and I wrote about web scraping. https://medium.com/@shenghongzhong/a-comprehensive-web-scraping-tutorial-385a2ac27107
[^5]: If you are like me using vim/nvim, you can install the plugin Comment.vim and then you can type `gcc` to comment or comment out

