# Chapter 11 – Asynchronous JavaScript

Modern web applications rarely perform only one task at a time. They fetch data from servers, respond to user interactions, load images, play videos, process files, and communicate with external services—all while remaining responsive to the user.

If JavaScript executed every task one after another and waited for each operation to finish before moving to the next, web pages would freeze whenever a slow operation occurred. To solve this problem, JavaScript uses asynchronous programming.

Asynchronous programming allows long-running operations to execute without blocking the rest of the application. While one task is waiting—for example, downloading data from an API—JavaScript can continue executing other code, updating the interface, and responding to user input.

This chapter introduces the concepts that make asynchronous programming possible. You will learn how the JavaScript engine handles asynchronous tasks using the Call Stack, the Event Loop, and the Callback Queue. You will explore callbacks, promises, `async` and `await`, the Fetch API, JSON, HTTP requests, and error handling.

By the end of this chapter, you will be able to build applications that communicate with remote servers and process data efficiently without blocking the user interface.

---

# Learning Objectives

After completing this chapter, you should be able to:

- Explain synchronous programming.
- Explain asynchronous programming.
- Describe the JavaScript execution model.
- Explain the Call Stack.
- Explain the Event Loop.
- Understand the Callback Queue.
- Write callback functions.
- Identify callback hell.
- Create and consume Promises.
- Chain Promises.
- Use `Promise.all()` and `Promise.race()`.
- Write asynchronous code using `async` and `await`.
- Handle asynchronous errors.
- Fetch data from APIs.
- Parse and generate JSON.
- Make HTTP GET and POST requests.
- Build applications that consume remote APIs.

---

# Prerequisites

Before beginning this chapter, you should be comfortable with:

- Variables and constants
- Functions
- Objects
- Arrays
- DOM manipulation
- Event handling

---

# Chapter Outline

11.1 Introduction to Asynchronous JavaScript

11.2 Synchronous vs Asynchronous Programming

11.3 The JavaScript Execution Model

11.4 The Call Stack

11.5 The Event Loop

11.6 The Callback Queue

11.7 Understanding Callbacks

11.8 Callback Hell

11.9 Promises

11.10 Promise States

11.11 Creating Promises

11.12 Consuming Promises

11.13 Promise Chaining

11.14 Promise.all()

11.15 Promise.race()

11.16 async and await

11.17 Error Handling with try...catch

11.18 Fetch API

11.19 Working with JSON

11.20 Making GET Requests

11.21 Making POST Requests

11.22 HTTP Status Codes

11.23 Mini Project – Weather Dashboard

11.24 Chapter Summary

11.25 Practice Exercises & Challenge Projects

---

# 11.1 Introduction to Asynchronous JavaScript

Modern web applications rarely perform just one task at a time.

When you open a social media website, numerous operations happen simultaneously. Images load, messages are retrieved from a server, notifications are checked, advertisements appear, and user interactions are processed—all without freezing the page.

This smooth user experience is made possible through **asynchronous programming**.

Asynchronous programming allows JavaScript to begin a task that may take some time to complete while continuing to execute other code. Instead of waiting for one operation to finish before starting another, JavaScript can perform multiple activities efficiently, keeping applications responsive.

Without asynchronous programming, every slow operation would cause the browser to become unresponsive, resulting in a poor user experience.

---

# Why Do We Need Asynchronous Programming?

Consider a web application that needs to download data from a remote server.

Downloading the data may take several seconds depending on the user's internet connection.

If JavaScript waited for the download to complete before executing the next line of code, the entire web page would appear frozen.

Users would not be able to:

- Click buttons
- Scroll the page
- Type into forms
- Open menus
- Interact with the application

Asynchronous programming prevents this problem.

---

## Figure 11.1

**Synchronous vs Asynchronous Behaviour**

```text
Synchronous

Task A

↓

Wait

↓

Task B

↓

Wait

↓

Task C
```

```text
Asynchronous

Task A

↓

Task Starts

↓

JavaScript Continues

↓

Task Completes Later

↓

Result Processed
```

---

# A Real-World Analogy

Imagine you visit a restaurant.

### Synchronous Approach

You place your order.

The waiter tells you to stand beside the kitchen until your food is ready.

During this time:

- You cannot sit.
- You cannot talk.
- You cannot do anything else.

Only after receiving your food can you continue.

This is inefficient.

---

### Asynchronous Approach

You place your order.

The waiter gives you a table number.

While the chef prepares your meal, you can:

- Sit down.
- Talk with friends.
- Read a book.
- Use your phone.

When the food is ready, the waiter brings it to your table.

This is how asynchronous programming works.

JavaScript starts a task, continues executing other code, and returns to process the result when it becomes available.

---

## Figure 11.2

**Restaurant Analogy**

```text
Place Order

↓

Kitchen Starts Cooking

↓

Customer Continues Eating, Talking, Relaxing

↓

Food Ready

↓

Waiter Delivers Meal
```

---

# Where Is Asynchronous Programming Used?

Almost every modern web application uses asynchronous programming.

Examples include:

- Loading user profiles
- Fetching weather information
- Playing videos
- Uploading files
- Downloading images
- Sending chat messages
- Searching while typing
- Displaying notifications
- Online banking
- E-commerce websites

Without asynchronous programming, these applications would feel slow and unresponsive.

---

# Common Asynchronous Operations

JavaScript frequently performs tasks that require waiting.

Examples include:

- Fetching data from APIs
- Reading files
- Uploading images
- Waiting for timers
- Receiving user input
- Playing audio or video
- Communicating with databases
- Accessing browser storage

These operations often take an unpredictable amount of time.

---

# The Challenge

JavaScript is a **single-threaded** programming language.

This means it executes one piece of JavaScript code at a time.

You might wonder:

> If JavaScript executes only one task at a time, how can it perform asynchronous operations?

The answer lies in the JavaScript runtime environment.

Modern browsers and environments such as Node.js provide features that allow long-running operations to execute outside the main JavaScript execution flow.

When those operations finish, JavaScript is notified and processes the results.

You will explore this mechanism later in this chapter when studying:

- The Call Stack
- The Web APIs
- The Callback Queue
- The Event Loop

Together, these components make asynchronous programming possible.

---

## Figure 11.3

**High-Level View of Asynchronous JavaScript**

```text
JavaScript Code

↓

Long-Running Task

↓

Browser / Runtime Handles Task

↓

Task Completes

↓

Result Returns to JavaScript

↓

Continue Execution
```

---

# Advantages of Asynchronous Programming

Asynchronous programming offers many benefits.

- Keeps web applications responsive.
- Prevents browser freezing.
- Improves user experience.
- Handles multiple activities efficiently.
- Makes network communication practical.
- Supports modern interactive applications.

Without asynchronous programming, today's web applications would be far less usable.

---

# Common Examples

### Example 1 — Waiting for a Timer

```javascript
console.log("Start");

setTimeout(() => {

    console.log("Timer Finished");

}, 3000);

console.log("End");
```

Output:

```text
Start
End
Timer Finished
```

Although the timer is started before `"End"` is logged, JavaScript continues executing the remaining code while waiting for the timer to complete.

---

### Example 2 — Fetching Data

```javascript
fetch("https://api.example.com/users");
```

Fetching data from a server may take several seconds.

Rather than freezing the page, JavaScript allows other code to continue executing while waiting for the server's response.

Later in this chapter, you will learn exactly how `fetch()` works.

---

# What You Will Learn in This Chapter

In this chapter, you will learn:

- Synchronous programming
- Asynchronous programming
- The JavaScript execution model
- The Call Stack
- The Event Loop
- Callback functions
- Callback hell
- Promises
- `async` and `await`
- Error handling
- Fetch API
- JSON
- HTTP requests
- Building asynchronous applications

These concepts form the foundation of modern JavaScript development.

---

# Best Practices

- Avoid blocking long-running operations.
- Understand the difference between synchronous and asynchronous code.
- Prefer modern asynchronous techniques such as Promises and `async`/`await`.
- Write asynchronous code that is easy to read and maintain.
- Handle errors appropriately.

---

# Common Beginner Misconceptions

## Misconception 1

"Asynchronous means JavaScript runs multiple pieces of JavaScript code at exactly the same time."

Not exactly.

JavaScript itself remains single-threaded. The browser or runtime environment handles many long-running operations, allowing JavaScript to continue executing other code.

---

## Misconception 2

"Asynchronous code always runs faster."

Not necessarily.

Asynchronous programming does not make an operation complete more quickly. Instead, it allows the application to remain responsive while waiting for the operation to finish.

---

# Section Summary

In this section, you learned why asynchronous programming is essential for modern JavaScript applications. You discovered how asynchronous programming allows JavaScript to remain responsive while waiting for long-running tasks such as network requests, timers, and file operations. You also saw how browsers and runtime environments assist JavaScript in handling these operations efficiently.

The next section will compare **synchronous programming** and **asynchronous programming** in detail, helping you understand exactly how their execution models differ.

---

# CodeTales Insight

> **Great user experiences are built on responsiveness. Users should never feel that an application has frozen while waiting for data or performing a task. Asynchronous programming enables JavaScript to keep applications interactive, responsive, and efficient—even when handling operations that take time to complete. Mastering this concept is a major milestone in becoming a professional JavaScript developer.**

---

# 11.2 Synchronous vs Asynchronous Programming

To understand asynchronous JavaScript, you must first understand how JavaScript normally executes code.

By default, JavaScript executes statements **one at a time**, in the exact order they appear.

This behavior is called **synchronous programming**.

However, modern applications frequently perform operations that take time to complete, such as downloading data, uploading files, or waiting for user input.

If JavaScript waited for every slow operation to finish before continuing, web applications would become slow and unresponsive.

To solve this problem, JavaScript supports **asynchronous programming**.

Understanding the difference between these two execution models is essential for becoming a professional JavaScript developer.

---

# What Is Synchronous Programming?

Synchronous programming means that JavaScript executes one statement completely before moving to the next.

Each task must finish before another task begins.

Think of it as standing in a queue at a bank.

The next customer cannot be served until the current customer is finished.

---

## Figure 11.4

**Synchronous Execution**

```text
Task 1

↓

Complete

↓

Task 2

↓

Complete

↓

Task 3

↓

Complete
```

---

# Example of Synchronous Code

```javascript
console.log("Start");

console.log("Learning JavaScript");

console.log("End");
```

Output

```text
Start

Learning JavaScript

End
```

Each statement waits for the previous one to complete.

The execution order is predictable.

---

# Characteristics of Synchronous Programming

Synchronous code has several characteristics.

- Executes line by line.
- Easy to read.
- Easy to debug.
- Predictable execution order.
- Each task blocks the next task until it finishes.

---

# The Problem with Synchronous Programming

Suppose downloading data takes five seconds.

```javascript
downloadLargeFile();

console.log("Finished");
```

If `downloadLargeFile()` blocks execution, JavaScript cannot continue until the download is complete.

During that time:

- Buttons stop responding.
- Animations freeze.
- The page feels slow.
- Users become frustrated.

This is known as **blocking code**.

---

## Figure 11.5

**Blocking Execution**

```text
Download File

█████████████

↓

Continue Program
```

The program waits until the task finishes.

---

# What Is Asynchronous Programming?

Asynchronous programming allows JavaScript to start a task without waiting for it to finish.

Instead of blocking the program, JavaScript continues executing other statements.

When the task eventually completes, JavaScript processes the result.

---

## Figure 11.6

**Asynchronous Execution**

```text
Start Task

↓

Continue Running Other Code

↓

Task Completes Later

↓

Process Result
```

---

# Example Using a Timer

```javascript
console.log("Start");

setTimeout(() => {

    console.log("Timer Finished");

}, 2000);

console.log("End");
```

Output

```text
Start

End

Timer Finished
```

Notice that JavaScript does **not** wait two seconds before printing `"End"`.

Instead:

1. The timer is started.
2. JavaScript continues executing.
3. The timer finishes later.
4. The callback function executes.

---

## Figure 11.7

**Timeline**

```text
Time

0 s

Start

↓

Timer Starts

↓

End

↓

2 Seconds Pass

↓

Timer Finished
```

---

# Comparing Synchronous and Asynchronous Programming

| Synchronous | Asynchronous |
|--------------|--------------|
| Executes one task at a time | Starts long-running tasks without blocking |
| Blocks later statements | Continues executing other code |
| Predictable order | Some results arrive later |
| Simple to understand | Requires additional concepts |
| Suitable for quick operations | Suitable for slow operations |

---

# Real-World Example

Imagine sending a package through a courier service.

### Synchronous

You stand at the courier office until the package reaches its destination.

Only then can you continue with your day.

Clearly, this is impractical.

---

### Asynchronous

You hand over the package.

The courier begins delivery.

You continue working.

Later, the courier sends you a notification that the package has arrived.

This is exactly how asynchronous programming works.

---

# Common Asynchronous Tasks

JavaScript commonly performs asynchronous operations such as:

- Network requests
- File uploads
- File downloads
- Reading files
- Playing audio
- Playing video
- Timers
- User interactions
- Database communication
- Browser APIs

These operations may complete immediately—or several seconds later.

---

# Why Not Make Everything Asynchronous?

Not every task should be asynchronous.

Simple operations like:

```javascript
let total = 25 + 10;

console.log(total);
```

execute almost instantly.

Making such operations asynchronous would unnecessarily increase complexity.

Asynchronous programming should be reserved for operations that involve waiting.

---

# Common Beginner Mistakes

## Mistake 1

Assuming asynchronous code executes before synchronous code.

Example

```javascript
console.log("One");

setTimeout(() => {

    console.log("Two");

}, 0);

console.log("Three");
```

Output

```text
One

Three

Two
```

Even with a delay of `0`, the callback runs after the synchronous code finishes.

---

## Mistake 2

Thinking asynchronous code runs on another JavaScript thread.

JavaScript itself remains single-threaded.

The browser or runtime environment manages long-running operations and notifies JavaScript when they complete.

---

# Best Practices

- Use synchronous code for fast, simple operations.
- Use asynchronous code for operations that involve waiting.
- Keep asynchronous code readable and organized.
- Prefer modern asynchronous techniques such as Promises and `async`/`await`.
- Always handle possible errors in asynchronous operations.

---

# Section Summary

In this section, you learned the difference between synchronous and asynchronous programming. Synchronous code executes one statement at a time and blocks later statements until the current task finishes. Asynchronous programming allows long-running operations to begin while JavaScript continues executing other code, improving responsiveness and user experience.

Understanding this distinction prepares you to learn how JavaScript coordinates asynchronous tasks internally.

---

# CodeTales Insight

> **Professional developers choose the right execution model for the task at hand. Fast computations are usually synchronous, while operations that involve waiting—such as network requests and timers—are asynchronous. Knowing when and why to use each approach is a key step toward writing efficient, responsive JavaScript applications.**


---

# 11.3 The JavaScript Execution Model

In the previous section, you learned that JavaScript can execute code both synchronously and asynchronously.

A natural question follows:

> **How does JavaScript manage asynchronous tasks if it executes only one piece of JavaScript code at a time?**

The answer lies in the **JavaScript Execution Model**.

The execution model describes how JavaScript works together with the browser (or Node.js) to execute code, manage function calls, handle asynchronous operations, and keep applications responsive.

Understanding this model is one of the biggest milestones in becoming a professional JavaScript developer.

---

# JavaScript Is Single-Threaded

JavaScript executes code using a **single thread**.

A thread is a sequence of instructions executed one after another.

Unlike some programming languages that execute multiple JavaScript statements simultaneously, JavaScript processes one statement at a time.

For example:

```javascript
console.log("A");

console.log("B");

console.log("C");
```

Output

```text
A

B

C
```

Each statement finishes before the next one begins.

---

## Figure 11.8

**Single-Threaded Execution**

```text
Instruction 1

↓

Instruction 2

↓

Instruction 3

↓

Instruction 4
```

Only one instruction is executed at any given moment.

---

# The Challenge

Imagine downloading a large file.

```javascript
downloadFile();

console.log("Done");
```

If JavaScript waited for the download to finish before executing the next statement, the application would become unresponsive.

Users would experience:

- Frozen interfaces
- Delayed button clicks
- Unresponsive forms
- Poor user experience

Fortunately, this does not happen.

Why?

Because JavaScript relies on its execution model.

---

# Components of the JavaScript Execution Model

The execution model consists of several components working together.

These include:

- JavaScript Engine
- Call Stack
- Browser Web APIs (or Node.js APIs)
- Callback Queue
- Event Loop

Each component has a specific responsibility.

---

## Figure 11.9

**The JavaScript Execution Model**

```text
JavaScript Code

↓

Call Stack

↓

Web APIs

↓

Callback Queue

↓

Event Loop

↓

Call Stack
```

These components cooperate continuously while your application is running.

---

# JavaScript Engine

The JavaScript engine executes JavaScript code.

Popular JavaScript engines include:

| Browser | JavaScript Engine |
|----------|-------------------|
| Chrome | V8 |
| Edge | V8 |
| Firefox | SpiderMonkey |
| Safari | JavaScriptCore |

The engine is responsible for:

- Reading JavaScript code
- Parsing the code
- Executing instructions
- Managing memory
- Calling functions

The engine itself does **not** provide browser features such as timers or network requests.

---

# Browser Web APIs

Features like:

- `setTimeout()`
- `fetch()`
- DOM events
- Geolocation
- Local Storage

are provided by the browser—not by the JavaScript language itself.

These browser features are commonly called **Web APIs**.

When JavaScript requests one of these operations, the browser handles it separately while JavaScript continues executing other code.

---

## Figure 11.10

**JavaScript and Web APIs**

```text
JavaScript

↓

Requests Timer

↓

Browser Handles Timer

↓

Timer Completes

↓

Notify JavaScript
```

---

# Callback Queue

When an asynchronous operation finishes, its callback function does **not** execute immediately.

Instead, it is placed inside the **Callback Queue**.

The callback waits there until JavaScript is ready to execute it.

Think of the Callback Queue as a waiting room.

Functions wait patiently until the Call Stack becomes available.

---

# Event Loop

The **Event Loop** continuously checks two things:

1. Is the Call Stack empty?
2. Does the Callback Queue contain waiting callbacks?

If the answer to both questions is yes, the Event Loop moves the first callback from the Callback Queue onto the Call Stack for execution.

This process repeats continuously while the program runs.

---

## Figure 11.11

**Role of the Event Loop**

```text
Callback Queue

↓

Event Loop

↓

Call Stack

↓

Execute Function
```

The Event Loop acts like a traffic controller that coordinates asynchronous execution.

---

# Putting Everything Together

Consider the following code.

```javascript
console.log("Start");

setTimeout(() => {

    console.log("Timer Finished");

}, 2000);

console.log("End");
```

Execution proceeds as follows:

1. `"Start"` is printed.
2. `setTimeout()` is sent to the browser's Web API.
3. JavaScript continues executing.
4. `"End"` is printed.
5. After two seconds, the timer completes.
6. The callback enters the Callback Queue.
7. The Event Loop waits until the Call Stack is empty.
8. The callback executes.
9. `"Timer Finished"` is printed.

Output

```text
Start

End

Timer Finished
```

---

## Figure 11.12

**Execution Timeline**

```text
Call Stack

↓

console.log("Start")

↓

setTimeout()

↓

console.log("End")

↓

Stack Empty

↓

Event Loop

↓

Timer Callback

↓

console.log("Timer Finished")
```

---

# Why This Model Is Important

Without the execution model:

- Browsers would freeze during downloads.
- Videos would stop playing.
- Buttons would not respond.
- Animations would pause.
- Modern web applications would be unusable.

The execution model enables JavaScript to remain responsive even while waiting for slow operations.

---

# Real-World Applications

The execution model powers features such as:

- Online banking
- Social media feeds
- Live chat applications
- Video streaming
- File uploads
- Maps
- Weather applications
- E-commerce websites

Every modern JavaScript application depends on this model.

---

# Best Practices

- Remember that JavaScript executes one piece of code at a time.
- Do not assume asynchronous callbacks execute immediately.
- Understand that browsers provide Web APIs.
- Learn the responsibilities of each execution model component.
- Build a solid understanding before studying Promises and `async`/`await`.

---

# Common Beginner Mistakes

## Mistake 1

Believing JavaScript itself creates multiple threads.

JavaScript remains single-threaded.

The browser or Node.js runtime handles long-running operations outside the Call Stack.

---

## Mistake 2

Thinking callbacks execute immediately after a timer finishes.

Callbacks first enter the Callback Queue.

They execute only when the Call Stack is empty.

---

## Mistake 3

Confusing the JavaScript Engine with the Browser.

The JavaScript engine executes JavaScript.

The browser provides additional APIs such as timers, networking, and the DOM.

---

# Section Summary

In this section, you learned how JavaScript coordinates synchronous and asynchronous operations through its execution model. You explored the roles of the JavaScript Engine, Call Stack, Web APIs, Callback Queue, and Event Loop, and saw how these components work together to execute code efficiently while keeping applications responsive.

The next section focuses on the **Call Stack**, the core data structure responsible for managing function execution.

---

# CodeTales Insight

> **The JavaScript execution model is like a well-organized team. The JavaScript engine executes your code, the browser handles long-running tasks, the Callback Queue waits patiently, and the Event Loop coordinates everything. Once you understand how these pieces work together, asynchronous JavaScript becomes far less mysterious and much easier to master.**

---

# 11.4 The Call Stack

In the previous section, you learned that the JavaScript execution model consists of several components working together.

One of the most important of these components is the **Call Stack**.

Every JavaScript function that executes is managed by the Call Stack.

Without the Call Stack, JavaScript would have no way of knowing:

- Which function should execute next.
- Which function is currently running.
- Which function should resume after another function finishes.

The Call Stack is the mechanism that keeps JavaScript execution organized.

---

# What Is the Call Stack?

The **Call Stack** is a data structure that keeps track of active function calls in a JavaScript program.

Whenever a function is called, it is placed on top of the stack.

When that function finishes executing, it is removed from the stack.

Because the Call Stack follows the **Last In, First Out (LIFO)** principle, the last function added is always the first one removed.

---

## Figure 11.13

**A Stack of Books**

```text
Top

Book C

Book B

Book A

Bottom
```

To remove **Book A**, you must first remove **Book C** and **Book B**.

The Call Stack behaves in the same way.

---

# Understanding LIFO

LIFO stands for:

**Last In, First Out**

This means:

- The most recently called function executes first.
- Earlier functions wait until later functions finish.

This ensures that JavaScript always knows where to return after a function completes.

---

# A Simple Example

```javascript
function greet() {

    console.log("Hello");

}

greet();
```

Execution steps:

1. The global execution context starts.
2. `greet()` is called.
3. `greet()` is pushed onto the Call Stack.
4. `"Hello"` is printed.
5. `greet()` finishes.
6. `greet()` is removed from the Call Stack.

Output

```text
Hello
```

---

## Figure 11.14

**Call Stack During Execution**

```text
Before Calling greet()

┌──────────────┐
│ Global       │
└──────────────┘
```

```text
During greet()

┌──────────────┐
│ greet()      │
├──────────────┤
│ Global       │
└──────────────┘
```

```text
After greet()

┌──────────────┐
│ Global       │
└──────────────┘
```

---

# Nested Function Calls

Functions often call other functions.

Example

```javascript
function first() {

    second();

}

function second() {

    third();

}

function third() {

    console.log("Learning JavaScript");

}

first();
```

Output

```text
Learning JavaScript
```

---

## How the Call Stack Changes

Initially

```text
Global
```

After calling `first()`

```text
first()

Global
```

After calling `second()`

```text
second()

first()

Global
```

After calling `third()`

```text
third()

second()

first()

Global
```

After `third()` finishes

```text
second()

first()

Global
```

After `second()` finishes

```text
first()

Global
```

After `first()` finishes

```text
Global
```

---

## Figure 11.15

**Nested Function Calls**

```text
third()

↓

second()

↓

first()

↓

Global
```

Execution moves from the top of the stack downward as functions complete.

---

# Why the Call Stack Matters

The Call Stack allows JavaScript to:

- Track function execution.
- Return to the correct location after a function finishes.
- Execute nested functions correctly.
- Manage recursion.
- Coordinate synchronous execution.

Without it, function calls would become disorganized.

---

# Stack Overflow

What happens if functions keep calling themselves forever?

Example

```javascript
function loop() {

    loop();

}

loop();
```

Eventually JavaScript runs out of stack space.

Error

```text
RangeError:
Maximum call stack size exceeded
```

This is called a **stack overflow**.

---

## Figure 11.16

**Stack Overflow**

```text
loop()

loop()

loop()

loop()

loop()

loop()

...

Stack Full

↓

Error
```

---

# Recursive Functions

A recursive function calls itself.

Example

```javascript
function countdown(number) {

    if (number === 0) {

        return;

    }

    console.log(number);

    countdown(number - 1);

}

countdown(3);
```

Output

```text
3

2

1
```

Each recursive call creates another entry on the Call Stack.

When the base case is reached, functions begin leaving the stack one by one.

---

# Real-World Example

Imagine customer support.

Each customer receives attention in order.

If the support agent needs help, they call another specialist.

Once the specialist finishes, control returns to the original support agent.

The Call Stack works similarly.

Each completed function returns execution to the function beneath it.

---

# Relationship Between the Call Stack and Asynchronous Code

The Call Stack only executes JavaScript code.

Long-running operations such as:

- Timers
- Network requests
- File operations

are handled outside the Call Stack.

When those operations finish, their callback functions wait until the Call Stack becomes empty before executing.

This interaction is coordinated by the Event Loop, which you will study shortly.

---

## Figure 11.17

**Call Stack and Asynchronous Operations**

```text
JavaScript

↓

Call Stack

↓

Stack Becomes Empty

↓

Event Loop

↓

Callback Executes
```

---

# Best Practices

- Keep functions focused on a single responsibility.
- Avoid unnecessary nesting.
- Ensure recursive functions always have a base case.
- Break large problems into smaller functions.
- Learn to read Call Stack error messages.

---

# Common Beginner Mistakes

## Mistake 1

Thinking multiple JavaScript functions execute simultaneously.

Only one JavaScript function executes on the Call Stack at a time.

---

## Mistake 2

Writing recursive functions without a stopping condition.

Always include a base case.

---

## Mistake 3

Ignoring stack traces in error messages.

A stack trace shows the sequence of function calls that led to an error and is one of the most valuable debugging tools available.

---

# Section Summary

In this section, you learned that the Call Stack is the data structure responsible for managing JavaScript function execution. You explored how functions are added and removed using the Last In, First Out (LIFO) principle, how nested function calls are organized, and why recursive functions can cause a stack overflow if they lack a proper base case. You also saw how the Call Stack works together with the Event Loop to support asynchronous programming.

The next section introduces the **Event Loop**, the component that coordinates asynchronous callbacks and keeps JavaScript applications responsive.

---

# CodeTales Insight

> **Every JavaScript program relies on the Call Stack. It silently tracks every function call, every return, and every nested execution. Once you understand how the Call Stack works, debugging becomes easier, recursion becomes clearer, and asynchronous JavaScript begins to make perfect sense.**

---

# 11.5 The Event Loop

In the previous section, you learned that the Call Stack manages the execution of JavaScript functions.

However, a question remains:

> **If JavaScript executes only one function at a time, how does it know when an asynchronous task is ready to run?**

The answer is the **Event Loop**.

The Event Loop is one of the most important parts of the JavaScript execution model. It coordinates communication between the Call Stack and asynchronous operations, allowing JavaScript applications to remain responsive even while performing long-running tasks.

Without the Event Loop, asynchronous JavaScript would not exist.

---

# What Is the Event Loop?

The **Event Loop** is a mechanism that continuously monitors:

- The Call Stack
- The Callback Queue

Its job is simple:

- If the Call Stack is busy, wait.
- If the Call Stack is empty and callbacks are waiting, move the first callback onto the Call Stack.

The Event Loop repeats this process continuously while the program is running.

---

## Figure 11.18

**The Event Loop**

```text
           JavaScript Code
                  │
                  ▼
            ┌───────────┐
            │ Call Stack│
            └───────────┘
                  ▲
                  │
            Event Loop
                  ▲
                  │
        ┌─────────────────┐
        │ Callback Queue  │
        └─────────────────┘
```

---

# Why Is the Event Loop Necessary?

Consider this example.

```javascript
console.log("Start");

setTimeout(() => {

    console.log("Timer");

}, 3000);

console.log("End");
```

Output

```text
Start

End

Timer
```

Many beginners expect:

```text
Start

Timer

End
```

But that is not what happens.

The Event Loop explains why.

---

# Step-by-Step Execution

### Step 1

JavaScript executes:

```javascript
console.log("Start");
```

Output

```text
Start
```

Call Stack

```text
console.log()

↓

Global
```

---

### Step 2

JavaScript encounters:

```javascript
setTimeout(...)
```

The timer is **not** managed by the Call Stack.

Instead, it is handed to the browser's **Web API**.

```text
Call Stack

↓

setTimeout()

↓

Browser Timer
```

---

### Step 3

JavaScript immediately continues.

```javascript
console.log("End");
```

Output

```text
Start

End
```

The Call Stack finishes executing all synchronous code.

---

### Step 4

Three seconds later...

The browser timer finishes.

The callback function is placed inside the **Callback Queue**.

```text
Callback Queue

↓

console.log("Timer")
```

---

### Step 5

The Event Loop checks:

- Is the Call Stack empty?

If the answer is **Yes**, the callback is moved onto the Call Stack.

```text
Callback Queue

↓

Event Loop

↓

Call Stack
```

---

### Step 6

The callback executes.

Output

```text
Timer
```

Final output

```text
Start

End

Timer
```

---

## Figure 11.19

**Complete Flow**

```text
JavaScript

↓

Call Stack

↓

Web API

↓

Callback Queue

↓

Event Loop

↓

Call Stack

↓

Execute Callback
```

---

# The Event Loop Never Stops

The Event Loop continuously repeats the same process.

```text
Is Stack Empty?

↓

Yes

↓

Queue Has Callback?

↓

Yes

↓

Move Callback

↓

Execute

↓

Repeat
```

This happens thousands of times every second.

---

# Another Example

```javascript
console.log("One");

setTimeout(() => {

    console.log("Two");

}, 0);

console.log("Three");
```

Output

```text
One

Three

Two
```

Why?

Even though the timer delay is **0 milliseconds**, the callback must still:

1. Wait for synchronous code to finish.
2. Enter the Callback Queue.
3. Wait for the Event Loop.

Only then can it execute.

---

# Event Loop vs Call Stack

| Call Stack | Event Loop |
|------------|------------|
| Executes JavaScript functions | Monitors the Call Stack |
| Holds active function calls | Moves callbacks to the Call Stack |
| Uses LIFO order | Runs continuously |
| Executes synchronous code | Coordinates asynchronous callbacks |

Both components work together.

---

# Real-World Analogy

Imagine a receptionist in an office.

Employees (the Call Stack) are busy working.

Visitors (callbacks) arrive and wait in the reception area (Callback Queue).

The receptionist (Event Loop) watches the employees.

Whenever an employee becomes available, the receptionist sends the next visitor into the office.

The receptionist never stops checking.

---

## Figure 11.20

**Office Analogy**

```text
Visitors

↓

Reception Area

↓

Receptionist

↓

Available Employee

↓

Meeting Starts
```

---

# Why the Event Loop Matters

Without the Event Loop:

- Timers would never execute.
- Fetch requests would never return data.
- Button clicks would never trigger callbacks.
- User interfaces would freeze.

The Event Loop makes JavaScript responsive.

---

# Best Practices

- Understand that asynchronous callbacks never interrupt synchronous code.
- Avoid writing long-running synchronous operations.
- Keep callbacks small and focused.
- Learn how the Event Loop coordinates execution before studying Promises and `async`/`await`.

---

# Common Beginner Mistakes

## Mistake 1

Believing `setTimeout(..., 0)` executes immediately.

It does not.

The callback must still wait until the Call Stack is empty.

---

## Mistake 2

Thinking the Event Loop executes callbacks.

The Event Loop **does not execute callbacks directly**.

Its responsibility is to move callbacks from the Callback Queue to the Call Stack when the Call Stack is empty.

The JavaScript engine then executes the callback.

---

## Mistake 3

Assuming asynchronous code can interrupt synchronous execution.

JavaScript always finishes the current synchronous work before processing queued callbacks.

---

# Section Summary

In this section, you learned that the Event Loop is responsible for coordinating asynchronous execution in JavaScript. It continuously monitors the Call Stack and the Callback Queue, moving waiting callbacks onto the Call Stack only when the stack becomes empty. This process allows JavaScript to remain responsive while handling timers, network requests, and other asynchronous operations.

The next section introduces the **Callback Queue**, where completed asynchronous callbacks wait before being executed.

---

# CodeTales Insight

> **The Event Loop is the traffic controller of JavaScript. It doesn't execute your code—it decides *when* your asynchronous callbacks are allowed to execute. Understanding this simple but powerful responsibility is the key to mastering timers, Promises, `async`/`await`, and every modern asynchronous JavaScript application.**

---

# 11.6 The Callback Queue

In the previous section, you learned that the Event Loop continuously monitors the Call Stack.

However, another important question remains:

> **Where do completed asynchronous tasks wait before they are executed?**

The answer is the **Callback Queue**.

The Callback Queue is an essential component of the JavaScript execution model. It temporarily stores callback functions that are ready to execute but must wait until the Call Stack becomes empty.

Understanding the Callback Queue helps explain why asynchronous callbacks execute only after synchronous code has finished.

---

# What Is the Callback Queue?

The **Callback Queue** is a First In, First Out (FIFO) data structure that stores callback functions waiting to be executed.

When an asynchronous operation completes, its callback function is placed at the end of the Callback Queue.

The callback remains there until:

- The Call Stack is empty.
- The Event Loop moves the callback onto the Call Stack.

---

## Figure 11.21

**Callback Queue**

```text
Front

Callback A

↓

Callback B

↓

Callback C

Back
```

The first callback to enter the queue is the first callback to leave.

---

# FIFO Principle

Unlike the Call Stack, which uses **Last In, First Out (LIFO)**, the Callback Queue follows the **First In, First Out (FIFO)** principle.

This means:

- First callback added
- First callback executed

Example

```text
Added

Callback A

Callback B

Callback C
```

Execution order

```text
Callback A

↓

Callback B

↓

Callback C
```

---

# How Callbacks Reach the Queue

Consider the following example.

```javascript
console.log("Start");

setTimeout(() => {

    console.log("First Timer");

}, 2000);

console.log("End");
```

Execution proceeds as follows.

---

### Step 1

JavaScript executes:

```javascript
console.log("Start");
```

Output

```text
Start
```

---

### Step 2

JavaScript encounters:

```javascript
setTimeout(...)
```

The timer is handed to the browser's Web API.

The Call Stack continues executing.

---

### Step 3

JavaScript executes:

```javascript
console.log("End");
```

Output

```text
Start

End
```

---

### Step 4

Two seconds later...

The timer finishes.

The callback function is placed inside the Callback Queue.

```text
Callback Queue

↓

console.log("First Timer")
```

---

### Step 5

The Event Loop checks whether the Call Stack is empty.

If it is empty, the callback moves onto the Call Stack.

---

### Step 6

The callback executes.

Output

```text
First Timer
```

Final output

```text
Start

End

First Timer
```

---

## Figure 11.22

**Journey of a Callback**

```text
setTimeout()

↓

Browser Timer

↓

Callback Queue

↓

Event Loop

↓

Call Stack

↓

Execute
```

---

# Multiple Callbacks

Suppose several timers complete.

```javascript
setTimeout(() => {

    console.log("A");

}, 1000);

setTimeout(() => {

    console.log("B");

}, 1000);

setTimeout(() => {

    console.log("C");

}, 1000);
```

All three callbacks eventually enter the Callback Queue.

```text
Front

A

↓

B

↓

C

Back
```

The Event Loop processes them in order.

Output

```text
A

B

C
```

---

# Callback Queue vs Call Stack

Many beginners confuse these two structures.

| Call Stack | Callback Queue |
|------------|----------------|
| Executes functions | Stores waiting callbacks |
| Uses LIFO | Uses FIFO |
| Holds active execution | Holds completed asynchronous callbacks |
| Managed directly by the JavaScript engine | Managed with help from the Event Loop |

The Callback Queue never executes code directly.

Its only job is to wait.

---

# Real-World Analogy

Imagine visiting a hospital.

Patients first wait in the reception area.

The doctor does not see everyone immediately.

Instead:

- Patients arrive.
- They wait in order.
- The doctor becomes available.
- The next patient enters.

The Callback Queue behaves similarly.

Callbacks patiently wait until JavaScript is ready to execute them.

---

## Figure 11.23

**Hospital Waiting Room**

```text
Patients Arrive

↓

Waiting Room

↓

Doctor Available

↓

Patient Enters Office
```

---

# Does Every Asynchronous Task Use the Callback Queue?

Many asynchronous APIs eventually place callbacks into a queue, but modern JavaScript distinguishes between different types of queues.

For example:

- Timer callbacks (`setTimeout()` and `setInterval()`) are scheduled through the callback (task) queue.
- Promise callbacks (`.then()`, `.catch()`, `.finally()`) are placed in a higher-priority **microtask queue**, which you will learn about later in this chapter.

For now, focus on understanding the standard Callback Queue. Later sections will explain how Promise callbacks are prioritized.

---

# Why the Callback Queue Is Important

Without the Callback Queue:

- Completed timers would execute unpredictably.
- Event handlers could interrupt running code.
- The Event Loop would have nowhere to retrieve waiting callbacks.

The Callback Queue keeps asynchronous execution orderly and predictable.

---

# Best Practices

- Remember that callbacks wait before executing.
- Do not assume an asynchronous callback runs immediately after its operation completes.
- Keep callback functions short and focused.
- Understand that the Event Loop controls when callbacks are executed.

---

# Common Beginner Mistakes

## Mistake 1

Thinking callbacks execute immediately after a timer finishes.

A completed timer only places its callback into the Callback Queue.

Execution still depends on the Event Loop and the Call Stack.

---

## Mistake 2

Confusing the Callback Queue with the Call Stack.

The Call Stack executes functions.

The Callback Queue only stores waiting callbacks.

---

## Mistake 3

Believing callbacks can interrupt synchronous code.

They cannot.

JavaScript always finishes the current synchronous execution before processing queued callbacks.

---

# Section Summary

In this section, you learned that the Callback Queue temporarily stores callback functions after asynchronous operations complete. You explored the FIFO principle, followed a callback from a browser timer to execution, and saw how the Event Loop moves callbacks from the queue to the Call Stack only when the stack becomes empty. You also learned that Promise callbacks use a separate, higher-priority microtask queue, which will be covered later in this chapter.

The next section introduces **callback functions**, one of the earliest techniques for handling asynchronous operations in JavaScript.

---

# CodeTales Insight

> **Think of the Callback Queue as an organized waiting room. Finishing an asynchronous task does not mean its callback executes immediately—it simply earns a place in the queue. Only when the Call Stack is clear does the Event Loop allow that callback to run. Understanding this sequence is essential for writing predictable asynchronous JavaScript.**

---

# 11.7 Understanding Callbacks

In the previous sections, you learned how the JavaScript execution model works using the Call Stack, Event Loop, and Callback Queue.

Now it is time to understand the code that makes asynchronous programming possible—the **callback function**.

Before Promises and `async`/`await` existed, callbacks were the primary technique for handling asynchronous operations in JavaScript.

Even today, callbacks remain an essential part of the language, and you will encounter them frequently when working with events, timers, APIs, and third-party libraries.

---

# What Is a Callback?

A **callback** is a function that is passed as an argument to another function so that it can be executed later.

Instead of executing immediately, the callback waits until the receiving function decides it is the appropriate time to run it.

In simple terms:

> **A callback is a function that another function "calls back" at a later time.**

---

## Figure 11.24

**Callback Concept**

```text
Main Function

↓

Receives Callback

↓

Performs Task

↓

Calls Callback
```

---

# A Simple Callback Example

```javascript
function greet(name) {

    console.log(`Hello, ${name}!`);

}

function processUser(callback) {

    callback("Alice");

}

processUser(greet);
```

Output

```text
Hello, Alice!
```

In this example:

- `greet` is the callback.
- `processUser` receives the callback.
- `processUser` decides when to execute it.

---

# Anonymous Callback Functions

Callbacks are often written as anonymous functions.

```javascript
function processUser(callback) {

    callback();

}

processUser(function () {

    console.log("Processing complete.");

});
```

Output

```text
Processing complete.
```

The callback has no name because it is used only once.

---

# Arrow Function Callbacks

Modern JavaScript commonly uses arrow functions for callbacks.

```javascript
function processUser(callback) {

    callback();

}

processUser(() => {

    console.log("Processing complete.");

});
```

Output

```text
Processing complete.
```

Arrow functions make callback code shorter and easier to read.

---

# Why Are Callbacks Useful?

Callbacks allow functions to become more flexible.

Instead of hardcoding behavior, a function can receive another function and execute it whenever appropriate.

For example:

```javascript
function calculate(a, b, operation) {

    operation(a, b);

}

calculate(10, 5, function (x, y) {

    console.log(x + y);

});
```

Output

```text
15
```

The `calculate()` function does not know what operation will be performed.

It simply executes the callback.

---

## Figure 11.25

**Flexible Functions**

```text
calculate()

↓

Receives Callback

↓

Callback Determines Action
```

---

# Callbacks with Timers

One of the most common callback examples uses `setTimeout()`.

```javascript
console.log("Start");

setTimeout(() => {

    console.log("Timer Finished");

}, 2000);

console.log("End");
```

Output

```text
Start

End

Timer Finished
```

The arrow function is the callback.

The browser executes it after two seconds.

---

# Callbacks with Events

Callbacks are also used when responding to user actions.

```javascript
const button = document.querySelector("button");

button.addEventListener("click", () => {

    console.log("Button clicked.");

});
```

The callback executes only when the user clicks the button.

---

## Figure 11.26

**Event Callback**

```text
User Clicks Button

↓

Browser Detects Event

↓

Execute Callback
```

---

# Synchronous vs Asynchronous Callbacks

Not every callback is asynchronous.

### Synchronous Callback

```javascript
const numbers = [1, 2, 3];

numbers.forEach(function (number) {

    console.log(number);

});
```

Output

```text
1

2

3
```

The callback executes immediately while `forEach()` is running.

---

### Asynchronous Callback

```javascript
setTimeout(() => {

    console.log("Executed Later");

}, 1000);
```

Output

```text
Executed Later
```

The callback executes after the timer completes.

---

# Advantages of Callbacks

Callbacks provide several benefits.

- Increase code flexibility.
- Allow custom behavior.
- Support asynchronous programming.
- Enable event-driven programming.
- Reduce duplicated code.

Callbacks are one of JavaScript's most powerful features.

---

# Limitations of Callbacks

Although callbacks are useful, they can become difficult to manage when many asynchronous operations depend on one another.

For example:

```javascript
login(function () {

    getProfile(function () {

        getMessages(function () {

            getNotifications(function () {

                console.log("Done");

            });

        });

    });

});
```

This deeply nested structure is difficult to read and maintain.

It is commonly known as **callback hell**.

You will study this problem in the next section.

---

## Figure 11.27

**Nested Callbacks**

```text
login()

↓

getProfile()

↓

getMessages()

↓

getNotifications()

↓

Done
```

---

# Best Practices

- Keep callback functions short.
- Use descriptive function names when callbacks are reused.
- Prefer arrow functions for simple callbacks.
- Avoid excessive nesting.
- Consider Promises or `async`/`await` for complex asynchronous workflows.

---

# Common Beginner Mistakes

## Mistake 1

Calling the callback immediately instead of passing it.

Incorrect

```javascript
processUser(greet());
```

Correct

```javascript
processUser(greet);
```

Passing `greet` allows `processUser()` to decide when to execute it.

---

## Mistake 2

Assuming every callback is asynchronous.

Functions such as `forEach()`, `map()`, and `filter()` use synchronous callbacks.

---

## Mistake 3

Creating deeply nested callbacks.

Deep nesting makes code difficult to read, debug, and maintain.

---

# Section Summary

In this section, you learned that a callback is a function passed to another function to be executed later. You explored synchronous and asynchronous callbacks, learned how callbacks are used with timers and events, and discovered both their strengths and their limitations. While callbacks are flexible and powerful, excessive nesting can make programs difficult to understand.

The next section explores **Callback Hell**, a common problem that motivated the introduction of Promises and `async`/`await`.

---

# CodeTales Insight

> **Callbacks were the original building blocks of asynchronous JavaScript. Although modern features like Promises and `async`/`await` simplify asynchronous code, they are built on the same fundamental idea: execute a function when a task has completed. Understanding callbacks gives you a deeper understanding of how modern JavaScript really works.**

---

# 11.8 Callback Hell

In the previous section, you learned that callbacks allow one function to execute another function after a task has completed.

Callbacks work well for simple asynchronous operations.

However, as applications become larger and more complex, multiple asynchronous tasks often depend on one another.

When callbacks become deeply nested, the resulting code becomes difficult to read, understand, debug, and maintain.

This problem is commonly known as **Callback Hell**.

---

# What Is Callback Hell?

**Callback Hell** occurs when multiple asynchronous operations are nested inside one another, creating deeply indented code that is difficult to follow.

Developers sometimes refer to it as the **Pyramid of Doom** because the increasing indentation resembles a pyramid.

---

## Figure 11.28

**The Pyramid of Doom**

```text
Task 1

    Task 2

        Task 3

            Task 4

                Task 5
```

As more asynchronous tasks are added, the code becomes increasingly difficult to manage.

---

# Why Does Callback Hell Happen?

Imagine an application where a user must:

1. Log in.
2. Retrieve their profile.
3. Load their messages.
4. Load their notifications.
5. Display the dashboard.

Each task depends on the successful completion of the previous one.

Using callbacks, the code might look like this:

```javascript
login(function () {

    getProfile(function () {

        getMessages(function () {

            getNotifications(function () {

                displayDashboard();

            });

        });

    });

});
```

Although this code works, it is difficult to read.

---

## Figure 11.29

**Nested Callback Structure**

```text
login()

↓

getProfile()

↓

getMessages()

↓

getNotifications()

↓

displayDashboard()
```

Each new task increases the nesting level.

---

# Problems with Callback Hell

Deeply nested callbacks introduce several problems.

## 1. Poor Readability

It becomes difficult to determine where each callback begins and ends.

Large applications may contain dozens of nested levels.

---

## 2. Difficult Maintenance

Adding or removing functionality often requires modifying several nested blocks.

This increases the likelihood of introducing bugs.

---

## 3. Error Handling Becomes Complicated

Every callback may produce an error.

Handling errors individually creates repetitive code.

Example:

```javascript
login(function (error, user) {

    if (error) {

        console.error(error);

        return;

    }

    getProfile(function (error, profile) {

        if (error) {

            console.error(error);

            return;

        }

        // More nested callbacks...

    });

});
```

The deeper the nesting, the more repetitive the error handling becomes.

---

## 4. Reduced Reusability

Callbacks buried inside other callbacks are difficult to reuse elsewhere in the application.

---

## Figure 11.30

**Increasing Complexity**

```text
Few Callbacks

↓

Easy to Read

↓

Many Nested Callbacks

↓

Difficult to Maintain
```

---

# A Real-World Analogy

Imagine building a tower using blocks.

One block supports another.

Then another.

Then another.

Eventually, the tower becomes unstable and difficult to manage.

Callback Hell is similar.

Every new callback increases complexity.

---

# Can Callback Hell Be Avoided?

Yes.

Developers use several techniques to reduce callback nesting.

### Technique 1

Break large callbacks into smaller named functions.

Instead of:

```javascript
login(function () {

    getProfile(function () {

        getMessages(function () {

            // ...

        });

    });

});
```

You can write:

```javascript
function loadMessages() {

    getMessages(displayDashboard);

}

function loadProfile() {

    getProfile(loadMessages);

}

login(loadProfile);
```

This approach improves readability.

---

### Technique 2

Use Promises.

Promises eliminate much of the deep nesting associated with callbacks.

Instead of nesting callbacks, asynchronous operations can be chained.

You will learn this in the next section.

---

### Technique 3

Use `async` and `await`.

Modern JavaScript provides `async` and `await`, making asynchronous code look almost identical to synchronous code.

Example:

```javascript
async function initializeApp() {

    await login();

    await getProfile();

    await getMessages();

    await getNotifications();

    displayDashboard();

}
```

This version is significantly easier to read.

---

## Figure 11.31

**Evolution of Asynchronous Code**

```text
Callbacks

↓

Callback Hell

↓

Promises

↓

async / await
```

Modern JavaScript has evolved to solve the problems created by excessive callback nesting.

---

# Why You Still Need to Learn Callbacks

You might wonder:

> "If Promises and async/await are better, why learn callbacks?"

The answer is simple.

Callbacks are still widely used in:

- Event listeners
- Timers
- Third-party libraries
- Legacy JavaScript applications
- Node.js APIs

Understanding callbacks helps you understand how Promises and `async`/`await` work internally.

---

# Best Practices

- Avoid deeply nested callbacks.
- Break large callbacks into reusable functions.
- Handle errors consistently.
- Prefer Promises for complex asynchronous workflows.
- Use `async` and `await` in modern applications whenever appropriate.

---

# Common Beginner Mistakes

## Mistake 1

Thinking callbacks are bad.

Callbacks themselves are not the problem.

The problem is excessive nesting.

---

## Mistake 2

Ignoring error handling.

Every asynchronous operation may fail.

Always anticipate and handle possible errors.

---

## Mistake 3

Trying to solve every problem with callbacks.

Modern JavaScript provides Promises and `async`/`await`, which often produce cleaner, more maintainable code.

---

# Section Summary

In this section, you learned that Callback Hell occurs when multiple asynchronous operations are deeply nested, making code difficult to read, debug, and maintain. You explored the problems associated with callback nesting and learned several techniques for reducing complexity, including breaking callbacks into smaller functions, using Promises, and adopting `async`/`await`.

The next section introduces **Promises**, a powerful feature that transformed asynchronous programming by making asynchronous workflows easier to read, chain, and manage.

---

# CodeTales Insight

> **Callback Hell wasn't a flaw in JavaScript—it was a sign that applications had become more sophisticated than the callback pattern could comfortably support. Promises and `async`/`await` didn't replace callbacks completely; they built upon them to create cleaner, more maintainable asynchronous code. Mastering this evolution will help you understand both modern and legacy JavaScript applications.**

---

# 11.9 Promises

In the previous section, you learned about **Callback Hell**, a situation where deeply nested callbacks make asynchronous code difficult to read, debug, and maintain.

As JavaScript applications became more sophisticated, developers needed a cleaner and more reliable way to manage asynchronous operations.

To address this challenge, **Promises** were introduced in ECMAScript 2015 (ES6).

Promises provide a structured way to represent the eventual completion or failure of an asynchronous operation. They allow developers to write asynchronous code that is easier to read, easier to chain, and easier to maintain than nested callbacks.

Today, Promises form the foundation of modern asynchronous JavaScript and are used extensively with APIs such as the Fetch API and `async`/`await`.

---

# What Is a Promise?

A **Promise** is a JavaScript object that represents the eventual result of an asynchronous operation.

Instead of returning a result immediately, a Promise returns an object that promises to provide a value sometime in the future.

Think of it as a placeholder for a value that is not yet available.

---

## Figure 11.32

**Promise Concept**

```text
Start Asynchronous Task

↓

Promise Created

↓

Task Running

↓

Success or Failure

↓

Promise Settled
```

---

# A Real-World Analogy

Imagine ordering a custom laptop online.

After placing your order, the store gives you an order receipt.

The receipt is **not** the laptop.

Instead, it is a promise that one of two things will happen later:

- The laptop will be delivered successfully.
- The order cannot be completed.

The receipt represents a Promise.

---

## Figure 11.33

**Online Order Analogy**

```text
Place Order

↓

Receive Receipt (Promise)

↓

Store Processes Order

↓

Delivered

OR

Order Cancelled
```

---

# Why Were Promises Introduced?

Promises solve several problems associated with callbacks.

They provide:

- Cleaner code
- Better readability
- Easier error handling
- Better scalability
- Sequential asynchronous workflows
- Improved maintainability

Instead of deeply nesting callbacks, Promises allow asynchronous operations to be chained together.

---

# Callback vs Promise

### Callback Approach

```javascript
login(function () {

    getProfile(function () {

        getMessages(function () {

            displayDashboard();

        });

    });

});
```

---

### Promise Approach

```javascript
login()
    .then(getProfile)
    .then(getMessages)
    .then(displayDashboard);
```

The Promise version is much easier to read because each operation is clearly separated.

---

## Figure 11.34

**Callbacks vs Promises**

```text
Callbacks

↓

Nested

↓

Hard to Read
```

```text
Promises

↓

Chained

↓

Easy to Read
```

---

# Promises Represent Future Results

Unlike synchronous functions that return values immediately, asynchronous operations may take time.

For example:

```javascript
const promise = fetch("https://api.example.com/users");
```

At this moment:

- The data has not yet arrived.
- The request is still running.
- JavaScript immediately returns a Promise object.

Later, the Promise will either:

- Resolve successfully.
- Reject because of an error.

---

# Creating a Simple Promise

```javascript
const promise = new Promise((resolve, reject) => {

    resolve("Operation completed successfully.");

});
```

Here:

- `resolve()` indicates success.
- `reject()` indicates failure.

The Promise decides which outcome occurs.

---

# Consuming a Promise

Promises are typically consumed using the `.then()` method.

Example:

```javascript
const promise = Promise.resolve("Hello, JavaScript!");

promise.then((message) => {

    console.log(message);

});
```

Output

```text
Hello, JavaScript!
```

The callback inside `.then()` executes after the Promise is fulfilled.

---

# Promise Workflow

Every Promise follows the same general workflow.

```text
Create Promise

↓

Task Executes

↓

Success?

↓

Yes → Resolve

↓

No → Reject

↓

Handle Result
```

---

## Figure 11.35

**Promise Lifecycle**

```text
Create Promise

↓

Running

↓

Resolve

OR

Reject
```

---

# Promises Improve Error Handling

Callbacks often require error handling at every level of nesting.

Promises centralize error handling.

Example:

```javascript
login()
    .then(getProfile)
    .then(getMessages)
    .catch((error) => {

        console.error(error);

    });
```

A single `.catch()` can handle errors from the entire Promise chain.

---

# Common Uses of Promises

Promises are used throughout modern JavaScript.

Examples include:

- Fetching API data
- Reading files
- Uploading files
- Database communication
- User authentication
- Cloud services
- Payment processing
- Browser APIs

If an operation takes time, it is often represented by a Promise.

---

# Advantages of Promises

Promises provide many benefits.

- Cleaner asynchronous code.
- Better readability.
- Easier debugging.
- Simplified error handling.
- Better composition of asynchronous tasks.
- Seamless integration with `async` and `await`.

Because of these advantages, Promises have become the standard approach for asynchronous programming.

---

# Best Practices

- Use Promises for asynchronous operations.
- Chain related operations instead of nesting them.
- Handle errors using `.catch()`.
- Return Promises from asynchronous functions.
- Prefer `async` and `await` when appropriate.

---

# Common Beginner Mistakes

## Mistake 1

Expecting a Promise to contain the final value immediately.

A Promise represents a value that may become available in the future.

---

## Mistake 2

Ignoring rejected Promises.

Always handle errors using `.catch()` or `try...catch` with `async`/`await`.

---

## Mistake 3

Mixing deeply nested callbacks with Promise chains.

Choose one approach whenever possible to keep code consistent and readable.

---

# Section Summary

In this section, you learned that Promises provide a modern way to manage asynchronous operations in JavaScript. You discovered why they were introduced, how they improve upon callbacks, and how they represent the eventual success or failure of an asynchronous task. You also learned how Promises improve readability, simplify error handling, and form the foundation for modern asynchronous programming.

The next section explores the **three Promise states**—**Pending**, **Fulfilled**, and **Rejected**—and explains how every Promise transitions through its lifecycle.

---

# CodeTales Insight

> **Promises transformed asynchronous JavaScript by replacing deeply nested callbacks with a structured, chainable workflow. They don't make asynchronous operations faster—they make them easier to understand, compose, and maintain. Once you master Promises, you'll be ready to take full advantage of `async` and `await`, the modern standard for asynchronous programming.**

---

# 11.10 Promise States

In the previous section, you learned that a Promise represents the eventual result of an asynchronous operation.

However, a Promise does not immediately contain its final value.

Instead, every Promise moves through a series of well-defined states during its lifetime.

Understanding these states is essential because every Promise you create or use will always be in one of them.

---

# The Three Promise States

Every Promise exists in one of three states:

1. **Pending**
2. **Fulfilled**
3. **Rejected**

A Promise always starts in the **Pending** state.

Eventually, it either becomes **Fulfilled** or **Rejected**.

Once a Promise is fulfilled or rejected, its state can never change again.

---

## Figure 11.36

**Promise Lifecycle**

```text
                Pending
                   │
         ┌─────────┴─────────┐
         │                   │
         ▼                   ▼
    Fulfilled            Rejected
```

A Promise can only move forward.

It can never return to the Pending state.

---

# Pending State

A Promise is **Pending** when the asynchronous operation is still in progress.

During this time:

- The task has started.
- No result is available yet.
- JavaScript continues executing other code.

Example:

```javascript
const promise = new Promise((resolve, reject) => {

    // Waiting...

});
```

At this point:

- The Promise has neither succeeded nor failed.

---

## Figure 11.37

**Pending State**

```text
Promise Created

↓

Task Running

↓

Waiting...
```

---

# Fulfilled State

A Promise becomes **Fulfilled** when the asynchronous operation completes successfully.

The Promise now contains a successful result.

Example:

```javascript
const promise = new Promise((resolve) => {

    resolve("Download complete.");

});
```

Output

```text
Download complete.
```

The Promise has finished successfully.

---

## Figure 11.38

**Fulfilled State**

```text
Task Completed

↓

resolve()

↓

Promise Fulfilled
```

---

# Rejected State

A Promise becomes **Rejected** when something goes wrong.

Possible reasons include:

- Network failure
- Invalid data
- Server error
- File not found
- Permission denied

Example

```javascript
const promise = new Promise((resolve, reject) => {

    reject("Network error.");

});
```

Output

```text
Network error.
```

---

## Figure 11.39

**Rejected State**

```text
Task Failed

↓

reject()

↓

Promise Rejected
```

---

# Promise State Transitions

A Promise can move only in one direction.

```text
Pending

↓

Fulfilled
```

OR

```text
Pending

↓

Rejected
```

It can never do this:

```text
Pending

↓

Fulfilled

↓

Rejected
```

Nor this:

```text
Rejected

↓

Fulfilled
```

Once settled, a Promise is **immutable**.

---

# Example of a Fulfilled Promise

```javascript
const promise = Promise.resolve("Success!");

promise.then((result) => {

    console.log(result);

});
```

Output

```text
Success!
```

The Promise is already fulfilled.

---

# Example of a Rejected Promise

```javascript
const promise = Promise.reject("Something went wrong.");

promise.catch((error) => {

    console.log(error);

});
```

Output

```text
Something went wrong.
```

The Promise is already rejected.

---

# Visualizing Promise States

Imagine ordering food online.

### Pending

Your order has been received.

The restaurant is preparing the meal.

```text
Order Received

↓

Preparing Food
```

---

### Fulfilled

The food arrives successfully.

```text
Preparing Food

↓

Delivered
```

---

### Rejected

The restaurant cannot complete the order.

```text
Preparing Food

↓

Cancelled
```

This is exactly how Promise states work.

---

## Figure 11.40

**Restaurant Analogy**

```text
Place Order

↓

Preparing

↓

Delivered

OR

Cancelled
```

---

# Why Promise States Matter

Understanding Promise states helps developers:

- Predict program behavior.
- Handle success correctly.
- Handle failures gracefully.
- Build reliable asynchronous applications.

Every Promise-based API follows these same rules.

---

# Promise State vs Promise Result

Many beginners confuse a Promise's **state** with its **result**.

Example:

```javascript
Promise

↓

State

Pending

↓

Result

Not Available Yet
```

Later:

```text
State

Fulfilled

↓

Result

Value Available
```

Or:

```text
State

Rejected

↓

Result

Error Available
```

The state describes the Promise itself.

The result describes what the Promise eventually produces.

---

# Best Practices

- Always assume a Promise may fail.
- Handle fulfilled Promises using `.then()`.
- Handle rejected Promises using `.catch()`.
- Remember that every Promise starts in the Pending state.
- Never assume an asynchronous task completes immediately.

---

# Common Beginner Mistakes

## Mistake 1

Thinking Pending means something is wrong.

Pending simply means the task is still running.

---

## Mistake 2

Believing a Promise can become fulfilled and later rejected.

A Promise settles only once.

Its state never changes afterward.

---

## Mistake 3

Ignoring rejected Promises.

Unhandled Promise rejections can cause application errors and make debugging more difficult.

Always handle errors appropriately.

---

# Section Summary

In this section, you learned that every Promise progresses through a lifecycle consisting of three possible states: Pending, Fulfilled, and Rejected. You discovered that every Promise begins in the Pending state, eventually settles as either Fulfilled or Rejected, and can never change state afterward. You also learned how Promise states relate to asynchronous operations and why proper error handling is essential.

The next section explains **how to create Promises**, where you will learn how the `Promise` constructor works and how to use the `resolve()` and `reject()` functions to represent successful and failed asynchronous operations.

---

# CodeTales Insight

> **Every Promise tells a story. It begins with uncertainty (Pending), ends in success (Fulfilled) or failure (Rejected), and never changes its outcome afterward. Once you understand these three states, you'll find it much easier to reason about asynchronous code and build reliable JavaScript applications.**


---

# 11.11 Creating Promises

In the previous section, you learned that every Promise has three possible states: **Pending**, **Fulfilled**, and **Rejected**.

Now it is time to learn how to create your own Promises.

Although JavaScript provides many built-in Promise-based APIs such as `fetch()`, there are situations where you may need to wrap your own asynchronous operations inside a Promise.

Creating Promises allows you to represent operations that may either succeed or fail in a structured and predictable way.

---

# The Promise Constructor

A Promise is created using the `Promise` constructor.

General syntax:

```javascript
const promise = new Promise((resolve, reject) => {

    // Asynchronous operation

});
```

The constructor accepts one argument:

- An **executor function**

The executor function itself receives two arguments:

- `resolve`
- `reject`

These functions determine how the Promise will eventually settle.

---

## Figure 11.41

**Creating a Promise**

```text
Promise

↓

Executor Function

↓

resolve()      reject()

↓

Promise Settled
```

---

# Understanding resolve()

The `resolve()` function is called when an asynchronous operation completes successfully.

Example:

```javascript
const promise = new Promise((resolve, reject) => {

    resolve("Operation successful.");

});
```

The Promise immediately becomes **Fulfilled**.

---

# Consuming the Promise

```javascript
promise.then((result) => {

    console.log(result);

});
```

Output

```text
Operation successful.
```

---

# Understanding reject()

The `reject()` function is called when an error occurs.

Example

```javascript
const promise = new Promise((resolve, reject) => {

    reject("Operation failed.");

});
```

The Promise immediately becomes **Rejected**.

---

# Handling Rejection

```javascript
promise.catch((error) => {

    console.log(error);

});
```

Output

```text
Operation failed.
```

---

## Figure 11.42

**Promise Outcomes**

```text
Task Starts

↓

Success?

↓

Yes → resolve()

↓

Fulfilled
```

```text
Task Starts

↓

Success?

↓

No → reject()

↓

Rejected
```

---

# Simulating an Asynchronous Operation

Promises are most useful for asynchronous work.

Example:

```javascript
const promise = new Promise((resolve, reject) => {

    setTimeout(() => {

        resolve("Download complete.");

    }, 2000);

});
```

Consuming the Promise:

```javascript
promise.then((result) => {

    console.log(result);

});
```

Output (after two seconds)

```text
Download complete.
```

---

# Simulating Failure

```javascript
const promise = new Promise((resolve, reject) => {

    setTimeout(() => {

        reject("Unable to connect to the server.");

    }, 2000);

});
```

Handling the error:

```javascript
promise.catch((error) => {

    console.log(error);

});
```

Output

```text
Unable to connect to the server.
```

---

# Returning Values

The value passed to `resolve()` becomes available inside `.then()`.

Example

```javascript
const promise = new Promise((resolve) => {

    resolve(100);

});

promise.then((value) => {

    console.log(value);

});
```

Output

```text
100
```

---

# Returning Objects

Promises can resolve with any JavaScript value.

Example

```javascript
const promise = new Promise((resolve) => {

    resolve({

        name: "Ada",

        age: 25

    });

});

promise.then((user) => {

    console.log(user.name);

});
```

Output

```text
Ada
```

---

# Choosing Between resolve() and reject()

Use `resolve()` when:

- The task completes successfully.
- Data is available.
- Validation succeeds.

Use `reject()` when:

- An error occurs.
- Validation fails.
- A network request cannot be completed.
- Required data is missing.

Only one of these functions should be called.

---

## Figure 11.43

**Decision Flow**

```text
Start Task

↓

Success?

↓

Yes

↓

resolve()

↓

Fulfilled
```

```text
Start Task

↓

Failure?

↓

Yes

↓

reject()

↓

Rejected
```

---

# Important Rule

A Promise can settle **only once**.

Example

```javascript
const promise = new Promise((resolve, reject) => {

    resolve("Success");

    reject("Failure");

});
```

Only the first call matters.

The Promise becomes **Fulfilled**, and the later call to `reject()` is ignored.

---

# Real-World Analogy

Imagine applying for a passport.

You submit your application.

Later, one of two outcomes occurs:

- Your passport is approved.
- Your application is rejected.

Both outcomes cannot happen.

Once a decision has been made, it is final.

Promises work the same way.

---

## Figure 11.44

**Passport Application**

```text
Submit Application

↓

Processing

↓

Approved

OR

Rejected
```

---

# Best Practices

- Always resolve or reject every Promise.
- Use meaningful values when calling `resolve()`.
- Provide descriptive error messages when calling `reject()`.
- Avoid creating unnecessary Promises when an API already returns one.
- Keep the executor function simple and focused.

---

# Common Beginner Mistakes

## Mistake 1

Calling both `resolve()` and `reject()`.

Only the first call has any effect.

---

## Mistake 2

Forgetting to handle rejected Promises.

Always use `.catch()` when a Promise might fail.

---

## Mistake 3

Using Promises for purely synchronous code.

Promises are intended for operations that involve waiting or asynchronous behavior.

---

# Section Summary

In this section, you learned how to create Promises using the `Promise` constructor. You explored the executor function, learned the roles of `resolve()` and `reject()`, created successful and failed Promises, and discovered how values passed to `resolve()` become available through `.then()`. You also learned that a Promise can settle only once and should always be handled appropriately.

The next section explains **how to consume Promises** using the `.then()`, `.catch()`, and `.finally()` methods.

---

# CodeTales Insight

> **Creating a Promise is like making a contract with the future. You begin an operation today, and you guarantee that it will eventually produce one of two outcomes: success or failure. By consistently using `resolve()` and `reject()` to represent these outcomes, you make your asynchronous code predictable, maintainable, and easier for other developers to understand.**

---

# 11.12 Consuming Promises

In the previous section, you learned how to create Promises using the `Promise` constructor and how to settle them using the `resolve()` and `reject()` functions.

Creating a Promise is only part of the process.

To make Promises useful, we must also learn how to **consume** them—that is, how to receive the successful result, handle errors, and execute cleanup code after the Promise has finished.

JavaScript provides three primary methods for consuming Promises:

- `.then()`
- `.catch()`
- `.finally()`

Together, these methods form the foundation of Promise-based asynchronous programming.

---

# The `.then()` Method

The `.then()` method is used to handle a Promise that has been **fulfilled**.

When a Promise resolves successfully, the value passed to `resolve()` becomes available inside `.then()`.

General syntax:

```javascript
promise.then((result) => {

    // Handle successful result

});
```

---

## Example

```javascript
const promise = Promise.resolve("Welcome to JavaScript!");

promise.then((message) => {

    console.log(message);

});
```

Output

```text
Welcome to JavaScript!
```

---

## Figure 11.45

**Using `.then()`**

```text
Promise

↓

Resolved

↓

.then()

↓

Use Result
```

---

# Receiving Different Types of Values

A Promise can resolve with any JavaScript value.

### Number

```javascript
Promise.resolve(250)

.then((value) => {

    console.log(value);

});
```

Output

```text
250
```

---

### Object

```javascript
Promise.resolve({

    name: "John",

    age: 28

})

.then((user) => {

    console.log(user.name);

});
```

Output

```text
John
```

---

### Array

```javascript
Promise.resolve(["HTML", "CSS", "JavaScript"])

.then((courses) => {

    console.log(courses[0]);

});
```

Output

```text
HTML
```

---

# The `.catch()` Method

Sometimes asynchronous operations fail.

The `.catch()` method handles rejected Promises.

General syntax

```javascript
promise.catch((error) => {

    // Handle error

});
```

---

## Example

```javascript
const promise = Promise.reject("Network error.");

promise.catch((error) => {

    console.log(error);

});
```

Output

```text
Network error.
```

---

## Figure 11.46

**Using `.catch()`**

```text
Promise

↓

Rejected

↓

.catch()

↓

Handle Error
```

---

# Why `.catch()` Is Important

Without proper error handling:

- Applications may crash.
- Users receive poor feedback.
- Debugging becomes more difficult.

Every Promise that can fail should have an appropriate error handler.

---

# The `.finally()` Method

The `.finally()` method executes regardless of whether a Promise succeeds or fails.

It is commonly used for cleanup tasks.

General syntax

```javascript
promise.finally(() => {

    // Cleanup code

});
```

---

## Example

```javascript
const promise = Promise.resolve("Completed");

promise
    .then((result) => {

        console.log(result);

    })
    .finally(() => {

        console.log("Operation finished.");

    });
```

Output

```text
Completed

Operation finished.
```

---

# `.finally()` After Failure

```javascript
const promise = Promise.reject("Server unavailable.");

promise
    .catch((error) => {

        console.log(error);

    })
    .finally(() => {

        console.log("Closing connection.");

    });
```

Output

```text
Server unavailable.

Closing connection.
```

Notice that `.finally()` executes in both cases.

---

## Figure 11.47

**`.finally()` Always Executes**

```text
Promise

↓

Resolved

OR

Rejected

↓

finally()
```

---

# Combining `.then()`, `.catch()`, and `.finally()`

The three methods are often used together.

Example

```javascript
const promise = new Promise((resolve, reject) => {

    resolve("File uploaded.");

});

promise
    .then((message) => {

        console.log(message);

    })
    .catch((error) => {

        console.log(error);

    })
    .finally(() => {

        console.log("Upload process finished.");

    });
```

Output

```text
File uploaded.

Upload process finished.
```

---

# Execution Flow

A Promise typically follows this sequence.

```text
Promise Created

↓

Resolve?

↓

Yes

↓

.then()

↓

finally()
```

OR

```text
Promise Created

↓

Reject?

↓

Yes

↓

.catch()

↓

finally()
```

---

## Figure 11.48

**Promise Consumption Flow**

```text
Promise

↓

Success?

↓

Yes → .then()

↓

finally()
```

```text
Promise

↓

Failure?

↓

Yes → .catch()

↓

finally()
```

---

# Real-World Example

Imagine downloading a document.

- If the download succeeds, display the document.
- If it fails, display an error message.
- Whether it succeeds or fails, hide the loading spinner.

This is exactly how `.then()`, `.catch()`, and `.finally()` work together.

---

# Best Practices

- Use `.then()` to process successful results.
- Use `.catch()` to handle all possible errors.
- Use `.finally()` for cleanup operations.
- Keep callback functions small and readable.
- Always anticipate the possibility of failure.

---

# Common Beginner Mistakes

## Mistake 1

Using `.then()` without considering failures.

Always provide an error-handling strategy.

---

## Mistake 2

Putting cleanup code inside `.then()`.

Cleanup code belongs in `.finally()` because it should execute regardless of the outcome.

---

## Mistake 3

Ignoring rejected Promises.

Unhandled Promise rejections make applications unreliable and harder to debug.

---

# Section Summary

In this section, you learned how to consume Promises using the `.then()`, `.catch()`, and `.finally()` methods. You discovered that `.then()` processes successful results, `.catch()` handles errors, and `.finally()` executes cleanup code regardless of the Promise's outcome. Together, these methods provide a structured and reliable approach to working with asynchronous operations in JavaScript.

The next section introduces **Promise Chaining**, where you will learn how to connect multiple asynchronous operations into a clean, readable sequence without falling into Callback Hell.

---

# CodeTales Insight

> **Creating a Promise is only the beginning. The true power of Promises lies in how you consume them. By consistently using `.then()` for success, `.catch()` for errors, and `.finally()` for cleanup, you create asynchronous code that is easier to read, easier to debug, and far more reliable in real-world applications.**

---

# 11.13 Promise Chaining

In the previous section, you learned how to consume Promises using `.then()`, `.catch()`, and `.finally()`.

While these methods are useful individually, their true power becomes apparent when multiple asynchronous operations must be performed in sequence.

Instead of nesting callbacks inside callbacks, Promises allow operations to be connected in a clean, readable chain.

This technique is known as **Promise Chaining**.

---

# What Is Promise Chaining?

**Promise Chaining** is the process of connecting multiple Promise-based operations together by returning a Promise (or a value) from one `.then()` method to the next.

Each `.then()` waits for the previous Promise to complete before executing.

This creates a sequence of asynchronous operations that reads from top to bottom.

---

## Figure 11.49

**Promise Chain**

```text
Promise

↓

.then()

↓

.then()

↓

.then()

↓

.catch()

↓

.finally()
```

Each step waits for the previous one to finish.

---

# Why Use Promise Chaining?

Without Promise chaining, developers often create deeply nested callbacks.

Example:

```javascript
login(function () {

    getProfile(function () {

        getMessages(function () {

            displayDashboard();

        });

    });

});
```

Although functional, this code becomes difficult to read and maintain.

Using Promise chaining:

```javascript
login()
    .then(getProfile)
    .then(getMessages)
    .then(displayDashboard);
```

The chained version is much cleaner.

---

# A Simple Promise Chain

```javascript
Promise.resolve(5)

.then((number) => {

    return number * 2;

})

.then((number) => {

    return number + 10;

})

.then((number) => {

    console.log(number);

});
```

Output

```text
20
```

Each `.then()` receives the value returned by the previous one.

---

## Figure 11.50

**Value Flow**

```text
5

↓

10

↓

20

↓

Display Result
```

---

# Returning Values

Each `.then()` may return a value.

That value automatically becomes the input for the next `.then()`.

Example

```javascript
Promise.resolve(100)

.then((value) => {

    return value / 2;

})

.then((value) => {

    console.log(value);

});
```

Output

```text
50
```

---

# Returning Another Promise

A `.then()` method may also return another Promise.

Example

```javascript
function double(value) {

    return Promise.resolve(value * 2);

}

Promise.resolve(10)

.then(double)

.then(double)

.then((result) => {

    console.log(result);

});
```

Output

```text
40
```

JavaScript automatically waits for each returned Promise to settle before moving to the next `.then()`.

---

# Real-World Example

Imagine registering a new user.

The application must:

1. Create the account.
2. Send a verification email.
3. Log the activity.
4. Display a success message.

Using Promise chaining:

```javascript
createAccount()

.then(sendVerificationEmail)

.then(logActivity)

.then(showSuccessMessage)

.catch(handleError);
```

Each step executes only after the previous one completes successfully.

---

## Figure 11.51

**User Registration Workflow**

```text
Create Account

↓

Send Email

↓

Log Activity

↓

Show Success Message
```

---

# Error Handling in Promise Chains

One advantage of Promise chaining is centralized error handling.

Example

```javascript
login()

.then(getProfile)

.then(getMessages)

.then(displayDashboard)

.catch((error) => {

    console.error(error);

});
```

If any Promise in the chain rejects, execution skips the remaining `.then()` methods and jumps directly to `.catch()`.

---

## Figure 11.52

**Error Flow**

```text
Promise

↓

.then()

↓

.then()

↓

Error

↓

.catch()
```

This simplifies error handling considerably.

---

# Adding `.finally()`

You can add `.finally()` at the end of the chain.

```javascript
login()

.then(getProfile)

.then(getMessages)

.catch((error) => {

    console.error(error);

})

.finally(() => {

    console.log("Process completed.");

});
```

Output (if successful)

```text
Process completed.
```

Output (if an error occurs)

```text
Process completed.
```

`.finally()` always executes.

---

# Benefits of Promise Chaining

Promise chaining offers several advantages.

- Eliminates Callback Hell.
- Improves readability.
- Simplifies debugging.
- Centralizes error handling.
- Makes asynchronous workflows easier to understand.
- Produces maintainable code.

---

# Common Mistakes

## Mistake 1

Forgetting to return a value.

Incorrect

```javascript
Promise.resolve(5)

.then((value) => {

    value * 2;

})

.then((value) => {

    console.log(value);

});
```

The second `.then()` receives `undefined`.

Correct

```javascript
Promise.resolve(5)

.then((value) => {

    return value * 2;

})

.then((value) => {

    console.log(value);

});
```

---

## Mistake 2

Creating unnecessary nesting.

Incorrect

```javascript
login().then(() => {

    getProfile().then(() => {

        getMessages();

    });

});
```

Correct

```javascript
login()

.then(getProfile)

.then(getMessages);
```

---

## Mistake 3

Ignoring errors.

Every Promise chain should end with a `.catch()` unless errors are handled elsewhere.

---

# Best Practices

- Return values from each `.then()` when appropriate.
- Return Promises instead of nesting them.
- Place a single `.catch()` near the end of the chain.
- Use `.finally()` for cleanup tasks.
- Keep each `.then()` focused on one responsibility.

---

# Section Summary

In this section, you learned how Promise Chaining allows multiple asynchronous operations to execute in sequence without deeply nested callbacks. You discovered how values and Promises flow through a chain, how errors propagate to a single `.catch()` handler, and how `.finally()` can perform cleanup regardless of the outcome. Promise chaining makes asynchronous JavaScript significantly cleaner and easier to maintain than traditional callback-based code.

The next section introduces **`async` and `await`**, which build on Promises to make asynchronous code look and behave much like synchronous code.

---

# CodeTales Insight

> **Promise chaining transformed asynchronous JavaScript by replacing the "Pyramid of Doom" with a clear, linear workflow. Each Promise builds on the result of the previous one, making your code easier to read, easier to debug, and easier to extend. This elegant approach laid the foundation for `async` and `await`, which you'll explore next.**

---

# 11.14 Async and Await

In the previous section, you learned how Promise chaining allows multiple asynchronous operations to execute in sequence.

Although Promise chaining is much cleaner than nested callbacks, long chains of `.then()` methods can still become difficult to read in large applications.

To simplify asynchronous programming even further, ECMAScript 2017 (ES8) introduced **`async`** and **`await`**.

These keywords allow developers to write asynchronous code that looks almost identical to synchronous code while still using Promises behind the scenes.

Today, `async` and `await` are considered the preferred way to write asynchronous JavaScript.

---

# What Are `async` and `await`?

`async` and `await` are special JavaScript keywords that simplify working with Promises.

- `async` declares that a function is asynchronous.
- `await` pauses the execution of that function until a Promise settles.

Together, they make asynchronous code easier to read and maintain.

---

## Figure 11.53

**Async Function Workflow**

```text
Call Async Function

↓

Run Until await

↓

Wait for Promise

↓

Promise Settles

↓

Continue Execution
```

---

# The `async` Keyword

A function becomes asynchronous by adding the `async` keyword before the `function` keyword.

Example

```javascript
async function greet() {

    return "Hello, JavaScript!";

}
```

Although the function appears to return a string, it actually returns a Promise.

---

## Example

```javascript
async function greet() {

    return "Hello";

}

greet().then((message) => {

    console.log(message);

});
```

Output

```text
Hello
```

---

# The `await` Keyword

The `await` keyword waits for a Promise to settle before continuing execution.

It can only be used inside an `async` function.

Example

```javascript
async function example() {

    const message = await Promise.resolve("Learning JavaScript");

    console.log(message);

}

example();
```

Output

```text
Learning JavaScript
```

---

## Figure 11.54

**Using `await`**

```text
Promise

↓

await

↓

Promise Resolves

↓

Continue Function
```

---

# Comparing Promises and `async`/`await`

### Promise Chaining

```javascript
login()

.then(getProfile)

.then(getMessages)

.then(displayDashboard)

.catch(handleError);
```

---

### Async/Await

```javascript
async function initializeApp() {

    try {

        await login();

        await getProfile();

        await getMessages();

        displayDashboard();

    } catch (error) {

        handleError(error);

    }

}
```

The second version is often easier to read because it resembles ordinary sequential code.

---

# Using `await` with `fetch()`

One of the most common uses of `await` is with the Fetch API.

```javascript
async function getUsers() {

    const response = await fetch("https://jsonplaceholder.typicode.com/users");

    const users = await response.json();

    console.log(users);

}

getUsers();
```

Here:

1. `await fetch(...)` waits for the HTTP request.
2. `await response.json()` waits for the JSON data to be parsed.
3. The resulting array is displayed.

---

# Execution Does Not Block the Entire Program

Although `await` pauses the current `async` function, it does **not** block the entire JavaScript program.

Other synchronous code and asynchronous tasks can continue executing.

Example

```javascript
async function demo() {

    console.log("Start");

    await Promise.resolve();

    console.log("End");

}

demo();

console.log("Outside");
```

Possible output

```text
Start

Outside

End
```

Only the `demo()` function pauses at `await`.

---

## Figure 11.55

**Execution Flow**

```text
Async Function

↓

await

↓

Pause Function

↓

Other Code Executes

↓

Resume Function
```

---

# Returning Values

An `async` function always returns a Promise.

Example

```javascript
async function add(a, b) {

    return a + b;

}

add(10, 20)

.then((result) => {

    console.log(result);

});
```

Output

```text
30
```

---

# Returning Awaited Results

```javascript
async function getNumber() {

    const value = await Promise.resolve(50);

    return value;

}

getNumber()

.then((number) => {

    console.log(number);

});
```

Output

```text
50
```

---

# Why `async` and `await` Are Better

Compared with Promise chaining, `async` and `await` provide several advantages.

- Cleaner syntax.
- Better readability.
- Easier debugging.
- Reduced nesting.
- Easier error handling.
- Code that resembles synchronous programming.

These advantages make them the preferred approach in modern JavaScript development.

---

# Real-World Analogy

Imagine baking a cake.

Traditional Promise chaining resembles repeatedly checking whether each step has finished before starting the next.

Using `async` and `await` is like following a recipe:

1. Mix the ingredients.
2. Wait for the cake to bake.
3. Remove it from the oven.
4. Decorate it.

Each step naturally follows the previous one.

---

## Figure 11.56

**Recipe Analogy**

```text
Mix Ingredients

↓

await Bake

↓

Decorate

↓

Serve
```

---

# Best Practices

- Use `async` for functions that perform asynchronous work.
- Use `await` only with Promises.
- Keep `async` functions focused on one responsibility.
- Handle errors using `try...catch`.
- Prefer `async` and `await` over long Promise chains for readability.

---

# Common Beginner Mistakes

## Mistake 1

Using `await` outside an `async` function.

Incorrect

```javascript
const data = await fetch(url);
```

Correct

```javascript
async function loadData() {

    const data = await fetch(url);

}
```

---

## Mistake 2

Thinking `await` blocks the entire program.

It pauses only the current `async` function.

---

## Mistake 3

Forgetting that an `async` function always returns a Promise.

Even when returning a normal value, JavaScript automatically wraps it in a Promise.

---

# Section Summary

In this section, you learned how the `async` and `await` keywords simplify asynchronous programming in JavaScript. You discovered that `async` functions always return Promises, `await` pauses execution until a Promise settles, and together they make asynchronous code cleaner, more readable, and easier to maintain than long Promise chains. You also learned how to use `await` with the Fetch API and why `async`/`await` has become the modern standard for asynchronous JavaScript.

The next section explains **error handling with `try...catch`**, where you'll learn how to manage failures in `async` functions gracefully and build more reliable applications.

---

# CodeTales Insight

> **`async` and `await` didn't replace Promises—they made them easier to use. Every `await` still works with a Promise behind the scenes, but the code becomes much more natural to read and write. Mastering `async` and `await` is one of the biggest steps toward writing professional-quality JavaScript.**

---

# 11.15 Error Handling with `try...catch`

In the previous section, you learned how `async` and `await` simplify asynchronous programming by making asynchronous code look like synchronous code.

However, asynchronous operations can fail.

For example:

- A network request may fail.
- A file may not exist.
- A server may return an error.
- User input may be invalid.
- A database connection may be unavailable.

Professional applications must anticipate these situations and respond appropriately.

JavaScript provides the **`try...catch` statement** to handle errors in synchronous code and, when combined with `async` and `await`, to manage errors in asynchronous code as well.

---

# What Is `try...catch`?

The `try...catch` statement allows you to execute code that may throw an error without causing the entire application to crash.

It consists of two parts:

- `try`
- `catch`

General syntax

```javascript
try {

    // Code that may throw an error

} catch (error) {

    // Handle the error

}
```

---

## Figure 11.57

**Structure of `try...catch`**

```text
try

↓

Error?

↓

No

↓

Continue Program
```

```text
try

↓

Error?

↓

Yes

↓

catch

↓

Handle Error
```

---

# A Simple Example

```javascript
try {

    console.log("Learning JavaScript.");

} catch (error) {

    console.log("An error occurred.");

}
```

Output

```text
Learning JavaScript.
```

Since no error occurs, the `catch` block is skipped.

---

# Catching an Error

```javascript
try {

    unknownFunction();

} catch (error) {

    console.log("Something went wrong.");

}
```

Output

```text
Something went wrong.
```

Instead of terminating the program, JavaScript executes the `catch` block.

---

# Understanding the Error Object

The `catch` block receives an **Error object**.

Example

```javascript
try {

    unknownFunction();

} catch (error) {

    console.log(error);

}
```

Possible output

```text
ReferenceError: unknownFunction is not defined
```

The Error object contains useful information for debugging.

---

# Useful Error Properties

The Error object provides several useful properties.

| Property | Description |
|----------|-------------|
| `name` | Type of error |
| `message` | Error description |
| `stack` | Call stack leading to the error |

Example

```javascript
try {

    unknownFunction();

} catch (error) {

    console.log(error.name);

    console.log(error.message);

}
```

Possible output

```text
ReferenceError

unknownFunction is not defined
```

---

## Figure 11.58

**Error Object**

```text
Error

├── name

├── message

└── stack
```

---

# Using `try...catch` with `async` and `await`

One of the biggest advantages of `async` and `await` is that Promise rejections can be handled using ordinary `try...catch` blocks.

Example

```javascript
async function getData() {

    try {

        const response = await fetch("https://invalid-url.com");

        console.log(response);

    } catch (error) {

        console.log("Request failed.");

    }

}

getData();
```

If the request fails, execution jumps directly to the `catch` block.

---

# Example with JSON

```javascript
async function getUsers() {

    try {

        const response = await fetch("https://jsonplaceholder.typicode.com/users");

        const users = await response.json();

        console.log(users);

    } catch (error) {

        console.log("Unable to load users.");

    }

}

getUsers();
```

If any step fails, the error is handled safely.

---

## Figure 11.59

**Async Error Handling**

```text
await Promise

↓

Success?

↓

Yes

↓

Continue
```

```text
await Promise

↓

Failure?

↓

Yes

↓

catch
```

---

# The `finally` Block

JavaScript also provides an optional `finally` block.

The `finally` block always executes, whether an error occurs or not.

General syntax

```javascript
try {

    // Code

} catch (error) {

    // Handle error

} finally {

    // Cleanup

}
```

---

## Example

```javascript
try {

    console.log("Connecting...");

} catch (error) {

    console.log("Connection failed.");

} finally {

    console.log("Connection closed.");

}
```

Output

```text
Connecting...

Connection closed.
```

The `finally` block executes regardless of the outcome.

---

## Figure 11.60

**Execution Flow**

```text
try

↓

Success?

↓

Yes

↓

finally
```

```text
try

↓

Failure?

↓

Yes

↓

catch

↓

finally
```

---

# Throwing Your Own Errors

You can create your own errors using the `throw` keyword.

Example

```javascript
function divide(a, b) {

    if (b === 0) {

        throw new Error("Division by zero is not allowed.");

    }

    return a / b;

}

try {

    console.log(divide(10, 0));

} catch (error) {

    console.log(error.message);

}
```

Output

```text
Division by zero is not allowed.
```

This allows developers to detect invalid situations and provide meaningful feedback.

---

# Real-World Example

Imagine an online banking application.

If transferring money fails because the internet connection is lost, the application should:

- Display an informative error message.
- Prevent the application from crashing.
- Allow the user to try again.

This is exactly what proper error handling achieves.

---

# Best Practices

- Use `try...catch` around code that may fail.
- Display helpful error messages.
- Log errors for debugging.
- Keep `try` blocks as small as practical.
- Use `finally` for cleanup tasks.
- Throw meaningful errors when validating data.

---

# Common Beginner Mistakes

## Mistake 1

Using an empty `catch` block.

Incorrect

```javascript
catch (error) {

}
```

Errors should be handled or logged appropriately.

---

## Mistake 2

Wrapping an entire application in one large `try` block.

Smaller `try` blocks make it easier to identify where an error occurred.

---

## Mistake 3

Ignoring Promise rejections.

Every asynchronous operation may fail.

Always provide appropriate error handling.

---

# Section Summary

In this section, you learned how to use `try...catch` to handle errors in both synchronous and asynchronous JavaScript code. You explored the Error object, learned about the optional `finally` block, and discovered how the `throw` keyword allows you to create custom errors. Proper error handling is essential for building reliable applications that can recover gracefully when unexpected situations occur.

The next section introduces **the Fetch API**, where you'll learn how modern JavaScript applications retrieve data from web servers using Promises and `async`/`await`.

---

# CodeTales Insight

> **Professional developers don't write code that never fails—they write code that handles failure gracefully. Effective error handling transforms unexpected problems into manageable situations, making applications more reliable, easier to debug, and far more user-friendly.**

---

# 11.16 The Fetch API

In the previous section, you learned how to handle errors using `try...catch` in asynchronous JavaScript.

Now it is time to apply everything you've learned by working with one of the most important APIs in modern JavaScript—the **Fetch API**.

The Fetch API allows JavaScript applications to communicate with web servers by sending HTTP requests and receiving responses.

Whether you are building a weather application, an e-commerce website, a social media platform, or an online banking system, the Fetch API is one of the primary tools used to retrieve and send data.

---

# What Is the Fetch API?

The **Fetch API** is a modern JavaScript interface for making HTTP requests.

It is built into modern browsers and returns a **Promise**, making it ideal for use with `.then()` or `async` and `await`.

General syntax

```javascript
fetch(url);
```

Since `fetch()` returns a Promise, it does not immediately return the requested data.

Instead, it returns a Promise that resolves when the server responds.

---

## Figure 11.61

**Fetch Request Flow**

```text
JavaScript

↓

fetch()

↓

HTTP Request

↓

Web Server

↓

HTTP Response

↓

Promise
```

---

# Making Your First Request

```javascript
fetch("https://jsonplaceholder.typicode.com/users")

.then((response) => {

    return response.json();

})

.then((users) => {

    console.log(users);

});
```

The steps are:

1. Send an HTTP request.
2. Wait for the response.
3. Convert the response into JavaScript objects.
4. Use the data.

---

# Understanding `response.json()`

The server usually sends data as **JSON**.

To convert the JSON into JavaScript objects, use:

```javascript
response.json()
```

This method also returns a Promise.

That is why another `.then()` or another `await` is required.

---

## Figure 11.62

**Processing Server Data**

```text
Server Response

↓

JSON

↓

response.json()

↓

JavaScript Object
```

---

# Using `async` and `await`

Modern JavaScript typically uses `async` and `await` with the Fetch API.

Example

```javascript
async function getUsers() {

    const response = await fetch(
        "https://jsonplaceholder.typicode.com/users"
    );

    const users = await response.json();

    console.log(users);

}

getUsers();
```

This version is easier to read because it resembles synchronous code.

---

# Handling Errors

Network requests can fail.

Always use `try...catch`.

Example

```javascript
async function getUsers() {

    try {

        const response = await fetch(
            "https://jsonplaceholder.typicode.com/users"
        );

        const users = await response.json();

        console.log(users);

    } catch (error) {

        console.log("Unable to retrieve users.");

    }

}

getUsers();
```

---

# Checking the HTTP Status

A successful network request does **not** always mean the server returned the data you expected.

For example:

- 404 Not Found
- 500 Internal Server Error

The `Response` object includes an `ok` property.

```javascript
async function getUsers() {

    try {

        const response = await fetch(
            "https://jsonplaceholder.typicode.com/users"
        );

        if (!response.ok) {

            throw new Error("Request failed.");

        }

        const users = await response.json();

        console.log(users);

    } catch (error) {

        console.log(error.message);

    }

}

getUsers();
```

Checking `response.ok` is considered a best practice.

---

## Figure 11.63

**Fetch Success Flow**

```text
Send Request

↓

Receive Response

↓

response.ok?

↓

Yes

↓

Read JSON

↓

Use Data
```

---

# Sending Data

The Fetch API can also send data to a server.

Example

```javascript
fetch("https://jsonplaceholder.typicode.com/posts", {

    method: "POST",

    headers: {

        "Content-Type": "application/json"

    },

    body: JSON.stringify({

        title: "JavaScript",

        author: "CodeTales Africa"

    })

});
```

In this example:

- `method` specifies the HTTP method.
- `headers` describe the request.
- `body` contains the data being sent.

---

# Common HTTP Methods

| Method | Purpose |
|---------|---------|
| GET | Retrieve data |
| POST | Create new data |
| PUT | Replace existing data |
| PATCH | Update part of existing data |
| DELETE | Remove data |

These methods form the foundation of RESTful APIs.

---

## Figure 11.64

**HTTP Methods**

```text
GET

↓

Read
```

```text
POST

↓

Create
```

```text
PUT / PATCH

↓

Update
```

```text
DELETE

↓

Remove
```

---

# Real-World Example

Imagine an online shopping website.

The application uses Fetch to:

- Load products.
- Display product details.
- Add items to a shopping cart.
- Submit customer orders.
- Retrieve order history.

Almost every modern web application communicates with servers in this way.

---

# Best Practices

- Prefer `async` and `await` for readability.
- Always use `try...catch`.
- Check `response.ok` before processing data.
- Validate server responses.
- Handle network failures gracefully.
- Use descriptive error messages.

---

# Common Beginner Mistakes

## Mistake 1

Forgetting to use `await` with `response.json()`.

Incorrect

```javascript
const users = response.json();
```

Correct

```javascript
const users = await response.json();
```

---

## Mistake 2

Ignoring HTTP status codes.

Always check `response.ok`.

---

## Mistake 3

Assuming every Fetch request succeeds.

Network failures and server errors are common.

Always handle them properly.

---

# Section Summary

In this section, you learned how to use the Fetch API to communicate with web servers. You explored how `fetch()` returns a Promise, how to process JSON responses, how to use `async` and `await` for cleaner code, and how to handle network errors using `try...catch`. You also learned how to send data to a server using HTTP methods such as GET and POST, preparing you to build modern, data-driven web applications.

The next section explores **Working with JSON**, where you'll learn how JavaScript converts objects to JSON and parses JSON received from servers.

---

# CodeTales Insight

> **The Fetch API is the bridge between your JavaScript application and the outside world. Almost every modern web application—from banking systems to social media platforms—relies on it to exchange data with servers. Mastering the Fetch API equips you with one of the most valuable skills in professional web development.**

---

# 11.17 Working with JSON

In the previous section, you learned how to retrieve data from web servers using the Fetch API.

When data travels between a browser and a server, it is usually transmitted in a format called **JSON**.

Understanding JSON is essential because nearly every modern web application exchanges information using it.

Whether you're building a weather application, an online store, a banking system, or a social media platform, you'll encounter JSON constantly.

---

# What Is JSON?

**JSON** stands for **JavaScript Object Notation**.

It is a lightweight, text-based format for storing and exchanging data.

Although JSON originated from JavaScript object syntax, it is language-independent and supported by almost every programming language.

JSON is easy for humans to read and easy for computers to process.

---

## Figure 11.65

**Data Exchange Using JSON**

```text
Browser

↓

JSON

↓

Server
```

---

# Why JSON Is Important

JSON is commonly used to:

- Exchange data between clients and servers.
- Store application settings.
- Save configuration files.
- Send API responses.
- Transfer structured information across networks.

Without JSON, modern web applications would have difficulty communicating efficiently.

---

# JSON Syntax

JSON represents data using **key-value pairs**.

Example

```json
{
    "name": "Ada",
    "age": 25,
    "country": "Nigeria"
}
```

Notice that:

- Keys are enclosed in double quotes.
- Values may be strings, numbers, booleans, arrays, objects, or `null`.
- Properties are separated by commas.

---

## Figure 11.66

**JSON Structure**

```text
{

    "key": value,

    "key": value

}
```

---

# JSON vs JavaScript Objects

Although they look similar, JSON and JavaScript objects are not identical.

### JavaScript Object

```javascript
const user = {

    name: "Ada",

    age: 25

};
```

### JSON

```json
{

    "name": "Ada",

    "age": 25

}
```

Differences:

- JavaScript object keys do not require quotes.
- JSON keys must always use double quotes.
- JSON is text.
- JavaScript objects are actual language objects.

---

# Converting Objects to JSON

JavaScript provides:

```javascript
JSON.stringify()
```

This method converts a JavaScript object into a JSON string.

Example

```javascript
const user = {

    name: "Ada",

    age: 25

};

const json = JSON.stringify(user);

console.log(json);
```

Output

```text
{"name":"Ada","age":25}
```

---

## Figure 11.67

**Object to JSON**

```text
JavaScript Object

↓

JSON.stringify()

↓

JSON String
```

---

# Converting JSON to Objects

JavaScript also provides:

```javascript
JSON.parse()
```

This method converts JSON text into a JavaScript object.

Example

```javascript
const json = '{"name":"Ada","age":25}';

const user = JSON.parse(json);

console.log(user.name);
```

Output

```text
Ada
```

---

## Figure 11.68

**JSON to Object**

```text
JSON String

↓

JSON.parse()

↓

JavaScript Object
```

---

# JSON Data Types

JSON supports six data types.

| Type | Example |
|------|---------|
| String | `"JavaScript"` |
| Number | `100` |
| Boolean | `true` |
| Object | `{}` |
| Array | `[]` |
| Null | `null` |

Unlike JavaScript, JSON does **not** support:

- Functions
- `undefined`
- Symbols
- Comments

---

# JSON Arrays

JSON can also store arrays.

Example

```json
{

    "courses": [

        "HTML",

        "CSS",

        "JavaScript"

    ]

}
```

Accessing the data:

```javascript
const json = `{

    "courses": [

        "HTML",

        "CSS",

        "JavaScript"

    ]

}`;

const data = JSON.parse(json);

console.log(data.courses[1]);
```

Output

```text
CSS
```

---

# JSON Objects Inside Objects

JSON supports nested objects.

Example

```json
{

    "student": {

        "name": "Ada",

        "age": 25

    }

}
```

After parsing:

```javascript
console.log(data.student.name);
```

Output

```text
Ada
```

---

# JSON and the Fetch API

When using the Fetch API, JSON is everywhere.

Example

```javascript
async function getUsers() {

    const response = await fetch(

        "https://jsonplaceholder.typicode.com/users"

    );

    const users = await response.json();

    console.log(users);

}

getUsers();
```

Notice:

```javascript
await response.json();
```

This converts the server's JSON response into JavaScript objects.

---

## Figure 11.69

**Fetch and JSON**

```text
Server

↓

JSON

↓

response.json()

↓

JavaScript Objects
```

---

# Real-World Example

Imagine an online bookstore.

The server sends:

```json
{

    "title": "JavaScript Fundamentals",

    "price": 39.99,

    "author": "CodeTales Africa"

}
```

The browser parses the JSON and displays:

- Book title
- Price
- Author

to the customer.

---

# Best Practices

- Always validate JSON received from external sources.
- Use `JSON.stringify()` before sending JavaScript objects to a server.
- Use `JSON.parse()` only with valid JSON strings.
- Remember that JSON keys require double quotes.
- Keep JSON data well-structured and easy to understand.

---

# Common Beginner Mistakes

## Mistake 1

Confusing JavaScript objects with JSON.

Objects and JSON look similar but are different.

---

## Mistake 2

Using single quotes around JSON keys.

Incorrect

```json
{

    'name': 'Ada'

}
```

Correct

```json
{

    "name": "Ada"

}
```

---

## Mistake 3

Trying to store functions in JSON.

JSON cannot represent functions.

---

# Section Summary

In this section, you learned that JSON (JavaScript Object Notation) is the standard format for exchanging data between web applications and servers. You explored JSON syntax, compared JSON with JavaScript objects, converted objects using `JSON.stringify()`, parsed JSON using `JSON.parse()`, and learned how the Fetch API automatically converts JSON responses into usable JavaScript objects.

The next section explores **Promise Utility Methods**, where you'll learn how to execute multiple asynchronous operations efficiently using methods such as `Promise.all()`, `Promise.allSettled()`, `Promise.race()`, and `Promise.any()`.

---

# CodeTales Insight

> **JSON is the universal language of modern web applications. While JavaScript gives your application intelligence, JSON gives it the ability to communicate. Mastering JSON enables your applications to exchange information with servers, APIs, databases, and countless other systems across the web.**

---

# 11.18 Promise Utility Methods

In the previous section, you learned how JSON allows JavaScript applications to exchange data with web servers.

In real-world applications, however, developers often need to work with **multiple Promises at the same time**.

For example, an application might need to:

- Load user information.
- Retrieve recent orders.
- Fetch notifications.
- Download profile pictures.

Instead of waiting for each operation individually, JavaScript provides several utility methods that help manage multiple Promises efficiently.

The four most commonly used utility methods are:

- `Promise.all()`
- `Promise.allSettled()`
- `Promise.race()`
- `Promise.any()`

Each method is designed for a different scenario.

---

# `Promise.all()`

`Promise.all()` waits for **all Promises** to complete successfully.

If every Promise is fulfilled, it returns an array containing their results.

However, if **any Promise rejects**, the entire operation rejects immediately.

General syntax

```javascript
Promise.all([

    promise1,

    promise2,

    promise3

]);
```

---

## Example

```javascript
const promise1 = Promise.resolve("HTML");

const promise2 = Promise.resolve("CSS");

const promise3 = Promise.resolve("JavaScript");

Promise.all([

    promise1,

    promise2,

    promise3

])

.then((results) => {

    console.log(results);

});
```

Output

```text
["HTML", "CSS", "JavaScript"]
```

---

## Figure 11.70

**`Promise.all()`**

```text
Promise 1 ✔

Promise 2 ✔

Promise 3 ✔

↓

Return All Results
```

---

# When One Promise Fails

```javascript
const promise1 = Promise.resolve("Success");

const promise2 = Promise.reject("Failure");

const promise3 = Promise.resolve("Success");

Promise.all([

    promise1,

    promise2,

    promise3

])

.catch((error) => {

    console.log(error);

});
```

Output

```text
Failure
```

The remaining fulfilled Promises are ignored because one Promise failed.

---

# When to Use `Promise.all()`

Use `Promise.all()` when:

- Every task is required.
- One failure should stop the entire process.
- Multiple independent requests can execute simultaneously.

Examples include:

- Loading multiple API resources.
- Downloading several files.
- Retrieving dashboard data.

---

# `Promise.allSettled()`

Sometimes you want to know the outcome of **every Promise**, even if some fail.

`Promise.allSettled()` waits until every Promise has either fulfilled or rejected.

Example

```javascript
const promise1 = Promise.resolve("HTML");

const promise2 = Promise.reject("Network Error");

const promise3 = Promise.resolve("JavaScript");

Promise.allSettled([

    promise1,

    promise2,

    promise3

])

.then((results) => {

    console.log(results);

});
```

Output

```text
[
  { status: "fulfilled", value: "HTML" },
  { status: "rejected", reason: "Network Error" },
  { status: "fulfilled", value: "JavaScript" }
]
```

---

## Figure 11.71

**`Promise.allSettled()`**

```text
Promise 1 ✔

Promise 2 ✘

Promise 3 ✔

↓

Return Every Result
```

---

# When to Use `Promise.allSettled()`

This method is useful when every result matters.

Examples:

- Uploading multiple images.
- Sending multiple emails.
- Running independent background tasks.

---

# `Promise.race()`

`Promise.race()` returns the result of **the first Promise that settles**, whether it fulfills or rejects.

Example

```javascript
const slow = new Promise((resolve) => {

    setTimeout(() => {

        resolve("Slow");

    }, 3000);

});

const fast = new Promise((resolve) => {

    setTimeout(() => {

        resolve("Fast");

    }, 1000);

});

Promise.race([

    slow,

    fast

])

.then((result) => {

    console.log(result);

});
```

Output

```text
Fast
```

---

## Figure 11.72

**`Promise.race()`**

```text
Promise A

Promise B

Promise C

↓

First Finished Wins
```

---

# When to Use `Promise.race()`

Examples include:

- Network request timeouts.
- Choosing the fastest available server.
- Competing asynchronous operations.

---

# `Promise.any()`

`Promise.any()` returns the **first fulfilled Promise**.

Rejected Promises are ignored unless **every Promise rejects**.

Example

```javascript
const promise1 = Promise.reject("Server A");

const promise2 = Promise.resolve("Server B");

const promise3 = Promise.resolve("Server C");

Promise.any([

    promise1,

    promise2,

    promise3

])

.then((result) => {

    console.log(result);

});
```

Output

```text
Server B
```

---

## Figure 11.73

**`Promise.any()`**

```text
Promise A ✘

Promise B ✔

Promise C ✔

↓

First Success Wins
```

---

# Comparing the Utility Methods

| Method | Waits For | Rejects When |
|---------|-----------|--------------|
| `Promise.all()` | All Promises | Any Promise rejects |
| `Promise.allSettled()` | All Promises | Never rejects because of an individual Promise |
| `Promise.race()` | First settled Promise | First settled Promise rejects |
| `Promise.any()` | First fulfilled Promise | All Promises reject |

Choosing the correct method depends on the problem you are solving.

---

# Real-World Example

Imagine an online travel application.

It requests flight prices from three different airlines.

- `Promise.race()` returns the first response.
- `Promise.any()` returns the first successful response.
- `Promise.all()` waits for prices from every airline.
- `Promise.allSettled()` reports which airlines responded successfully and which failed.

Each method serves a different business need.

---

# Best Practices

- Use `Promise.all()` when every operation must succeed.
- Use `Promise.allSettled()` when you need every outcome.
- Use `Promise.race()` for timeout and competition scenarios.
- Use `Promise.any()` when only one successful result is required.
- Handle rejected Promises appropriately.

---

# Common Beginner Mistakes

## Mistake 1

Using `Promise.all()` when partial success is acceptable.

Consider using `Promise.allSettled()` instead.

---

## Mistake 2

Assuming `Promise.race()` always returns a fulfilled Promise.

It returns the first Promise that settles, whether fulfilled or rejected.

---

## Mistake 3

Confusing `Promise.any()` with `Promise.race()`.

- `Promise.race()` returns the first settled Promise.
- `Promise.any()` returns the first fulfilled Promise.

---

# Section Summary

In this section, you learned how JavaScript provides several utility methods for coordinating multiple asynchronous operations. You explored `Promise.all()`, `Promise.allSettled()`, `Promise.race()`, and `Promise.any()`, learned when each method should be used, and compared their behavior in different scenarios. These methods make it possible to build efficient, scalable, and reliable asynchronous applications.

The next section explores **The Microtask Queue**, where you'll discover how Promise callbacks are prioritized over other asynchronous callbacks and how this affects the JavaScript Event Loop.

---

# CodeTales Insight

> **Professional JavaScript developers rarely work with a single asynchronous task. Real applications coordinate many operations simultaneously, and choosing the correct Promise utility method can improve performance, simplify error handling, and make your applications more responsive. Mastering these methods is an important step toward writing production-quality asynchronous JavaScript.**

---

# 11.19 The Microtask Queue

In the previous section, you learned how Promise utility methods help coordinate multiple asynchronous operations.

However, one important question remains.

Consider the following code:

```javascript
console.log("Start");

setTimeout(() => {

    console.log("Timer");

}, 0);

Promise.resolve()

.then(() => {

    console.log("Promise");

});

console.log("End");
```

What is the output?

Many beginners expect:

```text
Start

End

Timer

Promise
```

The actual output is:

```text
Start

End

Promise

Timer
```

Why does the Promise callback execute before the timer callback, even though the timer delay is zero?

The answer lies in the **Microtask Queue**.

---

# What Is the Microtask Queue?

The **Microtask Queue** is a special queue used by JavaScript to store high-priority asynchronous tasks.

Unlike the Callback Queue (also called the Task Queue or Macrotask Queue), the Microtask Queue is always processed **before** the Callback Queue whenever the Call Stack becomes empty.

---

## Figure 11.74

**JavaScript Queues**

```text
Call Stack

↓

Microtask Queue

↓

Callback Queue
```

JavaScript always gives priority to the Microtask Queue.

---

# What Goes Into the Microtask Queue?

The Microtask Queue contains callbacks from operations such as:

- Promise `.then()`
- Promise `.catch()`
- Promise `.finally()`
- `queueMicrotask()`
- `MutationObserver` (Browser API)

These callbacks are considered more urgent than timer callbacks.

---

# What Goes Into the Callback Queue?

The Callback Queue contains tasks such as:

- `setTimeout()`
- `setInterval()`
- DOM events (click, keypress, etc.)
- Other browser task callbacks

These tasks are executed **after** the Microtask Queue becomes empty.

---

## Figure 11.75

**Queue Priority**

```text
Highest Priority

↓

Microtask Queue

↓

Callback Queue

↓

Lowest Priority
```

---

# Example

```javascript
console.log("One");

Promise.resolve()

.then(() => {

    console.log("Two");

});

setTimeout(() => {

    console.log("Three");

}, 0);

console.log("Four");
```

Output

```text
One

Four

Two

Three
```

---

# Step-by-Step Execution

### Step 1

```javascript
console.log("One");
```

Output

```text
One
```

---

### Step 2

The Promise callback is placed inside the **Microtask Queue**.

---

### Step 3

The timer callback is placed inside the **Callback Queue**.

---

### Step 4

```javascript
console.log("Four");
```

Output

```text
Four
```

---

### Step 5

The Call Stack becomes empty.

JavaScript first checks the **Microtask Queue**.

Output

```text
Two
```

---

### Step 6

Only after the Microtask Queue becomes empty does JavaScript process the Callback Queue.

Output

```text
Three
```

Final output

```text
One

Four

Two

Three
```

---

## Figure 11.76

**Execution Order**

```text
Call Stack Empty

↓

Microtask Queue

↓

Callback Queue
```

---

# Another Example

```javascript
console.log("Start");

Promise.resolve()

.then(() => {

    console.log("Promise 1");

})

.then(() => {

    console.log("Promise 2");

});

setTimeout(() => {

    console.log("Timer");

}, 0);

console.log("End");
```

Output

```text
Start

End

Promise 1

Promise 2

Timer
```

Notice that JavaScript completely empties the Microtask Queue before processing the timer.

---

# Why Does JavaScript Prioritize Microtasks?

Microtasks are usually small operations that continue the execution of existing asynchronous workflows.

Examples include:

- Continuing Promise chains
- Completing `async`/`await` operations
- Finalizing asynchronous computations

Prioritizing microtasks helps keep Promise-based code predictable and consistent.

---

# Real-World Analogy

Imagine a hospital.

There are two waiting lines.

- Emergency patients
- Regular appointments

Whenever a doctor becomes available:

- Emergency patients are treated first.
- Regular appointments are handled afterward.

The Microtask Queue is like the emergency line.

The Callback Queue is like the regular appointment line.

---

## Figure 11.77

**Hospital Priority**

```text
Doctor Available

↓

Emergency Queue

↓

Regular Queue
```

---

# Why This Matters

Understanding the Microtask Queue helps explain:

- Why Promise callbacks execute before timers.
- How `async` and `await` work internally.
- The execution order of asynchronous JavaScript.
- Why some outputs appear different from what beginners expect.

This knowledge is especially valuable when debugging complex asynchronous applications.

---

# Best Practices

- Remember that Promise callbacks have higher priority than timer callbacks.
- Avoid relying on execution order without understanding the Event Loop.
- Keep microtasks short and efficient.
- Use Promises for asynchronous workflows instead of timers when appropriate.

---

# Common Beginner Mistakes

## Mistake 1

Assuming `setTimeout(..., 0)` executes immediately.

Even with a delay of zero milliseconds, timer callbacks wait until the Microtask Queue has been emptied.

---

## Mistake 2

Thinking all asynchronous callbacks have the same priority.

They do not.

Promise callbacks are processed before timer callbacks.

---

## Mistake 3

Ignoring the Microtask Queue when debugging asynchronous code.

Many seemingly "unexpected" execution orders are explained by the Microtask Queue.

---

# Section Summary

In this section, you learned that JavaScript uses two primary queues for asynchronous operations: the Microtask Queue and the Callback Queue. You discovered that Promise callbacks are placed in the Microtask Queue, which always has higher priority than the Callback Queue. This explains why Promise callbacks execute before timer callbacks, even when the timer delay is zero. Understanding the Microtask Queue completes your knowledge of the JavaScript execution model and prepares you to confidently reason about complex asynchronous behavior.

The next section concludes this chapter with a comprehensive review of the key concepts you've learned before moving on to the practice exercises and hands-on project.

---

# CodeTales Insight

> **The Microtask Queue is one of JavaScript's most misunderstood features. Once you understand that JavaScript always empties the Microtask Queue before processing the Callback Queue, many "mysterious" execution orders suddenly make perfect sense. This insight separates intermediate JavaScript developers from professionals who can confidently debug asynchronous applications.**

---

# 11.20 Chapter Summary

In this chapter, you explored one of the most important aspects of modern JavaScript development—**asynchronous programming**.

Unlike synchronous programming, where tasks execute one after another, asynchronous programming allows JavaScript to perform long-running operations without blocking the rest of the application. This capability enables web applications to remain fast, responsive, and interactive while waiting for operations such as network requests, file downloads, timers, or database queries to complete.

You began by understanding the difference between **synchronous** and **asynchronous** execution and learned why JavaScript, despite being single-threaded, can efficiently handle asynchronous operations through the cooperation of the browser, the Event Loop, and internal task queues.

Next, you examined the **JavaScript execution model**, including the **Call Stack**, **Web APIs**, the **Event Loop**, the **Callback Queue**, and later the **Microtask Queue**. These components work together to determine when and how asynchronous callbacks are executed.

You then learned about **callback functions**, one of JavaScript's earliest mechanisms for handling asynchronous operations. While callbacks provide flexibility, you also discovered how deeply nested callbacks can lead to **Callback Hell**, making applications difficult to read and maintain.

To overcome these challenges, you explored **Promises**, which represent the eventual completion or failure of asynchronous operations. You learned about the three Promise states—**Pending**, **Fulfilled**, and **Rejected**—and discovered how Promises simplify asynchronous programming through `.then()`, `.catch()`, `.finally()`, and Promise chaining.

Building upon Promises, you studied **`async`** and **`await`**, the modern syntax for writing asynchronous JavaScript. These keywords allow asynchronous code to resemble synchronous code while still leveraging Promises internally. You also learned how to combine `async`/`await` with **`try...catch`** to handle errors gracefully.

The chapter then introduced the **Fetch API**, demonstrating how JavaScript applications communicate with web servers. You learned how to retrieve data, send requests, process server responses, and work with **JSON**, the standard format for exchanging structured data across the web.

Finally, you explored advanced asynchronous concepts, including **Promise utility methods** such as `Promise.all()`, `Promise.allSettled()`, `Promise.race()`, and `Promise.any()`, as well as the **Microtask Queue**, which explains why Promise callbacks execute before timer callbacks.

Together, these concepts form the foundation of professional asynchronous programming in JavaScript.

---

# Key Takeaways

After completing this chapter, you should be able to:

- Explain the difference between synchronous and asynchronous programming.
- Describe how JavaScript uses the Call Stack, Web APIs, Event Loop, Callback Queue, and Microtask Queue.
- Write and use callback functions effectively.
- Recognize and avoid Callback Hell.
- Create and consume Promises.
- Understand Promise states and lifecycle.
- Chain Promises to perform sequential asynchronous operations.
- Use `async` and `await` to simplify asynchronous code.
- Handle errors using `try...catch`.
- Retrieve and send data using the Fetch API.
- Convert data between JavaScript objects and JSON.
- Choose the appropriate Promise utility method for different scenarios.
- Predict the execution order of asynchronous operations involving Promises and timers.

---

# Looking Ahead

Asynchronous programming is one of the most valuable skills in modern JavaScript development.

The concepts introduced in this chapter are used extensively in:

- Front-end web applications
- Node.js applications
- RESTful APIs
- Cloud computing
- Mobile applications
- Real-time communication
- Artificial intelligence services
- Database programming

In the next chapter, you will build upon these skills by exploring more advanced JavaScript concepts that are essential for creating scalable, maintainable, and professional applications.

---

# CodeTales Insight

> **Asynchronous programming changes the way you think about software development. Instead of waiting for one task to finish before starting another, JavaScript teaches you how to coordinate many operations efficiently without sacrificing responsiveness. By mastering callbacks, Promises, `async`/`await`, the Fetch API, and the Event Loop, you've taken a significant step toward becoming a professional JavaScript developer capable of building modern, high-performance web applications.**

---

# 11.21 Key Terms

The following terms were introduced in this chapter. Review them carefully to strengthen your understanding of asynchronous programming in JavaScript.

| Term | Definition |
|------|------------|
| **Asynchronous Programming** | A programming approach that allows JavaScript to perform long-running tasks without blocking the execution of other code. |
| **Synchronous Programming** | A programming model in which statements execute one after another, with each task waiting for the previous one to finish. |
| **Call Stack** | A data structure that keeps track of function calls during program execution. |
| **Execution Context** | The environment in which JavaScript code is evaluated and executed. |
| **Web APIs** | Browser-provided features such as timers, DOM events, and Fetch that perform tasks outside the JavaScript engine. |
| **Event Loop** | The mechanism that continuously checks whether the Call Stack is empty and moves pending callbacks into it. |
| **Callback Function** | A function passed as an argument to another function to be executed later. |
| **Callback Queue (Task Queue)** | A queue that stores callback functions waiting for the Call Stack to become available. |
| **Microtask Queue** | A high-priority queue that stores Promise callbacks and other microtasks, processed before the Callback Queue. |
| **Callback Hell** | A situation where deeply nested callbacks make code difficult to read, maintain, and debug. |
| **Promise** | An object representing the eventual completion or failure of an asynchronous operation. |
| **Pending** | The initial state of a Promise while an asynchronous operation is still in progress. |
| **Fulfilled** | The state of a Promise after it has completed successfully. |
| **Rejected** | The state of a Promise after an error or failure occurs. |
| **resolve()** | A function used to fulfill a Promise with a successful result. |
| **reject()** | A function used to reject a Promise with an error or failure. |
| **`.then()`** | A Promise method used to handle fulfilled Promises. |
| **`.catch()`** | A Promise method used to handle rejected Promises. |
| **`.finally()`** | A Promise method that executes after a Promise settles, regardless of success or failure. |
| **Promise Chaining** | Connecting multiple Promise operations together using successive `.then()` methods. |
| **`async` Function** | A function declared with the `async` keyword that automatically returns a Promise. |
| **`await`** | A keyword that pauses execution inside an `async` function until a Promise settles. |
| **`try...catch`** | A JavaScript statement used to handle exceptions and Promise rejections in `async` functions. |
| **Error Object** | An object containing information about an error, including its name, message, and stack trace. |
| **Fetch API** | A modern browser API for making HTTP requests to web servers. |
| **HTTP Request** | A message sent from a client to a server requesting data or performing an action. |
| **HTTP Response** | The message returned by a server after processing an HTTP request. |
| **JSON (JavaScript Object Notation)** | A lightweight text format used for storing and exchanging structured data. |
| **`JSON.stringify()`** | A method that converts a JavaScript object into a JSON string. |
| **`JSON.parse()`** | A method that converts a JSON string into a JavaScript object. |
| **HTTP GET** | An HTTP method used to retrieve data from a server. |
| **HTTP POST** | An HTTP method used to send new data to a server. |
| **HTTP PUT** | An HTTP method used to replace existing data on a server. |
| **HTTP PATCH** | An HTTP method used to partially update existing data on a server. |
| **HTTP DELETE** | An HTTP method used to remove data from a server. |
| **`Promise.all()`** | A utility method that waits for all Promises to fulfill or rejects immediately if one fails. |
| **`Promise.allSettled()`** | A utility method that waits for every Promise to settle, regardless of success or failure. |
| **`Promise.race()`** | A utility method that settles as soon as the first Promise settles. |
| **`Promise.any()`** | A utility method that fulfills as soon as the first Promise fulfills, ignoring rejected Promises unless all reject. |
| **REST API** | An application programming interface that follows the principles of Representational State Transfer (REST) for client-server communication. |
| **HTTP Status Code** | A numeric code returned by a server indicating the result of an HTTP request (for example, 200, 404, or 500). |

---

# CodeTales Insight

> **Learning JavaScript isn't just about memorizing syntax—it's about understanding the vocabulary of the language. These key terms represent the core concepts of asynchronous programming and modern web communication. Becoming comfortable with this terminology will make it easier to read documentation, collaborate with other developers, and solve real-world programming challenges.**

---

# 11.22 Chapter Review Questions

Test your understanding of the concepts covered in this chapter by answering the following questions. Try to answer each question without referring to the chapter notes. If necessary, revisit the relevant section before continuing.

---

# Part A — Multiple Choice Questions

Choose the correct answer.

### 1.

Which type of programming allows JavaScript to perform long-running operations without blocking other code?

A. Sequential Programming

B. Synchronous Programming

C. Asynchronous Programming

D. Procedural Programming

---

### 2.

Which data structure keeps track of currently executing functions?

A. Callback Queue

B. Event Loop

C. Call Stack

D. Promise Queue

---

### 3.

Which browser component monitors the Call Stack and moves callbacks into it when it becomes empty?

A. Web API

B. Promise

C. Event Loop

D. JSON Parser

---

### 4.

Which Promise state represents an operation that is still running?

A. Fulfilled

B. Pending

C. Rejected

D. Completed

---

### 5.

Which method is used to process a fulfilled Promise?

A. `.catch()`

B. `.finally()`

C. `.then()`

D. `.await()`

---

### 6.

Which keyword pauses an async function until a Promise settles?

A. async

B. defer

C. await

D. pause

---

### 7.

Which keyword declares an asynchronous function?

A. promise

B. async

C. await

D. defer

---

### 8.

Which Promise method always executes regardless of success or failure?

A. `.then()`

B. `.catch()`

C. `.finally()`

D. `.resolve()`

---

### 9.

Which JavaScript method converts an object into a JSON string?

A. `JSON.parse()`

B. `JSON.stringify()`

C. `JSON.object()`

D. `JSON.convert()`

---

### 10.

Which method converts JSON into a JavaScript object?

A. `JSON.stringify()`

B. `JSON.parse()`

C. `JSON.decode()`

D. `JSON.read()`

---

# Part B — True or False

Write **True** or **False**.

### 11.

JavaScript executes Promise callbacks before timer callbacks.

---

### 12.

A Promise can change from Fulfilled to Rejected.

---

### 13.

The Fetch API returns a Promise.

---

### 14.

JSON keys should always use double quotation marks.

---

### 15.

`await` can be used inside any JavaScript function.

---

### 16.

`Promise.all()` succeeds even when one Promise rejects.

---

### 17.

The Callback Queue has higher priority than the Microtask Queue.

---

### 18.

The `finally` block executes whether an error occurs or not.

---

### 19.

Callback Hell makes asynchronous code easier to maintain.

---

### 20.

`Promise.any()` returns the first fulfilled Promise.

---

# Part C — Short Answer Questions

Answer the following questions in your own words.

### 21.

What is asynchronous programming?

---

### 22.

Explain the role of the Event Loop.

---

### 23.

What is Callback Hell?

---

### 24.

List the three states of a Promise.

---

### 25.

What is the purpose of `resolve()`?

---

### 26.

What is the purpose of `reject()`?

---

### 27.

Why are Promises preferred over nested callbacks?

---

### 28.

What is the difference between `.then()` and `.catch()`?

---

### 29.

Explain the purpose of the `await` keyword.

---

### 30.

Why is JSON important in web development?

---

### 31.

Name four common HTTP methods.

---

### 32.

What is the difference between `JSON.stringify()` and `JSON.parse()`?

---

### 33.

Why should `response.ok` be checked when using the Fetch API?

---

### 34.

Explain the purpose of `Promise.allSettled()`.

---

### 35.

Why does the Microtask Queue have higher priority than the Callback Queue?

---

# Part D — Code Analysis

Study each code example and answer the question.

### 36.

```javascript
console.log("Start");

setTimeout(() => {

    console.log("Timer");

}, 0);

console.log("End");
```

**Question:**

What is the output?

---

### 37.

```javascript
Promise.resolve("JavaScript")

.then((message) => {

    console.log(message);

});
```

**Question:**

What is printed?

---

### 38.

```javascript
async function greet() {

    return "Hello";

}

greet().then(console.log);
```

**Question:**

What is the output?

---

### 39.

```javascript
console.log("One");

Promise.resolve()

.then(() => {

    console.log("Two");

});

console.log("Three");
```

**Question:**

Arrange the output in the correct order.

---

### 40.

```javascript
try {

    throw new Error("Oops!");

} catch (error) {

    console.log(error.message);

}
```

**Question:**

What is printed?

---

# Self-Assessment Checklist

Before proceeding to the practice exercises, confirm that you can confidently:

- Explain synchronous and asynchronous programming.
- Describe the JavaScript execution model.
- Use callback functions correctly.
- Explain Callback Hell.
- Create and consume Promises.
- Use `.then()`, `.catch()`, and `.finally()`.
- Write Promise chains.
- Use `async` and `await`.
- Handle errors with `try...catch`.
- Retrieve data using the Fetch API.
- Convert data using JSON.
- Use Promise utility methods.
- Explain the Microtask Queue and Event Loop.

If you answered **"No"** to any of these items, review the corresponding section before moving on to the practice exercises.

---

# CodeTales Insight

> **Knowledge becomes skill only through practice. These review questions are designed to help you identify areas of strength and topics that need further attention. Take your time, reason through each answer, and use any mistakes as opportunities to deepen your understanding before tackling the hands-on exercises.**


---

# 11.23 Practice Exercises

The following exercises are designed to strengthen your understanding of asynchronous JavaScript. Complete them in order without looking at the solutions. The exercises begin with basic concepts and gradually increase in difficulty.

---

# Level 1 — Fundamentals

### Exercise 1

Write a program that prints:

```text
JavaScript is awesome!
```

using `setTimeout()` with a delay of **2 seconds**.

---

### Exercise 2

Create a callback function that prints:

```text
Welcome to asynchronous programming.
```

Call the callback from another function.

---

### Exercise 3

Write a function named `greet()` that accepts a callback function and executes it.

---

### Exercise 4

Create two callback functions:

- `success()`
- `failure()`

Write another function that calls one of them.

---

### Exercise 5

Use nested callbacks to display:

```text
Step 1

Step 2

Step 3
```

Then identify why the code demonstrates Callback Hell.

---

# Level 2 — Promises

### Exercise 6

Create a Promise that resolves with:

```text
Learning Promises
```

Display the result using `.then()`.

---

### Exercise 7

Create a Promise that rejects with:

```text
Connection failed.
```

Handle the error using `.catch()`.

---

### Exercise 8

Create a Promise that resolves after **3 seconds** using `setTimeout()`.

---

### Exercise 9

Write a Promise that randomly succeeds or fails.

Display the result appropriately.

---

### Exercise 10

Use `.finally()` to print:

```text
Process Complete
```

whether the Promise succeeds or fails.

---

# Level 3 — Promise Chaining

### Exercise 11

Create a Promise chain that:

- starts with `10`
- multiplies it by `2`
- adds `5`
- prints the final result.

---

### Exercise 12

Create three `.then()` methods that transform a string step by step.

---

### Exercise 13

Return another Promise inside a `.then()` method.

---

### Exercise 14

Create a Promise chain that ends with `.catch()`.

Force an error to test it.

---

### Exercise 15

Add `.finally()` to Exercise 14.

---

# Level 4 — Async and Await

### Exercise 16

Create an `async` function that returns:

```text
Hello Async
```

---

### Exercise 17

Use `await` with `Promise.resolve()`.

---

### Exercise 18

Create an asynchronous function that waits **2 seconds** before printing:

```text
Finished
```

---

### Exercise 19

Convert the following Promise chain into `async`/`await`.

```javascript
Promise.resolve(5)

.then((number) => {

    return number * 2;

})

.then(console.log);
```

---

### Exercise 20

Write an `async` function that returns the square of a number.

---

# Level 5 — Error Handling

### Exercise 21

Use `try...catch` to handle a rejected Promise.

---

### Exercise 22

Throw a custom error when a number is negative.

---

### Exercise 23

Write a function that divides two numbers.

Throw an error if the denominator is zero.

---

### Exercise 24

Display only the error message using:

```javascript
error.message
```

---

### Exercise 25

Use `finally` to display:

```text
Cleaning up...
```

---

# Level 6 — Fetch API and JSON

### Exercise 26

Use the Fetch API to retrieve data from:

```text
https://jsonplaceholder.typicode.com/posts
```

Print the response.

---

### Exercise 27

Retrieve users from:

```text
https://jsonplaceholder.typicode.com/users
```

Display the name of the first user.

---

### Exercise 28

Convert this object into JSON.

```javascript
const student = {

    name: "Ada",

    age: 20

};
```

---

### Exercise 29

Convert the following JSON into a JavaScript object.

```json
{

    "language": "JavaScript",

    "version": "ES2025"

}
```

Display the language.

---

### Exercise 30

Use `Promise.all()` to wait for three resolved Promises.

Print the returned array.

---

# Challenge Exercises

The following exercises require combining multiple concepts.

---

### Challenge 1

Create a Promise that simulates downloading a file.

After **3 seconds**, display:

```text
Download Complete
```

---

### Challenge 2

Use `async` and `await` to retrieve data from the JSONPlaceholder API.

Display only the first five post titles.

---

### Challenge 3

Create three Promises that complete after different delays.

Use:

- `Promise.all()`
- `Promise.race()`
- `Promise.any()`

Observe the differences.

---

### Challenge 4

Create a function that fetches user data.

Handle every possible error using `try...catch`.

---

### Challenge 5

Write a small application that:

1. Fetches users.
2. Converts the response to JSON.
3. Displays every user's name.
4. Displays an error message if the request fails.
5. Prints:

```text
Finished loading users.
```

inside a `finally` block.

---

# Mini Debugging Challenges

Find and fix the errors.

### Debug Challenge 1

```javascript
await fetch(url);
```

---

### Debug Challenge 2

```javascript
Promise.resolve(5)

.then((number) => {

    number * 2;

})

.then(console.log);
```

---

### Debug Challenge 3

```javascript
const user = JSON.parse({

    name: "Ada"

});
```

---

### Debug Challenge 4

```javascript
Promise.all(

    promise1,

    promise2

);
```

---

### Debug Challenge 5

```javascript
async function loadData() {

    const response = fetch(url);

    const data = response.json();

}
```

---

# Practice Checklist

Before moving to the chapter project, ensure you can confidently:

- Create callback functions.
- Use timers.
- Create Promises.
- Consume Promises.
- Chain Promises.
- Use `async` and `await`.
- Handle asynchronous errors.
- Retrieve data using Fetch.
- Parse JSON.
- Use Promise utility methods.
- Predict asynchronous execution order.

---

# CodeTales Insight

> **Reading about asynchronous programming builds understanding, but writing asynchronous code builds mastery. Complete every exercise without copying solutions. Each mistake you fix strengthens your intuition and prepares you for the real-world project that follows.**

---

# 11.24 Chapter Project — Build an Asynchronous User Dashboard

Congratulations!

You have reached the end of Chapter 11.

Now it is time to combine everything you've learned into a practical project.

In this project, you will build a **User Dashboard** that retrieves user information from a web server using the Fetch API and displays it dynamically on a web page.

This project simulates a common task in modern web development and demonstrates how asynchronous JavaScript is used in real applications.

---

# Project Objectives

By completing this project, you will learn how to:

- Retrieve data from an external API.
- Use the Fetch API.
- Work with Promises.
- Use `async` and `await`.
- Handle errors using `try...catch`.
- Parse JSON responses.
- Update the DOM dynamically.
- Display loading and error messages.

---

# Project Preview

The completed application should display a list of users similar to the following:

```text
====================================

      USER DASHBOARD

====================================

👤 Leanne Graham

📧 Sincere@april.biz

📞 1-770-736-8031

🌍 Romaguera-Crona

------------------------------------

👤 Ervin Howell

📧 Shanna@melissa.tv

📞 010-692-6593

🌍 Deckow-Crist

------------------------------------
```

---

# Project Folder Structure

```text
user-dashboard/

│

├── index.html

├── css/

│   └── style.css

│

├── js/

│   └── app.js

│

└── images/
```

---

# Step 1 — Create the HTML

Create an `index.html` file containing:

- A page title.
- A heading.
- A **Load Users** button.
- A loading message.
- An empty container for user cards.

Suggested structure:

```html
<h1>User Dashboard</h1>

<button id="loadUsers">
    Load Users
</button>

<p id="loading"></p>

<div id="users"></div>
```

---

# Step 2 — Style the Page

Create a clean layout using CSS.

Suggested features:

- Centered heading
- Rounded user cards
- Soft shadows
- Responsive layout
- Hover effects
- Modern fonts
- Comfortable spacing

Feel free to customize the appearance.

---

# Step 3 — Retrieve User Data

Use the following API:

```text
https://jsonplaceholder.typicode.com/users
```

Create an asynchronous function named:

```javascript
loadUsers()
```

Inside the function:

- Use `fetch()`
- Await the response
- Convert the JSON
- Return the users

---

# Step 4 — Handle Errors

Wrap the asynchronous code inside:

```javascript
try {

}
catch {

}
```

Display a friendly error message if the request fails.

Example:

```text
Unable to load users.

Please check your internet connection.
```

---

# Step 5 — Show a Loading Message

Before the request begins, display:

```text
Loading users...
```

After the request finishes:

- Remove the loading message.

This improves the user experience.

---

# Step 6 — Display User Cards

For each user, display:

- Name
- Email
- Phone number
- Company
- Website

Example:

```text
Name

Email

Phone

Company

Website
```

Each user should appear inside its own card.

---

# Step 7 — Connect the Button

When the user clicks:

```text
Load Users
```

the application should:

1. Display the loading message.
2. Retrieve user data.
3. Display all users.
4. Hide the loading message.

---

# Step 8 — Challenge Yourself

Extend the project by adding:

- User avatars
- Search box
- Dark mode
- Refresh button
- User counter
- Loading spinner
- Animation effects
- Sort users alphabetically

---

# Bonus Challenges

### Challenge 1

Display only users whose company name begins with:

```text
R
```

---

### Challenge 2

Display users in alphabetical order.

---

### Challenge 3

Allow users to search by name.

---

### Challenge 4

Display the total number of users.

---

### Challenge 5

Add a **Reload Users** button.

---

# Expected Learning Outcomes

After completing this project, you should be able to:

- Work comfortably with asynchronous JavaScript.
- Retrieve remote data.
- Parse JSON.
- Manipulate the DOM dynamically.
- Handle errors professionally.
- Build interactive web applications.

---

# Extension Ideas

Once you've completed the project, consider expanding it into a more advanced application by adding:

- Pagination
- User profile pages
- REST API integration for creating and updating users
- Local storage for caching data
- Responsive navigation
- Loading skeletons
- Toast notifications
- Unit tests

These enhancements reflect techniques commonly used in production web applications.

---

# Project Checklist

Before marking this project as complete, ensure that you can:

- Fetch data from an API.
- Use `async` and `await`.
- Handle errors with `try...catch`.
- Parse JSON responses.
- Display data dynamically in the DOM.
- Show loading indicators.
- Build reusable JavaScript functions.
- Organize HTML, CSS, and JavaScript into separate files.

---

# Chapter Completion

Congratulations!

You have successfully completed **Chapter 11 – Asynchronous JavaScript**.

In this chapter, you learned how JavaScript performs asynchronous operations using callbacks, Promises, `async`/`await`, the Fetch API, JSON, and the Event Loop. These concepts are fundamental to modern web development and are used in nearly every professional JavaScript application.

As you move on to the next chapter, continue practicing these techniques. The more asynchronous code you write, the more naturally you'll understand execution order, error handling, and efficient communication with web services.

---

# CodeTales Insight

> **Professional developers don't just write code that works—they build applications that remain responsive, recover gracefully from failures, and communicate effectively with external services. By completing this project, you've taken another significant step toward becoming a developer capable of creating modern, interactive, and production-ready JavaScript applications.**
