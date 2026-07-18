# Chapter 12

# Object-Oriented Programming (OOP)

---

## Chapter Overview

As software applications grow larger and more complex, organizing code becomes increasingly important. Writing everything as independent variables and functions quickly becomes difficult to manage, maintain, and extend. Modern software development solves this challenge by organizing related data and behaviors into reusable objects.

Object-Oriented Programming (OOP) is one of the most influential programming paradigms in computer science. It enables developers to model real-world entities—such as students, vehicles, bank accounts, employees, and products—as objects that contain both data and behavior. This approach produces software that is easier to understand, reuse, test, and maintain.

JavaScript is a prototype-based language, but it fully supports object-oriented programming. Earlier versions of JavaScript relied on constructor functions and prototypes to implement OOP concepts. With the introduction of **ECMAScript 2015 (ES6)**, JavaScript gained the **class** syntax, making object-oriented programming more intuitive and familiar to developers coming from languages such as Java, C++, and C#.

In this chapter, you will learn how to create objects, define properties and methods, understand the `this` keyword, work with constructor functions and classes, implement inheritance, encapsulation, getters, setters, private fields, and explore useful object utility methods available in modern JavaScript.

By the end of this chapter, you will be able to design reusable, scalable, and maintainable applications using object-oriented principles. These skills form the foundation for professional JavaScript development and prepare you for more advanced topics in future volumes of this book.

---

# Learning Objectives

After studying this chapter, you should be able to:

- Explain the purpose of Object-Oriented Programming (OOP).
- Describe the four fundamental principles of OOP.
- Differentiate between primitive values and objects.
- Create objects using different techniques.
- Access, modify, add, and remove object properties.
- Define and use object methods.
- Understand and correctly use the `this` keyword.
- Create constructor functions.
- Explain the purpose of the `new` keyword.
- Understand JavaScript prototypes and prototype inheritance.
- Create classes using ES6 syntax.
- Define constructors, properties, and methods within classes.
- Create static properties and static methods.
- Implement inheritance using the `extends` keyword.
- Override inherited methods.
- Apply encapsulation using private fields.
- Create getters and setters.
- Use object destructuring.
- Use the spread operator with objects.
- Apply common Object utility methods.
- Use optional chaining and nullish coalescing with objects.
- Apply object-oriented programming concepts to real-world applications.

---

# Prerequisites

Before beginning this chapter, you should already understand:

- Variables and constants
- Data types
- Operators
- Conditional statements
- Loops
- Functions
- Arrays
- Objects
- DOM manipulation
- Asynchronous JavaScript

---

# Chapter Outline

12.1 Introduction to Object-Oriented Programming

12.2 Understanding Objects

12.3 Primitive Values vs Reference Values

12.4 Creating Objects

12.5 Properties and Methods

12.6 Accessing Object Properties

12.7 Adding, Updating, and Deleting Properties

12.8 Object Methods

12.9 Understanding the `this` Keyword

12.10 Constructor Functions

12.11 The `new` Keyword

12.12 Prototypes and the Prototype Chain

12.13 ES6 Classes

12.14 Constructors in Classes

12.15 Instance Properties and Methods

12.16 Static Properties and Methods

12.17 Inheritance

12.18 Method Overriding

12.19 Encapsulation

12.20 Getters and Setters

12.21 Private Class Fields

12.22 Object Destructuring

12.23 The Object Spread Operator

12.24 Useful Object Methods

12.25 Optional Chaining

12.26 Nullish Coalescing

12.27 Real-World Applications of OOP

12.28 Best Practices

12.29 Common Beginner Mistakes

12.30 Chapter Summary

12.31 Key Terms

12.32 Chapter Review Questions

12.33 Practice Exercises

12.34 Chapter Project — Student Management System

---

> **"Programs grow in complexity, but well-designed objects keep complexity under control. Mastering Object-Oriented Programming enables you to build software that is organized, reusable, and ready for the real world."**
>
> — *CodeTales Africa*

---

# 12.1 Introduction to Object-Oriented Programming

In the previous chapters, you learned how to write JavaScript programs using variables, functions, arrays, objects, the Document Object Model (DOM), and asynchronous programming. These concepts are sufficient for building small applications. However, as software grows in size and complexity, organizing code becomes increasingly important.

Imagine developing a school management system with thousands of students, hundreds of teachers, numerous courses, examination records, and financial transactions. Managing such a system with only variables and standalone functions would quickly become difficult. The code would be harder to understand, maintain, and extend.

Object-Oriented Programming (OOP) addresses this challenge by organizing related data and behavior into reusable objects. Instead of treating data and functions separately, OOP groups them together into logical units called **objects**.

This programming style makes applications easier to design, maintain, and scale.

---

# What Is Object-Oriented Programming?

**Object-Oriented Programming (OOP)** is a programming paradigm that organizes software around **objects**, rather than individual functions or procedures.

An object combines:

- **Data** (called **properties** or **attributes**)
- **Behavior** (called **methods**)

Together, these describe a real-world entity.

For example, consider a student.

A student has:

**Properties**

- Name
- Age
- Student ID
- Department

And the student can perform actions such as:

- Register courses
- Write examinations
- Pay school fees
- View results

Instead of storing these pieces of information separately, OOP groups them into one object.

---

## Figure 12.1

**An Object Combines Data and Behavior**

```text
               Student

        ┌───────────────────┐
        │     Properties    │
        │-------------------│
        │ Name              │
        │ Age               │
        │ Department        │
        ├───────────────────┤
        │      Methods      │
        │-------------------│
        │ registerCourse()  │
        │ payFees()         │
        │ viewResult()      │
        └───────────────────┘
```

---

# Why Do We Need OOP?

As applications become larger, developers face several challenges:

- Repeated code
- Difficult maintenance
- Poor organization
- Hard-to-find bugs
- Low code reusability

Object-Oriented Programming helps solve these problems by promoting:

- Reusability
- Organization
- Modularity
- Scalability
- Maintainability

Instead of writing the same logic repeatedly, developers create reusable objects that can be used throughout an application.

---

# A Real-World Analogy

Imagine a car.

Every car has:

Properties:

- Brand
- Model
- Color
- Speed

Behaviors:

- Start
- Stop
- Accelerate
- Brake

In JavaScript, a car object follows the same idea.

```javascript
const car = {

    brand: "Toyota",

    model: "Corolla",

    color: "Blue",

    start() {

        console.log("Engine started.");

    }

};
```

The object contains both information (**properties**) and actions (**methods**).

---

## Figure 12.2

**Real-World Object**

```text
Car

↓

Properties

• Brand

• Model

• Color

↓

Methods

• Start()

• Stop()

• Accelerate()
```

---

# Procedural Programming vs Object-Oriented Programming

Before OOP became popular, many applications were written using **procedural programming**.

In procedural programming:

- Data is separated from functions.
- Programs are organized as sequences of procedures.

Example:

```javascript
let studentName = "Ada";

function registerCourse() {

    console.log(studentName + " registered.");

}
```

In Object-Oriented Programming:

```javascript
const student = {

    name: "Ada",

    registerCourse() {

        console.log(this.name + " registered.");

    }

};
```

The object stores both the data and the behavior together.

---

## Figure 12.3

**Procedural Programming vs OOP**

```text
Procedural Programming

Data

↓

Functions

----------------------------

Object-Oriented Programming

Object

↓

Properties + Methods
```

---

# Characteristics of Object-Oriented Programming

Most object-oriented languages share several important characteristics.

They encourage developers to:

- Model real-world entities.
- Organize related code together.
- Reuse existing code.
- Reduce duplication.
- Build applications that are easier to maintain.

These characteristics make OOP especially useful for medium and large software projects.

---

# The Four Pillars of OOP

Object-Oriented Programming is built upon four fundamental principles.

They are:

1. Encapsulation
2. Abstraction
3. Inheritance
4. Polymorphism

You will study each of these principles later in this chapter.

---

## Figure 12.4

**The Four Pillars of OOP**

```text
Object-Oriented Programming

        │

────────┼────────

│       │        │        │

Encapsulation

Abstraction

Inheritance

Polymorphism
```

---

# Where Is OOP Used?

Object-Oriented Programming is widely used in:

- Web applications
- Mobile applications
- Desktop software
- Banking systems
- Hospital management systems
- E-commerce platforms
- School management systems
- Video games
- Artificial intelligence systems

Modern JavaScript frameworks such as Angular and many Node.js applications make extensive use of OOP concepts.

---

# Benefits of Learning OOP

Learning Object-Oriented Programming helps you:

- Write cleaner code.
- Reduce duplication.
- Reuse existing components.
- Simplify maintenance.
- Improve collaboration in teams.
- Build scalable software.
- Prepare for professional software development.

OOP is one of the most valuable skills for JavaScript developers because many real-world applications are built using object-oriented principles.

---

# Best Practices

- Think about real-world objects before writing code.
- Keep related data and methods together.
- Use meaningful object names.
- Design objects with a single responsibility whenever possible.
- Reuse existing objects instead of duplicating logic.

---

# Common Beginner Mistakes

## Mistake 1

Thinking that OOP is only about classes.

Classes are only one way to organize objects. The main goal of OOP is to model data and behavior together.

---

## Mistake 2

Creating very large objects that perform many unrelated tasks.

Instead, create smaller objects with clear responsibilities.

---

## Mistake 3

Trying to convert every problem into an object.

Not every programming problem requires an object-oriented solution. Choose the approach that best fits the problem.

---

# Section Summary

In this section, you were introduced to Object-Oriented Programming (OOP), a programming paradigm that organizes software around objects containing both data and behavior. You learned why OOP is important for building large, maintainable applications, compared procedural programming with object-oriented programming, explored real-world examples of objects, and discovered the four fundamental pillars of OOP. These ideas provide the foundation for the rest of this chapter.

In the next section, you will learn what objects are in JavaScript and how they differ from primitive values.

---

# CodeTales Insight

> **Object-Oriented Programming is more than a coding technique—it's a way of thinking. Instead of viewing a program as a collection of unrelated functions, OOP encourages you to see software as a community of interacting objects. Once you adopt this mindset, designing complex applications becomes more natural, organized, and maintainable.**

---

# 12.2 Understanding Objects

In the previous section, you learned that Object-Oriented Programming (OOP) organizes software around **objects**. Before learning how to create and manipulate objects, it is important to understand what an object is and why objects are central to JavaScript.

Everything in OOP revolves around objects. In fact, JavaScript is often described as an **object-oriented** and **prototype-based** programming language because objects play a major role in how programs are written and organized.

---

# What Is an Object?

An **object** is a collection of related data and functionality.

It groups together:

- **Properties** (data)
- **Methods** (functions that perform actions)

An object represents a single entity.

For example, a student can be represented as an object.

```javascript
const student = {

    name: "Ada",

    age: 21,

    department: "Computer Science",

    introduce() {

        console.log("Hello, I am " + this.name);

    }

};
```

In this example:

- `name`, `age`, and `department` are **properties**.
- `introduce()` is a **method**.

Together they describe one student.

---

## Figure 12.5

**Structure of a JavaScript Object**

```text
Object

│

├── Properties

│     ├── name

│     ├── age

│     └── department

│

└── Methods

      └── introduce()
```

---

# Objects Represent Real-World Things

Objects allow programmers to model real-world entities.

Consider a bank account.

Properties:

- Account Number
- Account Name
- Balance

Methods:

- Deposit
- Withdraw
- Check Balance

JavaScript object:

```javascript
const account = {

    accountNumber: "0012345678",

    accountName: "Ada",

    balance: 50000,

    deposit() {

        console.log("Money deposited.");

    },

    withdraw() {

        console.log("Money withdrawn.");

    }

};
```

The object stores everything related to the account in one place.

---

# Objects Help Organize Information

Without objects:

```javascript
let studentName = "Ada";

let studentAge = 20;

let studentDepartment = "Computer Science";
```

As your application grows, managing separate variables becomes difficult.

Using an object:

```javascript
const student = {

    name: "Ada",

    age: 20,

    department: "Computer Science"

};
```

The information is now organized logically.

---

## Figure 12.6

**Without Objects vs With Objects**

```text
Without Objects

name

age

department

------------------------

With Object

Student

├── name

├── age

└── department
```

---

# Objects Can Contain Different Data Types

An object is not limited to one type of data.

Example:

```javascript
const employee = {

    name: "David",

    age: 35,

    fullTime: true,

    salary: 850000,

    skills: [

        "JavaScript",

        "HTML",

        "CSS"

    ]

};
```

Notice that one object contains:

- Strings
- Numbers
- Booleans
- Arrays

Objects can even contain other objects.

---

# Nested Objects

Objects may contain other objects.

Example:

```javascript
const student = {

    name: "Ada",

    address: {

        city: "Enugu",

        country: "Nigeria"

    }

};
```

This is called a **nested object**.

Nested objects help represent more complex relationships.

---

## Figure 12.7

**Nested Objects**

```text
Student

│

├── name

└── address

      ├── city

      └── country
```

---

# Objects Can Contain Arrays

Objects frequently store collections of data using arrays.

Example:

```javascript
const course = {

    title: "JavaScript",

    students: [

        "Ada",

        "John",

        "Grace"

    ]

};
```

This combines two important JavaScript structures:

- Objects
- Arrays

Together they can represent complex data.

---

# Everything Is Not an Object

One common misconception is that everything in JavaScript is an object.

This is **not entirely true**.

Primitive values are **not objects**.

Examples of primitive values include:

- String
- Number
- Boolean
- Null
- Undefined
- Symbol
- BigInt

Objects are **reference values**, while primitive values are **stored directly**.

You will learn this difference in detail in the next section.

---

# Why Objects Matter

Objects are used throughout JavaScript.

Examples include:

- DOM elements
- Arrays
- Dates
- Maps
- Sets
- Errors
- Promises
- Browser APIs

Whenever you interact with the browser, chances are you are working with objects.

---

# Real-World Example

Imagine an online shopping application.

Each product can be represented as an object.

```javascript
const product = {

    name: "Laptop",

    price: 350000,

    quantity: 15,

    inStock: true

};
```

Instead of storing product information in separate variables, everything is grouped together logically.

---

# Benefits of Using Objects

Objects help developers:

- Organize related information.
- Reduce code duplication.
- Model real-world entities.
- Improve readability.
- Simplify maintenance.
- Build scalable applications.

For these reasons, objects are one of the most important features of JavaScript.

---

# Best Practices

- Use meaningful property names.
- Group related data together.
- Avoid creating unnecessary nested objects.
- Keep objects focused on one responsibility.
- Use consistent naming conventions.

---

# Common Beginner Mistakes

## Mistake 1

Confusing objects with arrays.

Objects store information using **named properties**, while arrays store information using **numbered indexes**.

---

## Mistake 2

Thinking methods and properties are the same.

Properties store values.

Methods perform actions.

---

## Mistake 3

Creating one enormous object to represent an entire application.

Instead, divide your application into smaller, manageable objects.

---

# Section Summary

In this section, you learned that an object is a collection of related properties and methods that represent a single entity. You discovered how objects organize data, store multiple data types, contain nested objects and arrays, and model real-world entities. You also learned why objects are fundamental to JavaScript and why they make applications easier to understand and maintain.

In the next section, you will explore the difference between **primitive values** and **reference values**, an essential concept for understanding how JavaScript stores and manipulates data.

---

# CodeTales Insight

> **Objects are the building blocks of modern JavaScript. They allow developers to organize data and behavior into meaningful units that closely resemble real-world entities. As your applications grow, well-designed objects become the foundation of clean, reusable, and maintainable code.**

---

# 12.3 Primitive Values vs Reference Values

In the previous section, you learned that objects are collections of related properties and methods. Before we begin creating and manipulating objects, it is important to understand **how JavaScript stores data in memory**.

Not all values are stored in the same way.

JavaScript divides values into two major categories:

- Primitive Values
- Reference Values

Understanding this distinction will help you explain why some variables behave independently while others appear to "share" the same data.

---

# What Are Primitive Values?

A **primitive value** is a simple value that is stored directly in memory.

Each variable owns its own copy of the value.

JavaScript has **seven primitive data types**:

- String
- Number
- Boolean
- Undefined
- Null
- Symbol
- BigInt

Example:

```javascript
let language = "JavaScript";

let version = 2025;

let isPopular = true;
```

Each variable stores its own value.

---

## Figure 12.8

**Primitive Values**

```text
Memory

language

↓

"JavaScript"

------------------------

version

↓

2025

------------------------

isPopular

↓

true
```

Each variable stores its own independent value.

---

# Copying Primitive Values

When a primitive value is assigned to another variable, JavaScript copies the value.

Example:

```javascript
let age = 25;

let anotherAge = age;

anotherAge = 30;

console.log(age);

console.log(anotherAge);
```

Output

```text
25

30
```

Changing `anotherAge` does not affect `age`.

Why?

Because JavaScript copied the value.

---

## Figure 12.9

**Copying Primitive Values**

```text
age

↓

25

------------------------

anotherAge

↓

25

↓

Changed to

↓

30
```

Each variable has its own copy.

---

# What Are Reference Values?

Objects are different.

An object is **not stored directly inside the variable**.

Instead, the variable stores a **reference (memory address)** pointing to where the object exists in memory.

Reference values include:

- Objects
- Arrays
- Functions
- Dates
- Maps
- Sets

These are stored by reference.

---

## Figure 12.10

**Reference Value**

```text
student

↓

Memory Address

↓

Object

{

name: "Ada"

}
```

The variable points to the object instead of containing the object itself.

---

# Copying Objects

Consider the following example.

```javascript
const student1 = {

    name: "Ada"

};

const student2 = student1;

student2.name = "Grace";

console.log(student1.name);

console.log(student2.name);
```

Output

```text
Grace

Grace
```

Many beginners expect:

```text
Ada

Grace
```

But that is incorrect.

Both variables reference the **same object**.

---

## Figure 12.11

**Two Variables Referencing the Same Object**

```text
student1

──────┐

      │

student2

──────┘

↓

{

name: "Ada"

}
```

There is only **one object** in memory.

---

# Why Did Both Variables Change?

This happened because JavaScript copied the **reference**, not the object.

When you changed:

```javascript
student2.name = "Grace";
```

you modified the single object in memory.

Since both variables point to that object, both variables see the updated value.

---

# Primitive Copy vs Object Copy

Primitive Example

```javascript
let x = 10;

let y = x;

y = 50;

console.log(x);
```

Output

```text
10
```

Object Example

```javascript
const x = {

    value: 10

};

const y = x;

y.value = 50;

console.log(x.value);
```

Output

```text
50
```

The behavior is different because objects are stored by reference.

---

## Figure 12.12

**Primitive vs Reference Copy**

```text
Primitive

x

↓

10

y

↓

10

Independent Copies

----------------------------

Object

x

──────┐

       │

y

──────┘

↓

One Shared Object
```

---

# Comparing Primitive Values

Primitive values are compared by their actual values.

Example

```javascript
console.log(10 === 10);

console.log("JavaScript" === "JavaScript");
```

Output

```text
true

true
```

---

# Comparing Objects

Objects are compared by their references.

Example

```javascript
const user1 = {

    name: "Ada"

};

const user2 = {

    name: "Ada"

};

console.log(user1 === user2);
```

Output

```text
false
```

Although both objects contain identical data, they occupy different memory locations.

---

## Figure 12.13

**Object Comparison**

```text
user1

↓

Object A

------------------------

user2

↓

Object B

Object A ≠ Object B
```

Different objects have different references.

---

# Shared References

Consider this example.

```javascript
const car = {

    brand: "Toyota"

};

const vehicle = car;

vehicle.brand = "Honda";

console.log(car.brand);
```

Output

```text
Honda
```

Again, both variables point to the same object.

---

# Why This Matters

Understanding reference values helps prevent unexpected bugs.

For example:

- Updating one object may unintentionally affect another variable.
- Passing objects into functions can modify the original object.
- Arrays behave exactly like objects because arrays are reference values.

You will learn techniques for creating independent object copies later in this chapter.

---

# Best Practices

- Remember that primitive values are copied by value.
- Remember that objects are copied by reference.
- Be careful when modifying shared objects.
- Use clear variable names when working with multiple object references.
- Understand how copying works before writing large applications.

---

# Common Beginner Mistakes

## Mistake 1

Assuming assigning one object to another creates a new object.

It only copies the reference.

---

## Mistake 2

Comparing two different objects using `===` and expecting `true`.

Two separate objects are never equal, even if they contain identical data.

---

## Mistake 3

Forgetting that arrays are reference values.

Arrays behave just like objects when assigned to another variable.

---

# Section Summary

In this section, you learned that JavaScript stores primitive values and reference values differently. Primitive values are stored directly in variables, and assigning them creates independent copies. Objects, arrays, and functions are stored as reference values, meaning variables hold references to shared data in memory. You also learned why object assignments share the same underlying object and why object comparisons are based on references rather than content.

In the next section, you will learn the different ways to **create objects in JavaScript**, including object literals, the `Object` constructor, factory functions, constructor functions, and ES6 classes.

---

# CodeTales Insight

> **Understanding the difference between primitive values and reference values is one of the biggest milestones in learning JavaScript. Once you grasp how memory works, confusing behaviors such as shared object updates and failed object comparisons become much easier to understand. This knowledge will help you write safer, more predictable, and more professional JavaScript code.**

---

# 12.4 Creating Objects

In the previous section, you learned that objects are reference values used to organize related data and behavior. The next step is learning how to create them.

JavaScript provides several ways to create objects. Some methods are simple and commonly used, while others are designed for creating many similar objects in large applications.

Understanding these techniques will help you choose the right approach for different programming scenarios.

---

# Ways to Create Objects in JavaScript

There are five common ways to create objects:

1. Object Literal
2. The `Object()` Constructor
3. Factory Functions
4. Constructor Functions
5. ES6 Classes

Each method has its own strengths and use cases.

---

## Figure 12.14

**Ways to Create Objects**

```text
JavaScript Objects

│

├── Object Literal

├── Object Constructor

├── Factory Function

├── Constructor Function

└── ES6 Class
```

---

# 1. Creating Objects Using Object Literals

The simplest and most common way to create an object is with an **object literal**.

Syntax:

```javascript
const objectName = {

    property: value,

    method() {

    }

};
```

Example:

```javascript
const student = {

    name: "Ada",

    age: 21,

    department: "Computer Science"

};
```

Output

```text
{

name: "Ada",

age: 21,

department: "Computer Science"

}
```

This method is ideal when creating a single object.

---

# Adding Methods

Objects can also contain methods.

Example:

```javascript
const student = {

    name: "Ada",

    greet() {

        console.log("Welcome!");

    }

};

student.greet();
```

Output

```text
Welcome!
```

---

## Figure 12.15

**Object Literal**

```text
Student Object

│

├── name

├── age

└── greet()
```

---

# Advantages of Object Literals

Object literals are:

- Simple
- Easy to read
- Easy to write
- Perfect for small applications
- The most commonly used approach in JavaScript

---

# Limitation of Object Literals

Suppose you need to create 500 students.

Using object literals repeatedly becomes repetitive.

Example:

```javascript
const student1 = {

    name: "Ada"

};

const student2 = {

    name: "John"

};

const student3 = {

    name: "Grace"

};
```

Notice how the same structure is written repeatedly.

This is where factory functions and classes become useful.

---

# 2. Creating Objects with the Object Constructor

JavaScript provides a built-in constructor named `Object()`.

Example:

```javascript
const student = new Object();

student.name = "Ada";

student.age = 21;

student.department = "Computer Science";
```

Output

```text
{

name: "Ada",

age: 21,

department: "Computer Science"

}
```

---

# Adding Methods

Methods can also be added.

```javascript
const student = new Object();

student.greet = function () {

    console.log("Hello!");

};

student.greet();
```

Output

```text
Hello!
```

---

## Figure 12.16

**Object Constructor**

```text
new Object()

↓

Empty Object

↓

Properties Added

↓

Completed Object
```

---

# Object Literal vs Object Constructor

Both approaches create objects.

Object Literal

```javascript
const user = {

    name: "Ada"

};
```

Object Constructor

```javascript
const user = new Object();

user.name = "Ada";
```

Both produce similar results.

However, object literals are shorter and more readable.

For this reason, most JavaScript developers prefer object literals.

---

# Which Should You Use?

In modern JavaScript:

✅ Prefer object literals.

Use the `Object()` constructor only when there is a specific reason to do so.

---

# Looking Ahead

Object literals and the `Object()` constructor work well when creating individual objects.

However, if you need to create many similar objects, repeating the same code becomes inefficient.

In the next sections, you will learn about **factory functions**, **constructor functions**, and **ES6 classes**, which solve this problem by allowing you to generate multiple objects from a reusable blueprint.

---

# Best Practices

- Prefer object literals for creating individual objects.
- Use meaningful property names.
- Keep related data together.
- Add methods only when they represent behaviors of the object.
- Use consistent formatting for better readability.

---

# Common Beginner Mistakes

## Mistake 1

Using `new Object()` for every object.

Object literals are simpler and are the preferred style in modern JavaScript.

---

## Mistake 2

Creating multiple objects with identical code.

When many objects share the same structure, use factory functions, constructor functions, or classes.

---

## Mistake 3

Forgetting commas between object properties.

Incorrect:

```javascript
const student = {

    name: "Ada"

    age: 21

};
```

Correct:

```javascript
const student = {

    name: "Ada",

    age: 21

};
```

---

# Section Summary

In this section, you learned the different ways JavaScript can create objects. You explored object literals, the simplest and most widely used approach, and the built-in `Object()` constructor. You also learned the strengths and limitations of each technique and saw why object literals are generally preferred for creating individual objects. In the next sections, you'll discover more powerful approaches—factory functions, constructor functions, and ES6 classes—for creating multiple objects efficiently.

---

# CodeTales Insight

> **Choosing the right way to create an object depends on the problem you're solving. Object literals are perfect for individual objects, while factory functions, constructor functions, and classes become invaluable when building applications that require many objects with the same structure. As your JavaScript skills grow, selecting the appropriate object creation technique will make your code cleaner, more reusable, and easier to maintain.**

---

# 12.5 Properties and Methods

In the previous section, you learned different ways to create objects in JavaScript. However, creating an object is only the beginning. To make objects useful, they must contain information and be able to perform actions.

Objects achieve this through **properties** and **methods**.

Think of an object as a real-world entity. Every entity has characteristics that describe it and actions that it can perform.

For example, a smartphone has characteristics such as its brand, model, storage capacity, and battery level. It can also perform actions like making calls, sending messages, taking photos, and playing music.

In JavaScript, these characteristics are represented by **properties**, while the actions are represented by **methods**.

---

# What Are Properties?

A **property** is a named value that stores information about an object.

Properties describe the characteristics or state of an object.

For example:

```javascript
const student = {

    name: "Ada",

    age: 21,

    department: "Computer Science"

};
```

In this object:

- `name` is a property.
- `age` is a property.
- `department` is a property.

Each property stores a value that describes the student.

---

## Figure 12.17

**Object Properties**

```text
Student

│

├── name → "Ada"

├── age → 21

└── department → "Computer Science"
```

---

# Properties Can Store Different Data Types

A property can store almost any JavaScript value.

Example:

```javascript
const employee = {

    name: "David",

    age: 35,

    fullTime: true,

    salary: 850000,

    skills: ["HTML", "CSS", "JavaScript"]

};
```

Property values may include:

- Strings
- Numbers
- Booleans
- Arrays
- Objects
- Functions
- Even other objects

This flexibility makes objects powerful and expressive.

---

# What Are Methods?

A **method** is a function that belongs to an object.

While properties describe an object, methods define what the object can do.

Example:

```javascript
const student = {

    name: "Ada",

    greet() {

        console.log("Hello!");

    }

};

student.greet();
```

Output

```text
Hello!
```

Here, `greet()` is a method because it is a function stored inside the object.

---

## Figure 12.18

**Properties vs Methods**

```text
Student

Properties

────────────

name

age

department

────────────

Methods

────────────

greet()

study()

graduate()
```

---

# Why Use Methods?

Methods allow related behavior to stay with the data it operates on.

Consider the following object:

```javascript
const bankAccount = {

    owner: "Ada",

    balance: 50000,

    deposit(amount) {

        this.balance += amount;

    }

};
```

The `deposit()` method changes the account's balance.

Instead of creating a separate function elsewhere in the program, the behavior is stored inside the object where it naturally belongs.

---

# Methods Can Accept Parameters

Methods work just like ordinary functions.

They can receive parameters.

Example:

```javascript
const calculator = {

    add(a, b) {

        return a + b;

    }

};

console.log(calculator.add(5, 7));
```

Output

```text
12
```

The only difference is that the function belongs to an object.

---

# Methods Can Return Values

Methods may also return results.

Example:

```javascript
const rectangle = {

    length: 10,

    width: 5,

    area() {

        return this.length * this.width;

    }

};

console.log(rectangle.area());
```

Output

```text
50
```

The `area()` method calculates and returns the rectangle's area.

---

# Property vs Method

Consider this object:

```javascript
const car = {

    brand: "Toyota",

    color: "Blue",

    start() {

        console.log("Engine started.");

    }

};
```

Here:

| Member | Type |
|---------|------|
| `brand` | Property |
| `color` | Property |
| `start()` | Method |

Properties hold values.

Methods perform actions.

---

## Figure 12.19

**Relationship Between Properties and Methods**

```text
Object

│

├── Properties

│     Store Data

│

└── Methods

      Perform Actions
```

---

# Real-World Example

Imagine a library book.

Properties:

- Title
- Author
- ISBN
- Available

Methods:

- borrow()
- returnBook()
- displayDetails()

Everything related to the book is grouped together in one object.

This organization is one of the strengths of Object-Oriented Programming.

---

# Benefits of Properties and Methods

Using properties and methods together helps you:

- Keep related information together.
- Improve code readability.
- Reduce duplication.
- Build reusable objects.
- Model real-world entities naturally.

---

# Best Practices

- Use nouns for property names.
- Use verbs for method names.
- Keep methods focused on one task.
- Choose meaningful names.
- Store only related data inside an object.

---

# Common Beginner Mistakes

## Mistake 1

Treating properties and methods as the same thing.

Properties store values.

Methods perform actions.

---

## Mistake 2

Giving methods noun-like names.

Instead of:

```javascript
student.registration
```

Use:

```javascript
student.register()
```

Methods should describe actions.

---

## Mistake 3

Creating methods that perform too many unrelated tasks.

A method should have a clear and single responsibility.

---

# Section Summary

In this section, you learned that objects consist of **properties** and **methods**. Properties store information about an object, while methods define the actions the object can perform. You also learned that methods are simply functions stored inside objects and that they can accept parameters, return values, and operate on the object's data. Understanding this distinction is fundamental to writing organized, object-oriented JavaScript code.

In the next section, you will learn how to **access object properties** using **dot notation** and **bracket notation**, two essential techniques for working with objects in JavaScript.

---

# CodeTales Insight

> **Properties describe an object, while methods bring it to life. Together, they allow you to model real-world entities in code, making your programs more intuitive, organized, and easier to maintain. Mastering the relationship between properties and methods is a foundational step toward writing professional object-oriented JavaScript applications.**

---

# 12.6 Accessing Object Properties

Creating an object is only the first step. To make an object useful, you must be able to retrieve the values stored in its properties.

JavaScript provides two primary ways to access object properties:

- Dot notation (`.`)
- Bracket notation (`[]`)

Both approaches allow you to retrieve the value of a property, but each has situations where it is more appropriate.

---

# Dot Notation

**Dot notation** is the simplest and most commonly used way to access an object's properties.

Syntax:

```javascript
objectName.propertyName
```

Example:

```javascript
const student = {

    name: "Ada",

    age: 21,

    department: "Computer Science"

};

console.log(student.name);

console.log(student.age);

console.log(student.department);
```

Output

```text
Ada

21

Computer Science
```

The dot (`.`) tells JavaScript to retrieve a specific property from the object.

---

## Figure 12.20

**Accessing Properties Using Dot Notation**

```text
student

│

├── name

├── age

└── department

student.name

↓

"Ada"
```

---

# Accessing Methods with Dot Notation

Dot notation is also used to call methods.

Example:

```javascript
const student = {

    name: "Ada",

    greet() {

        console.log("Welcome!");

    }

};

student.greet();
```

Output

```text
Welcome!
```

Notice the parentheses `()`.

Without them, JavaScript refers to the function itself instead of executing it.

---

# Bracket Notation

JavaScript also allows properties to be accessed using **bracket notation**.

Syntax:

```javascript
objectName["propertyName"]
```

Example:

```javascript
const student = {

    name: "Ada",

    age: 21

};

console.log(student["name"]);

console.log(student["age"]);
```

Output

```text
Ada

21
```

Bracket notation produces the same result as dot notation.

---

## Figure 12.21

**Accessing Properties Using Bracket Notation**

```text
student

↓

"name"

↓

"Ada"
```

---

# Dot Notation vs Bracket Notation

These two examples are equivalent.

Dot notation

```javascript
student.name
```

Bracket notation

```javascript
student["name"]
```

Both return:

```text
Ada
```

---

# When Should You Use Dot Notation?

Use dot notation when the property name is known and follows JavaScript identifier rules.

Example:

```javascript
const book = {

    title: "Cracking JavaScript",

    author: "CodeTales Africa"

};

console.log(book.title);

console.log(book.author);
```

Dot notation is:

- Shorter
- Easier to read
- More commonly used

---

# When Should You Use Bracket Notation?

Bracket notation is useful when the property name:

- Is stored in a variable.
- Contains spaces.
- Contains special characters.
- Is determined dynamically at runtime.

Example:

```javascript
const student = {

    name: "Ada",

    age: 21

};

const property = "name";

console.log(student[property]);
```

Output

```text
Ada
```

Dot notation cannot do this.

Incorrect:

```javascript
console.log(student.property);
```

Output

```text
undefined
```

JavaScript looks for a property literally named `property`, which does not exist.

---

# Properties with Spaces

Suppose an object contains a property with spaces.

Example:

```javascript
const employee = {

    "full name": "David Johnson"

};

console.log(employee["full name"]);
```

Output

```text
David Johnson
```

Dot notation cannot be used here.

Incorrect:

```javascript
employee.full name
```

This causes a syntax error.

---

# Dynamic Property Access

One advantage of bracket notation is that it supports dynamic property names.

Example:

```javascript
const product = {

    name: "Laptop",

    price: 350000,

    quantity: 12

};

const key = "price";

console.log(product[key]);
```

Output

```text
350000
```

This technique is common in large applications where property names are determined while the program is running.

---

## Figure 12.22

**Dynamic Property Access**

```text
Variable

↓

"price"

↓

product["price"]

↓

350000
```

---

# Accessing Nested Object Properties

Objects often contain other objects.

Example:

```javascript
const student = {

    name: "Ada",

    address: {

        city: "Enugu",

        country: "Nigeria"

    }

};

console.log(student.address.city);

console.log(student.address.country);
```

Output

```text
Enugu

Nigeria
```

Each dot moves one level deeper into the object.

---

# Combining Dot and Bracket Notation

Both approaches can be combined.

Example:

```javascript
const student = {

    address: {

        city: "Enugu"

    }

};

console.log(student["address"].city);
```

Output

```text
Enugu
```

This is perfectly valid JavaScript.

---

# Benefits of Dot Notation

- Easy to read
- Short syntax
- Preferred by most developers
- Ideal when property names are known

---

# Benefits of Bracket Notation

- Supports dynamic property names
- Works with variables
- Supports spaces and special characters
- Useful when working with APIs and JSON

---

# Best Practices

- Use dot notation whenever possible.
- Use bracket notation when property names are dynamic.
- Choose descriptive property names.
- Avoid spaces in property names unless necessary.
- Use consistent naming conventions.

---

# Common Beginner Mistakes

## Mistake 1

Forgetting quotation marks inside brackets.

Incorrect:

```javascript
student[name]
```

If `name` is not a variable, JavaScript throws an error.

Correct:

```javascript
student["name"]
```

---

## Mistake 2

Using dot notation for property names containing spaces.

Incorrect:

```javascript
employee.full name
```

Correct:

```javascript
employee["full name"]
```

---

## Mistake 3

Confusing variable names with property names.

Remember:

```javascript
student[property]
```

uses the value stored in `property`.

```javascript
student.property
```

looks for a property literally named `property`.

---

# Section Summary

In this section, you learned the two primary ways to access object properties in JavaScript: dot notation and bracket notation. You discovered that dot notation is the preferred approach for known property names, while bracket notation is essential for dynamic property access and properties containing spaces or special characters. You also learned how to access nested object properties and combine both notations when necessary.

In the next section, you will learn how to **add new properties, update existing properties, and delete properties** from objects.

---

# CodeTales Insight

> **Accessing object properties is one of the most common operations in JavaScript. While dot notation keeps your code clean and readable, bracket notation provides the flexibility needed for dynamic applications. Knowing when to use each approach is a hallmark of confident JavaScript developers.**

---

# 12.7 Adding, Updating, and Deleting Properties

Objects in JavaScript are dynamic. Unlike many programming languages where an object's structure is fixed after creation, JavaScript allows you to modify objects at any time.

You can:

- Add new properties.
- Update existing properties.
- Delete properties that are no longer needed.

This flexibility makes JavaScript objects extremely powerful for building dynamic applications.

---

# Adding New Properties

Adding a property to an object is straightforward.

Simply assign a value to a property that does not already exist.

Syntax:

```javascript
objectName.newProperty = value;
```

Example:

```javascript
const student = {

    name: "Ada",

    age: 21

};

student.department = "Computer Science";

console.log(student);
```

Output

```text
{
    name: "Ada",
    age: 21,
    department: "Computer Science"
}
```

JavaScript automatically creates the new property.

---

## Figure 12.23

**Adding a Property**

```text
Before

Student

├── name

└── age

↓

Add

department

↓

After

Student

├── name

├── age

└── department
```

---

# Adding Properties Using Bracket Notation

Properties can also be added using bracket notation.

Example:

```javascript
const student = {

    name: "Ada"

};

student["level"] = 300;

console.log(student);
```

Output

```text
{
    name: "Ada",
    level: 300
}
```

This approach is useful when the property name is stored in a variable.

---

# Dynamic Property Names

Example:

```javascript
const student = {

    name: "Ada"

};

const key = "department";

student[key] = "Computer Science";

console.log(student);
```

Output

```text
{
    name: "Ada",
    department: "Computer Science"
}
```

The value of `key` becomes the new property name.

---

# Updating Existing Properties

Updating a property works exactly like adding one.

If the property already exists, JavaScript replaces its value.

Example:

```javascript
const student = {

    name: "Ada",

    age: 21

};

student.age = 22;

console.log(student.age);
```

Output

```text
22
```

The old value is overwritten.

---

## Figure 12.24

**Updating a Property**

```text
Before

age

↓

21

↓

Update

↓

22
```

---

# Updating Multiple Properties

You can update several properties one after another.

Example:

```javascript
const employee = {

    name: "David",

    salary: 500000,

    department: "Sales"

};

employee.salary = 650000;

employee.department = "Marketing";

console.log(employee);
```

Output

```text
{
    name: "David",
    salary: 650000,
    department: "Marketing"
}
```

---

# Deleting Properties

JavaScript provides the `delete` operator to remove properties from an object.

Syntax:

```javascript
delete objectName.propertyName;
```

Example:

```javascript
const student = {

    name: "Ada",

    age: 21,

    department: "Computer Science"

};

delete student.age;

console.log(student);
```

Output

```text
{
    name: "Ada",
    department: "Computer Science"
}
```

The `age` property no longer exists.

---

## Figure 12.25

**Deleting a Property**

```text
Before

Student

├── name

├── age

└── department

↓

Delete age

↓

After

Student

├── name

└── department
```

---

# Deleting with Bracket Notation

Example:

```javascript
const product = {

    name: "Laptop",

    price: 350000

};

delete product["price"];

console.log(product);
```

Output

```text
{
    name: "Laptop"
}
```

---

# Checking Whether a Property Exists

Sometimes you need to determine whether an object contains a particular property.

Use the `in` operator.

Example:

```javascript
const student = {

    name: "Ada",

    age: 21

};

console.log("age" in student);

console.log("department" in student);
```

Output

```text
true

false
```

---

# What Happens If You Delete a Non-Existent Property?

Deleting a property that does not exist does not produce an error.

Example:

```javascript
const student = {

    name: "Ada"

};

delete student.department;

console.log(student);
```

Output

```text
{
    name: "Ada"
}
```

Nothing changes.

---

# Adding Methods

Methods can be added just like properties.

Example:

```javascript
const student = {

    name: "Ada"

};

student.greet = function () {

    console.log("Welcome!");

};

student.greet();
```

Output

```text
Welcome!
```

Remember that methods are simply properties whose values are functions.

---

# Replacing Methods

Methods can also be replaced.

Example:

```javascript
const student = {

    greet() {

        console.log("Hello!");

    }

};

student.greet = function () {

    console.log("Good morning!");

};

student.greet();
```

Output

```text
Good morning!
```

---

# Real-World Example

Suppose an online shopping application stores product information.

```javascript
const product = {

    name: "Laptop",

    price: 350000

};
```

Later:

```javascript
product.quantity = 15;

product.price = 320000;

delete product.discount;
```

The object changes as the application's data changes.

---

# Best Practices

- Use meaningful property names.
- Avoid deleting properties unless necessary.
- Update only the properties that need to change.
- Prefer dot notation when property names are known.
- Use bracket notation for dynamic property names.

---

# Common Beginner Mistakes

## Mistake 1

Thinking that adding a property requires recreating the object.

JavaScript objects can be modified at any time.

---

## Mistake 2

Using `delete` to remove variables.

`delete` removes object properties—not variables declared with `let`, `const`, or `var`.

---

## Mistake 3

Assuming deleting a property destroys the object.

Only the specified property is removed. The object itself remains.

---

# Section Summary

In this section, you learned how to modify JavaScript objects after they have been created. You discovered how to add new properties, update existing ones, delete unwanted properties, and check whether a property exists using the `in` operator. You also learned that methods can be added, updated, and removed just like any other property. These capabilities make JavaScript objects highly flexible and adaptable to changing application requirements.

In the next section, you will explore **Object Methods** in greater depth and learn how methods allow objects to perform meaningful actions and interact with their own data.

---

# CodeTales Insight

> **One of JavaScript's greatest strengths is the flexibility of its objects. They can evolve as your application evolves—gaining new properties, updating existing information, and discarding what is no longer needed. Learning to modify objects confidently is an essential skill for building dynamic, real-world applications.**

---

# 12.8 Object Methods

In the previous section, you learned how to add, update, and delete object properties. While properties describe an object's characteristics, they do not define what an object can do.

Objects become much more useful when they contain **methods**.

Methods allow objects to perform actions, process data, and interact with their own properties. In Object-Oriented Programming (OOP), methods represent the behavior of an object.

---

# What Is an Object Method?

An **object method** is simply a function stored as a property of an object.

Unlike ordinary functions, methods belong to a specific object.

Example:

```javascript
const student = {

    name: "Ada",

    greet() {

        console.log("Welcome to JavaScript!");

    }

};

student.greet();
```

Output

```text
Welcome to JavaScript!
```

Here:

- `name` is a property.
- `greet()` is a method.

---

## Figure 12.26

**An Object Containing a Method**

```text
Student Object

│

├── name

└── greet()

        │

        ▼

Displays a message
```

---

# Why Do Objects Need Methods?

Imagine a banking application.

The account stores information such as:

- Account Name
- Account Number
- Balance

But a bank account should also be able to:

- Deposit money
- Withdraw money
- Display balance

Those actions are represented as methods.

Example:

```javascript
const account = {

    owner: "Ada",

    balance: 50000,

    deposit(amount) {

        this.balance += amount;

    }

};
```

Methods give an object functionality.

---

# Different Ways to Define Methods

JavaScript provides multiple ways to create object methods.

### Method Shorthand (Recommended)

```javascript
const student = {

    greet() {

        console.log("Hello!");

    }

};
```

---

### Function Expression

```javascript
const student = {

    greet: function () {

        console.log("Hello!");

    }

};
```

Both produce the same result.

The shorthand syntax is preferred in modern JavaScript because it is shorter and easier to read.

---

# Calling Object Methods

Methods are called using dot notation followed by parentheses.

Syntax

```javascript
objectName.methodName();
```

Example

```javascript
const calculator = {

    add() {

        console.log(10 + 5);

    }

};

calculator.add();
```

Output

```text
15
```

Without the parentheses, JavaScript returns the function itself instead of executing it.

Example

```javascript
console.log(calculator.add);
```

Output

```text
[Function: add]
```

---

# Methods Can Accept Parameters

Methods work exactly like normal functions.

They can receive parameters.

Example

```javascript
const calculator = {

    multiply(a, b) {

        return a * b;

    }

};

console.log(calculator.multiply(6, 7));
```

Output

```text
42
```

Parameters make methods reusable.

---

# Methods Can Return Values

Methods often calculate and return results.

Example

```javascript
const rectangle = {

    length: 12,

    width: 8,

    area() {

        return this.length * this.width;

    }

};

console.log(rectangle.area());
```

Output

```text
96
```

The returned value can be stored or used elsewhere in the program.

---

## Figure 12.27

**Method Execution**

```text
rectangle.area()

↓

Method Executes

↓

Returns

96
```

---

# Objects Can Have Multiple Methods

An object may contain several methods.

Example

```javascript
const player = {

    name: "David",

    play() {

        console.log("Playing...");

    },

    pause() {

        console.log("Paused.");

    },

    stop() {

        console.log("Stopped.");

    }

};

player.play();

player.pause();

player.stop();
```

Output

```text
Playing...

Paused.

Stopped.
```

Each method performs a different task.

---

# Methods Can Call Other Methods

Methods inside the same object can work together.

Example

```javascript
const printer = {

    start() {

        console.log("Printer started.");

    },

    print() {

        this.start();

        console.log("Printing document...");

    }

};

printer.print();
```

Output

```text
Printer started.

Printing document...
```

This promotes code reuse and avoids duplication.

---

# Methods and the `this` Keyword

Methods frequently need access to the object's own properties.

Example

```javascript
const student = {

    name: "Ada",

    greet() {

        console.log("Hello, " + this.name);

    }

};

student.greet();
```

Output

```text
Hello, Ada
```

The keyword `this` refers to the current object.

You will study `this` in detail in the next section.

---

## Figure 12.28

**Method Accessing Object Data**

```text
Student

│

├── name

└── greet()

        │

        ▼

this.name

        │

        ▼

"Ada"
```

---

# Real-World Example

Imagine an online shopping application.

```javascript
const product = {

    name: "Laptop",

    price: 350000,

    discount(percent) {

        return this.price - (this.price * percent / 100);

    }

};

console.log(product.discount(10));
```

Output

```text
315000
```

The method performs a useful calculation using the object's own data.

---

# Benefits of Object Methods

Object methods help developers:

- Organize related behavior.
- Reuse code.
- Improve readability.
- Reduce duplication.
- Model real-world actions.
- Build maintainable applications.

Methods are one of the key features that make Object-Oriented Programming powerful.

---

# Best Practices

- Use verbs when naming methods.
- Keep each method focused on one responsibility.
- Return values instead of printing them when appropriate.
- Use method shorthand in modern JavaScript.
- Group related methods within the same object.

---

# Common Beginner Mistakes

## Mistake 1

Forgetting the parentheses when calling a method.

Incorrect

```javascript
student.greet;
```

Correct

```javascript
student.greet();
```

---

## Mistake 2

Writing very large methods.

Large methods become difficult to understand and maintain.

Break complex tasks into smaller methods.

---

## Mistake 3

Creating methods that are unrelated to the object.

Every method should describe something the object naturally does.

---

# Section Summary

In this section, you learned that object methods are functions stored inside objects that define an object's behavior. You discovered different ways to define methods, how to call them, pass arguments, return values, and organize multiple methods within a single object. You also received an introduction to the `this` keyword, which allows methods to access the object's own properties. Understanding object methods is an essential step toward mastering Object-Oriented Programming in JavaScript.

In the next section, you will study the **`this` keyword** in depth and learn how JavaScript determines what `this` refers to in different contexts.

---

# CodeTales Insight

> **Properties describe an object's state, but methods give it purpose. A well-designed object doesn't just hold information—it knows how to use that information to perform meaningful actions. This combination of data and behavior is the essence of Object-Oriented Programming and one of the reasons it remains a dominant approach to software development.**


---

# 12.9 Understanding the `this` Keyword

The `this` keyword is one of the most powerful—and often misunderstood—features of JavaScript.

Many beginners assume that `this` always refers to the object where it was written. In reality, the value of `this` depends on **how a function is called**, not where it is defined.

Understanding `this` is essential because it is widely used in:

- Object methods
- Constructor functions
- ES6 classes
- Event handlers
- JavaScript frameworks
- Browser APIs

Mastering `this` will help you write cleaner, more predictable, and professional JavaScript code.

---

# What Is `this`?

The keyword `this` is a special JavaScript keyword that refers to **an object**.

Exactly **which object** it refers to depends on the context in which it is used.

Think of `this` as meaning:

> **"the current object."**

---

# `this` Inside an Object Method

The most common use of `this` is inside object methods.

Example:

```javascript
const student = {

    name: "Ada",

    age: 21,

    introduce() {

        console.log("My name is " + this.name);

    }

};

student.introduce();
```

Output

```text
My name is Ada
```

Notice:

```javascript
this.name
```

is the same as writing

```javascript
student.name
```

except that `this` makes the code reusable.

---

## Figure 12.29

**`this` Inside an Object**

```text
Student Object

│

├── name

│      │

│      ▼

│    "Ada"

│

└── introduce()

        │

        ▼

    this.name

        │

        ▼

      "Ada"
```

---

# Why Not Use the Object Name?

Instead of:

```javascript
const student = {

    name: "Ada",

    introduce() {

        console.log(student.name);

    }

};
```

we write

```javascript
const student = {

    name: "Ada",

    introduce() {

        console.log(this.name);

    }

};
```

Using `this` makes the method reusable.

If the object name changes, the method still works correctly.

---

# Another Example

```javascript
const car = {

    brand: "Toyota",

    start() {

        console.log(this.brand + " started.");

    }

};

car.start();
```

Output

```text
Toyota started.
```

Again,

```javascript
this.brand
```

refers to

```javascript
car.brand
```

---

# `this` Refers to the Object Before the Dot

Consider:

```javascript
const student = {

    name: "Ada",

    show() {

        console.log(this.name);

    }

};

student.show();
```

Output

```text
Ada
```

The object before the dot is

```javascript
student
```

Therefore,

```javascript
this
```

refers to `student`.

---

## Figure 12.30

**Object Before the Dot**

```text
student.show()

│

▼

student

↓

this

↓

Student Object
```

---

# Methods Access Their Own Properties

Consider:

```javascript
const employee = {

    name: "David",

    salary: 500000,

    displaySalary() {

        console.log(this.salary);

    }

};

employee.displaySalary();
```

Output

```text
500000
```

The method retrieves information from the same object.

---

# Objects Can Share Methods

Suppose two different objects have similar methods.

```javascript
const person1 = {

    name: "Ada",

    greet() {

        console.log("Hello " + this.name);

    }

};

const person2 = {

    name: "John",

    greet() {

        console.log("Hello " + this.name);

    }

};

person1.greet();

person2.greet();
```

Output

```text
Hello Ada

Hello John
```

The same logic works because `this` refers to the object that called the method.

---

# `this` Inside Regular Functions

Consider:

```javascript
function show() {

    console.log(this);

}

show();
```

In browsers (non-strict mode), `this` usually refers to the global object (`window`).

In strict mode, it is `undefined`.

For beginners, the most important rule is:

> Inside object methods, `this` refers to the object that calls the method.

You will learn more advanced behavior later in your JavaScript journey.

---

# Common Uses of `this`

The `this` keyword is frequently used to:

- Access object properties
- Call another method in the same object
- Update object data
- Build reusable classes
- Create constructor functions

It is one of the foundations of Object-Oriented Programming.

---

# Real-World Example

Imagine an online bank account.

```javascript
const account = {

    owner: "Ada",

    balance: 50000,

    deposit(amount) {

        this.balance += amount;

    }

};

account.deposit(10000);

console.log(account.balance);
```

Output

```text
60000
```

The method updates the balance belonging to the same object.

---

## Figure 12.31

**Using `this` to Modify Object Data**

```text
deposit()

↓

this.balance

↓

50000

↓

+10000

↓

60000
```

---

# Benefits of Using `this`

Using `this` makes your code:

- Reusable
- Flexible
- Easier to maintain
- Independent of object names
- More suitable for classes and constructors

Without `this`, Object-Oriented Programming would be much less practical.

---

# Best Practices

- Use `this` inside object methods to access the object's own properties.
- Prefer `this` instead of hardcoding object names.
- Keep methods focused on the object they belong to.
- Learn how `this` behaves before working with classes.

---

# Common Beginner Mistakes

## Mistake 1

Using the object name instead of `this`.

```javascript
student.name
```

works, but

```javascript
this.name
```

is more reusable.

---

## Mistake 2

Assuming `this` always refers to the same object.

It depends on **how the function is called**.

---

## Mistake 3

Thinking `this` stores a fixed value.

It does not.

JavaScript determines its value at runtime.

---

# Section Summary

In this section, you learned that the `this` keyword refers to an object, but the exact object depends on how a function is called. You discovered how `this` allows methods to access and modify an object's own properties, making code more reusable and maintainable. You also learned why using `this` is preferable to hardcoding object names and why it is a cornerstone of Object-Oriented Programming in JavaScript.

In the next section, you will learn about **constructor functions**, one of the traditional ways JavaScript creates multiple objects before the introduction of ES6 classes.

---

# CodeTales Insight

> **The `this` keyword is not a variable—it is a relationship. It connects a method to the object that invoked it, allowing that method to work with the object's own data. Once you understand this relationship, many advanced JavaScript concepts, including constructor functions and classes, become much easier to grasp.**

---

# 12.10 Constructor Functions

In the previous section, you learned how the `this` keyword enables object methods to access and modify their own data. While object literals are excellent for creating individual objects, they become inefficient when you need to create many objects with the same structure.

Imagine building a school management system with thousands of students.

Using object literals, you might write:

```javascript
const student1 = {

    name: "Ada",

    age: 21,

    department: "Computer Science"

};

const student2 = {

    name: "John",

    age: 20,

    department: "Software Engineering"

};

const student3 = {

    name: "Grace",

    age: 22,

    department: "Cybersecurity"

};
```

Although the values are different, the structure is identical.

Repeating the same code hundreds or thousands of times violates one of the most important principles of programming:

> **Don't Repeat Yourself (DRY).**

Constructor functions solve this problem by providing a reusable blueprint for creating multiple similar objects.

---

# What Is a Constructor Function?

A **constructor function** is a special function used to create and initialize objects.

Unlike ordinary functions, constructor functions are intended to be called with the `new` keyword.

By convention, constructor function names begin with a capital letter.

Example:

```javascript
function Student(name, age, department) {

    this.name = name;

    this.age = age;

    this.department = department;

}
```

Notice the use of:

- `this`
- Capitalized function name (`Student`)

These are conventions that make constructor functions easy to recognize.

---

## Figure 12.32

**Constructor Function as a Blueprint**

```text
Constructor Function

        │

        ▼

Blueprint

        │

        ▼

Student Objects

Student A

Student B

Student C
```

---

# Creating Objects with a Constructor Function

Once the constructor function has been defined, you can create objects from it.

Example:

```javascript
function Student(name, age, department) {

    this.name = name;

    this.age = age;

    this.department = department;

}

const student1 = new Student(

    "Ada",

    21,

    "Computer Science"

);

const student2 = new Student(

    "John",

    20,

    "Software Engineering"

);

console.log(student1);

console.log(student2);
```

Output

```text
Student {

    name: "Ada",

    age: 21,

    department: "Computer Science"

}

Student {

    name: "John",

    age: 20,

    department: "Software Engineering"

}
```

Each object has its own independent data.

---

# How Constructor Functions Work

When JavaScript executes:

```javascript
new Student(...)
```

it performs several steps automatically:

1. Creates a new empty object.
2. Sets `this` to refer to the new object.
3. Adds the specified properties.
4. Returns the completed object.

These steps happen behind the scenes.

---

## Figure 12.33

**Creating an Object**

```text
new Student()

        │

        ▼

Create Empty Object

        │

        ▼

Assign Properties

        │

        ▼

Return Object
```

---

# Constructor Parameters

Constructor functions receive parameters just like ordinary functions.

Example:

```javascript
function Employee(name, salary) {

    this.name = name;

    this.salary = salary;

}

const employee = new Employee(

    "David",

    850000

);

console.log(employee);
```

Output

```text
Employee {

    name: "David",

    salary: 850000

}
```

Each parameter becomes part of the new object.

---

# Adding Methods to Constructor Functions

Constructor functions can also define methods.

Example:

```javascript
function Student(name) {

    this.name = name;

    this.greet = function () {

        console.log(

            "Hello, " + this.name

        );

    };

}

const student = new Student("Ada");

student.greet();
```

Output

```text
Hello, Ada
```

The object now contains both data and behavior.

---

# Multiple Objects from One Constructor

One constructor can create many objects.

Example:

```javascript
const student1 = new Student("Ada");

const student2 = new Student("John");

const student3 = new Student("Grace");
```

All three objects share the same structure but contain different values.

---

## Figure 12.34

**One Constructor, Many Objects**

```text
Student()

│

├── student1

├── student2

├── student3

└── student4
```

---

# Why Use Constructor Functions?

Constructor functions provide several benefits:

- Reduce repeated code.
- Create objects consistently.
- Improve readability.
- Simplify maintenance.
- Form the basis of traditional JavaScript OOP.

Before ES6 classes were introduced, constructor functions were the standard way to build reusable objects.

---

# Constructor Function Naming Convention

Constructor functions are usually written using **PascalCase**.

Examples:

```javascript
Student

Employee

Product

BankAccount

Rectangle
```

Ordinary functions typically use camelCase.

Example:

```javascript
calculateArea()

displayMessage()

registerStudent()
```

Following these naming conventions makes your code easier to understand.

---

# Constructor Functions vs Object Literals

Object Literal

```javascript
const student = {

    name: "Ada"

};
```

Constructor Function

```javascript
const student = new Student(

    "Ada"

);
```

Object literals are ideal for creating one or two objects.

Constructor functions are better when creating many similar objects.

---

# Best Practices

- Name constructor functions using PascalCase.
- Always use the `new` keyword when calling a constructor.
- Keep constructors focused on initializing object data.
- Avoid placing large amounts of business logic inside constructors.
- Use meaningful parameter names.

---

# Common Beginner Mistakes

## Mistake 1

Calling a constructor without `new`.

Incorrect:

```javascript
const student = Student(

    "Ada"

);
```

This does not create a new object correctly.

Correct:

```javascript
const student = new Student(

    "Ada"

);
```

---

## Mistake 2

Using lowercase names for constructors.

Incorrect:

```javascript
function student() {}
```

Preferred:

```javascript
function Student() {}
```

---

## Mistake 3

Confusing constructor functions with ordinary functions.

Constructor functions are designed to create objects, while ordinary functions perform general tasks.

---

# Section Summary

In this section, you learned that constructor functions provide a reusable blueprint for creating multiple objects with the same structure. You discovered how constructor functions use parameters to initialize object properties, how the `this` keyword refers to the newly created object, and why constructor functions reduce code duplication. You also learned the importance of the `new` keyword and the PascalCase naming convention.

In the next section, you will examine the **`new` keyword** in detail and discover exactly what JavaScript does behind the scenes each time a new object is created.

---

# CodeTales Insight

> **Constructor functions marked JavaScript's first major step toward object-oriented programming. Although modern applications often use ES6 classes, constructor functions remain an important part of the language's history and foundation. Understanding them will help you read legacy code, appreciate how classes work internally, and become a more complete JavaScript developer.**

---

# 12.11 The `new` Keyword

In the previous section, you learned how constructor functions allow you to create multiple objects from a single blueprint. Every time you created an object, you used the `new` keyword.

For example:

```javascript
const student = new Student(

    "Ada",

    21,

    "Computer Science"

);
```

Although this syntax looks simple, JavaScript performs several important operations behind the scenes.

Understanding the `new` keyword helps you understand how objects are actually created and why constructor functions work the way they do.

---

# What Is the `new` Keyword?

The `new` keyword tells JavaScript to create a **new object** using a constructor function.

It transforms an ordinary function into an object creator.

Without `new`, a constructor function behaves like a normal function.

With `new`, JavaScript creates and returns a brand-new object.

---

# Basic Example

```javascript
function Student(name) {

    this.name = name;

}

const student = new Student("Ada");

console.log(student);
```

Output

```text
Student {

    name: "Ada"

}
```

The object was automatically created by the `new` keyword.

---

## Figure 12.35

**Creating an Object with `new`**

```text
Constructor Function

        │

new Student()

        │

        ▼

New Object Created

        │

        ▼

Properties Initialized

        │

        ▼

Object Returned
```

---

# What Happens Behind the Scenes?

When JavaScript executes:

```javascript
new Student("Ada")
```

it performs four important steps automatically.

---

## Step 1 — Create an Empty Object

JavaScript first creates a brand-new empty object.

Conceptually:

```javascript
const obj = {};
```

This object is created automatically.

---

## Step 2 — Bind `this` to the New Object

Next, JavaScript makes `this` refer to the newly created object.

Inside the constructor:

```javascript
this.name = name;
```

actually becomes

```javascript
obj.name = name;
```

because `this` now points to the new object.

---

## Step 3 — Link the Object to the Constructor's Prototype

JavaScript connects the new object to the constructor's prototype.

This enables the object to inherit shared methods and properties.

You will study prototypes in the next chapter section.

---

## Step 4 — Return the New Object

Finally, JavaScript automatically returns the completed object.

Conceptually:

```javascript
return obj;
```

This return statement is added automatically.

---

## Figure 12.36

**The Four Steps of `new`**

```text
new Student()

        │

        ▼

1. Create Empty Object

        │

        ▼

2. Bind this

        │

        ▼

3. Connect Prototype

        │

        ▼

4. Return Object
```

---

# Why Is `new` Necessary?

Consider this constructor.

```javascript
function Student(name) {

    this.name = name;

}
```

Correct usage:

```javascript
const student = new Student("Ada");
```

Without `new`:

```javascript
const student = Student("Ada");
```

The constructor no longer creates an object.

Instead, it behaves like an ordinary function.

Depending on whether strict mode is enabled, this can result in unexpected behavior or even an error.

---

# Example with `new`

```javascript
function Employee(name) {

    this.name = name;

}

const employee = new Employee("David");

console.log(employee.name);
```

Output

```text
David
```

---

# Example Without `new`

```javascript
function Employee(name) {

    this.name = name;

}

Employee("David");
```

In modern JavaScript (strict mode), this typically produces:

```text
TypeError
```

because `this` is `undefined`.

This is one reason why constructor functions should always be called with `new`.

---

# Every Object Is Independent

Each time you use `new`, JavaScript creates a completely new object.

Example:

```javascript
function Student(name) {

    this.name = name;

}

const student1 = new Student("Ada");

const student2 = new Student("John");

console.log(student1);

console.log(student2);
```

Output

```text
Student { name: "Ada" }

Student { name: "John" }
```

Although both objects were created from the same constructor, they are separate objects.

---

## Figure 12.37

**Multiple Objects Created**

```text
Student()

│

├── new

│     │

│     ▼

│   Object 1

│

├── new

│     │

│     ▼

│   Object 2

│

└── new

      │

      ▼

    Object 3
```

---

# The `instanceof` Operator

JavaScript provides the `instanceof` operator to determine whether an object was created by a particular constructor.

Example:

```javascript
function Student(name) {

    this.name = name;

}

const student = new Student("Ada");

console.log(student instanceof Student);
```

Output

```text
true
```

This confirms that the object was created using the `Student` constructor.

---

# Constructor Functions and `new`

Remember:

```javascript
new Student()
```

means:

> "Create a brand-new object using the `Student` constructor."

The constructor itself does not create the object.

The `new` keyword performs that task.

---

# Real-World Example

Suppose a company hires many employees.

Instead of manually creating every employee object:

```javascript
const employee1 = {

    name: "David"

};

const employee2 = {

    name: "Grace"

};
```

You simply write:

```javascript
const employee1 = new Employee("David");

const employee2 = new Employee("Grace");

const employee3 = new Employee("John");
```

Each call creates a completely new employee object.

---

# Best Practices

- Always use `new` when calling constructor functions.
- Name constructors using PascalCase.
- Keep constructors focused on initializing object data.
- Use constructors when creating many similar objects.
- Avoid calling constructors like ordinary functions.

---

# Common Beginner Mistakes

## Mistake 1

Forgetting the `new` keyword.

This prevents JavaScript from creating a new object.

---

## Mistake 2

Thinking the constructor creates the object.

The constructor initializes the object.

The `new` keyword creates it.

---

## Mistake 3

Assuming all objects created from one constructor are the same object.

Each call to `new` creates a separate object.

---

# Section Summary

In this section, you learned that the `new` keyword creates a new object from a constructor function. You explored the four steps JavaScript performs behind the scenes: creating an empty object, binding `this` to that object, linking it to the constructor's prototype, and returning the completed object. You also learned why omitting `new` causes problems and how the `instanceof` operator verifies an object's constructor. These concepts form the foundation for understanding JavaScript's prototype system.

In the next section, you will explore **prototypes and the prototype chain**, one of JavaScript's most powerful features and the mechanism that enables inheritance.

---

# CodeTales Insight

> **The `new` keyword does far more than call a function—it creates an entirely new object, establishes its relationship with a constructor, and prepares it for inheritance through the prototype chain. Once you understand what happens behind the scenes, constructor functions and classes become much less mysterious, and JavaScript's object model begins to make perfect sense.**

---

# 12.12 Prototypes and the Prototype Chain

In the previous section, you learned how the `new` keyword creates objects from constructor functions. However, one important question remains:

> **How do multiple objects created from the same constructor share common behavior without duplicating code?**

The answer is **prototypes**.

Prototypes are one of JavaScript's most powerful features. They allow objects to share methods efficiently, reducing memory usage and making applications easier to maintain.

Understanding prototypes is essential because:

- Constructor functions rely on them.
- ES6 classes are built on them.
- JavaScript inheritance is powered by them.

---

# What Is a Prototype?

A **prototype** is another object that JavaScript uses as a fallback when a property or method cannot be found on the current object.

Every JavaScript object has an internal link to another object called its **prototype**.

When you try to access a property, JavaScript first searches the object itself.

If the property is not found, JavaScript automatically searches the object's prototype.

---

## Figure 12.38

**Object and Its Prototype**

```text
Student Object

│

├── name

├── age

│

└──────────────► Prototype

                    │

                    ├── greet()

                    ├── study()

                    └── graduate()
```

---

# Why Do Prototypes Exist?

Imagine creating one thousand student objects.

Without prototypes:

```javascript
student1.greet = function () {};

student2.greet = function () {};

student3.greet = function () {};
```

Each object stores its own copy of the same function.

This wastes memory.

Instead, JavaScript stores one shared method in the prototype.

Every object uses that single method.

---

# Adding Methods to the Prototype

Consider this constructor.

```javascript
function Student(name) {

    this.name = name;

}
```

Instead of placing methods inside the constructor:

```javascript
Student.prototype.greet = function () {

    console.log(

        "Hello, " + this.name

    );

};
```

Now create two students.

```javascript
const student1 = new Student("Ada");

const student2 = new Student("John");

student1.greet();

student2.greet();
```

Output

```text
Hello, Ada

Hello, John
```

Both objects use the same shared method.

---

## Figure 12.39

**Shared Prototype Method**

```text
Student.prototype

│

└── greet()

        ▲

        │

student1

student2

student3

student4
```

One method is shared by every object.

---

# How Property Lookup Works

Suppose we have:

```javascript
function Student(name) {

    this.name = name;

}

Student.prototype.country = "Nigeria";

const student = new Student("Ada");
```

Now execute:

```javascript
console.log(student.country);
```

Output

```text
Nigeria
```

Even though `country` does not exist inside `student`, JavaScript finds it inside the prototype.

---

## Figure 12.40

**Property Lookup**

```text
student

│

├── name

└── country ?

        │

        ▼

Prototype

│

└── country

↓

"Nigeria"
```

JavaScript searches upward until it finds the property.

---

# The Prototype Chain

If JavaScript cannot find a property in the object, it searches:

1. The object itself.
2. Its prototype.
3. The prototype's prototype.
4. And so on.

This process is called the **prototype chain**.

---

## Figure 12.41

**Prototype Chain**

```text
Object

↓

Prototype

↓

Prototype

↓

Prototype

↓

null
```

The search continues until JavaScript reaches `null`.

---

# Example of the Prototype Chain

```javascript
function Student(name) {

    this.name = name;

}

Student.prototype.country = "Nigeria";

const student = new Student("Ada");

console.log(student.name);

console.log(student.country);
```

Output

```text
Ada

Nigeria
```

Lookup process:

For `name`:

```text
Student Object

↓

Found
```

For `country`:

```text
Student Object

↓

Not Found

↓

Prototype

↓

Found
```

---

# Checking Prototype Relationships

JavaScript provides the `isPrototypeOf()` method.

Example:

```javascript
function Student() {}

const student = new Student();

console.log(

    Student.prototype.isPrototypeOf(student)

);
```

Output

```text
true
```

This confirms that the student's prototype is `Student.prototype`.

---

# Viewing an Object's Prototype

JavaScript provides:

```javascript
Object.getPrototypeOf()
```

Example:

```javascript
function Student() {}

const student = new Student();

console.log(

    Object.getPrototypeOf(student)

);
```

Output

```text
Student {}
```

This returns the prototype object.

---

# Why Use Prototypes?

Prototypes provide several advantages:

- Reduce memory usage.
- Avoid duplicate methods.
- Improve application performance.
- Enable inheritance.
- Support reusable code.

Without prototypes, every object would contain its own copy of every method.

---

# Real-World Example

Suppose a game contains 10,000 player objects.

Each player needs:

```javascript
move()

jump()

attack()

defend()
```

Without prototypes:

Each player stores four separate methods.

With prototypes:

All players share the same four methods.

This saves a significant amount of memory.

---

## Figure 12.42

**Without vs With Prototypes**

```text
Without Prototype

Player 1

├── move()

├── jump()

├── attack()

Player 2

├── move()

├── jump()

├── attack()

----------------------------

With Prototype

Player 1

Player 2

Player 3

      │

      ▼

Shared Prototype

├── move()

├── jump()

└── attack()
```

---

# Best Practices

- Store shared methods on the prototype.
- Keep constructors focused on initializing object data.
- Avoid duplicating identical methods inside every object.
- Learn prototypes before relying heavily on classes.
- Remember that classes use prototypes behind the scenes.

---

# Common Beginner Mistakes

## Mistake 1

Defining methods inside the constructor when every object uses the same implementation.

Move shared methods to the prototype instead.

---

## Mistake 2

Thinking prototypes copy methods into every object.

Objects share methods through the prototype—they do not receive separate copies.

---

## Mistake 3

Confusing prototypes with inheritance.

A prototype is the mechanism that enables inheritance; it is not inheritance itself.

---

# Section Summary

In this section, you learned that every JavaScript object has a prototype that acts as a fallback when properties or methods are not found on the object itself. You discovered how shared methods are stored on prototypes, how JavaScript searches through the prototype chain, and why this approach reduces memory usage and supports inheritance. Understanding prototypes provides the foundation for mastering JavaScript's object model and understanding how modern ES6 classes work internally.

In the next section, you will learn about **ES6 Classes**, the modern and more readable syntax for creating objects while still using JavaScript's prototype-based inheritance system.

---

# CodeTales Insight

> **Prototypes are the engine behind JavaScript's object-oriented programming model. While modern developers often write classes, the JavaScript engine still relies on prototypes to share methods and implement inheritance. Understanding prototypes allows you to see beyond the syntax and truly understand how JavaScript works under the hood.**

---

# 12.13 ES6 Classes

Until now, you have learned how JavaScript creates objects using object literals and constructor functions. Although constructor functions are powerful, they can become difficult to read as applications grow larger.

To make object-oriented programming easier to write and understand, **ECMAScript 2015 (ES6)** introduced **classes**.

Classes provide a cleaner and more organized syntax for creating objects.

It is important to understand that **JavaScript classes do not replace prototypes**. Instead, they provide a simpler way to work with JavaScript's prototype-based inheritance system.

---

# What Is a Class?

A **class** is a blueprint for creating objects.

It defines:

- The properties an object should have.
- The methods an object should perform.

Instead of repeatedly creating similar objects, you define a class once and create as many objects as needed.

---

## Figure 12.43

**Class as a Blueprint**

```text
Student Class

        │

        ▼

Blueprint

        │

        ▼

Student Objects

Student A

Student B

Student C
```

---

# Creating Your First Class

A class is declared using the `class` keyword.

Syntax:

```javascript
class ClassName {

}
```

Example:

```javascript
class Student {

}
```

By convention, class names use **PascalCase**.

Examples:

```text
Student

Employee

BankAccount

Rectangle

Product
```

---

# Creating Objects from a Class

Objects are created from a class using the `new` keyword.

Example:

```javascript
class Student {

}

const student = new Student();

console.log(student);
```

Output

```text
Student {}
```

The class acts as a blueprint for creating new objects.

---

# The Constructor Method

Every class may contain a special method named `constructor()`.

The constructor executes automatically whenever a new object is created.

Example:

```javascript
class Student {

    constructor(name, age) {

        this.name = name;

        this.age = age;

    }

}

const student = new Student(

    "Ada",

    21

);

console.log(student);
```

Output

```text
Student {

    name: "Ada",

    age: 21

}
```

---

## Figure 12.44

**Object Creation Using a Class**

```text
Student Class

        │

new Student()

        │

        ▼

constructor()

        │

        ▼

Object Created
```

---

# Adding Methods

Methods are written directly inside the class.

Example:

```javascript
class Student {

    constructor(name) {

        this.name = name;

    }

    greet() {

        console.log(

            "Hello, " + this.name

        );

    }

}

const student = new Student("Ada");

student.greet();
```

Output

```text
Hello, Ada
```

Notice that methods inside classes **do not use the `function` keyword**.

Incorrect:

```javascript
function greet() {

}
```

Correct:

```javascript
greet() {

}
```

---

# Creating Multiple Objects

One class can create many objects.

Example:

```javascript
const student1 = new Student("Ada");

const student2 = new Student("John");

const student3 = new Student("Grace");
```

Each object has its own data while sharing the same methods.

---

## Figure 12.45

**One Class, Many Objects**

```text
Student Class

│

├── Student 1

├── Student 2

├── Student 3

└── Student 4
```

---

# Classes Use Prototypes

Although classes look different from constructor functions, JavaScript still stores methods on the prototype.

For example:

```javascript
class Student {

    greet() {

        console.log("Hello");

    }

}
```

Behind the scenes, JavaScript behaves similarly to:

```javascript
function Student() {

}

Student.prototype.greet = function () {

    console.log("Hello");

};
```

This means classes are **syntactic sugar** over JavaScript's prototype system.

---

# Class Example

```javascript
class Rectangle {

    constructor(length, width) {

        this.length = length;

        this.width = width;

    }

    area() {

        return this.length * this.width;

    }

}

const rectangle = new Rectangle(

    12,

    8

);

console.log(rectangle.area());
```

Output

```text
96
```

The object stores both data and behavior.

---

# Constructor Functions vs Classes

Constructor Function

```javascript
function Student(name) {

    this.name = name;

}
```

Class

```javascript
class Student {

    constructor(name) {

        this.name = name;

    }

}
```

Both produce similar objects.

Classes simply provide cleaner syntax.

---

## Figure 12.46

**Constructor Function vs Class**

```text
Constructor Function

↓

Older Syntax

----------------------

Class

↓

Modern Syntax
```

---

# Why Use Classes?

Classes make programs:

- Easier to read.
- Easier to organize.
- Easier to maintain.
- More consistent.
- Better suited for large applications.

Most modern JavaScript applications use classes extensively.

---

# Best Practices

- Use PascalCase for class names.
- Keep constructors focused on initialization.
- Place behavior inside methods.
- Use meaningful method names.
- Create multiple objects from one class rather than duplicating code.

---

# Common Beginner Mistakes

## Mistake 1

Forgetting the `new` keyword.

Incorrect:

```javascript
const student = Student();
```

Correct:

```javascript
const student = new Student();
```

---

## Mistake 2

Using the `function` keyword inside a class.

Incorrect:

```javascript
function greet() {

}
```

Correct:

```javascript
greet() {

}
```

---

## Mistake 3

Thinking classes replace prototypes.

Classes are built on top of JavaScript's prototype system.

---

# Section Summary

In this section, you learned that ES6 classes provide a cleaner and more readable way to create objects in JavaScript. You explored how to define classes, create objects using the `new` keyword, initialize object properties with the `constructor()` method, and define methods directly inside a class. You also discovered that classes are built on JavaScript's prototype system rather than replacing it. Together, these concepts form the foundation of modern object-oriented programming in JavaScript.

In the next section, you will learn about **inheritance**, where one class can build upon another by reusing its properties and methods. Inheritance is one of the four fundamental pillars of Object-Oriented Programming.

---

# CodeTales Insight

> **Classes make object-oriented programming feel natural and organized, but they are not a new object model. Behind every JavaScript class is the same prototype system you've already learned. By understanding both the modern class syntax and the underlying prototype mechanism, you'll be able to read legacy code, build modern applications, and appreciate how JavaScript truly works under the hood.**

---

# 12.14 Inheritance

As software applications grow, developers often encounter situations where different objects share many of the same properties and methods.

For example, consider the following classes:

- Student
- Teacher
- Administrator

All three have:

- Name
- Email
- Age

However, each also has its own unique features.

Without inheritance, we would have to duplicate the common properties and methods in every class.

This repetition makes programs difficult to maintain.

Inheritance solves this problem.

---

# What Is Inheritance?

**Inheritance** is the process by which one class acquires the properties and methods of another class.

The existing class is called the **parent class** (or superclass).

The new class is called the **child class** (or subclass).

The child class automatically inherits the features of the parent class and can also define its own unique properties and methods.

Inheritance promotes **code reuse**, one of the most important principles of software engineering.

---

## Figure 12.47

**Inheritance**

```text
        Person

           │

    ───────┼────────

     │              │

 Student       Teacher
```

The child classes inherit common features from the `Person` class.

---

# Why Use Inheritance?

Imagine creating separate classes like this:

```javascript
class Student {

    constructor(name, age) {

        this.name = name;

        this.age = age;

    }

}

class Teacher {

    constructor(name, age) {

        this.name = name;

        this.age = age;

    }

}
```

Notice that the same code appears twice.

As more classes are added, duplication increases.

Inheritance eliminates this duplication.

---

# The `extends` Keyword

JavaScript uses the `extends` keyword to create inheritance.

Syntax:

```javascript
class ChildClass extends ParentClass {

}
```

The child class automatically inherits the parent class's properties and methods.

---

# Creating a Parent Class

```javascript
class Person {

    constructor(name, age) {

        this.name = name;

        this.age = age;

    }

    introduce() {

        console.log(

            `My name is ${this.name}.`

        );

    }

}
```

The `Person` class contains information common to all people.

---

# Creating a Child Class

```javascript
class Student extends Person {

}
```

Although `Student` is empty, it already inherits everything from `Person`.

---

## Figure 12.48

**Parent and Child Classes**

```text
Person

├── name

├── age

└── introduce()

        │

        ▼

Student

(Inherits Everything)
```

---

# Using the `super()` Keyword

When a child class defines its own constructor, it must call the parent's constructor using `super()`.

Example:

```javascript
class Person {

    constructor(name, age) {

        this.name = name;

        this.age = age;

    }

}

class Student extends Person {

    constructor(name, age, course) {

        super(name, age);

        this.course = course;

    }

}

const student = new Student(

    "Ada",

    21,

    "Computer Science"

);

console.log(student);
```

Output

```text
Student {

    name: "Ada",

    age: 21,

    course: "Computer Science"

}
```

`super()` initializes the inherited properties.

---

# Inheriting Methods

Methods are inherited automatically.

Example:

```javascript
class Person {

    constructor(name) {

        this.name = name;

    }

    greet() {

        console.log(

            `Hello, ${this.name}!`

        );

    }

}

class Student extends Person {

}

const student = new Student("Ada");

student.greet();
```

Output

```text
Hello, Ada!
```

The `Student` class did not define `greet()`, yet it can use it because it inherited it from `Person`.

---

## Figure 12.49

**Method Inheritance**

```text
Person

└── greet()

      │

      ▼

Student

↓

student.greet()
```

---

# Adding Child-Specific Methods

Child classes can define their own methods in addition to inherited ones.

Example:

```javascript
class Person {

    constructor(name) {

        this.name = name;

    }

}

class Student extends Person {

    study() {

        console.log(

            `${this.name} is studying.`

        );

    }

}

const student = new Student("Ada");

student.study();
```

Output

```text
Ada is studying.
```

Now the `Student` class has both inherited and unique behavior.

---

# Overriding Methods

A child class can replace an inherited method by defining a method with the same name.

Example:

```javascript
class Person {

    greet() {

        console.log("Hello!");

    }

}

class Student extends Person {

    greet() {

        console.log(

            "Welcome, Student!"

        );

    }

}

const student = new Student();

student.greet();
```

Output

```text
Welcome, Student!
```

This is called **method overriding**.

---

## Figure 12.50

**Method Overriding**

```text
Parent

greet()

        │

        ▼

Child

greet()

(Replaces Parent Version)
```

---

# Real-World Example

Consider a university management system.

```text
Person

│

├── Student

├── Lecturer

├── Administrator

└── Accountant
```

Every class shares:

- Name
- Email
- Phone Number

Each class also has unique responsibilities.

Inheritance keeps the shared code in one place.

---

# Benefits of Inheritance

Inheritance helps developers:

- Reuse code.
- Reduce duplication.
- Improve maintainability.
- Build organized applications.
- Create logical class hierarchies.

---

# Best Practices

- Place common functionality in the parent class.
- Keep child classes focused on specialized behavior.
- Use inheritance only when there is a genuine "is-a" relationship.
- Avoid creating unnecessarily deep inheritance chains.
- Override methods only when the child needs different behavior.

---

# Common Beginner Mistakes

## Mistake 1

Forgetting to call `super()` inside a child constructor.

Incorrect:

```javascript
constructor(name) {

    this.name = name;

}
```

Correct:

```javascript
constructor(name) {

    super(name);

}
```

---

## Mistake 2

Duplicating code that already exists in the parent class.

Reuse inherited functionality whenever possible.

---

## Mistake 3

Using inheritance when classes are unrelated.

Inheritance should represent a true relationship.

For example:

```text
Student is a Person ✔

Car is a Person ✘
```

---

# Section Summary

In this section, you learned that inheritance allows one class to reuse the properties and methods of another class. You explored how the `extends` keyword creates parent-child relationships, how `super()` initializes inherited properties, how child classes inherit methods automatically, and how methods can be overridden to provide specialized behavior. Inheritance reduces code duplication, improves maintainability, and is one of the four fundamental pillars of Object-Oriented Programming.

In the next section, you will learn about **encapsulation**, the OOP principle that protects an object's internal data by controlling how it is accessed and modified.

---

# CodeTales Insight

> **Inheritance is about building on existing work rather than starting from scratch. By placing shared features in a parent class and allowing child classes to inherit them, you write less code, reduce duplication, and create applications that are easier to extend and maintain. Used wisely, inheritance is one of the most powerful tools in object-oriented programming.**

---

# 12.15 Encapsulation

In the previous section, you learned how inheritance allows one class to reuse the properties and methods of another class. While inheritance promotes code reuse, it does not address another important challenge:

> **How do we protect an object's data from being modified incorrectly?**

Imagine a bank account.

A customer should be able to deposit or withdraw money, but they should not be able to directly set their balance to any value they choose.

For example:

```javascript
account.balance = -500000;
```

Allowing unrestricted access to important data can lead to errors and inconsistent application behavior.

This is where **encapsulation** becomes important.

---

# What Is Encapsulation?

**Encapsulation** is the practice of bundling an object's data and the methods that operate on that data into a single unit while controlling how the data is accessed or modified.

In simple terms:

> **Encapsulation protects an object's internal data by exposing only what is necessary.**

Instead of allowing direct access to sensitive data, an object provides methods that safely manage it.

---

## Figure 12.51

**Encapsulation**

```text
             Object

    ┌────────────────────┐

    │   Private Data     │

    │        ▲           │

    │        │           │

    │  Public Methods    │

    └────────────────────┘

Outside code interacts only through methods.
```

---

# Why Is Encapsulation Important?

Without encapsulation, any part of a program could change important data.

Example:

```javascript
class BankAccount {

    constructor(owner, balance) {

        this.owner = owner;

        this.balance = balance;

    }

}

const account = new BankAccount("Ada", 50000);

account.balance = -100000;

console.log(account.balance);
```

Output

```text
-100000
```

The account now has an invalid balance.

This is not desirable.

---

# Using Methods to Protect Data

A better approach is to provide methods that control how data changes.

Example:

```javascript
class BankAccount {

    constructor(owner, balance) {

        this.owner = owner;

        this.balance = balance;

    }

    deposit(amount) {

        if (amount > 0) {

            this.balance += amount;

        }

    }

}

const account = new BankAccount("Ada", 50000);

account.deposit(10000);

console.log(account.balance);
```

Output

```text
60000
```

The object now decides how its own data is modified.

---

## Figure 12.52

**Controlled Access**

```text
Outside Code

      │

deposit()

      │

      ▼

Validation

      │

      ▼

Update Balance
```

---

# Another Example

Consider a student's score.

Instead of allowing any value:

```javascript
student.score = 500;
```

we can validate it.

```javascript
class Student {

    constructor(name) {

        this.name = name;

        this.score = 0;

    }

    setScore(score) {

        if (score >= 0 && score <= 100) {

            this.score = score;

        }

    }

}

const student = new Student("Ada");

student.setScore(90);

console.log(student.score);
```

Output

```text
90
```

The validation prevents invalid scores from being stored.

---

# Encapsulation Improves Reliability

Encapsulation helps ensure that:

- Data remains consistent.
- Invalid values are rejected.
- Objects manage their own state.
- Other parts of the program cannot accidentally corrupt important information.

This makes applications more reliable.

---

# Real-World Example

Think of an ATM.

Customers cannot directly change the amount of money inside the bank's database.

Instead, they use approved operations:

- Deposit
- Withdraw
- Check Balance

The ATM validates every operation before updating the account.

Encapsulation works in the same way.

---

## Figure 12.53

**ATM Example**

```text
Customer

      │

Withdraw()

      │

      ▼

Validation

      │

      ▼

Bank Account Updated
```

---

# Encapsulation in Modern JavaScript

Modern JavaScript provides several tools that support encapsulation.

These include:

- Public methods
- Getters
- Setters
- Private class fields (`#`)

You will study these features in the next sections.

---

# Benefits of Encapsulation

Encapsulation helps developers:

- Protect important data.
- Prevent invalid updates.
- Reduce bugs.
- Improve maintainability.
- Hide unnecessary implementation details.
- Build safer applications.

---

# Best Practices

- Keep sensitive data protected.
- Provide methods to modify important values.
- Validate user input before updating object properties.
- Expose only what other parts of the program need.
- Keep an object's internal implementation private whenever possible.

---

# Common Beginner Mistakes

## Mistake 1

Allowing direct modification of important data.

Instead of:

```javascript
account.balance = -100;
```

Provide a method that validates the value.

---

## Mistake 2

Placing validation outside the object.

The object itself should be responsible for protecting its own data.

---

## Mistake 3

Thinking encapsulation means hiding everything.

Only implementation details should be hidden.

Useful functionality should remain accessible through well-designed methods.

---

# Section Summary

In this section, you learned that encapsulation is the practice of combining data and behavior into a single unit while controlling access to that data. You discovered why direct modification of important properties can lead to inconsistent application behavior and how methods can safely validate and update object data. Encapsulation improves reliability, reduces bugs, and makes applications easier to maintain. You also learned that modern JavaScript supports encapsulation through getters, setters, and private class fields, which you will explore next.

In the next section, you will learn about **polymorphism**, another fundamental pillar of Object-Oriented Programming that allows different objects to respond differently to the same method call.

---

# CodeTales Insight

> **Encapsulation is about responsibility. A well-designed object protects its own data, validates every important change, and exposes only the operations that make sense. By allowing objects to manage themselves, you create software that is safer, easier to maintain, and more resistant to errors.**

---

# 12.16 Polymorphism

In the previous section, you learned about encapsulation, which protects an object's internal data by controlling how it is accessed and modified.

Another important principle of Object-Oriented Programming is **polymorphism**.

Polymorphism allows different objects to respond differently to the same method call.

The word **polymorphism** comes from two Greek words:

- **Poly** – many
- **Morph** – forms

Together, polymorphism means:

> **"Many forms."**

In programming, it means that different objects can provide their own implementation of the same method.

---

# What Is Polymorphism?

**Polymorphism** is the ability of different classes to use the same method name while performing different actions.

Each class defines its own version of the method.

This allows programs to become more flexible and easier to extend.

---

## Figure 12.54

**One Method, Different Behaviors**

```text
          Animal

            │

     ───────┼────────

      │              │

     Dog           Cat

      │              │

    speak()       speak()

      │              │

    "Bark!"       "Meow!"
```

Each class uses the same method name but produces a different result.

---

# A Simple Example

```javascript
class Animal {

    speak() {

        console.log("Animal makes a sound.");

    }

}

class Dog extends Animal {

    speak() {

        console.log("Dog barks.");

    }

}

class Cat extends Animal {

    speak() {

        console.log("Cat meows.");

    }

}

const dog = new Dog();

const cat = new Cat();

dog.speak();

cat.speak();
```

Output

```text
Dog barks.

Cat meows.
```

Although both objects use the method `speak()`, each behaves differently.

---

# Method Overriding

Polymorphism is commonly achieved through **method overriding**.

A child class replaces the implementation inherited from its parent.

Example:

```javascript
class Vehicle {

    start() {

        console.log("Vehicle started.");

    }

}

class Car extends Vehicle {

    start() {

        console.log("Car engine started.");

    }

}

class Motorcycle extends Vehicle {

    start() {

        console.log("Motorcycle engine started.");

    }

}
```

Each class overrides the inherited `start()` method.

---

## Figure 12.55

**Method Overriding**

```text
Vehicle

│

└── start()

       │

────────┼────────

│                │

Car          Motorcycle

│                │

start()       start()
```

---

# Why Is Polymorphism Useful?

Imagine writing software for different payment methods.

Each payment type processes payments differently.

```text
Credit Card

Bank Transfer

Mobile Wallet

Cash
```

Instead of creating completely different program logic for each one, every payment class can provide its own `pay()` method.

This keeps the program organized and easy to extend.

---

# Real-World Example

```javascript
class Payment {

    pay() {

        console.log("Processing payment.");

    }

}

class CreditCard extends Payment {

    pay() {

        console.log("Processing credit card payment.");

    }

}

class BankTransfer extends Payment {

    pay() {

        console.log("Processing bank transfer.");

    }

}

const card = new CreditCard();

const transfer = new BankTransfer();

card.pay();

transfer.pay();
```

Output

```text
Processing credit card payment.

Processing bank transfer.
```

---

# Another Example

Consider different employees in a company.

```javascript
class Employee {

    work() {

        console.log("Employee is working.");

    }

}

class Developer extends Employee {

    work() {

        console.log("Developer is writing code.");

    }

}

class Designer extends Employee {

    work() {

        console.log("Designer is creating interfaces.");

    }

}
```

Every employee "works," but the work differs depending on the role.

---

## Figure 12.56

**Polymorphism in Action**

```text
Employee

│

└── work()

      │

───────────────

│             │

Developer   Designer

│             │

work()      work()
```

---

# Polymorphism Makes Code Flexible

Imagine a program that stores different animals.

```javascript
const animals = [

    new Dog(),

    new Cat()

];

for (const animal of animals) {

    animal.speak();

}
```

Output

```text
Dog barks.

Cat meows.
```

The loop does not need to know which type of animal it is working with.

Each object responds appropriately.

---

# Benefits of Polymorphism

Polymorphism helps developers:

- Write reusable code.
- Reduce conditional statements.
- Simplify program design.
- Improve maintainability.
- Extend applications more easily.
- Build flexible software architectures.

---

# Real-World Analogy

Think about a television remote.

You press the **Power** button on different televisions.

Although every television performs the same general action—turning on—it does so using its own internal electronics.

The interface is the same.

The implementation is different.

That is polymorphism.

---

## Figure 12.57

**Remote Control Analogy**

```text
Power Button

      │

──────────────

│            │

TV A       TV B

│            │

Turns On   Turns On

(Own internal process)
```

---

# Best Practices

- Use meaningful parent classes.
- Override methods only when behavior should differ.
- Keep method names consistent across related classes.
- Avoid unnecessary duplication of code.
- Design parent classes around shared behavior.

---

# Common Beginner Mistakes

## Mistake 1

Changing the method name in the child class.

Incorrect:

```javascript
class Dog {

    bark() {}

}
```

Correct:

```javascript
class Dog extends Animal {

    speak() {}

}
```

Use the same method name to achieve polymorphism.

---

## Mistake 2

Duplicating code instead of overriding methods.

Reuse inherited functionality whenever possible.

---

## Mistake 3

Using inheritance when no "is-a" relationship exists.

Polymorphism works best with meaningful class hierarchies.

---

# Section Summary

In this section, you learned that polymorphism allows different classes to respond differently to the same method call. You explored how child classes override inherited methods to provide specialized behavior while maintaining a consistent interface. Through practical examples involving animals, vehicles, payments, and employees, you discovered how polymorphism makes programs more flexible, reusable, and easier to maintain. Together with inheritance and encapsulation, polymorphism forms one of the core pillars of Object-Oriented Programming.

In the next section, you will learn about **static methods and static properties**, which belong to the class itself rather than to individual objects created from the class.

---

# CodeTales Insight

> **Polymorphism allows software to grow without becoming complicated. By giving different objects the freedom to implement the same method in their own way, you can write code that is flexible, reusable, and open to future expansion. Rather than asking what an object is, polymorphism focuses on what the object can do—a principle that lies at the heart of elegant object-oriented design.**

---

# 12.17 Static Methods and Static Properties

So far, every property and method you have created has belonged to an **object (instance)** of a class.

For example:

```javascript
class Student {

    constructor(name) {

        this.name = name;

    }

    greet() {

        console.log(`Hello, ${this.name}!`);

    }

}

const student = new Student("Ada");

student.greet();
```

Output

```text
Hello, Ada!
```

The `greet()` method belongs to the `student` object.

However, sometimes a method should belong to the **class itself**, not to any individual object.

JavaScript provides **static methods** and **static properties** for this purpose.

---

# What Is a Static Method?

A **static method** belongs to the class itself rather than to objects created from the class.

Static methods are declared using the `static` keyword.

Syntax:

```javascript
class ClassName {

    static methodName() {

    }

}
```

---

## Figure 12.58

**Instance Methods vs Static Methods**

```text
             Student Class

        ┌────────────────────┐
        │ static school()    │
        └────────────────────┘
                 ▲
                 │
      Called on the class

────────────────────────────────

Student Object

├── name
└── greet()

Called on an object
```

---

# Creating a Static Method

Example:

```javascript
class Student {

    static school() {

        console.log("CodeTales Academy");

    }

}

Student.school();
```

Output

```text
CodeTales Academy
```

Notice that the method is called using the class name.

---

# Calling Static Methods

Correct:

```javascript
Student.school();
```

Incorrect:

```javascript
const student = new Student();

student.school();
```

Output

```text
TypeError
```

Static methods belong to the class—not to its objects.

---

# Why Use Static Methods?

Suppose you want a utility function that is shared by every student.

Example:

```javascript
class Calculator {

    static add(a, b) {

        return a + b;

    }

}

console.log(

    Calculator.add(10, 5)

);
```

Output

```text
15
```

There is no need to create a `Calculator` object.

The calculation belongs to the class itself.

---

## Figure 12.59

**Calling a Static Method**

```text
Calculator

│

└── add()

      │

      ▼

Calculator.add(10, 5)

↓

15
```

---

# Static Properties

Just like methods, properties can also be static.

Example:

```javascript
class School {

    static name = "CodeTales Academy";

}

console.log(School.name);
```

Output

```text
CodeTales Academy
```

The property belongs to the class.

---

# Static Properties Are Shared

Every object created from the class shares the same static property.

Example:

```javascript
class Company {

    static country = "Nigeria";

    constructor(name) {

        this.name = name;

    }

}

const employee1 = new Company("Ada");

const employee2 = new Company("John");

console.log(Company.country);
```

Output

```text
Nigeria
```

Neither employee stores its own copy of `country`.

---

# Static vs Instance Members

Consider this example.

```javascript
class Student {

    static school = "CodeTales Academy";

    constructor(name) {

        this.name = name;

    }

    greet() {

        console.log(

            `Hello, ${this.name}`

        );

    }

}
```

Static member:

```javascript
Student.school
```

Instance members:

```javascript
student.name

student.greet()
```

---

## Figure 12.60

**Static vs Instance Members**

```text
Student Class

├── static school
├── static register()

────────────────────

Student Object

├── name
└── greet()
```

---

# Real-World Example

Imagine a banking system.

Every account belongs to the same bank.

Instead of storing the bank name in every object:

```javascript
class Bank {

    static bankName = "First Digital Bank";

    constructor(owner) {

        this.owner = owner;

    }

}
```

Access it like this:

```javascript
console.log(Bank.bankName);
```

Output

```text
First Digital Bank
```

---

# Utility Classes

Static methods are commonly used for utility classes.

Example:

```javascript
class MathHelper {

    static square(number) {

        return number * number;

    }

}

console.log(

    MathHelper.square(8)

);
```

Output

```text
64
```

This is similar to JavaScript's built-in `Math` object.

For example:

```javascript
Math.max(10, 20);

Math.random();
```

---

# Benefits of Static Members

Static members help developers:

- Share common data.
- Create utility methods.
- Avoid unnecessary objects.
- Organize related functionality.
- Improve readability.

---

# Best Practices

- Use static methods for utility functions.
- Store shared information in static properties.
- Access static members using the class name.
- Do not use static members for object-specific data.
- Keep static methods independent of instance properties.

---

# Common Beginner Mistakes

## Mistake 1

Calling a static method on an object.

Incorrect:

```javascript
student.school();
```

Correct:

```javascript
Student.school();
```

---

## Mistake 2

Trying to access instance properties inside a static method using `this.name`.

Static methods do not automatically have access to instance properties.

---

## Mistake 3

Using static properties for data that belongs to individual objects.

Store object-specific information as instance properties instead.

---

# Section Summary

In this section, you learned that static methods and static properties belong to a class rather than to individual objects created from that class. You discovered how to declare static members using the `static` keyword, how to access them through the class name, and when they are appropriate. Static members are ideal for utility methods and information shared by all instances, while instance members remain responsible for object-specific data.

In the next section, you will learn about **getters and setters**, powerful features that allow you to safely access and modify object properties while keeping your code clean and maintainable.

---

# CodeTales Insight

> **Not everything belongs to an object. Some information and behaviors are shared by every instance of a class. Static members provide a clean way to represent these shared responsibilities, helping you organize your code more effectively while avoiding unnecessary object creation.**

---

# 12.18 Getters and Setters

In the previous sections, you learned that encapsulation helps protect an object's internal data by controlling how it is accessed and modified.

JavaScript provides two special methods that make this process both elegant and convenient:

- **Getters**
- **Setters**

These methods allow you to access and update properties while still performing validation or additional processing behind the scenes.

---

# What Is a Getter?

A **getter** is a special method used to retrieve the value of a property.

Instead of calling it like a function, you access it as though it were a normal property.

Getters are declared using the `get` keyword.

Syntax:

```javascript
class ClassName {

    get propertyName() {

    }

}
```

---

## Figure 12.61

**Getter**

```text
Object

│

└── get fullName()

        │

        ▼

Returns Property Value
```

---

# Creating Your First Getter

Example:

```javascript
class Student {

    constructor(name) {

        this.name = name;

    }

    get studentName() {

        return this.name;

    }

}

const student = new Student("Ada");

console.log(student.studentName);
```

Output

```text
Ada
```

Notice that the getter is accessed like a property.

Correct:

```javascript
student.studentName
```

Incorrect:

```javascript
student.studentName()
```

---

# Why Use Getters?

Suppose you want to return a formatted value.

Example:

```javascript
class Student {

    constructor(name) {

        this.name = name;

    }

    get greeting() {

        return `Welcome, ${this.name}!`;

    }

}

const student = new Student("Ada");

console.log(student.greeting);
```

Output

```text
Welcome, Ada!
```

The caller doesn't need to know how the value is generated.

---

# What Is a Setter?

A **setter** is a special method used to update the value of a property.

Setters are declared using the `set` keyword.

Syntax:

```javascript
class ClassName {

    set propertyName(value) {

    }

}
```

Unlike ordinary methods, setters are assigned values using the assignment operator (`=`).

---

## Figure 12.62

**Setter**

```text
New Value

      │

      ▼

set property(value)

      │

      ▼

Validation

      │

      ▼

Store Value
```

---

# Creating Your First Setter

Example:

```javascript
class Student {

    constructor(name) {

        this.name = name;

    }

    set studentName(value) {

        this.name = value;

    }

}

const student = new Student("Ada");

student.studentName = "John";

console.log(student.name);
```

Output

```text
John
```

Again, the setter is used like a property assignment.

---

# Using Getters and Setters Together

Most applications use both getters and setters.

Example:

```javascript
class Student {

    constructor(name) {

        this.name = name;

    }

    get studentName() {

        return this.name;

    }

    set studentName(value) {

        this.name = value;

    }

}

const student = new Student("Ada");

console.log(student.studentName);

student.studentName = "Grace";

console.log(student.studentName);
```

Output

```text
Ada

Grace
```

---

# Validating Data with Setters

One major advantage of setters is validation.

Example:

```javascript
class Student {

    constructor(score) {

        this.score = score;

    }

    set studentScore(value) {

        if (value >= 0 && value <= 100) {

            this.score = value;

        }

    }

    get studentScore() {

        return this.score;

    }

}

const student = new Student(80);

student.studentScore = 95;

console.log(student.studentScore);
```

Output

```text
95
```

Only valid scores are accepted.

---

# Rejecting Invalid Values

Example:

```javascript
class Student {

    constructor(score) {

        this.score = score;

    }

    set studentScore(value) {

        if (value >= 0 && value <= 100) {

            this.score = value;

        } else {

            console.log("Invalid score.");

        }

    }

}

const student = new Student(80);

student.studentScore = 120;
```

Output

```text
Invalid score.
```

The object's data remains protected.

---

## Figure 12.63

**Setter Validation**

```text
Assign Value

      │

      ▼

Is Value Valid?

   Yes      No

    │        │

Store     Reject
```

---

# Real-World Example

Imagine an employee management system.

```javascript
class Employee {

    constructor(salary) {

        this.salary = salary;

    }

    set employeeSalary(value) {

        if (value > 0) {

            this.salary = value;

        }

    }

    get employeeSalary() {

        return this.salary;

    }

}

const employee = new Employee(250000);

employee.employeeSalary = 300000;

console.log(employee.employeeSalary);
```

Output

```text
300000
```

The setter prevents invalid salaries from being assigned.

---

# Why Not Use Ordinary Methods?

Without getters and setters, you might write:

```javascript
student.getName();

student.setName("Ada");
```

With getters and setters, JavaScript allows a cleaner syntax:

```javascript
student.studentName;

student.studentName = "Ada";
```

This makes code easier to read and more natural to use.

---

# Benefits of Getters and Setters

They help developers:

- Validate data.
- Protect object state.
- Hide implementation details.
- Compute values dynamically.
- Improve readability.
- Support encapsulation.

---

# Best Practices

- Use getters for computed or protected values.
- Validate important data inside setters.
- Keep getter logic simple.
- Avoid expensive computations inside getters.
- Use meaningful property names.

---

# Common Beginner Mistakes

## Mistake 1

Calling a getter like a function.

Incorrect:

```javascript
student.studentName();
```

Correct:

```javascript
student.studentName;
```

---

## Mistake 2

Trying to pass arguments to a getter.

Getters do not accept parameters.

---

## Mistake 3

Writing setters without validation when validation is required.

Always validate important business data before storing it.

---

# Section Summary

In this section, you learned that getters and setters provide a controlled way to access and modify object properties. You explored how getters return values like ordinary properties, while setters update values and can perform validation before storing them. These features improve encapsulation by protecting an object's internal state while keeping your code clean and easy to read. Together, getters and setters help create more reliable and maintainable JavaScript applications.

In the next section, you will learn about **private class fields**, a modern JavaScript feature that allows class data to be truly private and inaccessible from outside the class.

---

# CodeTales Insight

> **Getters and setters provide the perfect balance between convenience and control. To other parts of your program, a property appears simple to read or write. Behind the scenes, however, your class can validate input, calculate values, and protect its internal state—all without changing how the property is used. This elegant design is one of the reasons modern JavaScript classes are both powerful and easy to work with.**

---

# 12.19 Private Class Fields

Throughout this chapter, you have learned that encapsulation is about protecting an object's internal data.

Using methods, getters, and setters allows us to control how data is accessed and modified. However, until recently, JavaScript did not provide a way to make object properties truly private.

Beginning with **ECMAScript 2022 (ES2022)**, JavaScript introduced **private class fields**.

Private class fields allow developers to hide data completely from code outside the class.

---

# What Are Private Class Fields?

A **private class field** is a property that can only be accessed from inside the class in which it is declared.

Private fields are identified using the **`#` (hash)** symbol.

Syntax:

```javascript
class ClassName {

    #propertyName;

}
```

Unlike public properties, private fields cannot be accessed directly from outside the class.

---

## Figure 12.64

**Private Class Field**

```text
             Student

    ┌────────────────────┐

    │ #score            │

    │                   │

    │ getScore()        │

    │ setScore()        │

    └────────────────────┘

Outside code cannot access #score directly.
```

---

# Creating Your First Private Field

Example:

```javascript
class Student {

    #name;

    constructor(name) {

        this.#name = name;

    }

}
```

Here, `#name` is private.

Only methods inside the `Student` class can access it.

---

# Accessing a Private Field

Private fields are accessed using the `#` symbol.

Example:

```javascript
class Student {

    #name;

    constructor(name) {

        this.#name = name;

    }

    displayName() {

        console.log(this.#name);

    }

}

const student = new Student("Ada");

student.displayName();
```

Output

```text
Ada
```

The method can access the private field because it belongs to the same class.

---

# Attempting Direct Access

Consider the following code:

```javascript
class Student {

    #name = "Ada";

}

const student = new Student();

console.log(student.#name);
```

Output

```text
SyntaxError
```

JavaScript does not allow code outside the class to access private fields.

---

## Figure 12.65

**Access Control**

```text
Outside Code

      │

      ▼

student.#name

      │

      ▼

Access Denied
```

---

# Using Getters with Private Fields

Private fields are often accessed through getters.

Example:

```javascript
class Student {

    #name;

    constructor(name) {

        this.#name = name;

    }

    get name() {

        return this.#name;

    }

}

const student = new Student("Ada");

console.log(student.name);
```

Output

```text
Ada
```

The getter provides safe access without exposing the private field itself.

---

# Using Setters with Private Fields

Private fields can also be updated through setters.

Example:

```javascript
class Student {

    #score = 0;

    set score(value) {

        if (value >= 0 && value <= 100) {

            this.#score = value;

        }

    }

    get score() {

        return this.#score;

    }

}

const student = new Student();

student.score = 95;

console.log(student.score);
```

Output

```text
95
```

The setter validates the value before storing it.

---

# Real-World Example

Consider a bank account.

```javascript
class BankAccount {

    #balance = 0;

    deposit(amount) {

        if (amount > 0) {

            this.#balance += amount;

        }

    }

    get balance() {

        return this.#balance;

    }

}

const account = new BankAccount();

account.deposit(10000);

console.log(account.balance);
```

Output

```text
10000
```

Notice that the balance cannot be changed directly from outside the class.

---

## Figure 12.66

**Private Data Flow**

```text
Outside Code

      │

deposit()

      │

      ▼

Private Field

(#balance)

      │

      ▼

Getter

      │

      ▼

Display Value
```

---

# Public Fields vs Private Fields

Public field:

```javascript
class Student {

    name = "Ada";

}
```

Accessible from anywhere.

Private field:

```javascript
class Student {

    #name = "Ada";

}
```

Accessible only inside the class.

---

## Figure 12.67

**Public vs Private Fields**

```text
Public

name

✔ Accessible

------------------

Private

#name

✘ Outside Access
```

---

# When Should You Use Private Fields?

Private fields are useful when:

- Data should never be modified directly.
- Business rules must always be enforced.
- Sensitive information should remain hidden.
- You want to prevent accidental changes.

Examples include:

- Bank balances
- Passwords
- Authentication tokens
- PIN numbers
- Internal application state

---

# Benefits of Private Fields

Private fields help developers:

- Strengthen encapsulation.
- Prevent accidental modification.
- Hide implementation details.
- Improve code reliability.
- Build secure applications.

---

# Best Practices

- Use private fields for sensitive or internal data.
- Access private fields through public methods, getters, or setters.
- Validate important data before storing it.
- Use meaningful names for private fields.
- Avoid exposing private data unnecessarily.

---

# Common Beginner Mistakes

## Mistake 1

Trying to access a private field directly.

Incorrect:

```javascript
student.#name;
```

Correct:

```javascript
student.name;
```

(using a getter)

---

## Mistake 2

Forgetting the `#` inside the class.

Incorrect:

```javascript
this.name = value;
```

Correct:

```javascript
this.#name = value;
```

---

## Mistake 3

Making every field private.

Only fields that require protection should be private.

Public data that does not require validation can remain public.

---

# Section Summary

In this section, you learned that private class fields provide true data privacy in modern JavaScript. By prefixing a field with the `#` symbol, you restrict access to that field so it can only be used within its own class. You also learned how getters and setters work together with private fields to safely expose or update protected data. Private class fields strengthen encapsulation and help developers create secure, reliable, and maintainable applications.

The next section concludes this chapter with a comprehensive review of everything you have learned about objects, classes, inheritance, encapsulation, polymorphism, static members, getters, setters, and private fields.

---

# CodeTales Insight

> **Encapsulation reaches its highest level with private class fields. Rather than relying only on developer discipline, JavaScript itself enforces privacy by preventing outside code from accessing protected data. By combining private fields with well-designed methods, getters, and setters, you create classes that are secure, predictable, and easier to maintain—qualities that distinguish professional software from simple programs.**

---

# 12.20 Chapter Summary

Congratulations! You have completed **Chapter 12: Objects and Object-Oriented Programming**.

This chapter introduced one of the most important concepts in JavaScript—**objects**. Unlike primitive values, objects allow you to model real-world entities by combining related data and behavior into a single structure. As your applications grow larger, objects become the primary way to organize and manage complexity.

You began by learning what objects are, how they differ from primitive data types, and how to create them using object literals. You explored object properties, methods, and learned how to access, update, add, and remove properties using both dot notation and bracket notation.

Next, you learned how JavaScript uses the `this` keyword inside object methods to refer to the current object, making methods reusable and easier to maintain.

From there, you transitioned into **Object-Oriented Programming (OOP)**. You explored constructor functions, the `new` keyword, prototypes, and the prototype chain, gaining insight into the mechanisms that power JavaScript's object model.

Building on these foundations, you learned how **ES6 classes** provide a cleaner and more readable syntax for creating objects while still relying on JavaScript's prototype-based inheritance system.

You then studied three of the four fundamental pillars of Object-Oriented Programming:

- **Inheritance**, which allows one class to reuse the properties and methods of another.
- **Encapsulation**, which protects an object's internal data and controls how it is accessed and modified.
- **Polymorphism**, which allows different objects to respond differently to the same method call.

Finally, you explored several modern JavaScript features that support professional software development, including:

- Static methods and static properties.
- Getters and setters.
- Private class fields.

Together, these features enable developers to build applications that are modular, maintainable, reusable, and secure.

---

# Key Concepts Learned

By completing this chapter, you should now be able to:

- Explain what an object is.
- Differentiate between primitive values and objects.
- Create objects using object literals.
- Access properties using dot notation and bracket notation.
- Add, update, and delete object properties.
- Create and invoke object methods.
- Use the `this` keyword correctly.
- Create constructor functions.
- Use the `new` keyword to instantiate objects.
- Explain how prototypes and the prototype chain work.
- Create classes using ES6 syntax.
- Apply inheritance using the `extends` keyword.
- Use the `super()` method in child classes.
- Explain encapsulation and its benefits.
- Demonstrate polymorphism through method overriding.
- Create and use static methods and static properties.
- Implement getters and setters.
- Protect object data with private class fields.

---

## Figure 12.68

**Concept Map of Chapter 12**

```text
Objects

│

├── Properties

├── Methods

├── this

│

├── Constructor Functions

├── new Keyword

├── Prototypes

├── ES6 Classes

│

├── Inheritance

├── Encapsulation

├── Polymorphism

│

├── Static Members

├── Getters

├── Setters

└── Private Fields
```

---

# Practical Skills Acquired

After completing this chapter, you are capable of building applications that use:

- Objects to organize related data.
- Classes to model real-world entities.
- Constructors to create reusable object templates.
- Inheritance to reduce duplicated code.
- Encapsulation to protect application data.
- Polymorphism to write flexible software.
- Modern JavaScript class features for cleaner, more maintainable code.

These skills are essential for building professional JavaScript applications.

---

# How This Chapter Connects to the Rest of the Book

The concepts introduced in this chapter serve as the foundation for many advanced JavaScript topics.

In the chapters ahead, you will build upon these ideas as you learn:

- The Document Object Model (DOM)
- Browser Events
- Asynchronous JavaScript
- APIs and Fetch
- Modules
- Error Handling
- Modern Frameworks
- Full-Stack JavaScript

Nearly every modern JavaScript application relies heavily on objects and object-oriented principles.

---

# Final Thoughts

Object-Oriented Programming is not simply about learning new syntax. It is a way of thinking about software design.

By organizing related data and behavior into reusable objects and classes, you can build applications that are easier to understand, extend, test, and maintain.

As you continue your JavaScript journey, strive not only to write code that works, but to write code that is clean, organized, and reusable.

The knowledge gained in this chapter will serve you throughout the rest of this book and throughout your career as a JavaScript developer.

---

# Chapter 12 Checklist

Before moving to the next chapter, make sure you can confidently answer **"Yes"** to each of the following:

- □ I can explain what an object is.
- □ I can create objects using object literals.
- □ I can access and modify object properties.
- □ I understand the difference between properties and methods.
- □ I know how the `this` keyword works inside object methods.
- □ I can create objects using constructor functions.
- □ I understand the purpose of the `new` keyword.
- □ I can explain prototypes and the prototype chain.
- □ I can create and use ES6 classes.
- □ I understand inheritance and the `extends` keyword.
- □ I understand encapsulation and why it matters.
- □ I can explain polymorphism with practical examples.
- □ I know when to use static methods and static properties.
- □ I can implement getters and setters.
- □ I understand private class fields and their purpose.

If you answered **"Yes"** to every item, you are well prepared to continue to the next chapter.

---

# CodeTales Insight

> **Objects are the language of modern software. Whether you're building websites, mobile applications, desktop software, games, APIs, or artificial intelligence systems, you'll constantly use objects to represent real-world concepts. By mastering objects and object-oriented programming, you've taken a major step toward becoming a professional JavaScript developer capable of designing software that is not only functional but also scalable, maintainable, and elegant.**
