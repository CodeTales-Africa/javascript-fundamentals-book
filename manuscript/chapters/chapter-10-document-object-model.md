# CHAPTER 10

# The Document Object Model (DOM)

## Chapter Overview

Up to this point, you have learned how to write JavaScript programs using variables, functions, arrays, objects, and other core language features. However, most of these programs executed in the browser console or as standalone scripts.

In this chapter, you will learn how JavaScript interacts with web pages through the **Document Object Model (DOM)**. The DOM is one of the most important concepts in front-end web development because it enables JavaScript to read, modify, create, and remove HTML elements dynamically.

By understanding the DOM, you will be able to build interactive websites that respond to user actions, update content without reloading the page, validate forms, create animations, and much more.

This chapter marks the transition from learning JavaScript as a programming language to using JavaScript as a tool for building real web applications.

---

# Learning Objectives

After studying this chapter, you should be able to:

- Explain what the Document Object Model (DOM) is.
- Understand how the browser creates the DOM tree.
- Access HTML elements using different DOM selection methods.
- Modify HTML content dynamically.
- Change CSS styles with JavaScript.
- Create, insert, replace, and remove HTML elements.
- Navigate through the DOM tree.
- Handle common DOM manipulation tasks.
- Build interactive web pages using JavaScript.

---

# Prerequisites

Before studying this chapter, you should already understand:

- Variables
- Data Types
- Operators
- Conditional Statements
- Loops
- Functions
- Arrays
- Objects

You should also have a working knowledge of HTML and CSS.

---

# Real-World Applications

The DOM is used in virtually every modern website and web application, including:

- Navigation menus
- Image sliders
- Shopping carts
- Login systems
- Registration forms
- Dashboards
- Social media feeds
- Online banking systems
- E-learning platforms
- Content management systems
- Single Page Applications (SPAs)

---

# Chapter Outline

10.1 What Is the Document Object Model (DOM)?

10.2 Understanding the DOM Tree

10.3 How Browsers Create the DOM

10.4 Selecting Elements by ID

10.5 Selecting Elements by Class Name

10.6 Selecting Elements by Tag Name

10.7 querySelector() and querySelectorAll()

10.8 Reading and Changing HTML Content

10.9 Working with Text Content

10.10 Modifying HTML Attributes

10.11 Changing CSS Styles with JavaScript

10.12 Creating HTML Elements

10.13 Appending and Inserting Elements

10.14 Replacing Elements

10.15 Removing Elements

10.16 Navigating the DOM Tree

10.17 Mini Project: Interactive Student Profile

10.18 Chapter Review

10.19 Practice Exercises

10.20 Programming Challenges

10.21 Key Terms

10.22 Chapter Summary

10.23 Looking Ahead

---

# Estimated Reading Time

Approximately 3–5 hours

---

# Difficulty Level

Beginner → Intermediate

---

# Why This Chapter Matters

Everything you build on the web involves the DOM.

Whenever a button changes color, a form validates input, a shopping cart updates automatically, or a notification appears without refreshing the page, JavaScript is interacting with the DOM.

Mastering the DOM is the first major step toward becoming a professional front-end JavaScript developer.

---

# CodeTales Insight

> **JavaScript gives your web pages intelligence, but the DOM gives JavaScript access to the page itself. Once you understand the DOM, you'll move from writing simple scripts to creating interactive web applications that users can see and use.**

---

# 10.1 What Is the Document Object Model (DOM)?

Imagine opening your favorite website in a web browser. You see headings, paragraphs, images, buttons, links, forms, and many other elements displayed on the screen.

Although you see a web page, the browser sees something different.

When a browser loads an HTML document, it reads the HTML code and converts it into a structured representation known as the **Document Object Model (DOM)**.

The DOM allows JavaScript to interact with every part of a web page. Using the DOM, JavaScript can:

- Read HTML elements.
- Change text and images.
- Modify CSS styles.
- Create new elements.
- Remove existing elements.
- Respond to user interactions such as clicks and keyboard input.

Without the DOM, JavaScript would not be able to change the contents of a web page after it has loaded.

---

# What Does DOM Mean?

The term **DOM** stands for:

- **Document** – The HTML page loaded in the browser.
- **Object** – Every HTML element becomes an object.
- **Model** – A structured representation of the document that JavaScript can work with.

Together, the Document Object Model is a programming interface that represents an HTML document as a collection of interconnected objects.

---

## Figure 10.1

**Meaning of DOM**

```text
DOM

│

├── Document
│      The HTML page

├── Object
│      HTML elements become objects

└── Model
       A structured representation
       of the document
```

**Figure 10.1:** The three parts of the term "Document Object Model."

---

# The Browser's Perspective

Consider the following HTML document.

```html
<!DOCTYPE html>

<html>

<head>

    <title>My Website</title>

</head>

<body>

    <h1>Hello World</h1>

    <p>Welcome to JavaScript.</p>

</body>

</html>
```

When the browser loads this page, it does not simply display the HTML code.

Instead, it converts the document into a hierarchy of objects.

Each HTML element becomes a JavaScript object that can be accessed and manipulated.

---

## Figure 10.2

**HTML Document Becomes a DOM Tree**

```text
HTML Document

        │

        ▼

Browser

        │

        ▼

Document Object Model (DOM)

        │

        ▼

JavaScript Can Access Every Element
```

---

# Why Was the DOM Created?

Early web pages were static.

Once a page loaded, its contents could not be changed without refreshing the entire page.

As websites became more interactive, developers needed a way to update web pages dynamically.

The DOM was introduced to solve this problem.

Today, the DOM enables JavaScript to:

- Update text instantly.
- Display notifications.
- Validate forms.
- Show or hide content.
- Build interactive dashboards.
- Create modern web applications.

---

# JavaScript and the DOM

JavaScript communicates with the browser through the DOM.

The browser provides a global object called `document`.

This object represents the entire HTML document.

Example:

```javascript
console.log(document);
```

When executed in the browser's Developer Tools Console, JavaScript displays the entire document object.

The `document` object is the starting point for almost every DOM operation.

---

## Figure 10.3

**JavaScript Communicating with the DOM**

```text
JavaScript

      │

      ▼

document

      │

      ▼

DOM

      │

      ▼

HTML Elements
```

---

# Real-World Example

Suppose you have the following HTML page.

```html
<h1 id="title">
    Welcome
</h1>
```

Using JavaScript, you can change the heading.

```javascript
const heading = document.getElementById("title");

heading.textContent = "Welcome to Cracking JavaScript!";
```

After the code runs, the browser displays:

```html
<h1 id="title">
    Welcome to Cracking JavaScript!
</h1>
```

Notice that the page updates immediately without requiring a refresh.

This dynamic behavior is possible because JavaScript modifies the DOM.

---

# Advantages of the DOM

The DOM provides many benefits:

- Makes web pages interactive.
- Allows dynamic content updates.
- Enables JavaScript to modify HTML and CSS.
- Supports user interaction.
- Forms the foundation of modern front-end frameworks such as React, Vue, and Angular.

---

# Best Practices

- Always access elements through the `document` object.
- Write JavaScript after the HTML has loaded or use appropriate loading techniques.
- Use meaningful IDs and class names to simplify element selection.
- Keep HTML, CSS, and JavaScript organized and separated where possible.

---

# Common Beginner Mistakes

## Mistake 1: Thinking the DOM Is the Same as HTML

HTML is the source code of the page.

The DOM is the browser's object representation of that HTML.

---

## Mistake 2: Confusing JavaScript with the DOM

JavaScript is a programming language.

The DOM is an interface provided by the browser.

JavaScript uses the DOM to interact with web pages.

---

## Mistake 3: Trying to Use `document` Outside the Browser

The `document` object exists in web browsers.

If you run the following code in a non-browser JavaScript environment, such as Node.js:

```javascript
console.log(document);
```

you will receive an error because Node.js does not provide a DOM by default.

---

# Chapter Connection

In the previous chapter, you learned how to organize data using objects.

In this chapter, you will learn that every HTML element is also represented as an object.

This means your knowledge of JavaScript objects will help you understand how the DOM works.

---

# Section Summary

In this section, you learned that the Document Object Model (DOM) is the browser's object representation of an HTML document. You discovered that every HTML element becomes an object that JavaScript can access and modify. You also learned that the `document` object serves as the entry point for interacting with the DOM, enabling developers to create dynamic and interactive web pages.

---

# CodeTales Insight

> **Think of HTML as the blueprint of a house and the DOM as the finished house that you can walk through and modify. JavaScript acts like the homeowner—it can repaint walls, move furniture, add new rooms, or remove old ones. Understanding this relationship is the key to mastering front-end web development.**

---

# 10.2 Understanding the DOM Tree

When a browser loads an HTML document, it does not treat the document as a long block of text.

Instead, it organizes every HTML element into a hierarchical structure called the **DOM Tree**.

This tree shows the relationship between elements, making it possible for JavaScript to navigate through the page and manipulate individual elements.

Understanding the DOM Tree is essential because almost every DOM operation depends on these relationships.

---

# What Is a Tree Structure?

A tree is a way of organizing data into levels.

Just like a family tree has parents, children, and siblings, the DOM Tree has similar relationships between HTML elements.

Each HTML element is called a **node**.

Nodes are connected to one another through parent-child relationships.

---

## Figure 10.4

**Basic Tree Structure**

```text
            Root

             │

     ┌───────┴────────┐

   Child A         Child B

      │                │

 ┌────┴────┐      ┌────┴────┐

Child   Child   Child   Child
```

**Figure 10.4:** A simple tree structure showing parent and child relationships.

---

# Example HTML Document

Consider the following HTML page.

```html
<!DOCTYPE html>

<html>

<head>

    <title>My Website</title>

</head>

<body>

    <h1>Welcome</h1>

    <p>Learning the DOM is fun.</p>

</body>

</html>
```

The browser converts this into the following DOM Tree.

---

## Figure 10.5

**DOM Tree**

```text
Document

│

└── html

    ├── head

    │

    │── title

    │

    └── body

         ├── h1

         └── p
```

**Figure 10.5:** The browser converts HTML into a hierarchical DOM Tree.

---

# The Root Node

Every DOM Tree begins with the **Document** node.

This node represents the entire HTML document.

Below the document node is the `<html>` element.

The `<html>` element contains every other element on the page.

```text
Document

↓

html
```

The `document` object in JavaScript represents this root node.

---

# Parent Nodes

A parent node is an element that contains one or more child elements.

Example:

```html
<body>

    <h1>Welcome</h1>

    <p>Hello World</p>

</body>
```

Here:

- `<body>` is the parent.
- `<h1>` is a child.
- `<p>` is another child.

---

## Figure 10.6

**Parent Node**

```text
body

├── h1

└── p
```

---

# Child Nodes

A child node is an element contained inside another element.

Example:

```html
<ul>

    <li>HTML</li>

    <li>CSS</li>

    <li>JavaScript</li>

</ul>
```

Here:

- `<ul>` is the parent.
- Every `<li>` is a child node.

---

## Figure 10.7

**Child Nodes**

```text
ul

├── li

├── li

└── li
```

---

# Sibling Nodes

Sibling nodes share the same parent.

Example:

```html
<body>

    <h1>Welcome</h1>

    <p>Paragraph One</p>

    <button>Click Me</button>

</body>
```

The following elements are siblings because they all belong to `<body>`:

- `<h1>`
- `<p>`
- `<button>`

---

## Figure 10.8

**Sibling Nodes**

```text
body

├── h1

├── p

└── button
```

---

# Ancestor Nodes

An ancestor is any node above another node in the tree.

Example:

```html
<html>

<body>

<section>

<p>Hello</p>

</section>

</body>

</html>
```

For the `<p>` element:

- Parent → `<section>`
- Grandparent → `<body>`
- Great-grandparent → `<html>`

---

# Descendant Nodes

A descendant is any node located below another node.

Example:

```html
<body>

<section>

<p>Hello</p>

</section>

</body>
```

The descendants of `<body>` include:

- `<section>`
- `<p>`

---

## Figure 10.9

**Family Relationships**

```text
Document

│

html

│

body

│

section

│

p
```

---

# Why the DOM Tree Matters

The DOM Tree allows JavaScript to:

- Find elements quickly.
- Move between related elements.
- Insert new elements.
- Remove existing elements.
- Replace elements.
- Change text and styles.
- Build interactive web applications.

Without the tree structure, JavaScript would not know where an element is located.

---

# Real-World Example

Consider a navigation menu.

```html
<nav>

<ul>

<li>Home</li>

<li>About</li>

<li>Contact</li>

</ul>

</nav>
```

DOM Tree

```text
nav

│

ul

├── li

├── li

└── li
```

JavaScript can access any of these nodes individually.

---

# Browser Developer Tools

You can actually view the DOM Tree in your browser.

Steps:

1. Open any website.
2. Press **F12** (or **Ctrl + Shift + I**).
3. Select the **Elements** tab.

You will see the complete DOM Tree generated by the browser.

This is one of the most valuable tools for front-end developers.

---

# Best Practices

- Think of HTML as a tree, not as plain text.
- Understand parent-child relationships before writing DOM code.
- Use meaningful HTML structure to make navigation easier.
- Keep your HTML well organized and properly nested.

---

# Common Beginner Mistakes

## Mistake 1: Confusing Parent and Child

Remember:

The element that contains another element is the parent.

The contained element is the child.

---

## Mistake 2: Thinking Every Element Has Only One Child

Some elements have:

- No children
- One child
- Many children

---

## Mistake 3: Ignoring Proper Nesting

Incorrect:

```html
<p>

<div>Hello</div>

</p>
```

This creates invalid HTML.

Always nest elements correctly.

---

# Section Summary

In this section, you learned that browsers organize HTML documents into a hierarchical structure called the DOM Tree. Every HTML element becomes a node connected through parent, child, sibling, ancestor, and descendant relationships. Understanding these relationships is essential because JavaScript uses them to locate, traverse, and manipulate elements on a web page.

---

# CodeTales Insight

> **Professional JavaScript developers don't memorize the DOM—they visualize it. Before writing code, picture the HTML as a tree of connected nodes. Once you understand the relationships between elements, DOM manipulation becomes much more intuitive and efficient.**

---

# 10.3 How Browsers Create the DOM

Every time you enter a website address into your browser or click a link, a series of events takes place before the web page appears on your screen.

Although this process happens in a fraction of a second, understanding it will help you write better JavaScript and avoid common mistakes when working with the DOM.

In this section, you will learn how browsers transform an HTML document into the Document Object Model (DOM).

---

# Step 1: The Browser Requests the HTML Document

When you visit a website, your browser sends a request to the web server asking for the HTML document.

For example, if you visit:

```text
https://www.example.com
```

the browser requests the page from the server.

The server responds by sending the HTML file.

---

## Figure 10.10

**Browser Requests a Web Page**

```text
User

   │

   ▼

Browser

   │

   ▼

Request HTML Page

   │

   ▼

Web Server

   │

   ▼

HTML Document
```

---

# Step 2: The Browser Reads the HTML

Once the browser receives the HTML document, it begins reading it from top to bottom.

Example:

```html
<!DOCTYPE html>

<html>

<head>

    <title>My Website</title>

</head>

<body>

    <h1>Hello World</h1>

    <p>Learning JavaScript.</p>

</body>

</html>
```

The browser reads each HTML tag in the order it appears.

---

# Step 3: The Browser Parses the HTML

Parsing means analyzing the HTML and understanding its structure.

During parsing, the browser identifies:

- Elements
- Attributes
- Text nodes
- Parent-child relationships

It also checks for syntax errors and attempts to recover from invalid HTML whenever possible.

---

## Figure 10.11

**Parsing Process**

```text
HTML Source

      │

      ▼

Browser Parser

      │

      ▼

Recognizes HTML Elements

      │

      ▼

Builds the DOM Tree
```

---

# Step 4: The Browser Creates DOM Nodes

Every HTML element becomes a node in the DOM Tree.

Consider the following HTML:

```html
<body>

    <h1>Welcome</h1>

    <p>Learning JavaScript.</p>

</body>
```

The browser creates the following nodes:

```text
Document

│

html

│

body

├── h1

└── p
```

Each node becomes an object that JavaScript can access.

---

# Step 5: The Browser Builds the DOM Tree

After parsing every element, the browser connects them together into a hierarchical structure.

This completed structure is called the **DOM Tree**.

JavaScript can now navigate through this tree to find, modify, or remove elements.

---

## Figure 10.12

**DOM Construction**

```text
HTML

      │

      ▼

Parse HTML

      │

      ▼

Create Nodes

      │

      ▼

Connect Nodes

      │

      ▼

DOM Tree
```

---

# Step 6: JavaScript Accesses the DOM

After the DOM has been created, JavaScript can begin interacting with it.

Example:

```javascript
const heading = document.getElementById("title");

heading.textContent = "Welcome!";
```

JavaScript finds the element with the ID `title` and changes its displayed text.

---

# The Rendering Process

Once the DOM has been built, the browser renders the page.

Rendering involves:

- Displaying text
- Drawing images
- Applying CSS styles
- Positioning elements
- Showing the finished page on the screen

The rendered page is what the user sees and interacts with.

---

## Figure 10.13

**Complete Browser Workflow**

```text
User Opens Website

        │

        ▼

Browser Requests HTML

        │

        ▼

Server Sends HTML

        │

        ▼

Browser Parses HTML

        │

        ▼

Browser Builds DOM

        │

        ▼

CSS Is Applied

        │

        ▼

JavaScript Executes

        │

        ▼

Page Is Rendered
```

---

# Why Timing Matters

Because JavaScript works with the DOM, it cannot manipulate elements that do not yet exist.

Consider this HTML:

```html
<script>

const heading = document.getElementById("title");

</script>

<h1 id="title">
Hello
</h1>
```

When the script runs, the `<h1>` element has not yet been parsed.

As a result:

```javascript
heading
```

will be:

```text
null
```

This happens because the browser has not yet created the corresponding DOM node.

---

# Correct Ways to Avoid This Problem

One common solution is to place the `<script>` tag just before the closing `</body>` tag.

Example:

```html
<body>

<h1 id="title">
Hello
</h1>

<script src="script.js"></script>

</body>
```

By this point, the browser has already created the DOM, so JavaScript can safely access the elements.

> **Note:** In modern web development, another common approach is to load scripts with the `defer` attribute. You will learn about this later in the book.

---

# Real-World Example

Imagine constructing a house.

1. The architect creates the blueprint (HTML).
2. Builders construct the house (Browser parses HTML).
3. The completed house is ready (DOM Tree).
4. The homeowner decorates and rearranges furniture (JavaScript manipulates the DOM).

Without the completed house, there is nothing to decorate.

Similarly, JavaScript must wait until the DOM exists before manipulating it.

---

# Best Practices

- Write valid HTML.
- Place scripts after the HTML they depend on, or use `defer`.
- Avoid manipulating DOM elements before they exist.
- Keep HTML, CSS, and JavaScript in separate files whenever practical.

---

# Common Beginner Mistakes

## Mistake 1: Running JavaScript Too Early

Trying to access an element before the browser creates it results in `null`.

---

## Mistake 2: Assuming HTML Is the DOM

HTML is the source document.

The DOM is the browser's object representation of that document.

---

## Mistake 3: Ignoring Browser Parsing

Understanding the order in which browsers parse HTML helps explain many DOM-related errors.

---

# Section Summary

In this section, you learned how browsers transform an HTML document into the Document Object Model. You explored the complete process—from requesting the HTML document to parsing it, creating DOM nodes, building the DOM Tree, and rendering the page. You also learned why JavaScript must wait until the DOM is available before attempting to manipulate HTML elements.

---

# CodeTales Insight

> **When debugging DOM problems, always ask yourself one question: "Has the browser created this element yet?" Understanding the browser's loading process will save you countless hours of debugging throughout your career as a web developer.**

---

# 10.4 Selecting Elements by ID

One of the first tasks in DOM manipulation is locating an HTML element.

Before JavaScript can modify an element, it must first find that element in the Document Object Model (DOM).

The most common way to locate a single element is by using its **ID**.

JavaScript provides the `document.getElementById()` method for this purpose.

---

# What Is an ID?

An **ID** is a unique identifier assigned to an HTML element.

Each ID should appear only once within an HTML document.

Example:

```html
<h1 id="title">Welcome</h1>
```

Here:

- `h1` is the HTML element.
- `title` is its unique ID.

---

## Figure 10.14

**An HTML Element with an ID**

```text
<h1 id="title">

│

├── Element → h1

└── ID → title
```

---

# The `document.getElementById()` Method

Syntax:

```javascript
document.getElementById("id");
```

Replace `"id"` with the actual ID of the element.

Example:

```html
<h1 id="title">Welcome</h1>
```

```javascript
const heading = document.getElementById("title");
```

JavaScript searches the DOM and returns the `<h1>` element.

---

# Storing the Element

It is good practice to store the selected element in a variable.

```javascript
const heading = document.getElementById("title");
```

Now the variable `heading` refers to the HTML element.

You can use it multiple times without searching the DOM again.

---

# Viewing the Element

You can display the selected element in the browser console.

```javascript
const heading = document.getElementById("title");

console.log(heading);
```

Output:

```text
<h1 id="title">Welcome</h1>
```

The browser prints the actual HTML element.

---

# Example 1: Selecting a Paragraph

HTML

```html
<p id="message">
Learning JavaScript is exciting!
</p>
```

JavaScript

```javascript
const paragraph = document.getElementById("message");

console.log(paragraph);
```

Output

```text
<p id="message">
Learning JavaScript is exciting!
</p>
```

---

# Example 2: Selecting a Button

HTML

```html
<button id="submitButton">

Submit

</button>
```

JavaScript

```javascript
const button = document.getElementById("submitButton");

console.log(button);
```

---

# Example 3: Selecting an Image

HTML

```html
<img

id="logo"

src="logo.png"

alt="Company Logo">
```

JavaScript

```javascript
const logo = document.getElementById("logo");

console.log(logo);
```

---

# What Happens If the ID Does Not Exist?

Suppose the HTML document contains:

```html
<h1 id="heading">
Hello
</h1>
```

But JavaScript searches for:

```javascript
const title = document.getElementById("title");

console.log(title);
```

Output:

```text
null
```

The browser returns `null` because no element with the ID `"title"` exists.

---

# Checking for `null`

Always check that an element exists before using it.

```javascript
const heading = document.getElementById("title");

if (heading) {

    console.log("Element found.");

} else {

    console.log("Element not found.");

}
```

This helps prevent runtime errors.

---

# Why IDs Should Be Unique

Incorrect HTML:

```html
<h1 id="title">Welcome</h1>

<p id="title">
Paragraph
</p>
```

Two elements share the same ID.

This is invalid HTML.

Correct HTML:

```html
<h1 id="title">Welcome</h1>

<p id="description">
Paragraph
</p>
```

Each element has its own unique ID.

---

## Figure 10.15

**Unique IDs**

```text
Correct

title

description

submitButton

Incorrect

title

title

title
```

---

# Practical Example

HTML

```html
<!DOCTYPE html>

<html>

<head>

<title>DOM Example</title>

</head>

<body>

<h1 id="title">

Welcome to JavaScript

</h1>

<script>

const heading = document.getElementById("title");

console.log(heading);

</script>

</body>

</html>
```

When the page loads, the browser prints the `<h1>` element in the console.

---

# Real-World Uses

Developers commonly use IDs for:

- Main headings
- Login forms
- Search boxes
- Submit buttons
- Navigation bars
- Hero sections
- Modal windows
- Page containers

Any element that needs to be uniquely identified is a good candidate for an ID.

---

# Best Practices

- Use meaningful ID names.
- Keep IDs unique.
- Use lowercase letters where possible.
- Avoid spaces in IDs.
- Store selected elements in variables.

Good examples:

```text
header

mainMenu

loginForm

searchBox

submitButton
```

Avoid:

```text
abc

x

test1

thing

item
```

---

# Common Beginner Mistakes

## Mistake 1: Forgetting the Exact ID

HTML

```html
<h1 id="Title">
Hello
</h1>
```

JavaScript

```javascript
document.getElementById("title");
```

This returns:

```text
null
```

because IDs are **case-sensitive**.

---

## Mistake 2: Including the `#` Symbol

Incorrect:

```javascript
document.getElementById("#title");
```

Correct:

```javascript
document.getElementById("title");
```

Unlike CSS selectors, `getElementById()` expects only the ID name.

---

## Mistake 3: Using Duplicate IDs

Duplicate IDs make your HTML invalid and can produce unexpected results.

Always keep IDs unique.

---

# Section Summary

In this section, you learned how to locate HTML elements using `document.getElementById()`. You discovered that IDs uniquely identify elements within a page, how to store selected elements in variables, how to handle cases where an element does not exist, and why unique IDs are important for reliable DOM manipulation.

---

# CodeTales Insight

> **The first step in changing a web page is finding the element you want to change. Master `document.getElementById()` thoroughly—it is one of the most frequently used DOM methods and forms the foundation for more advanced DOM manipulation techniques you'll learn throughout this chapter.**

---

# 10.5 Selecting Elements by Class Name

In the previous section, you learned how to select a single HTML element using its unique ID.

However, many web pages contain multiple elements that share the same styling or functionality. Instead of assigning each element a different ID, developers use **classes**.

JavaScript allows you to select all elements that share the same class name using the `document.getElementsByClassName()` method.

---

# What Is a Class?

A class is an attribute that groups multiple HTML elements together.

Unlike IDs, a class can be used on many elements.

Example:

```html
<p class="note">First Note</p>

<p class="note">Second Note</p>

<p class="note">Third Note</p>
```

All three paragraphs belong to the class **note**.

---

## Figure 10.16

**Multiple Elements Sharing the Same Class**

```text
Class: note

├── Paragraph 1

├── Paragraph 2

└── Paragraph 3
```

---

# The `document.getElementsByClassName()` Method

Syntax

```javascript
document.getElementsByClassName("className");
```

Example

```javascript
const notes = document.getElementsByClassName("note");
```

JavaScript searches the DOM and returns every element that belongs to the class **note**.

---

# HTMLCollection

Unlike `getElementById()`, this method does **not** return a single element.

Instead, it returns an **HTMLCollection**.

Think of an HTMLCollection as a list of HTML elements.

Example

```html
<p class="note">HTML</p>

<p class="note">CSS</p>

<p class="note">JavaScript</p>
```

```javascript
const notes = document.getElementsByClassName("note");

console.log(notes);
```

Output

```text
HTMLCollection(3)
```

The number indicates how many matching elements were found.

---

## Figure 10.17

**HTMLCollection**

```text
notes

│

├── notes[0]

├── notes[1]

└── notes[2]
```

---

# Accessing Individual Elements

Because an HTMLCollection behaves like a list, you use an index to access individual elements.

Example

```javascript
const notes = document.getElementsByClassName("note");

console.log(notes[0]);
```

Output

```html
<p class="note">HTML</p>
```

---

# Accessing the Second Element

```javascript
console.log(notes[1]);
```

Output

```html
<p class="note">CSS</p>
```

---

# Accessing the Third Element

```javascript
console.log(notes[2]);
```

Output

```html
<p class="note">JavaScript</p>
```

---

# Looping Through an HTMLCollection

Most of the time, you will want to work with every matching element.

Example

```javascript
const notes = document.getElementsByClassName("note");

for (let i = 0; i < notes.length; i++) {

    console.log(notes[i]);

}
```

The loop visits every element in the collection.

---

# Using the `length` Property

The `length` property tells you how many elements were found.

Example

```javascript
const notes = document.getElementsByClassName("note");

console.log(notes.length);
```

Output

```text
3
```

---

# Practical Example

HTML

```html
<ul>

    <li class="language">HTML</li>

    <li class="language">CSS</li>

    <li class="language">JavaScript</li>

    <li class="language">Python</li>

</ul>
```

JavaScript

```javascript
const languages = document.getElementsByClassName("language");

for (let i = 0; i < languages.length; i++) {

    console.log(languages[i].textContent);

}
```

Output

```text
HTML

CSS

JavaScript

Python
```

---

# What Happens If No Elements Are Found?

Example

```javascript
const items = document.getElementsByClassName("student");

console.log(items);
```

Output

```text
HTMLCollection []
```

Unlike `getElementById()`, which returns `null`, this method returns an empty HTMLCollection.

---

# IDs vs Classes

| Feature | ID | Class |
|---------|----|-------|
| Unique | Yes | No |
| Number of Matches | One | Many |
| Method | `getElementById()` | `getElementsByClassName()` |
| Return Value | Element | HTMLCollection |

---

## Figure 10.18

**ID vs Class**

```text
ID

↓

One Element

---------------------

Class

↓

Many Elements
```

---

# Real-World Uses

Classes are commonly used for:

- Navigation links
- Product cards
- Blog posts
- Buttons
- Images
- Form fields
- Menu items
- Notifications
- Articles
- Cards

---

# Best Practices

- Use classes for groups of similar elements.
- Use meaningful class names.
- Loop through collections when multiple elements need processing.
- Use IDs only for elements that should be unique.

---

# Common Beginner Mistakes

## Mistake 1: Expecting One Element

Incorrect

```javascript
const note = document.getElementsByClassName("note");

note.textContent = "Hello";
```

This causes an error because `note` is an HTMLCollection.

Correct

```javascript
note[0].textContent = "Hello";
```

or loop through the collection.

---

## Mistake 2: Forgetting the Index

Remember:

```javascript
notes[0]
```

is an element.

```javascript
notes
```

is the entire collection.

---

## Mistake 3: Confusing HTMLCollection with an Array

An HTMLCollection looks similar to an array, but it is **not** an actual JavaScript array.

Some array methods cannot be used directly on an HTMLCollection.

You will learn how to convert collections into arrays later in this book.

---

# Section Summary

In this section, you learned how to select multiple HTML elements using `document.getElementsByClassName()`. You discovered that this method returns an HTMLCollection rather than a single element, how to access elements by index, how to loop through a collection, and when to use classes instead of IDs.

---

# CodeTales Insight

> **When selecting elements, think about your goal. If you need one unique element, use an ID. If you need to work with a group of similar elements, use a class. Choosing the right selector makes your code cleaner, easier to maintain, and more efficient.**

---

# 10.6 Selecting Elements by Tag Name

In the previous sections, you learned how to select elements by their **ID** and **class name**.

Sometimes, however, you may want to select **every element of a particular HTML type**, such as all paragraphs, all headings, all buttons, or all images.

JavaScript provides the `document.getElementsByTagName()` method for this purpose.

---

# What Is a Tag Name?

A tag name is the name of an HTML element.

Examples include:

```html
<h1>

<p>

<div>

<img>

<button>

<ul>

<li>
```

In each example:

- `h1`
- `p`
- `div`
- `img`
- `button`
- `ul`
- `li`

are tag names.

---

## Figure 10.19

**HTML Tag Names**

```text
HTML Elements

├── h1

├── p

├── div

├── img

├── button

├── ul

└── li
```

---

# The `document.getElementsByTagName()` Method

Syntax

```javascript
document.getElementsByTagName("tagName");
```

Example

```javascript
const paragraphs = document.getElementsByTagName("p");
```

JavaScript searches the DOM and returns every `<p>` element.

---

# Example 1: Selecting All Paragraphs

HTML

```html
<p>Paragraph One</p>

<p>Paragraph Two</p>

<p>Paragraph Three</p>
```

JavaScript

```javascript
const paragraphs = document.getElementsByTagName("p");

console.log(paragraphs);
```

Output

```text
HTMLCollection(3)
```

---

# HTMLCollection Again

Just like `getElementsByClassName()`, this method returns an **HTMLCollection**.

```text
paragraphs

│

├── paragraphs[0]

├── paragraphs[1]

└── paragraphs[2]
```

Each element can be accessed using its index.

---

# Accessing Individual Elements

Example

```javascript
const paragraphs = document.getElementsByTagName("p");

console.log(paragraphs[0]);
```

Output

```html
<p>Paragraph One</p>
```

---

# Looping Through All Elements

HTML

```html
<p>HTML</p>

<p>CSS</p>

<p>JavaScript</p>

<p>Python</p>
```

JavaScript

```javascript
const paragraphs = document.getElementsByTagName("p");

for (let i = 0; i < paragraphs.length; i++) {

    console.log(paragraphs[i].textContent);

}
```

Output

```text
HTML

CSS

JavaScript

Python
```

---

# Example 2: Selecting All Buttons

HTML

```html
<button>Save</button>

<button>Edit</button>

<button>Delete</button>
```

JavaScript

```javascript
const buttons = document.getElementsByTagName("button");

console.log(buttons.length);
```

Output

```text
3
```

---

# Example 3: Selecting All Images

HTML

```html
<img src="logo.png">

<img src="banner.jpg">

<img src="profile.png">
```

JavaScript

```javascript
const images = document.getElementsByTagName("img");

console.log(images.length);
```

Output

```text
3
```

---

# Selecting Elements Inside Another Element

You can also search within a specific element instead of the entire document.

HTML

```html
<div id="container">

    <p>First</p>

    <p>Second</p>

</div>
```

JavaScript

```javascript
const container = document.getElementById("container");

const paragraphs = container.getElementsByTagName("p");

console.log(paragraphs.length);
```

Output

```text
2
```

This limits the search to the selected container.

---

## Figure 10.20

**Searching Within an Element**

```text
document

│

└── div#container

      ├── p

      └── p
```

---

# What Happens If No Elements Exist?

Example

```javascript
const videos = document.getElementsByTagName("video");

console.log(videos);
```

Output

```text
HTMLCollection []
```

An empty HTMLCollection is returned.

---

# Class Name vs Tag Name

| Feature | Class Name | Tag Name |
|---------|------------|----------|
| Selects | Elements with the same class | Elements with the same HTML tag |
| Method | `getElementsByClassName()` | `getElementsByTagName()` |
| Return Type | HTMLCollection | HTMLCollection |

---

# When Should You Use Tag Names?

Selecting by tag name is useful when you want to:

- Count all images on a page.
- Loop through every paragraph.
- Modify all buttons.
- Process every list item.
- Apply changes to all headings.

If you only need one specific element, an ID or a CSS selector is usually a better choice.

---

# Best Practices

- Use tag names when working with groups of the same element type.
- Narrow your search to a specific parent element whenever possible.
- Store collections in variables for reuse.
- Use loops to process all matching elements.

---

# Common Beginner Mistakes

## Mistake 1: Expecting a Single Element

Incorrect

```javascript
const paragraph = document.getElementsByTagName("p");

paragraph.textContent = "Hello";
```

`paragraph` is an HTMLCollection, not a single element.

Correct

```javascript
paragraph[0].textContent = "Hello";
```

---

## Mistake 2: Forgetting That Searches Are Case-Insensitive in HTML

Use standard lowercase tag names:

```javascript
document.getElementsByTagName("p");
```

instead of:

```javascript
document.getElementsByTagName("P");
```

Lowercase improves readability and follows HTML conventions.

---

## Mistake 3: Searching the Entire Document Unnecessarily

If you already have a parent element, search within it instead of searching the whole document.

This makes your code more focused and easier to maintain.

---

# Section Summary

In this section, you learned how to select HTML elements by their tag names using `document.getElementsByTagName()`. You discovered that this method returns an HTMLCollection, how to access elements by index, how to loop through matching elements, and how to search within a specific parent element.

---

# CodeTales Insight

> **Choosing the right selector is an important programming skill. Selecting by tag name is simple and useful when working with all elements of the same type, but for more precise selection, modern JavaScript developers often use CSS selectors. In the next section, you'll learn the powerful `querySelector()` and `querySelectorAll()` methods, which combine the flexibility of CSS with the power of JavaScript.**

---

# 10.7 `querySelector()` and `querySelectorAll()`

In the previous sections, you learned how to select elements using:

- `getElementById()`
- `getElementsByClassName()`
- `getElementsByTagName()`

While these methods are still widely used, modern JavaScript developers often prefer **`querySelector()`** and **`querySelectorAll()`** because they allow you to use **CSS selectors** to locate elements.

These methods are flexible, powerful, and supported by all modern browsers.

---

# What Is a CSS Selector?

A CSS selector identifies one or more HTML elements.

For example:

| CSS Selector | Selects |
|--------------|---------|
| `#title` | Element with the ID `title` |
| `.note` | All elements with the class `note` |
| `p` | All paragraph elements |
| `button` | All button elements |
| `div p` | All `<p>` elements inside a `<div>` |

Since `querySelector()` and `querySelectorAll()` use CSS selectors, if you already know CSS, you'll find these methods easy to use.

---

# The `querySelector()` Method

The `querySelector()` method returns **the first element** that matches the specified CSS selector.

### Syntax

```javascript
document.querySelector("selector");
```

---

# Example 1: Selecting an Element by ID

HTML

```html
<h1 id="title">Welcome</h1>
```

JavaScript

```javascript
const heading = document.querySelector("#title");

console.log(heading);
```

Output

```html
<h1 id="title">Welcome</h1>
```

Notice the `#` symbol because IDs use the CSS ID selector.

---

# Example 2: Selecting an Element by Class

HTML

```html
<p class="note">Learning JavaScript</p>
```

JavaScript

```javascript
const note = document.querySelector(".note");

console.log(note);
```

Output

```html
<p class="note">Learning JavaScript</p>
```

Classes use the `.` symbol.

---

# Example 3: Selecting by Tag Name

HTML

```html
<p>First Paragraph</p>

<p>Second Paragraph</p>
```

JavaScript

```javascript
const paragraph = document.querySelector("p");

console.log(paragraph);
```

Output

```html
<p>First Paragraph</p>
```

Only the **first** matching paragraph is returned.

---

## Figure 10.21

**querySelector()**

```text
HTML

p

p

p

↓

querySelector("p")

↓

First p only
```

---

# The `querySelectorAll()` Method

Unlike `querySelector()`, the `querySelectorAll()` method returns **all matching elements**.

### Syntax

```javascript
document.querySelectorAll("selector");
```

---

# Example 4: Selecting All Paragraphs

HTML

```html
<p>HTML</p>

<p>CSS</p>

<p>JavaScript</p>
```

JavaScript

```javascript
const paragraphs = document.querySelectorAll("p");

console.log(paragraphs);
```

Output

```text
NodeList(3)
```

---

# What Is a NodeList?

`querySelectorAll()` returns a **NodeList**.

A NodeList is a collection of matching DOM nodes.

Example

```text
paragraphs

├── paragraphs[0]

├── paragraphs[1]

└── paragraphs[2]
```

---

# Accessing Individual Elements

```javascript
const paragraphs = document.querySelectorAll("p");

console.log(paragraphs[1]);
```

Output

```html
<p>CSS</p>
```

---

# Looping Through a NodeList

One advantage of a NodeList is that it supports the `forEach()` method.

```javascript
const paragraphs = document.querySelectorAll("p");

paragraphs.forEach(function (paragraph) {

    console.log(paragraph.textContent);

});
```

Output

```text
HTML

CSS

JavaScript
```

---

# Example 5: Selecting All Buttons

HTML

```html
<button>Save</button>

<button>Edit</button>

<button>Delete</button>
```

JavaScript

```javascript
const buttons = document.querySelectorAll("button");

console.log(buttons.length);
```

Output

```text
3
```

---

# Using Complex CSS Selectors

One of the greatest advantages of `querySelector()` is that it supports complex selectors.

HTML

```html
<div class="card">

    <h2>JavaScript</h2>

</div>
```

JavaScript

```javascript
const heading = document.querySelector(".card h2");

console.log(heading);
```

This selects the `<h2>` inside the `.card` element.

---

## Figure 10.22

**Nested CSS Selector**

```text
.card

│

└── h2

↓

querySelector(".card h2")
```

---

# Selecting Checked Inputs

HTML

```html
<input type="checkbox" checked>
```

JavaScript

```javascript
const checkbox = document.querySelector("input:checked");
```

This demonstrates how CSS pseudo-classes can also be used.

---

# `querySelector()` vs `querySelectorAll()`

| Feature | `querySelector()` | `querySelectorAll()` |
|---------|-------------------|----------------------|
| Returns | First matching element | All matching elements |
| Return Type | Element | NodeList |
| CSS Selectors | Yes | Yes |

---

# `HTMLCollection` vs `NodeList`

| Feature | HTMLCollection | NodeList |
|---------|----------------|----------|
| Returned By | `getElementsBy...()` | `querySelectorAll()` |
| Supports `forEach()` | No | Yes |
| Indexed Access | Yes | Yes |
| `length` Property | Yes | Yes |

---

# Real-World Uses

Developers commonly use `querySelector()` to:

- Select navigation menus.
- Access login forms.
- Modify buttons.
- Update headings.
- Change images.
- Handle modal windows.
- Manipulate cards and components.

---

# Best Practices

- Use `querySelector()` when you only need one element.
- Use `querySelectorAll()` when you need multiple elements.
- Use meaningful CSS selectors.
- Store selected elements in variables.
- Keep selectors as simple as possible.

---

# Common Beginner Mistakes

## Mistake 1: Forgetting CSS Selector Symbols

Incorrect

```javascript
document.querySelector("title");
```

Correct

```javascript
document.querySelector("#title");
```

---

## Mistake 2: Expecting `querySelector()` to Return Multiple Elements

```javascript
document.querySelector("p");
```

returns only the **first** paragraph.

---

## Mistake 3: Forgetting to Loop Through a NodeList

```javascript
const paragraphs = document.querySelectorAll("p");

paragraphs.forEach((paragraph) => {

    console.log(paragraph.textContent);

});
```

---

# Why Modern Developers Prefer These Methods

`querySelector()` and `querySelectorAll()` combine the power of CSS selectors with JavaScript.

Instead of remembering many different selection methods, developers can use one consistent approach for selecting almost any element in the DOM.

Because of their flexibility and readability, these methods are the preferred choice in many modern JavaScript projects.

---

# Section Summary

In this section, you learned how to use `querySelector()` and `querySelectorAll()` to select HTML elements with CSS selectors. You learned the difference between selecting a single element and multiple elements, how to work with a NodeList, how to loop through selected elements, and why these methods are widely used in modern web development.

---

# CodeTales Insight

> **If you already know CSS selectors, you've already learned half of modern DOM selection. `querySelector()` and `querySelectorAll()` let you use that same knowledge in JavaScript, making your code cleaner, more expressive, and easier to maintain. These two methods will become some of the most frequently used tools in your JavaScript toolkit.**

---

# 10.8 Reading and Changing HTML Content

One of the most common tasks in DOM manipulation is reading and changing the content of HTML elements.

Imagine clicking a button that changes a heading, updates a score, displays a welcome message, or loads new information from a server. These actions all involve modifying the contents of HTML elements.

JavaScript provides three commonly used properties for working with HTML content:

- `textContent`
- `innerText`
- `innerHTML`

Although they appear similar, each serves a different purpose.

---

# Reading Text Content

Consider the following HTML.

```html
<h1 id="title">
    Welcome to CodeTales Africa
</h1>
```

JavaScript

```javascript
const heading = document.getElementById("title");

console.log(heading.textContent);
```

Output

```text
Welcome to CodeTales Africa
```

The `textContent` property returns the text inside the element.

---

## Figure 10.23

**Reading Text Content**

```text
HTML Element

↓

textContent

↓

Text Returned
```

---

# Changing Text Content

The `textContent` property can also change the text inside an element.

HTML

```html
<h1 id="title">
    Welcome
</h1>
```

JavaScript

```javascript
const heading = document.getElementById("title");

heading.textContent = "Welcome to Cracking JavaScript!";
```

Updated HTML

```html
<h1 id="title">
    Welcome to Cracking JavaScript!
</h1>
```

The browser updates the page immediately.

---

# Using `innerText`

The `innerText` property is similar to `textContent`.

Example

```javascript
const heading = document.getElementById("title");

console.log(heading.innerText);
```

Output

```text
Welcome to Cracking JavaScript!
```

Like `textContent`, it can also change text.

```javascript
heading.innerText = "Learning DOM";
```

---

# `textContent` vs `innerText`

Although these properties often return similar results, they behave differently.

| `textContent` | `innerText` |
|---------------|-------------|
| Returns all text inside an element | Returns only visible text |
| Ignores CSS styling | Respects CSS visibility |
| Faster | Slightly slower because it considers layout |

In most situations, `textContent` is the preferred choice when you simply need to read or update text.

---

# Using `innerHTML`

The `innerHTML` property reads or changes the HTML inside an element.

HTML

```html
<div id="content">

    <p>Hello World</p>

</div>
```

JavaScript

```javascript
const content = document.getElementById("content");

console.log(content.innerHTML);
```

Output

```html
<p>Hello World</p>
```

Unlike `textContent`, `innerHTML` includes HTML tags.

---

# Changing HTML

Suppose you want to replace the paragraph with a heading.

```javascript
content.innerHTML = "<h2>JavaScript DOM</h2>";
```

The browser updates the page to:

```html
<div id="content">

    <h2>JavaScript DOM</h2>

</div>
```

---

## Figure 10.24

**Using `innerHTML`**

```text
Old HTML

↓

innerHTML

↓

New HTML
```

---

# Adding HTML Dynamically

You can insert multiple elements.

```javascript
content.innerHTML = `
    <h2>Courses</h2>

    <ul>
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
    </ul>
`;
```

The browser creates the new elements automatically.

---

# Practical Example

HTML

```html
<p id="message">
    Loading...
</p>
```

JavaScript

```javascript
const message = document.getElementById("message");

message.textContent = "Data loaded successfully.";
```

The displayed message changes immediately without refreshing the page.

---

# Another Example

HTML

```html
<div id="result">

</div>
```

JavaScript

```javascript
const result = document.getElementById("result");

result.innerHTML = `
    <h3>Login Successful</h3>

    <p>Welcome back!</p>
`;
```

---

# Choosing the Right Property

| Property | Best Used For |
|----------|---------------|
| `textContent` | Reading or changing plain text |
| `innerText` | Reading visible text only |
| `innerHTML` | Reading or inserting HTML markup |

---

# Security Considerations

Be careful when using `innerHTML`.

If you insert HTML that comes directly from an untrusted source (such as user input), malicious code could be executed in the browser.

For example:

```javascript
content.innerHTML = userInput;
```

If `userInput` contains harmful HTML or JavaScript, it may create a security vulnerability.

Whenever you only need to display text, prefer:

```javascript
textContent
```

instead of:

```javascript
innerHTML
```

---

# Best Practices

- Use `textContent` for plain text.
- Use `innerHTML` only when you intentionally need to insert HTML.
- Avoid inserting untrusted content with `innerHTML`.
- Keep your HTML readable and properly indented.

---

# Common Beginner Mistakes

## Mistake 1: Using `innerHTML` for Plain Text

Incorrect

```javascript
heading.innerHTML = "Welcome";
```

Better

```javascript
heading.textContent = "Welcome";
```

---

## Mistake 2: Forgetting That `innerHTML` Replaces Existing Content

```javascript
content.innerHTML = "<p>New Content</p>";
```

The old content is completely removed.

---

## Mistake 3: Confusing Text with HTML

```javascript
heading.textContent = "<strong>Hello</strong>";
```

Output

```text
<strong>Hello</strong>
```

The tags are displayed as text.

To render the tags as HTML:

```javascript
heading.innerHTML = "<strong>Hello</strong>";
```

---

# Section Summary

In this section, you learned how to read and change the content of HTML elements using `textContent`, `innerText`, and `innerHTML`. You learned the differences between these properties, when to use each one, and why `textContent` is generally safer for displaying plain text while `innerHTML` should be reserved for situations where HTML markup needs to be inserted.

---

# CodeTales Insight

> **A professional developer chooses the simplest tool that solves the problem. If you're only displaying text, use `textContent`. Reserve `innerHTML` for cases where you truly need to generate HTML. Making this distinction leads to safer, faster, and more maintainable web applications.**

---

# 10.9 Working with Text Content

Displaying information on a web page is only part of what JavaScript can do. Modern web applications constantly update text in response to user actions.

For example:

- A shopping cart displays the number of selected items.
- A banking application updates an account balance.
- A quiz displays the player's current score.
- A weather application updates the current temperature.
- A social media platform displays new notifications.

These updates are made by changing the text content of HTML elements.

In this section, you will learn practical techniques for reading, updating, appending, clearing, and formatting text using JavaScript.

---

# Reading Text

HTML

```html
<p id="message">
Welcome to CodeTales Africa.
</p>
```

JavaScript

```javascript
const message = document.getElementById("message");

console.log(message.textContent);
```

Output

```text
Welcome to CodeTales Africa.
```

---

# Updating Text

You can replace existing text.

HTML

```html
<p id="status">
Loading...
</p>
```

JavaScript

```javascript
const status = document.getElementById("status");

status.textContent = "Loading complete.";
```

The paragraph immediately changes to:

```text
Loading complete.
```

---

## Figure 10.25

**Updating Text**

```text
Before

Loading...

↓

JavaScript

↓

After

Loading complete.
```

---

# Appending Text

Sometimes you want to add new text without replacing the existing content.

HTML

```html
<p id="course">
JavaScript
</p>
```

JavaScript

```javascript
const course = document.getElementById("course");

course.textContent += " Fundamentals";
```

Output

```text
JavaScript Fundamentals
```

The `+=` operator appends additional text.

---

# Clearing Text

To remove all text from an element, assign an empty string.

HTML

```html
<p id="notification">
You have 5 new messages.
</p>
```

JavaScript

```javascript
const notification = document.getElementById("notification");

notification.textContent = "";
```

The paragraph becomes empty.

---

# Updating Multiple Elements

HTML

```html
<p class="student">Alice</p>

<p class="student">David</p>

<p class="student">Grace</p>
```

JavaScript

```javascript
const students = document.querySelectorAll(".student");

students.forEach((student) => {

    student.textContent += " ✓";

});
```

Output

```text
Alice ✓

David ✓

Grace ✓
```

---

# Combining Variables with Text

JavaScript often combines variables and text using template literals.

HTML

```html
<p id="score"></p>
```

JavaScript

```javascript
const playerName = "Chidozie";

const score = 95;

const result = document.getElementById("score");

result.textContent = `${playerName} scored ${score} marks.`;
```

Output

```text
Chidozie scored 95 marks.
```

---

# Displaying Dynamic Messages

HTML

```html
<h2 id="welcome"></h2>
```

JavaScript

```javascript
const username = "Harrison";

const heading = document.getElementById("welcome");

heading.textContent = `Welcome, ${username}!`;
```

Output

```text
Welcome, Harrison!
```

---

# Working with Numbers

JavaScript automatically converts numbers to text when assigning them to `textContent`.

HTML

```html
<p id="counter"></p>
```

JavaScript

```javascript
let count = 10;

document.getElementById("counter").textContent = count;
```

Output

```text
10
```

---

# Updating a Counter

```javascript
let count = 0;

const counter = document.getElementById("counter");

count++;

counter.textContent = count;
```

Output

```text
1
```

This technique is commonly used in:

- Counters
- Shopping carts
- Notification badges
- Quiz scores
- Timers

---

## Figure 10.26

**Counter Update**

```text
0

↓

Button Click

↓

1

↓

Button Click

↓

2
```

---

# Formatting Text

JavaScript string methods work well with `textContent`.

Example

```javascript
const name = "javascript";

document.getElementById("title").textContent =
name.toUpperCase();
```

Output

```text
JAVASCRIPT
```

Another example

```javascript
const language = "JAVASCRIPT";

document.getElementById("title").textContent =
language.toLowerCase();
```

Output

```text
javascript
```

---

# Removing Extra Spaces

```javascript
const input = "   JavaScript   ";

document.getElementById("output").textContent =
input.trim();
```

Output

```text
JavaScript
```

---

# Real-World Example

Suppose a student logs into an online learning platform.

HTML

```html
<h1 id="dashboard"></h1>
```

JavaScript

```javascript
const studentName = "Grace";

document.getElementById("dashboard").textContent =
`Welcome back, ${studentName}!`;
```

Output

```text
Welcome back, Grace!
```

---

# Best Practices

- Use `textContent` for plain text updates.
- Use template literals for combining text and variables.
- Keep displayed messages short and meaningful.
- Use descriptive variable names.
- Update only the elements that need changing.

---

# Common Beginner Mistakes

## Mistake 1: Forgetting Template Literal Syntax

Incorrect

```javascript
"Welcome ${name}"
```

Correct

```javascript
`Welcome ${name}`
```

Template literals use backticks (`` ` ``), not quotation marks.

---

## Mistake 2: Replacing Instead of Appending

Incorrect

```javascript
message.textContent = "World";
```

This replaces the original text.

To append:

```javascript
message.textContent += " World";
```

---

## Mistake 3: Using `innerHTML` for Plain Text

If you are only displaying text, prefer:

```javascript
textContent
```

instead of:

```javascript
innerHTML
```

---

# Section Summary

In this section, you learned practical techniques for working with text content in the DOM. You learned how to read, update, append, and clear text, combine variables with template literals, display dynamic messages, work with numbers, and format text using JavaScript string methods.

These skills form the basis of many interactive web applications, from scoreboards and dashboards to shopping carts and notification systems.

---

# CodeTales Insight

> **Every interactive website communicates with users through text. Whether you're displaying a welcome message, updating a score, or showing a notification, mastering text manipulation allows you to create web pages that respond naturally to user actions and provide meaningful feedback.**

---

# 10.10 Modifying HTML Attributes

HTML elements contain **attributes** that provide additional information about the element.

For example:

- An image has a `src` attribute.
- A link has an `href` attribute.
- A text box has a `placeholder` attribute.
- A button may have a `disabled` attribute.
- An input checkbox may have a `checked` attribute.

JavaScript allows you to read, change, add, and remove these attributes dynamically.

This ability is essential for building modern interactive websites.

---

# What Is an HTML Attribute?

An attribute is additional information placed inside an HTML tag.

Example:

```html
<img

src="logo.png"

alt="Company Logo">
```

Here:

- `src` is an attribute.
- `alt` is another attribute.

---

## Figure 10.27

**HTML Attributes**

```text
<img

src="logo.png"

alt="Company Logo">

│

├── src

└── alt
```

---

# Reading an Attribute

Use the `getAttribute()` method.

HTML

```html
<img

id="logo"

src="logo.png"

alt="Company Logo">
```

JavaScript

```javascript
const logo = document.getElementById("logo");

console.log(logo.getAttribute("src"));
```

Output

```text
logo.png
```

---

# Reading Another Attribute

```javascript
console.log(logo.getAttribute("alt"));
```

Output

```text
Company Logo
```

---

# Changing an Attribute

Use the `setAttribute()` method.

Syntax

```javascript
element.setAttribute("attribute", "value");
```

Example

```javascript
logo.setAttribute("src", "new-logo.png");
```

Updated HTML

```html
<img

id="logo"

src="new-logo.png"

alt="Company Logo">
```

---

# Changing Multiple Attributes

```javascript
logo.setAttribute("src", "profile.jpg");

logo.setAttribute("alt", "Profile Picture");
```

---

## Figure 10.28

**Updating an Attribute**

```text
Old Value

↓

setAttribute()

↓

New Value
```

---

# Modifying Links

HTML

```html
<a

id="website"

href="https://example.com">

Visit Website

</a>
```

JavaScript

```javascript
const link = document.getElementById("website");

link.setAttribute("href", "https://codetales.africa");
```

The link now points to the new website.

---

# Working with Input Fields

HTML

```html
<input

id="username"

placeholder="Enter your username">
```

JavaScript

```javascript
const input = document.getElementById("username");

input.setAttribute("placeholder", "Enter your full name");
```

---

# Working with Images

HTML

```html
<img

id="photo"

src="student.jpg"

alt="Student">
```

JavaScript

```javascript
const photo = document.getElementById("photo");

photo.setAttribute("src", "teacher.jpg");
```

The displayed image changes immediately.

---

# Removing an Attribute

Use the `removeAttribute()` method.

Example

```javascript
input.removeAttribute("placeholder");
```

The placeholder attribute is removed.

---

# Checking Whether an Attribute Exists

Use the `hasAttribute()` method.

Example

```javascript
if (photo.hasAttribute("src")) {

    console.log("Image found.");

}
```

Output

```text
Image found.
```

---

# Working with Boolean Attributes

Some attributes are either present or absent.

Examples include:

- `disabled`
- `checked`
- `required`
- `readonly`

Example

```html
<button

id="save"

disabled>

Save

</button>
```

Enable the button.

```javascript
const button = document.getElementById("save");

button.removeAttribute("disabled");
```

The button becomes clickable.

---

# Another Example

Disable the button again.

```javascript
button.setAttribute("disabled", "");
```

---

# Using Properties Instead of Methods

Many common attributes can also be accessed as properties.

Example

```javascript
const image = document.getElementById("photo");

image.src = "banner.jpg";

image.alt = "Banner Image";
```

This is often shorter and easier to read than using `setAttribute()`.

---

# Real-World Example

Imagine a website that switches between a light and dark theme.

HTML

```html
<img

id="themeIcon"

src="sun.png"

alt="Light Mode">
```

JavaScript

```javascript
const icon = document.getElementById("themeIcon");

icon.setAttribute("src", "moon.png");

icon.setAttribute("alt", "Dark Mode");
```

The icon updates instantly when the theme changes.

---

# Commonly Modified Attributes

| Element | Common Attributes |
|----------|-------------------|
| `<img>` | `src`, `alt`, `width`, `height` |
| `<a>` | `href`, `target` |
| `<input>` | `value`, `placeholder`, `required`, `checked` |
| `<button>` | `disabled` |
| `<form>` | `action`, `method` |

---

# Best Practices

- Use meaningful attribute values.
- Prefer element properties (`element.src`, `element.href`) for common attributes when appropriate.
- Remove unnecessary attributes instead of leaving unused values.
- Validate user input before assigning attribute values.

---

# Common Beginner Mistakes

## Mistake 1: Misspelling Attribute Names

Incorrect

```javascript
image.setAttribute("scr", "logo.png");
```

Correct

```javascript
image.setAttribute("src", "logo.png");
```

---

## Mistake 2: Forgetting That `getAttribute()` Returns a String

```javascript
const value = input.getAttribute("maxlength");
```

The returned value is a string.

Convert it if you need a number.

---

## Mistake 3: Using `setAttribute()` for Everything

Although `setAttribute()` works well, many common attributes can be modified more naturally using properties.

Example

```javascript
image.src = "banner.jpg";

link.href = "https://example.com";

input.value = "JavaScript";
```

These property assignments are common in modern JavaScript.

---

# Section Summary

In this section, you learned how to work with HTML attributes using JavaScript. You explored how to read attributes with `getAttribute()`, update them with `setAttribute()`, remove them with `removeAttribute()`, check for their existence using `hasAttribute()`, and modify common attributes through element properties.

These techniques are essential for creating dynamic interfaces that update images, links, forms, and other HTML elements in response to user interaction.

---

# CodeTales Insight

> **Attributes define the behavior of HTML elements, and JavaScript gives you the power to change those behaviors instantly. Whether you're updating an image, enabling a button, or changing a form field, attribute manipulation is a core skill you'll use in almost every web application you build.**

---

# 10.11 Changing CSS Styles with JavaScript

One of JavaScript's greatest strengths is its ability to change the appearance of a web page while it is running.

For example, JavaScript can:

- Change text colors.
- Change background colors.
- Increase or decrease font sizes.
- Show or hide elements.
- Move elements.
- Add borders and shadows.
- Change layouts dynamically.

These visual changes make websites more interactive and responsive to user actions.

---

# The `style` Property

Every HTML element has a `style` property.

The `style` property allows JavaScript to modify an element's inline CSS.

Syntax

```javascript
element.style.property = "value";
```

Example

```javascript
heading.style.color = "blue";
```

---

# Changing Text Color

HTML

```html
<h1 id="title">
Welcome
</h1>
```

JavaScript

```javascript
const heading = document.getElementById("title");

heading.style.color = "blue";
```

Result

The heading text becomes blue.

---

## Figure 10.29

**Changing Text Color**

```text
Before

Black Text

↓

JavaScript

↓

Blue Text
```

---

# Changing Background Color

HTML

```html
<div id="box">
Hello World
</div>
```

JavaScript

```javascript
const box = document.getElementById("box");

box.style.backgroundColor = "yellow";
```

Notice that CSS's `background-color` becomes `backgroundColor` in JavaScript.

---

# CSS Property Names in JavaScript

Many CSS property names contain hyphens.

JavaScript uses **camelCase** instead.

| CSS | JavaScript |
|------|------------|
| background-color | backgroundColor |
| font-size | fontSize |
| border-radius | borderRadius |
| margin-top | marginTop |
| padding-left | paddingLeft |

---

# Changing Font Size

HTML

```html
<p id="message">
Learning JavaScript
</p>
```

JavaScript

```javascript
const message = document.getElementById("message");

message.style.fontSize = "24px";
```

---

# Changing Font Weight

```javascript
message.style.fontWeight = "bold";
```

---

# Changing Font Family

```javascript
message.style.fontFamily = "Arial";
```

---

# Changing Multiple Styles

```javascript
message.style.color = "white";

message.style.backgroundColor = "green";

message.style.padding = "20px";

message.style.borderRadius = "10px";
```

The paragraph immediately adopts all four styles.

---

## Figure 10.30

**Applying Multiple Styles**

```text
Original Element

↓

JavaScript

↓

Color

Background

Padding

Rounded Corners
```

---

# Showing and Hiding Elements

HTML

```html
<p id="notice">
Registration Closed
</p>
```

Hide the element.

```javascript
const notice = document.getElementById("notice");

notice.style.display = "none";
```

The paragraph disappears.

Show it again.

```javascript
notice.style.display = "block";
```

---

# Changing Visibility

Invisible but still occupies space.

```javascript
notice.style.visibility = "hidden";
```

Visible again.

```javascript
notice.style.visibility = "visible";
```

---

# Changing Width and Height

HTML

```html
<div id="card"></div>
```

JavaScript

```javascript
const card = document.getElementById("card");

card.style.width = "300px";

card.style.height = "150px";
```

---

# Adding Borders

```javascript
card.style.border = "2px solid black";
```

---

# Adding Rounded Corners

```javascript
card.style.borderRadius = "12px";
```

---

# Adding Shadows

```javascript
card.style.boxShadow =
"0 4px 10px rgba(0,0,0,0.3)";
```

---

# Changing the Cursor

```javascript
button.style.cursor = "pointer";
```

---

# Changing Opacity

```javascript
card.style.opacity = "0.5";
```

Opacity values range from:

```text
0

↓

1
```

Where:

- 0 = completely transparent
- 1 = fully visible

---

# Practical Example

HTML

```html
<button id="changeTheme">

Dark Mode

</button>

<h1 id="heading">

CodeTales Africa

</h1>
```

JavaScript

```javascript
const heading =
document.getElementById("heading");

heading.style.color = "white";

heading.style.backgroundColor = "#1e293b";

heading.style.padding = "20px";
```

The heading immediately adopts a dark theme.

---

# Real-World Applications

Changing CSS styles with JavaScript is used in:

- Dark mode
- Navigation menus
- Image galleries
- Notifications
- Form validation
- Loading indicators
- Progress bars
- Interactive dashboards
- Games
- Animations

---

# Best Practices

- Use JavaScript to change styles dynamically.
- Keep most styling in CSS files.
- Use descriptive CSS class names.
- Avoid writing large amounts of inline styles.
- Prefer adding or removing CSS classes for complex styling.

> **Preview:** In a later section, you'll learn how to use `classList` to add, remove, and toggle CSS classes. This is the preferred approach for most real-world applications.

---

# Common Beginner Mistakes

## Mistake 1: Using Hyphens

Incorrect

```javascript
element.style.background-color =
"blue";
```

Correct

```javascript
element.style.backgroundColor =
"blue";
```

---

## Mistake 2: Forgetting Units

Incorrect

```javascript
element.style.width = 300;
```

Correct

```javascript
element.style.width = "300px";
```

Always include CSS units where required.

---

## Mistake 3: Replacing CSS Unnecessarily

Avoid writing dozens of style changes directly in JavaScript.

Instead, create CSS classes and let JavaScript switch between them.

---

# Inline Styles vs CSS Classes

| Inline Styles | CSS Classes |
|---------------|-------------|
| Good for quick, dynamic changes | Better for reusable styling |
| Written with `element.style` | Managed with CSS files |
| Can become difficult to maintain | Easier to organize and update |

For small changes, inline styles are acceptable. For larger projects, adding or removing CSS classes is the preferred approach.

---

# Section Summary

In this section, you learned how to change the appearance of HTML elements using JavaScript. You explored the `style` property, changed colors, fonts, backgrounds, borders, spacing, visibility, dimensions, opacity, and other CSS properties. You also learned why JavaScript uses camelCase for CSS property names and why CSS classes are generally preferred for managing larger sets of styles.

---

# CodeTales Insight

> **A great web application is not only functional—it is also visually engaging. JavaScript allows you to respond instantly to user actions by changing the appearance of a page. Mastering style manipulation helps you create interfaces that feel dynamic, polished, and professional.**

---

# 10.12 Creating HTML Elements

Until now, you have been working with HTML elements that already existed on the page.

However, modern web applications frequently create new elements while the application is running.

For example:

- A to-do list creates a new task.
- A shopping cart adds a new product.
- A chat application displays a new message.
- A social media platform adds a new comment.
- A notification system displays new alerts.

Instead of writing these elements directly in the HTML file, JavaScript creates them dynamically.

In this section, you will learn how to create new HTML elements using the DOM.

---

# The `createElement()` Method

JavaScript creates new elements using the `document.createElement()` method.

### Syntax

```javascript
document.createElement("tagName");
```

The method creates the element in memory, but it does **not** automatically display it on the web page.

---

# Example: Creating a Paragraph

```javascript
const paragraph = document.createElement("p");
```

A new `<p>` element has been created.

At this stage, it exists only in memory.

It is **not yet visible** in the browser.

---

## Figure 10.31

**Creating an Element**

```text
JavaScript

↓

createElement()

↓

New HTML Element (Memory)

↓

Not Yet Visible
```

---

# Adding Text to the Element

Once the element has been created, you can add text to it.

```javascript
const paragraph = document.createElement("p");

paragraph.textContent = "Welcome to CodeTales Africa!";
```

The paragraph now contains text, but it still has not been added to the document.

---

# Creating a Heading

```javascript
const heading = document.createElement("h2");

heading.textContent = "JavaScript DOM";
```

---

# Creating an Image

```javascript
const image = document.createElement("img");

image.src = "logo.png";

image.alt = "Company Logo";
```

Notice that common attributes such as `src` and `alt` can be assigned directly as properties.

---

# Creating a Button

```javascript
const button = document.createElement("button");

button.textContent = "Submit";
```

---

# Creating a List Item

```javascript
const item = document.createElement("li");

item.textContent = "Learn JavaScript";
```

---

# Creating Multiple Elements

You can create as many elements as needed.

```javascript
const heading = document.createElement("h2");

const paragraph = document.createElement("p");

const button = document.createElement("button");
```

Each element exists independently until it is added to the page.

---

## Figure 10.32

**Multiple Elements in Memory**

```text
Memory

├── h2

├── p

└── button
```

---

# Creating Nested Elements

You can create parent and child elements separately.

```javascript
const card = document.createElement("div");

const title = document.createElement("h3");

const description = document.createElement("p");
```

Later, you will connect these elements to form a complete HTML structure.

---

# Practical Example

```javascript
const message = document.createElement("p");

message.textContent = "Registration Successful!";
```

At this point:

- The paragraph exists.
- It contains text.
- It is still **not visible** because it has not been inserted into the DOM.

---

# Real-World Example

Imagine a chat application.

Every time a user sends a message, JavaScript creates a new paragraph.

```javascript
const chatMessage = document.createElement("p");

chatMessage.textContent = "Hello everyone!";
```

The message has been created.

The next step will be inserting it into the chat window.

---

# Why Elements Are Created in Memory First

Creating elements in memory before displaying them provides several advantages.

You can:

- Add text.
- Set attributes.
- Apply styles.
- Attach event listeners.
- Organize child elements.

Only after everything is ready do you insert the completed element into the page.

This approach improves code organization and performance.

---

# Common Elements Created Dynamically

Developers frequently create:

- `<div>`
- `<p>`
- `<h1>` to `<h6>`
- `<button>`
- `<img>`
- `<input>`
- `<label>`
- `<li>`
- `<tr>`
- `<td>`
- `<section>`
- `<article>`

---

# Best Practices

- Create only the elements you need.
- Configure the element before inserting it into the document.
- Use meaningful variable names.
- Keep related code together for readability.

---

# Common Beginner Mistakes

## Mistake 1: Expecting the Element to Appear Automatically

```javascript
const heading = document.createElement("h1");
```

Creating an element does **not** display it on the page.

It must be inserted into the DOM.

---

## Mistake 2: Forgetting to Add Content

```javascript
const button = document.createElement("button");
```

An empty button is created.

Remember to add text or other content.

```javascript
button.textContent = "Click Me";
```

---

## Mistake 3: Creating Too Many Elements Unnecessarily

Avoid creating elements that your application never uses.

Only create elements when they are actually needed.

---

# Section Summary

In this section, you learned how to create new HTML elements using `document.createElement()`. You created headings, paragraphs, buttons, images, list items, and other elements, and learned that newly created elements exist in memory until they are inserted into the DOM.

Creating elements dynamically is a fundamental technique used in modern web applications to generate content on demand.

---

# CodeTales Insight

> **Think of `createElement()` as building a piece of furniture in a workshop. You assemble it, paint it, and inspect it before moving it into the house. Likewise, JavaScript lets you prepare an element completely in memory before placing it into the document, resulting in cleaner, more organized, and more efficient code.**

---

# 10.13 Appending and Inserting Elements

In the previous section, you learned how to create new HTML elements using `document.createElement()`.

However, creating an element does not automatically display it on the web page.

A newly created element exists only in memory until it is inserted into the Document Object Model (DOM).

In this section, you will learn how to insert new elements into the DOM using methods such as:

- `appendChild()`
- `append()`
- `prepend()`
- `before()`
- `after()`

These methods are widely used in modern web development.

---

# Appending an Element with `appendChild()`

The `appendChild()` method adds a new child element to the end of a parent element.

### Syntax

```javascript
parent.appendChild(child);
```

---

# Example 1: Appending a Paragraph

HTML

```html
<div id="container"></div>
```

JavaScript

```javascript
const container = document.getElementById("container");

const paragraph = document.createElement("p");

paragraph.textContent = "Welcome to Cracking JavaScript.";

container.appendChild(paragraph);
```

The browser displays:

```html
<div id="container">
    <p>Welcome to Cracking JavaScript.</p>
</div>
```

---

## Figure 10.33

**Appending a Child**

```text
Container

↓

appendChild()

↓

Container

└── Paragraph
```

---

# Appending Multiple Elements

```javascript
const list = document.getElementById("languages");

const html = document.createElement("li");
html.textContent = "HTML";

const css = document.createElement("li");
css.textContent = "CSS";

const js = document.createElement("li");
js.textContent = "JavaScript";

list.appendChild(html);
list.appendChild(css);
list.appendChild(js);
```

Result

```html
<ul id="languages">
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ul>
```

---

# Using `append()`

The `append()` method is similar to `appendChild()`, but it is more flexible.

It can append:

- Elements
- Text
- Multiple items at once

Example

```javascript
const container = document.getElementById("container");

container.append("Hello World");
```

You can also append multiple elements.

```javascript
container.append(paragraph, button);
```

---

# `appendChild()` vs `append()`

| appendChild() | append() |
|----------------|----------|
| Accepts one node | Accepts multiple nodes |
| Cannot append plain text directly | Can append text |
| Returns the appended node | Returns `undefined` |

For modern projects, `append()` is often more convenient.

---

# Using `prepend()`

The `prepend()` method inserts an element at the beginning of a parent element.

HTML

```html
<ul id="tasks">

<li>Study JavaScript</li>

</ul>
```

JavaScript

```javascript
const tasks = document.getElementById("tasks");

const item = document.createElement("li");

item.textContent = "Wake Up Early";

tasks.prepend(item);
```

Result

```html
<ul id="tasks">

<li>Wake Up Early</li>

<li>Study JavaScript</li>

</ul>
```

---

## Figure 10.34

**Prepend**

```text
Before

Task A

↓

prepend()

↓

New Task

Task A
```

---

# Using `before()`

The `before()` method inserts an element immediately before another element.

HTML

```html
<p id="second">
Second Paragraph
</p>
```

JavaScript

```javascript
const second = document.getElementById("second");

const first = document.createElement("p");

first.textContent = "First Paragraph";

second.before(first);
```

---

# Using `after()`

The `after()` method inserts an element immediately after another element.

```javascript
const third = document.createElement("p");

third.textContent = "Third Paragraph";

second.after(third);
```

Result

```html
<p>First Paragraph</p>

<p id="second">Second Paragraph</p>

<p>Third Paragraph</p>
```

---

## Figure 10.35

**before() and after()**

```text
Before()

New Element

↓

Existing Element

↓

after()

New Element
```

---

# Building a Card Dynamically

```javascript
const card = document.createElement("div");

const heading = document.createElement("h2");

const paragraph = document.createElement("p");

heading.textContent = "JavaScript";

paragraph.textContent =
"Learn DOM Manipulation.";

card.append(heading, paragraph);

document.body.appendChild(card);
```

This creates the following structure:

```html
<div>

<h2>JavaScript</h2>

<p>Learn DOM Manipulation.</p>

</div>
```

---

# Practical Example

Suppose a student submits a new assignment.

Instead of refreshing the page, JavaScript creates a new list item.

```javascript
const assignment =
document.createElement("li");

assignment.textContent =
"Complete Chapter 10";

document
.getElementById("assignments")
.appendChild(assignment);
```

The assignment immediately appears on the page.

---

# Real-World Applications

These insertion methods are used in:

- Shopping carts
- Chat applications
- To-do lists
- Social media feeds
- Notification systems
- Comment sections
- Dashboards
- Messaging applications

Every time new content appears without refreshing the page, JavaScript is inserting new DOM elements.

---

# Best Practices

- Configure elements before inserting them into the DOM.
- Use `append()` when you need to insert multiple items.
- Use `prepend()` when new content belongs at the top.
- Keep related insertion logic together for readability.

---

# Common Beginner Mistakes

## Mistake 1: Forgetting the Parent Element

Incorrect

```javascript
paragraph.appendChild(container);
```

Correct

```javascript
container.appendChild(paragraph);
```

The parent receives the child—not the other way around.

---

## Mistake 2: Trying to Append the Same Element Twice

A DOM element can exist in only one location at a time.

Appending it elsewhere moves it rather than creating a copy.

If you need another copy, create a new element or clone the existing one.

---

## Mistake 3: Forgetting to Create the Element

Incorrect

```javascript
container.appendChild(paragraph);
```

if `paragraph` has never been created.

Always create the element first.

```javascript
const paragraph =
document.createElement("p");
```

---

# Section Summary

In this section, you learned how to insert newly created elements into the DOM using `appendChild()`, `append()`, `prepend()`, `before()`, and `after()`. You also learned the differences between these methods, how to build nested HTML structures dynamically, and how modern web applications use these techniques to display new content without reloading the page.

---

# CodeTales Insight

> **Creating an element is only the first step. The real power of the DOM comes when you insert that element into the document at exactly the right place. Mastering insertion methods allows you to build dynamic interfaces that grow, change, and respond instantly to user actions—the hallmark of modern web applications.**

---

# 10.14 Replacing Elements

As users interact with a web application, there are times when an existing HTML element needs to be replaced with a different one.

For example:

- Replacing a "Loading..." message with actual content.
- Replacing a "Login" button with a "Logout" button.
- Updating an old notification with a new one.
- Replacing an image after uploading a new profile picture.
- Updating a product card after editing its details.

JavaScript provides several ways to replace elements in the DOM.

In this section, you will learn how to use:

- `replaceChild()`
- `replaceWith()`

---

# Why Replace Elements?

Sometimes modifying an element is not enough.

Instead of changing every property individually, it is often easier to create a new element and replace the old one.

This approach keeps your code simple and organized.

---

# The `replaceChild()` Method

The `replaceChild()` method replaces one child element with another.

### Syntax

```javascript
parent.replaceChild(newChild, oldChild);
```

Where:

- `parent` is the parent element.
- `newChild` is the new element.
- `oldChild` is the element to be replaced.

---

# Example 1: Replacing a Paragraph

HTML

```html
<div id="container">

    <p id="oldMessage">
        Loading...
    </p>

</div>
```

JavaScript

```javascript
const container =
document.getElementById("container");

const oldMessage =
document.getElementById("oldMessage");

const newMessage =
document.createElement("p");

newMessage.textContent =
"Data loaded successfully.";

container.replaceChild(newMessage, oldMessage);
```

Result

```html
<div id="container">

    <p>
        Data loaded successfully.
    </p>

</div>
```

---

## Figure 10.36

**Replacing a Child Element**

```text
Container

│

└── Old Paragraph

↓

replaceChild()

↓

Container

│

└── New Paragraph
```

---

# Replacing a Heading

HTML

```html
<h1 id="title">
Welcome
</h1>
```

JavaScript

```javascript
const title =
document.getElementById("title");

const heading =
document.createElement("h2");

heading.textContent =
"Welcome to Cracking JavaScript";

title.replaceWith(heading);
```

Result

```html
<h2>
Welcome to Cracking JavaScript
</h2>
```

---

# The `replaceWith()` Method

The `replaceWith()` method is a modern and simpler alternative.

### Syntax

```javascript
oldElement.replaceWith(newElement);
```

Unlike `replaceChild()`, you do not need to reference the parent element.

---

# Example 2: Replacing an Image

HTML

```html
<img

id="profile"

src="student.jpg"

alt="Student">
```

JavaScript

```javascript
const image =
document.getElementById("profile");

const newImage =
document.createElement("img");

newImage.src = "teacher.jpg";

newImage.alt = "Teacher";

image.replaceWith(newImage);
```

The old image is replaced immediately.

---

# Replacing a Button

HTML

```html
<button id="login">

Login

</button>
```

JavaScript

```javascript
const loginButton =
document.getElementById("login");

const logoutButton =
document.createElement("button");

logoutButton.textContent =
"Logout";

loginButton.replaceWith(logoutButton);
```

Result

```html
<button>

Logout

</button>
```

---

## Figure 10.37

**Replacing an Element**

```text
Old Button

↓

replaceWith()

↓

New Button
```

---

# Replacing an Entire Section

HTML

```html
<section id="news">

Loading news...

</section>
```

JavaScript

```javascript
const news =
document.getElementById("news");

const article =
document.createElement("article");

article.innerHTML = `
<h2>Breaking News</h2>

<p>JavaScript continues to dominate web development.</p>
`;

news.replaceWith(article);
```

The placeholder section is replaced with a complete article.

---

# Practical Example

Suppose a student submits an examination.

Before submission:

```text
Status:

Not Submitted
```

After clicking **Submit**:

```text
Status:

Submitted Successfully
```

Instead of updating every part of the original element, JavaScript creates a new status element and replaces the old one.

---

# Real-World Applications

Replacing elements is commonly used in:

- Loading screens
- Login/logout interfaces
- Notification systems
- Product updates
- User profile updates
- Online dashboards
- Single Page Applications (SPAs)
- Interactive forms

---

# `replaceChild()` vs `replaceWith()`

| `replaceChild()` | `replaceWith()` |
|------------------|-----------------|
| Requires the parent element | Does not require the parent element |
| Older DOM method | Modern DOM method |
| More verbose | Simpler and easier to read |

For most modern applications, `replaceWith()` is the preferred option because it is more concise.

---

# Best Practices

- Create and configure the new element before replacing the old one.
- Use meaningful variable names.
- Prefer `replaceWith()` when browser support meets your project's requirements.
- Test replacements to ensure the new element behaves as expected.

---

# Common Beginner Mistakes

## Mistake 1: Forgetting the Parent in `replaceChild()`

Incorrect

```javascript
oldElement.replaceChild(newElement);
```

Correct

```javascript
parent.replaceChild(newElement, oldElement);
```

---

## Mistake 2: Replacing an Element Before It Exists

Always make sure the element has been selected successfully.

```javascript
const element =
document.getElementById("message");
```

If `element` is `null`, replacement will fail.

---

## Mistake 3: Losing Event Listeners

When an element is replaced, any event listeners attached to the old element are removed with it.

If the new element should respond to user interactions, attach the necessary event listeners after creating or replacing it.

---

# Section Summary

In this section, you learned how to replace existing DOM elements using `replaceChild()` and `replaceWith()`. You discovered the differences between these methods, learned how to replace headings, images, buttons, and sections, and explored practical situations where replacing elements is more effective than modifying them individually.

Replacing elements is an important technique for building responsive and dynamic web interfaces.

---

# CodeTales Insight

> **Professional developers don't just change content—they redesign interfaces on the fly. Replacing elements allows you to swap outdated content for new components quickly and cleanly, making your applications feel responsive and modern without requiring a page refresh.**

---

# 10.15 Removing Elements

In many web applications, elements do not remain on the page forever.

For example:

- A completed task is removed from a to-do list.
- A product is removed from a shopping cart.
- A notification disappears after being read.
- A chat message is deleted.
- An advertisement is closed.
- A temporary loading message disappears after data has loaded.

JavaScript allows you to remove HTML elements from the Document Object Model (DOM) dynamically.

In this section, you will learn how to remove elements using:

- `remove()`
- `removeChild()`

---

# Why Remove Elements?

Removing unnecessary elements keeps a web page clean and improves the user experience.

Instead of hiding elements with CSS, removing them completely deletes them from the DOM.

Once removed, they no longer occupy space on the page.

---

# The `remove()` Method

The easiest way to remove an element is by using the `remove()` method.

### Syntax

```javascript
element.remove();
```

---

# Example 1: Removing a Paragraph

HTML

```html
<p id="message">
This message will disappear.
</p>
```

JavaScript

```javascript
const message =
document.getElementById("message");

message.remove();
```

Result

The paragraph is completely removed from the page.

---

## Figure 10.38

**Removing an Element**

```text
Before

Paragraph

↓

remove()

↓

Paragraph Deleted
```

---

# Removing a Button

HTML

```html
<button id="deleteButton">

Delete

</button>
```

JavaScript

```javascript
const button =
document.getElementById("deleteButton");

button.remove();
```

The button disappears immediately.

---

# Removing an Image

HTML

```html
<img

id="photo"

src="student.jpg"

alt="Student">
```

JavaScript

```javascript
const image =
document.getElementById("photo");

image.remove();
```

The image is removed from the document.

---

# The `removeChild()` Method

Older JavaScript code commonly uses the `removeChild()` method.

Unlike `remove()`, it must be called on the parent element.

### Syntax

```javascript
parent.removeChild(child);
```

---

# Example 2: Removing a List Item

HTML

```html
<ul id="languages">

    <li id="html">HTML</li>

    <li>CSS</li>

    <li>JavaScript</li>

</ul>
```

JavaScript

```javascript
const list =
document.getElementById("languages");

const html =
document.getElementById("html");

list.removeChild(html);
```

Result

```html
<ul id="languages">

    <li>CSS</li>

    <li>JavaScript</li>

</ul>
```

---

## Figure 10.39

**Removing a Child Element**

```text
Parent

├── HTML

├── CSS

└── JavaScript

↓

removeChild()

↓

Parent

├── CSS

└── JavaScript
```

---

# Removing the Last Child

JavaScript provides useful properties such as:

```javascript
parent.lastElementChild
```

Example

```javascript
const list =
document.getElementById("languages");

list.lastElementChild.remove();
```

The last list item is removed.

---

# Removing the First Child

```javascript
list.firstElementChild.remove();
```

The first list item disappears.

---

# Removing All Child Elements

Suppose you want to clear an entire container.

HTML

```html
<div id="container">

    <p>HTML</p>

    <p>CSS</p>

    <p>JavaScript</p>

</div>
```

JavaScript

```javascript
const container =
document.getElementById("container");

while (container.firstChild) {

    container.removeChild(container.firstChild);

}
```

Result

```html
<div id="container"></div>
```

The container remains, but all of its child elements have been removed.

---

# Practical Example

Imagine a notification system.

HTML

```html
<div id="notification">

Assignment Submitted Successfully

</div>
```

JavaScript

```javascript
const notification =
document.getElementById("notification");

notification.remove();
```

The notification disappears after the action is complete.

---

# Real-World Example

Consider a shopping cart.

HTML

```html
<li id="item1">

Wireless Mouse

</li>
```

When the user clicks **Remove**, JavaScript executes:

```javascript
document.getElementById("item1").remove();
```

The product is instantly removed from the shopping cart.

---

# `remove()` vs `removeChild()`

| `remove()` | `removeChild()` |
|-------------|-----------------|
| Called on the element itself | Called on the parent element |
| Simpler | Slightly more verbose |
| Modern DOM method | Older DOM method |
| Preferred for modern projects | Still useful when working with older code |

---

# Real-World Applications

Removing elements is commonly used in:

- Shopping carts
- To-do lists
- Chat applications
- Notification systems
- Email clients
- Online dashboards
- Dynamic forms
- Single Page Applications (SPAs)

---

# Best Practices

- Confirm that an element exists before removing it.
- Remove only elements that are no longer needed.
- Prefer `remove()` for modern JavaScript projects.
- Be careful when removing parent elements because all of their children are removed as well.

---

# Common Beginner Mistakes

## Mistake 1: Removing an Element That Does Not Exist

Incorrect

```javascript
const item =
document.getElementById("missing");

item.remove();
```

If `item` is `null`, an error occurs.

Safer approach

```javascript
if (item) {

    item.remove();

}
```

---

## Mistake 2: Forgetting the Parent

Incorrect

```javascript
child.removeChild(parent);
```

Correct

```javascript
parent.removeChild(child);
```

---

## Mistake 3: Confusing `remove()` with Hiding

```javascript
element.style.display = "none";
```

This hides the element.

```javascript
element.remove();
```

This completely removes it from the DOM.

Choose the method that best matches your application's needs.

---

# Section Summary

In this section, you learned how to remove HTML elements dynamically using `remove()` and `removeChild()`. You explored the differences between these methods, learned how to remove individual elements and child elements, clear entire containers, and apply these techniques to real-world scenarios such as shopping carts, notifications, and task management applications.

---

# CodeTales Insight

> **Adding and removing elements are two sides of the same coin. Great web applications continuously create, update, and remove content to reflect the current state of the application. Mastering element removal allows you to build cleaner, faster, and more responsive user interfaces that feel natural to users.**

---

# 10.16 Navigating the DOM Tree

The Document Object Model (DOM) is organized as a tree.

Every HTML element is connected to other elements through parent-child and sibling relationships.

Instead of searching the entire document repeatedly, JavaScript allows you to move directly between related elements.

This process is called **DOM navigation**.

DOM navigation is one of the most important skills in JavaScript because it allows you to efficiently locate and manipulate elements.

---

# Understanding DOM Relationships

Consider the following HTML.

```html
<div id="container">

    <h2>Programming Languages</h2>

    <ul>

        <li>HTML</li>

        <li>CSS</li>

        <li>JavaScript</li>

    </ul>

</div>
```

The DOM tree looks like this:

```text
div

├── h2

└── ul

    ├── li

    ├── li

    └── li
```

Each node has relationships with the others.

---

## Figure 10.40

**Parent–Child Relationships**

```text
          div
         /   \
      h2      ul
             / | \
           li li li
```

---

# Getting the Parent Element

Every element knows its parent.

Use the `parentElement` property.

```javascript
const list =
document.querySelector("ul");

console.log(list.parentElement);
```

Output

```html
<div id="container">
...
</div>
```

---

# Getting Child Elements

Use the `children` property.

```javascript
const container =
document.getElementById("container");

console.log(container.children);
```

Output

```text
HTMLCollection(2)
```

The collection contains:

- `<h2>`
- `<ul>`

---

# Accessing Individual Children

```javascript
const container =
document.getElementById("container");

console.log(container.children[0]);
```

Output

```html
<h2>Programming Languages</h2>
```

---

# Getting the First Child Element

```javascript
const container =
document.getElementById("container");

console.log(container.firstElementChild);
```

Output

```html
<h2>Programming Languages</h2>
```

---

# Getting the Last Child Element

```javascript
console.log(container.lastElementChild);
```

Output

```html
<ul>...</ul>
```

---

## Figure 10.41

**First and Last Child**

```text
Container

├── First Child

│

└── Last Child
```

---

# Navigating to the Next Sibling

Every element can access its next sibling.

HTML

```html
<li>HTML</li>

<li>CSS</li>

<li>JavaScript</li>
```

JavaScript

```javascript
const first =
document.querySelector("li");

console.log(first.nextElementSibling);
```

Output

```html
<li>CSS</li>
```

---

# Navigating to the Previous Sibling

```javascript
const second =
first.nextElementSibling;

console.log(second.previousElementSibling);
```

Output

```html
<li>HTML</li>
```

---

## Figure 10.42

**Sibling Navigation**

```text
HTML

↓

nextElementSibling

↓

CSS

↓

nextElementSibling

↓

JavaScript
```

---

# Finding All Child Elements

```javascript
const list =
document.querySelector("ul");

for (const item of list.children) {

    console.log(item.textContent);

}
```

Output

```text
HTML

CSS

JavaScript
```

---

# Navigating Up the Tree

Suppose you select a list item.

```javascript
const item =
document.querySelector("li");
```

Its parent is:

```javascript
item.parentElement
```

Its grandparent is:

```javascript
item.parentElement.parentElement
```

This eventually reaches:

```html
<div id="container">
```

---

# Practical Example

HTML

```html
<div class="card">

    <h3>JavaScript</h3>

    <button>Delete</button>

</div>
```

Suppose the user clicks the button.

```javascript
const button =
document.querySelector("button");

const card =
button.parentElement;

card.remove();
```

Instead of searching for the card again, JavaScript simply moves up to the parent element.

This technique is extremely common in web applications.

---

# Real-World Example

Imagine a shopping cart.

```text
Shopping Cart

├── Product

│   ├── Name

│   ├── Price

│   └── Remove Button
```

When the user clicks **Remove**, JavaScript can locate the product card using:

```javascript
button.parentElement.remove();
```

No additional search is required.

---

# Useful Navigation Properties

| Property | Description |
|----------|-------------|
| `parentElement` | Parent element |
| `children` | All child elements |
| `firstElementChild` | First child |
| `lastElementChild` | Last child |
| `nextElementSibling` | Next sibling |
| `previousElementSibling` | Previous sibling |

These are among the most frequently used DOM navigation properties.

---

# `children` vs `childNodes`

| `children` | `childNodes` |
|------------|--------------|
| Returns only HTML elements | Returns all nodes |
| Ignores text nodes | Includes whitespace and text nodes |
| Preferred in most cases | Used when every node matters |

Most developers prefer `children` because it avoids whitespace nodes.

---

# Best Practices

- Use navigation properties before searching the entire document.
- Prefer `children` instead of `childNodes` unless text nodes are required.
- Use descriptive variable names such as `parent`, `card`, and `list`.
- Check that related elements exist before accessing them.

---

# Common Beginner Mistakes

## Mistake 1: Confusing Parent with Child

Incorrect

```javascript
parent.children.parentElement
```

Remember:

- `parentElement` moves upward.
- `children` moves downward.

---

## Mistake 2: Forgetting That `children` Returns a Collection

Incorrect

```javascript
container.children.textContent
```

Correct

```javascript
container.children[0].textContent
```

---

## Mistake 3: Using `nextElementSibling` Without Checking

Incorrect

```javascript
lastItem.nextElementSibling.textContent
```

The last element has no next sibling.

Safer approach

```javascript
if (lastItem.nextElementSibling) {

    console.log(lastItem.nextElementSibling);

}
```

---

# Section Summary

In this section, you learned how to navigate the DOM tree using `parentElement`, `children`, `firstElementChild`, `lastElementChild`, `nextElementSibling`, and `previousElementSibling`. You also learned how these relationships allow JavaScript to move efficiently between related elements without repeatedly searching the document.

DOM navigation is one of the most valuable skills for building interactive applications because it makes your code faster, cleaner, and easier to maintain.

---

# CodeTales Insight

> **Think of the DOM as a family tree. Every element has parents, children, brothers, and sisters. Once you understand these relationships, you no longer need to search the entire document—you can move directly to the element you need. Professional developers rely on DOM navigation every day because it leads to cleaner, more efficient, and more maintainable code.**

---

# 10.17 Working with CSS Classes (`classList`)

In the previous section, you learned how to change CSS styles using the `style` property.

Although this works well for small changes, professional developers rarely use inline styles for complex interfaces.

Instead, they create CSS classes and use JavaScript to add, remove, or switch between those classes.

This approach produces cleaner, more maintainable, and more reusable code.

JavaScript provides the `classList` property to make working with CSS classes simple and efficient.

---

# Why Use CSS Classes?

Consider the following CSS.

```css
.highlight {

    background-color: yellow;

    color: black;

    padding: 15px;

    border-radius: 8px;

}
```

Instead of writing four JavaScript statements:

```javascript
element.style.backgroundColor = "yellow";
element.style.color = "black";
element.style.padding = "15px";
element.style.borderRadius = "8px";
```

You can simply write:

```javascript
element.classList.add("highlight");
```

This is cleaner and easier to maintain.

---

## Figure 10.43

**Using CSS Classes**

```text
CSS Class

↓

classList.add()

↓

Element Styled
```

---

# The `classList` Property

Every HTML element has a `classList` property.

It provides methods for adding, removing, toggling, and checking CSS classes.

Common methods include:

- `add()`
- `remove()`
- `toggle()`
- `contains()`
- `replace()`

---

# Adding a Class

HTML

```html
<p id="message">
Welcome!
</p>
```

CSS

```css
.highlight {

    color: white;

    background: green;

}
```

JavaScript

```javascript
const message =
document.getElementById("message");

message.classList.add("highlight");
```

The paragraph immediately receives the styles defined in the `.highlight` class.

---

# Adding Multiple Classes

```javascript
message.classList.add(
    "highlight",
    "large",
    "shadow"
);
```

Several classes can be added at once.

---

# Removing a Class

```javascript
message.classList.remove("highlight");
```

The element immediately loses the styles associated with that class.

---

## Figure 10.44

**Removing a Class**

```text
Styled Element

↓

classList.remove()

↓

Original Element
```

---

# Toggling a Class

The `toggle()` method is one of the most useful methods in JavaScript.

If the class exists, it is removed.

If it does not exist, it is added.

Example

```javascript
message.classList.toggle("highlight");
```

This is perfect for features like:

- Dark mode
- Navigation menus
- Accordions
- Dropdowns
- Sidebars

---

# Checking Whether a Class Exists

Use the `contains()` method.

```javascript
if (message.classList.contains("highlight")) {

    console.log("Highlighted");

}
```

Output

```text
Highlighted
```

---

# Replacing a Class

Suppose you want to replace one class with another.

CSS

```css
.success {

    color: green;

}

.error {

    color: red;

}
```

JavaScript

```javascript
message.classList.replace(
    "success",
    "error"
);
```

The `success` class is removed and the `error` class is added.

---

# Practical Example: Dark Mode

HTML

```html
<body>

<button id="themeButton">

Toggle Theme

</button>

</body>
```

CSS

```css
.dark {

    background: #1e293b;

    color: white;

}
```

JavaScript

```javascript
const button =
document.getElementById("themeButton");

button.addEventListener("click", () => {

    document.body.classList.toggle("dark");

});
```

Each button click switches between light mode and dark mode.

---

## Figure 10.45

**Dark Mode Toggle**

```text
Light Mode

↓

Click

↓

Dark Mode

↓

Click

↓

Light Mode
```

---

# Practical Example: Active Navigation Link

HTML

```html
<a class="nav-link">
Home
</a>
```

JavaScript

```javascript
const link =
document.querySelector(".nav-link");

link.classList.add("active");
```

The navigation link immediately receives the styles defined for the `.active` class.

---

# Practical Example: Form Validation

CSS

```css
.error {

    border: 2px solid red;

}
```

JavaScript

```javascript
const input =
document.getElementById("username");

input.classList.add("error");
```

The text box immediately displays a red border to indicate invalid input.

---

# Real-World Applications

The `classList` property is used in:

- Dark mode
- Mobile navigation menus
- Dropdown menus
- Tabs
- Accordions
- Image galleries
- Form validation
- Notifications
- Modals
- Toast messages
- Shopping carts

Nearly every modern website uses `classList`.

---

# `classList` vs `style`

| `classList` | `style` |
|-------------|---------|
| Uses CSS classes | Uses inline styles |
| Better for large projects | Better for small changes |
| Easy to maintain | Can become repetitive |
| Encourages reusable CSS | Can duplicate styling logic |

For most production applications, `classList` is the preferred approach.

---

# Best Practices

- Keep styling in CSS files.
- Use JavaScript to add or remove classes.
- Give classes descriptive names such as `active`, `hidden`, `success`, or `error`.
- Avoid mixing too many inline styles with CSS classes.

---

# Common Beginner Mistakes

## Mistake 1: Forgetting the Dot

Incorrect

```javascript
element.classList.add(".active");
```

Correct

```javascript
element.classList.add("active");
```

The dot (`.`) is used only in CSS selectors, not in `classList`.

---

## Mistake 2: Replacing `toggle()` with `add()`

Incorrect

```javascript
button.classList.add("dark");
```

Every click keeps the class added.

Correct

```javascript
button.classList.toggle("dark");
```

This alternates between adding and removing the class.

---

## Mistake 3: Expecting `contains()` to Add a Class

Incorrect

```javascript
element.classList.contains("active");
```

`contains()` only checks whether a class exists.

To add a class:

```javascript
element.classList.add("active");
```

---

# Section Summary

In this section, you learned how to use the `classList` property to manage CSS classes dynamically. You explored the `add()`, `remove()`, `toggle()`, `contains()`, and `replace()` methods, and learned how they simplify styling compared to inline CSS. You also applied these methods to practical examples such as dark mode, navigation menus, and form validation.

The `classList` API is one of the most frequently used DOM features in modern web development because it helps keep JavaScript focused on behavior while CSS handles presentation.

---

# CodeTales Insight

> **Professional developers rarely hard-code visual styles in JavaScript. Instead, they define reusable CSS classes and let JavaScript simply decide *when* those classes should be applied. This separation of concerns leads to cleaner code, easier maintenance, and scalable web applications.**

---

# 10.18 DOM Events and Event Handling

A web page becomes truly interactive when it responds to user actions.

Imagine the following situations:

- A button performs an action when clicked.
- A form validates user input while typing.
- A navigation menu opens when the mouse hovers over it.
- An image gallery changes pictures when the user clicks Next.
- A shopping cart updates automatically after adding an item.

These interactions are possible because of **events**.

An **event** is an action or occurrence detected by the browser.

JavaScript listens for these events and executes code in response.

---

# What Is an Event?

An event is anything that happens on a web page.

Examples include:

- Clicking a button
- Moving the mouse
- Pressing a keyboard key
- Submitting a form
- Loading a page
- Resizing the browser window
- Scrolling the page
- Focusing on an input field

JavaScript allows us to react to these events.

---

## Figure 10.46

**How Events Work**

```text
User Action

↓

Browser Detects Event

↓

JavaScript Executes Code

↓

Web Page Updates
```

---

# Event Handlers

An **event handler** is a JavaScript function that runs when an event occurs.

Example

```javascript
function greet() {

    console.log("Welcome!");

}
```

The function itself does nothing until it is connected to an event.

---

# The `addEventListener()` Method

The modern way to listen for events is with `addEventListener()`.

### Syntax

```javascript
element.addEventListener(event, callback);
```

Where:

- `element` is the HTML element.
- `event` is the event name.
- `callback` is the function to execute.

---

# Example 1: Click Event

HTML

```html
<button id="btn">

Click Me

</button>
```

JavaScript

```javascript
const button =
document.getElementById("btn");

button.addEventListener("click", () => {

    console.log("Button clicked!");

});
```

Every click prints:

```text
Button clicked!
```

---

## Figure 10.47

**Click Event**

```text
User Clicks Button

↓

click Event

↓

JavaScript Function Runs
```

---

# Using a Named Function

Instead of an anonymous function, you can use a named function.

```javascript
function showMessage() {

    console.log("Hello, World!");

}

button.addEventListener("click", showMessage);
```

Notice that the function name is passed **without parentheses**.

---

# Multiple Event Listeners

An element can respond to multiple events.

```javascript
button.addEventListener("click", () => {

    console.log("Clicked");

});

button.addEventListener("mouseover", () => {

    console.log("Mouse entered");

});
```

The same button now reacts to different user actions.

---

# Common Mouse Events

| Event | Description |
|--------|-------------|
| `click` | User clicks an element |
| `dblclick` | User double-clicks |
| `mouseover` | Mouse enters an element |
| `mouseout` | Mouse leaves an element |
| `mousedown` | Mouse button pressed |
| `mouseup` | Mouse button released |
| `mousemove` | Mouse moves over an element |

---

# Common Keyboard Events

| Event | Description |
|--------|-------------|
| `keydown` | Key is pressed |
| `keyup` | Key is released |

Example

```javascript
document.addEventListener("keydown", () => {

    console.log("Key pressed");

});
```

---

# Common Form Events

| Event | Description |
|--------|-------------|
| `submit` | Form submitted |
| `input` | User types |
| `change` | Input value changes |
| `focus` | Element gains focus |
| `blur` | Element loses focus |

These events are essential for form validation.

---

# The Event Object

Whenever an event occurs, JavaScript automatically creates an **event object**.

Example

```javascript
button.addEventListener("click", (event) => {

    console.log(event);

});
```

The event object contains useful information about the event.

Examples include:

- Which element triggered the event
- Mouse position
- Keyboard key pressed
- Event type

---

# Reading the Event Type

```javascript
button.addEventListener("click", (event) => {

    console.log(event.type);

});
```

Output

```text
click
```

---

# Reading the Event Target

```javascript
button.addEventListener("click", (event) => {

    console.log(event.target);

});
```

Output

```html
<button>Click Me</button>
```

`event.target` refers to the element that triggered the event.

---

## Figure 10.48

**The Event Object**

```text
User Action

↓

Event Object

├── type

├── target

├── key

└── mouse position
```

---

# Practical Example

HTML

```html
<button id="welcomeButton">

Show Welcome

</button>
```

JavaScript

```javascript
const welcomeButton =
document.getElementById("welcomeButton");

welcomeButton.addEventListener("click", () => {

    alert("Welcome to Cracking JavaScript!");

});
```

When the user clicks the button, an alert appears.

---

# Real-World Applications

Events are used in:

- Login forms
- Registration forms
- Shopping carts
- Games
- Navigation menus
- Image sliders
- Search boxes
- Dashboards
- Video players
- Interactive maps

Nearly every interactive website depends on event handling.

---

# Best Practices

- Prefer `addEventListener()` over inline HTML event attributes.
- Keep event handler functions small and focused.
- Use meaningful function names.
- Remove unused event listeners when they are no longer needed.
- Avoid putting too much logic inside a single event handler.

---

# Common Beginner Mistakes

## Mistake 1: Calling the Function Immediately

Incorrect

```javascript
button.addEventListener("click", greet());
```

This executes the function immediately.

Correct

```javascript
button.addEventListener("click", greet);
```

---

## Mistake 2: Misspelling Event Names

Incorrect

```javascript
button.addEventListener("clicked", greet);
```

Correct

```javascript
button.addEventListener("click", greet);
```

---

## Mistake 3: Forgetting to Select the Element

Incorrect

```javascript
button.addEventListener("click", greet);
```

if `button` has never been defined.

Always select the element first.

```javascript
const button =
document.getElementById("btn");
```

---

# Section Summary

In this section, you learned what events are and how JavaScript responds to user interactions using `addEventListener()`. You explored common mouse, keyboard, and form events, learned how to use callback functions, and discovered how the event object provides information about the event that occurred.

Event handling is one of the most important concepts in JavaScript because it transforms static web pages into interactive applications.

---

# CodeTales Insight

> **A web page is like a conversation between the user and the browser. Events are how users speak, and event handlers are how your JavaScript responds. Mastering events enables you to build applications that feel responsive, intuitive, and engaging.**

---

# 10.19 Event Propagation (Bubbling and Capturing)

When an event occurs on a web page, it does not happen only on the element that the user interacts with.

Instead, the event travels through the Document Object Model (DOM).

This movement of an event through the DOM is called **event propagation**.

Understanding event propagation is important because it helps you control how events behave in complex web applications.

---

# What Is Event Propagation?

Suppose you have the following HTML.

```html
<div id="container">

    <button id="btn">

        Click Me

    </button>

</div>
```

If the user clicks the button, what happens?

Most beginners think only the button receives the event.

In reality, the event travels through the DOM.

---

## Figure 10.49

**Event Propagation**

```text
Document

↓

HTML

↓

Body

↓

Div

↓

Button

↓

User Click
```

After reaching the target element, the event travels back upward.

---

# The Three Phases of Event Propagation

Every DOM event has three phases.

1. Capturing Phase
2. Target Phase
3. Bubbling Phase

```text
Document

↓

HTML

↓

Body

↓

Div

↓

Button

(Target)

↑

Div

↑

Body

↑

HTML

↑

Document
```

---

# Phase 1: Capturing

During the capturing phase, the event travels from the top of the document toward the target element.

```text
Document

↓

HTML

↓

Body

↓

Div

↓

Button
```

Capturing is also called **event trickling**.

---

# Phase 2: Target

The target phase occurs when the event reaches the element that the user interacted with.

Example

```text
User clicks

↓

Button
```

The button is called the **event target**.

---

# Phase 3: Bubbling

After reaching the target, the event travels back upward through its parent elements.

```text
Button

↑

Div

↑

Body

↑

HTML

↑

Document
```

This is called **event bubbling**.

Most DOM events bubble by default.

---

## Figure 10.50

**Event Bubbling**

```text
Button

↑

Parent

↑

Grandparent

↑

Document
```

---

# Demonstrating Event Bubbling

HTML

```html
<div id="container">

    <button id="btn">

        Click Me

    </button>

</div>
```

JavaScript

```javascript
const container =
document.getElementById("container");

const button =
document.getElementById("btn");

container.addEventListener("click", () => {

    console.log("Container clicked");

});

button.addEventListener("click", () => {

    console.log("Button clicked");

});
```

If the button is clicked, the output is:

```text
Button clicked

Container clicked
```

The button receives the event first.

The event then bubbles to the container.

---

# Demonstrating Capturing

By default, `addEventListener()` listens during the bubbling phase.

To listen during the capturing phase, pass a third argument of `true`.

```javascript
container.addEventListener(

    "click",

    () => {

        console.log("Container");

    },

    true

);
```

Now the output becomes:

```text
Container

Button
```

The container receives the event before the button.

---

# The Event Object

The event object helps us understand propagation.

Example

```javascript
button.addEventListener("click", (event) => {

    console.log(event.target);

});
```

Output

```html
<button>

Click Me

</button>
```

---

# `event.target`

`event.target` refers to the element that originally triggered the event.

Even if the event bubbles to another element, `event.target` still points to the original element.

---

# `event.currentTarget`

`event.currentTarget` refers to the element whose event listener is currently executing.

Example

```javascript
container.addEventListener("click", (event) => {

    console.log(event.target);

    console.log(event.currentTarget);

});
```

If the button is clicked:

```text
event.target

↓

Button

event.currentTarget

↓

Container
```

---

## Figure 10.51

**target vs currentTarget**

```text
User Clicks

↓

Button

↓

Bubbles

↓

Container

target → Button

currentTarget → Container
```

---

# Stopping Event Propagation

Sometimes you do not want an event to continue bubbling.

Use:

```javascript
event.stopPropagation();
```

Example

```javascript
button.addEventListener("click", (event) => {

    event.stopPropagation();

    console.log("Button clicked");

});
```

Now clicking the button produces:

```text
Button clicked
```

The container's event listener is never executed.

---

# Practical Example

Imagine a notification panel.

Clicking inside the notification should not close it.

However, clicking outside the notification should close it.

`stopPropagation()` prevents clicks inside the panel from reaching the page's outer event listeners.

---

# Real-World Applications

Event propagation is important in:

- Navigation menus
- Dropdown menus
- Modals
- Dialog boxes
- Notification panels
- Context menus
- Interactive dashboards
- Image galleries

Understanding propagation prevents unexpected behavior.

---

# Bubbling vs Capturing

| Bubbling | Capturing |
|----------|-----------|
| Default behavior | Optional behavior |
| Event moves upward | Event moves downward |
| Most commonly used | Less common |
| Easier for event delegation | Useful in specialized cases |

---

# Best Practices

- Use bubbling unless capturing is specifically required.
- Call `stopPropagation()` only when necessary.
- Understand the difference between `target` and `currentTarget`.
- Keep event handlers simple and focused.

---

# Common Beginner Mistakes

## Mistake 1: Assuming Only the Clicked Element Receives the Event

A click on a child element may also trigger listeners on its parent elements because of event bubbling.

---

## Mistake 2: Overusing `stopPropagation()`

Avoid stopping propagation unless it solves a specific problem.

Excessive use can make debugging more difficult.

---

## Mistake 3: Confusing `target` with `currentTarget`

Remember:

- `event.target` is the element that initiated the event.
- `event.currentTarget` is the element whose listener is currently running.

---

# Section Summary

In this section, you learned how events travel through the DOM using event propagation. You explored the three phases of propagation—capturing, target, and bubbling—and learned how to use `event.target`, `event.currentTarget`, and `event.stopPropagation()`. You also discovered how these concepts help build predictable and maintainable interactive web applications.

Understanding event propagation is essential because many advanced JavaScript techniques, including event delegation, rely on it.

---

# CodeTales Insight

> **Every click on a web page begins a journey through the DOM. Professional developers don't just respond to events—they understand how those events travel. Mastering event propagation gives you precise control over user interactions and prepares you for building sophisticated, high-performance web applications.**

---

# 10.20 Event Delegation

In the previous section, you learned that most DOM events bubble from the target element up through its parent elements.

This behavior allows us to use a powerful technique called **event delegation**.

Instead of attaching an event listener to every individual element, we attach **one event listener** to a common parent element.

When an event bubbles up, the parent determines which child element triggered the event.

Event delegation is one of the most efficient techniques for handling events in large applications.

---

# Why Use Event Delegation?

Imagine a list containing 500 items.

One approach is to attach a click event to every list item.

```text
500 List Items

↓

500 Event Listeners
```

A better approach is to attach **one** event listener to the parent.

```text
Parent Element

↓

1 Event Listener

↓

Handles All Child Elements
```

This improves:

- Performance
- Memory usage
- Maintainability
- Scalability

---

## Figure 10.52

**Without Event Delegation**

```text
li → Listener

li → Listener

li → Listener

li → Listener

li → Listener
```

---

## Figure 10.53

**With Event Delegation**

```text
ul

↓

One Listener

↓

Handles Every li
```

---

# Example HTML

```html
<ul id="languages">

    <li>HTML</li>

    <li>CSS</li>

    <li>JavaScript</li>

</ul>
```

---

# The Traditional Approach

```javascript
const items =
document.querySelectorAll("li");

items.forEach((item) => {

    item.addEventListener("click", () => {

        console.log(item.textContent);

    });

});
```

This works, but each `<li>` receives its own event listener.

If hundreds of items exist, hundreds of listeners are created.

---

# Event Delegation Approach

Instead, place the event listener on the parent element.

```javascript
const list =
document.getElementById("languages");

list.addEventListener("click", (event) => {

    console.log(event.target.textContent);

});
```

Now every list item is handled by a single event listener.

---

## Figure 10.54

**How Event Delegation Works**

```text
User Clicks

↓

li

↓

Event Bubbles

↓

ul Listener Executes

↓

event.target Identifies li
```

---

# Understanding `event.target`

Suppose the user clicks:

```html
<li>CSS</li>
```

The event listener is attached to:

```html
<ul>
```

Inside the event handler:

```javascript
console.log(event.target);
```

Output

```html
<li>CSS</li>
```

Although the listener belongs to the `<ul>`, the target is still the clicked `<li>`.

---

# Using `matches()`

Sometimes a parent contains different types of child elements.

Use `matches()` to check whether the clicked element matches a selector.

Example

```javascript
list.addEventListener("click", (event) => {

    if (event.target.matches("li")) {

        console.log(event.target.textContent);

    }

});
```

This ensures that only list items trigger the code.

---

# Using `closest()`

Sometimes the user clicks inside a nested element.

Example

```html
<li>

    <span>JavaScript</span>

</li>
```

If the user clicks the `<span>`, `event.target` becomes the `<span>`.

To locate the nearest `<li>`, use `closest()`.

```javascript
const item =
event.target.closest("li");
```

If an ancestor matching `"li"` exists, it is returned.

---

# Practical Example: Removing a Task

HTML

```html
<ul id="tasks">

    <li>

        Study JavaScript

        <button>Delete</button>

    </li>

</ul>
```

JavaScript

```javascript
const tasks =
document.getElementById("tasks");

tasks.addEventListener("click", (event) => {

    if (event.target.matches("button")) {

        event.target.parentElement.remove();

    }

});
```

Clicking the **Delete** button removes the correct task.

Only one event listener is required.

---

## Figure 10.55

**Deleting a Task**

```text
Button Click

↓

Event Bubbles

↓

Parent Listener

↓

Task Removed
```

---

# Dynamically Added Elements

One major advantage of event delegation is that it also works for elements created after the page loads.

Example

```javascript
const item =
document.createElement("li");

item.textContent = "React";

list.appendChild(item);
```

No additional event listener is needed.

The parent listener automatically handles the new item.

---

# Real-World Applications

Event delegation is widely used in:

- To-do lists
- Shopping carts
- Comment systems
- Chat applications
- File managers
- Data tables
- Social media feeds
- Dashboards
- Kanban boards
- Dynamic forms

---

# Event Delegation vs Individual Listeners

| Individual Listeners | Event Delegation |
|----------------------|------------------|
| One listener per element | One listener on the parent |
| Higher memory usage | Lower memory usage |
| Harder to maintain | Easier to maintain |
| New elements need new listeners | Automatically works with new elements |

For applications with many similar elements, event delegation is generally the better choice.

---

# Best Practices

- Use event delegation when managing many similar child elements.
- Use `matches()` or `closest()` to identify the correct target.
- Avoid attaching unnecessary listeners to every child.
- Keep delegated event handlers concise and easy to read.

---

# Common Beginner Mistakes

## Mistake 1: Forgetting About Bubbling

Event delegation depends on event bubbling.

If bubbling is stopped with `event.stopPropagation()`, delegated handlers may not execute.

---

## Mistake 2: Assuming `event.target` Is Always the Desired Element

If nested elements exist, `event.target` may refer to a child element.

Use:

```javascript
event.target.closest("li");
```

to find the intended ancestor.

---

## Mistake 3: Delegating From the Wrong Parent

Attach the event listener to the closest common parent of the elements you want to manage.

Attaching it too high in the DOM can make your code harder to understand and maintain.

---

# Section Summary

In this section, you learned how event delegation uses event bubbling to handle events efficiently. You explored how a single parent event listener can manage many child elements, learned how to identify the clicked element with `event.target`, `matches()`, and `closest()`, and discovered why event delegation is widely used in modern JavaScript applications.

By reducing the number of event listeners, event delegation improves performance, simplifies maintenance, and automatically supports dynamically created elements.

---

# CodeTales Insight

> **Professional developers don't attach hundreds of event listeners when one will do. Event delegation takes advantage of the way events travel through the DOM, allowing a single, well-placed listener to manage an entire collection of elements. It's a simple idea that delivers cleaner code, better performance, and greater scalability.**

---

# 10.21 Mini Project – Interactive Student Profile

## Project Overview

In this mini project, you will build an **Interactive Student Profile** using JavaScript and the Document Object Model (DOM).

This project combines many of the concepts you learned throughout this chapter, including:

- Selecting DOM elements
- Reading and updating content
- Changing CSS classes
- Modifying attributes
- Creating new elements
- Removing elements
- Event handling
- Event delegation
- DOM navigation

By the end of this project, you will have created an interactive web page that responds to user actions without reloading the browser.

---

# Project Preview

The application displays a student's profile containing:

- Student photo
- Student name
- Department
- Biography
- Skills
- Buttons for interacting with the profile

Users can:

- Change the student's name
- Toggle Dark Mode
- Add a new skill
- Remove skills
- Change the profile picture
- Count total skills

---

## Figure 10.56

**Application Layout**

```text
-----------------------------------------

Student Profile

[ Profile Picture ]

Name: John Doe

Department: Computer Science

Bio:
Future Full-Stack Developer

Skills

• HTML
• CSS
• JavaScript

[ Add Skill ]

[ Change Name ]

[ Change Photo ]

[ Dark Mode ]

-----------------------------------------
```

---

# Project Folder Structure

```text
interactive-student-profile/

│

├── index.html

├── style.css

├── script.js

└── images/

      profile.jpg
```

---

# Step 1 — Create the HTML

Create the following structure.

```html
<!DOCTYPE html>
<html lang="en">
<head>

<meta charset="UTF-8">

<meta name="viewport"
content="width=device-width, initial-scale=1.0">

<title>Interactive Student Profile</title>

<link rel="stylesheet"
href="style.css">

</head>

<body>

<div class="card">

<img
id="profileImage"
src="images/profile.jpg"
alt="Student">

<h2 id="studentName">

John Doe

</h2>

<p id="department">

Computer Science

</p>

<p id="bio">

Future Full-Stack Developer

</p>

<h3>

Skills

</h3>

<ul id="skills">

<li>HTML</li>

<li>CSS</li>

<li>JavaScript</li>

</ul>

<button id="changeName">

Change Name

</button>

<button id="addSkill">

Add Skill

</button>

<button id="changePhoto">

Change Photo

</button>

<button id="darkMode">

Toggle Dark Mode

</button>

</div>

<script src="script.js"></script>

</body>

</html>
```

---

# Step 2 — Create the CSS

```css
body{

font-family:Arial, sans-serif;

background:#f2f2f2;

padding:40px;

}

.card{

width:350px;

margin:auto;

background:white;

padding:20px;

border-radius:10px;

text-align:center;

box-shadow:0 5px 15px rgba(0,0,0,.2);

}

img{

width:150px;

height:150px;

border-radius:50%;

object-fit:cover;

}

button{

margin:5px;

padding:10px 15px;

cursor:pointer;

}

.dark{

background:#222;

color:white;
}
```

---

# Step 3 — Change the Student Name

```javascript
const changeName =
document.getElementById("changeName");

changeName.addEventListener("click", () => {

document.getElementById("studentName").textContent =
"Jane Smith";

});
```

Try clicking the button.

The student's name changes immediately.

---

# Step 4 — Toggle Dark Mode

```javascript
const darkButton =
document.getElementById("darkMode");

darkButton.addEventListener("click", () => {

document.body.classList.toggle("dark");

});
```

The page now switches between light mode and dark mode.

---

# Step 5 — Add a New Skill

```javascript
const addSkill =
document.getElementById("addSkill");

addSkill.addEventListener("click", () => {

const skill =
prompt("Enter a new skill:");

if(skill){

const item =
document.createElement("li");

item.textContent = skill;

document
.getElementById("skills")
.appendChild(item);

}

});
```

Every new skill is added to the list.

---

# Step 6 — Remove a Skill

Instead of adding a delete button to every skill, use **event delegation**.

```javascript
const skills =
document.getElementById("skills");

skills.addEventListener("click", (event)=>{

if(event.target.matches("li")){

event.target.remove();

}

});
```

Click any skill to remove it.

---

# Step 7 — Change the Profile Picture

```javascript
const photo =
document.getElementById("changePhoto");

photo.addEventListener("click", ()=>{

document
.getElementById("profileImage")
.src="images/profile2.jpg";

});
```

The profile image changes.

---

# Step 8 — Count Skills

```javascript
const total =
document
.getElementById("skills")
.children.length;

console.log(total);
```

The console displays the number of skills.

---

# Challenge Improvements

Extend the application by adding:

- Edit profile button
- Change biography
- Upload a custom profile picture
- Favorite skill
- Search skills
- Sort skills alphabetically
- Display total number of skills
- Delete all skills
- Confirm before deleting
- Save data using Local Storage

These improvements will prepare you for larger JavaScript applications.

---

# Technologies Used

This project uses:

- HTML5
- CSS3
- JavaScript
- DOM API

No external libraries or frameworks are required.

---

# Learning Outcomes

After completing this project, you should be able to:

- Select DOM elements
- Modify text content
- Change attributes
- Toggle CSS classes
- Create HTML elements
- Remove HTML elements
- Handle events
- Use event delegation
- Navigate the DOM
- Build simple interactive applications

---

# Project Review Questions

1. Which DOM methods were used to select elements?
2. Why was `classList.toggle()` used for Dark Mode?
3. Why is event delegation used to remove skills?
4. Which method creates new HTML elements?
5. Which method inserts new elements into the page?
6. Which method removes elements?
7. Why is `textContent` used instead of `innerHTML`?
8. Which event is attached to the buttons?
9. How many event listeners were created?
10. Which DOM concepts were used most frequently?

Try answering these questions before reviewing the code again.

---

# Mini Project Summary

In this project, you combined nearly every DOM concept introduced in this chapter to build a complete interactive application. You selected elements, modified content, created and removed elements, handled user events, navigated the DOM, and used event delegation to simplify event management.

Projects like this demonstrate how the DOM enables JavaScript to create dynamic and engaging user experiences without reloading the page.

---

# CodeTales Insight

> **Reading about the DOM builds knowledge, but building a project develops skill. Every interactive application—from simple profile cards to large social media platforms—relies on the same core techniques you practiced here. Mastering these fundamentals prepares you for more advanced JavaScript topics and real-world development.**

---

# 10.22 Chapter Summary

Congratulations!

You have successfully completed **Chapter 10: Document Object Model (DOM)**.

This chapter introduced one of the most powerful features of JavaScript—the ability to interact with and manipulate web pages dynamically.

Before learning the DOM, your JavaScript programs mainly performed calculations, stored data, and made decisions. With the DOM, your code can now respond to user interactions, modify HTML, update CSS, create new content, and build interactive web applications.

The skills you learned in this chapter form the foundation of modern front-end development.

---

# What You Learned

Throughout this chapter, you explored how JavaScript communicates with HTML through the Document Object Model.

You learned how to:

- Understand the structure of the DOM tree.
- Select HTML elements using various DOM methods.
- Read and modify text and HTML content.
- Change HTML attributes dynamically.
- Modify CSS styles using JavaScript.
- Manage CSS classes with `classList`.
- Create new HTML elements.
- Insert elements into the document.
- Replace existing elements.
- Remove elements from the DOM.
- Navigate between parent, child, and sibling elements.
- Respond to user interactions with event listeners.
- Understand event propagation.
- Use event delegation to write efficient event-handling code.
- Build an interactive project using the DOM.

Each topic builds on the previous one, creating a complete workflow for manipulating web pages.

---

# Key DOM Methods Covered

By the end of this chapter, you became familiar with many essential DOM methods and properties, including:

### Element Selection

- `getElementById()`
- `getElementsByClassName()`
- `getElementsByTagName()`
- `querySelector()`
- `querySelectorAll()`

### Content Manipulation

- `textContent`
- `innerHTML`
- `innerText`

### Attribute Manipulation

- `getAttribute()`
- `setAttribute()`
- `removeAttribute()`
- `hasAttribute()`

### Style Manipulation

- `style`
- `classList.add()`
- `classList.remove()`
- `classList.toggle()`
- `classList.contains()`
- `classList.replace()`

### Creating and Removing Elements

- `createElement()`
- `appendChild()`
- `append()`
- `prepend()`
- `before()`
- `after()`
- `replaceChild()`
- `replaceWith()`
- `remove()`
- `removeChild()`

### DOM Navigation

- `parentElement`
- `children`
- `firstElementChild`
- `lastElementChild`
- `nextElementSibling`
- `previousElementSibling`

### Events

- `addEventListener()`
- `event.target`
- `event.currentTarget`
- `event.stopPropagation()`

These methods represent the core toolkit for DOM manipulation.

---

## Figure 10.57

**The DOM Development Workflow**

```text
Select Element

↓

Read Data

↓

Modify Content

↓

Change Styles

↓

Handle Events

↓

Update the Web Page
```

---

# The Importance of the DOM

The DOM is what transforms a static HTML document into an interactive application.

Without the DOM:

- Buttons would not respond.
- Forms could not be validated.
- Menus would not open.
- Shopping carts would not update.
- Notifications would not appear.
- Dynamic content would not exist.

Nearly every website and web application depends on DOM manipulation.

---

# Best Practices to Remember

As you continue learning JavaScript, keep these best practices in mind:

- Select elements efficiently.
- Prefer `querySelector()` and `querySelectorAll()` for flexible selection.
- Use `textContent` when inserting plain text.
- Use `innerHTML` only when HTML markup is required.
- Keep presentation in CSS and behavior in JavaScript.
- Use `classList` instead of repeatedly modifying inline styles.
- Prefer `addEventListener()` over inline event attributes.
- Use event delegation when managing many similar elements.
- Write clean, readable, and maintainable code.

These habits will help you build scalable applications.

---

# Common Mistakes to Avoid

Many beginners make similar mistakes while learning the DOM.

Avoid the following:

- Forgetting to select an element before using it.
- Trying to manipulate elements that do not exist.
- Overusing `innerHTML`.
- Mixing HTML, CSS, and JavaScript responsibilities.
- Creating unnecessary event listeners.
- Ignoring event bubbling and propagation.
- Forgetting to check for `null` when selecting elements.

Recognizing these mistakes early will save debugging time.

---

# How This Chapter Connects to the Next

The DOM allows JavaScript to interact with a web page.

The next step is learning how JavaScript communicates with external data and performs tasks asynchronously.

In the upcoming chapters, you will learn about concepts such as:

- Timers
- Asynchronous programming
- Callbacks
- Promises
- `async` and `await`
- Fetch API
- JSON
- APIs
- Modern web application architecture

These topics build directly on the DOM skills you have developed.

---

# Knowledge Checklist

Before moving on, make sure you can confidently answer **Yes** to the following questions:

- Can I explain what the DOM is?
- Can I select elements using different DOM methods?
- Can I modify HTML content?
- Can I update CSS styles?
- Can I create and remove HTML elements?
- Can I navigate between parent and child elements?
- Can I respond to user events?
- Can I explain event bubbling?
- Can I implement event delegation?
- Can I build a simple interactive web application?

If you answered "Yes" to most of these questions, you are ready to continue.

---

# Final Thoughts

The DOM is one of the most practical parts of JavaScript because it connects your code directly to the user interface.

Everything you build in front-end development—from buttons and forms to dashboards and full-scale applications—depends on the concepts introduced in this chapter.

Mastering the DOM gives you the confidence to create web pages that are dynamic, interactive, and engaging.

As you continue your JavaScript journey, these skills will become second nature and will serve as the foundation for more advanced topics and frameworks.

---

# CodeTales Insight

> **The DOM is where JavaScript comes alive. Variables, functions, and objects provide the logic, but the DOM gives that logic a visible presence on the screen. Every click, animation, notification, and interactive feature you encounter on the web is powered by the principles you learned in this chapter. Master these fundamentals, and you'll be well prepared to build modern, professional web applications.**

---

# 10.23 Practice Exercises & Challenge Projects

Congratulations on completing **Chapter 10: Document Object Model (DOM)**.

Learning happens through practice. These exercises are designed to help you strengthen your understanding of DOM manipulation, event handling, and interactive web development.

Work through the exercises in order. Avoid looking at the solutions until you have attempted each problem.

---

# Part A – Review Questions

Answer the following questions in your own words.

1. What is the Document Object Model (DOM)?
2. How does the browser create the DOM from an HTML document?
3. What is the difference between the DOM tree and the HTML source code?
4. Explain the relationship between parent, child, and sibling elements.
5. What is the difference between `getElementById()` and `querySelector()`?
6. When would you use `querySelectorAll()` instead of `getElementsByClassName()`?
7. Explain the difference between `textContent`, `innerText`, and `innerHTML`.
8. What is the purpose of the `classList` property?
9. Explain the difference between `appendChild()` and `append()`.
10. When would you use `replaceWith()` instead of modifying an element directly?
11. What is the difference between `remove()` and `removeChild()`?
12. What is event propagation?
13. Explain the three phases of event propagation.
14. What is the difference between `event.target` and `event.currentTarget`?
15. What is event delegation, and why is it useful?

---

# Part B – Multiple Choice Questions

Choose the correct answer.

### Question 1

Which method selects an element by its ID?

A. `querySelectorAll()`

B. `getElementById()`

C. `getElementsByClassName()`

D. `createElement()`

---

### Question 2

Which property changes plain text inside an element?

A. `innerHTML`

B. `classList`

C. `textContent`

D. `style`

---

### Question 3

Which method creates a new HTML element?

A. `appendChild()`

B. `createElement()`

C. `replaceWith()`

D. `remove()`

---

### Question 4

Which method removes an element from the DOM?

A. `deleteElement()`

B. `remove()`

C. `destroy()`

D. `erase()`

---

### Question 5

Which method adds an event listener?

A. `listen()`

B. `onEvent()`

C. `addEventListener()`

D. `attachEvent()`

---

# Part C – Practical Exercises

## Exercise 1

Create a web page containing:

- A heading
- A paragraph
- A button

When the button is clicked, change the heading text.

---

## Exercise 2

Create a button that changes the background color of the page each time it is clicked.

---

## Exercise 3

Create a list of programming languages.

Add a button that inserts a new language into the list.

---

## Exercise 4

Create a list of students.

Allow the user to remove any student by clicking the student's name.

---

## Exercise 5

Create a profile card containing:

- Photo
- Name
- Department

Add a button that changes the student's department.

---

## Exercise 6

Create a "Show/Hide" button.

Use `classList.toggle()` to hide and display a paragraph.

---

## Exercise 7

Create a shopping list.

Allow users to:

- Add items
- Remove items
- Count total items

---

## Exercise 8

Create a gallery of three images.

Add "Next" and "Previous" buttons to switch between images.

---

## Exercise 9

Create a simple calculator interface.

Use buttons to perform addition, subtraction, multiplication, and division.

---

## Exercise 10

Create a digital clock that updates every second.

---

# Part D – Debugging Exercises

Each example below contains an error.

Find and fix the problem.

---

## Debugging Exercise 1

```javascript
document.getElementByID("title");
```

---

## Debugging Exercise 2

```javascript
button.addEventListener("clicked", showMessage);
```

---

## Debugging Exercise 3

```javascript
element.classList.add(".active");
```

---

## Debugging Exercise 4

```javascript
document.querySelector("#box").removeChild();
```

---

## Debugging Exercise 5

```javascript
const title =
document.getElementById("heading");

title.textcontent = "Hello";
```

---

# Part E – Build It Yourself

Create the following applications using only HTML, CSS, and JavaScript.

1. To-Do List
2. Notes Application
3. Student Registration Form
4. Shopping Cart
5. Quiz Application
6. Weather Dashboard (with sample data)
7. Contact Manager
8. Expense Tracker
9. Countdown Timer
10. Image Slider

---

# Part F – Portfolio Challenge Projects

These projects are suitable for your GitHub portfolio.

## Beginner

- Random Quote Generator
- Color Palette Generator
- BMI Calculator
- Unit Converter
- Age Calculator

---

## Intermediate

- Music Playlist Manager
- Movie Search Interface
- Employee Directory
- Recipe Finder
- Student Grade Calculator

---

## Advanced

- Kanban Task Board
- Personal Finance Dashboard
- Mini E-Commerce Store
- Chat Interface
- Online Examination System

---

# Chapter Challenge

Build a **Student Management System** with the following features:

- Add new students
- Edit student information
- Delete students
- Search students
- Filter by department
- Sort alphabetically
- Count total students
- Toggle dark mode
- Display profile pictures
- Save data using Local Storage

This challenge combines nearly every DOM concept from this chapter.

---

# Self-Assessment Checklist

Before continuing to the next chapter, confirm that you can confidently:

- Explain the DOM.
- Select elements using multiple methods.
- Modify text and HTML.
- Change attributes.
- Apply and remove CSS classes.
- Create and remove elements.
- Navigate the DOM tree.
- Handle browser events.
- Explain event propagation.
- Implement event delegation.
- Build interactive web applications.

If you can complete these tasks without referring to the chapter, you have mastered the fundamentals.

---

# Looking Ahead

In the next chapter, you will move beyond manipulating the page and begin working with **asynchronous JavaScript**.

You will learn how to:

- Delay code execution
- Schedule repeated tasks
- Handle asynchronous operations
- Work with callbacks
- Understand promises
- Use `async` and `await`
- Fetch data from APIs
- Process JSON
- Build applications that communicate with remote servers

These concepts are essential for modern web development.

---

# Final Words

The Document Object Model is the bridge between JavaScript and the web page. By mastering the DOM, you have learned how to transform static HTML into dynamic, responsive, and interactive applications.

Keep practicing, experiment with your own ideas, and revisit these exercises as you progress. The more projects you build, the more confident and capable you will become as a JavaScript developer.

---

# CodeTales Insight

> **Knowledge becomes skill only through consistent practice. Every professional JavaScript developer once wrote their first `getElementById()`, attached their first event listener, and debugged their first DOM error. Keep building, keep experimenting, and remember: every project you complete is another step toward mastery.**
