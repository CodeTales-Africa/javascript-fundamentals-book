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
