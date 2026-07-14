# Chapter 6: Loops and Iteration

## 6.1 Introduction to Loops and Iteration

Imagine you are asked to display the message **"Welcome to CodeTales Africa!"** one hundred times.

One approach would be to write:

```javascript
console.log("Welcome to CodeTales Africa!");
console.log("Welcome to CodeTales Africa!");
console.log("Welcome to CodeTales Africa!");
```

You could continue copying and pasting the same statement until it appears one hundred times.

Although this approach would produce the desired result, it would be extremely inefficient. The program would become unnecessarily long, difficult to maintain, and prone to errors. If you later decided to change the message, you would need to modify it in one hundred different places.

Programming offers a much better solution.

Instead of repeating the same code manually, JavaScript provides **loops**, which allow a block of code to execute repeatedly until a specified condition is no longer true.

Loops are one of the three fundamental control structures found in nearly every programming language:

- **Sequence** – Executing statements one after another.
- **Selection** – Making decisions using conditional statements such as `if` and `switch`.
- **Iteration** – Repeating a block of code using loops.

In the previous chapter, you learned how JavaScript makes decisions through conditional statements. In this chapter, you will learn how JavaScript performs repetitive tasks efficiently using iteration.

---

## What Is Iteration?

**Iteration** is the process of repeating a set of instructions multiple times.

Each repetition of a loop is called an **iteration**.

For example, suppose you want to display the numbers from **1 to 5**.

Without a loop, you might write:

```javascript
console.log(1);
console.log(2);
console.log(3);
console.log(4);
console.log(5);
```

Using a loop, the same task can be completed with much less code:

```javascript
for (let number = 1; number <= 5; number++) {
    console.log(number);
}
```

The loop automatically repeats the `console.log()` statement while updating the value of `number` during each iteration.

This approach is shorter, easier to read, and much easier to maintain.

---

## Why Loops Are Important

Loops help programmers:

- Eliminate repetitive code.
- Reduce programming errors.
- Improve readability.
- Process large amounts of data efficiently.
- Automate repetitive tasks.
- Simplify complex algorithms.

Imagine writing a program that displays one million numbers.

Without loops, this would be practically impossible.

With loops, JavaScript can perform the task in just a few lines of code.

---

## Everyday Examples of Iteration

Even outside programming, repetition is part of everyday life.

Examples include:

- Counting from 1 to 100.
- Taking attendance in a classroom.
- Checking every email in an inbox.
- Watering each plant in a garden.
- Printing hundreds of invoices.
- Processing customer orders.
- Scanning items at a supermarket.
- Counting votes during an election.

Each of these activities involves performing the same action repeatedly until all items have been processed.

Programming loops work in exactly the same way.

---

## A Simple Analogy

Imagine a teacher grading examination papers.

The teacher follows the same steps for every student:

1. Pick up a paper.
2. Mark the answers.
3. Record the score.
4. Move to the next paper.

These steps continue until there are no more papers left.

This repetitive process is similar to how a loop operates.

---

## Components of Every Loop

Although JavaScript provides several types of loops, every loop includes the same basic ideas:

- **Starting point** – Where the loop begins.
- **Condition** – Determines whether another iteration should occur.
- **Update** – Changes the loop variable after each iteration.
- **Loop body** – The statements that execute repeatedly.

For example:

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

In this example:

- `let i = 1` initializes the loop.
- `i <= 5` is the condition.
- `i++` updates the counter after each iteration.
- `console.log(i)` is the loop body.

You will examine each of these components in detail later in this chapter.

---

## Real-World Applications of Loops

Loops appear in almost every software application.

Examples include:

- Displaying products in an online store.
- Reading records from a database.
- Processing payroll information.
- Calculating examination results.
- Displaying social media posts.
- Sending notifications.
- Processing online orders.
- Reading files.
- Generating reports.
- Creating animations in games.

Without loops, many modern applications would be slow, repetitive to write, and difficult to maintain.

---

> **Figure 6.1**
>
> **Iteration in Everyday Life**
>
> *(Insert an illustration showing repetitive activities such as grading papers, scanning supermarket items, counting ballots, watering plants, and processing customer orders. Include arrows to emphasize repetition.)*

---

> **CodeTales Insight**
>
> One of the biggest differences between beginner and professional programmers is recognizing opportunities to automate repetitive work. Whenever you notice yourself writing nearly identical lines of code multiple times, pause and ask: *"Can a loop do this instead?"* Learning to think this way will make your programs shorter, cleaner, and far more efficient.

---

## Section Summary

In this section, you were introduced to the concept of **loops** and **iteration** in JavaScript. You learned that loops allow programs to execute a block of code repeatedly, eliminating unnecessary repetition and making programs more efficient. You also explored everyday examples of iteration, examined the common components shared by all loops, and discovered why iteration is one of the fundamental building blocks of modern software development.

In the next section, you will explore **why loops matter** and see how they help solve practical programming problems that would otherwise require large amounts of repetitive code.

## 6.2 Why Loops Matter

One of the defining characteristics of computers is their ability to perform repetitive tasks quickly and accurately. Unlike humans, computers do not become tired or lose concentration when repeating the same operation thousands—or even millions—of times.

As programmers, we often need to instruct a computer to perform the same action repeatedly. Writing the same statements over and over again would make programs unnecessarily long, difficult to maintain, and more likely to contain errors.

Loops solve this problem by allowing a block of code to execute repeatedly until a specified condition is no longer satisfied.

---

## The Problem Without Loops

Suppose you want to display the numbers from **1 to 10**.

Without using a loop, you might write:

```javascript
console.log(1);
console.log(2);
console.log(3);
console.log(4);
console.log(5);
console.log(6);
console.log(7);
console.log(8);
console.log(9);
console.log(10);
```

Although this program works, it is not an efficient solution.

Now imagine displaying the numbers from **1 to 10,000**.

Writing ten thousand `console.log()` statements would clearly be impractical.

---

## The Solution With Loops

A loop performs the same task using only a few lines of code:

```javascript
for (let number = 1; number <= 10; number++) {
    console.log(number);
}
```

This program is:

- Shorter
- Easier to read
- Easier to modify
- Easier to debug
- More efficient

Changing the range from 10 to 100 only requires updating a single value.

```javascript
for (let number = 1; number <= 100; number++) {
    console.log(number);
}
```

This demonstrates one of the greatest advantages of loops: **small changes can produce significantly different results without rewriting large sections of code.**

---

## Reducing Repetition

One of the fundamental principles of software development is to avoid unnecessary repetition.

Consider the following task:

Display the message:

```text
Learning JavaScript with CodeTales Africa
```

fifty times.

Without loops, you would need fifty separate `console.log()` statements.

With a loop:

```javascript
for (let count = 1; count <= 50; count++) {
    console.log("Learning JavaScript with CodeTales Africa");
}
```

The program becomes much cleaner and easier to understand.

---

## Easier Maintenance

Imagine that after writing your program, you decide to change the message to:

```text
Master JavaScript with CodeTales Africa
```

If you manually repeated the statement fifty times, you would need to edit fifty separate lines.

With a loop, you change only one line:

```javascript
console.log("Master JavaScript with CodeTales Africa");
```

This illustrates why loops improve maintainability.

Programs are easier to update when repetitive code is replaced with loops.

---

## Improved Accuracy

Humans naturally make mistakes when performing repetitive tasks.

Examples include:

- Skipping a number.
- Duplicating a statement.
- Forgetting to update one occurrence.
- Introducing inconsistent formatting.

Loops reduce these risks because the repeated instructions are written only once.

As long as the loop is correct, every iteration behaves consistently.

---

## Working with Large Amounts of Data

Modern applications often process enormous amounts of information.

Examples include:

- Thousands of customer records.
- Millions of social media posts.
- Product catalogs with tens of thousands of items.
- Banking transactions.
- Student examination results.
- Weather observations.
- Medical records.

Instead of processing each item manually, loops allow JavaScript to process collections of data automatically.

---

## Automation Through Iteration

Automation is one of the primary goals of programming.

Consider a payroll application.

Each employee must have:

- Salary calculated.
- Tax deducted.
- Pension deducted.
- Net salary displayed.

If a company has 2,000 employees, manually writing the same code for each employee would be impossible.

Instead, a loop performs the calculations repeatedly for every employee.

---

## Loops Improve Scalability

A well-written loop can often handle any amount of data.

Whether there are:

- 10 products,
- 100 products,
- 10,000 products, or
- 1,000,000 products,

the same loop can process them without changing the program's overall structure.

This ability to scale makes loops one of the most powerful tools in programming.

---

## Real-World Examples

Loops are used in countless software systems.

Examples include:

### Banking Systems

- Process daily transactions.
- Calculate account balances.
- Generate customer statements.

### E-Commerce Websites

- Display products.
- Calculate shopping cart totals.
- Process customer orders.

### Educational Systems

- Calculate grades.
- Generate report cards.
- Process examination results.

### Social Media Platforms

- Display posts.
- Load comments.
- Count likes and reactions.

### Healthcare Systems

- Process patient records.
- Schedule appointments.
- Generate prescriptions.

### Gaming

- Update player positions.
- Detect collisions.
- Animate game objects.

Almost every modern application relies on loops.

---

> **Figure 6.2**
>
> **How Loops Reduce Repetition**
>
> *(Insert a side-by-side illustration comparing repetitive manual code with a concise loop that produces the same output. Highlight the reduction in code length and improved maintainability.)*

---

> **CodeTales Insight**
>
> Professional developers rarely think of loops as a way to "repeat code." Instead, they think of loops as a way to **process data**. Whether it's users, products, files, messages, or database records, loops allow one set of instructions to operate on many items efficiently. Developing this mindset will help you write software that scales from a handful of records to millions.

---

## Section Summary

Loops are essential because they eliminate repetitive code, improve readability, simplify maintenance, reduce programming errors, and enable software to process large amounts of data efficiently. Rather than writing the same statements repeatedly, programmers write the logic once and allow the loop to execute it as many times as needed. This makes programs shorter, more flexible, and easier to maintain.

In the next section, you will examine the **anatomy of a loop** and learn about the four fundamental components that every JavaScript loop contains.

## 6.3 Anatomy of a Loop

Before learning the different types of loops available in JavaScript, it is important to understand the structure that all loops have in common.

Although the syntax of `for`, `while`, and `do...while` loops differs slightly, every loop is built around the same four fundamental components:

1. Initialization
2. Condition
3. Update
4. Loop Body

Understanding these components will help you read, write, and debug loops with confidence.

---

## The Four Components of Every Loop

Consider the following example:

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

At first glance, this may look like a single statement, but it actually contains four separate parts that work together.

---

## Component 1: Initialization

Initialization creates and assigns the starting value of the loop variable.

Example:

```javascript
let i = 1;
```

This statement tells JavaScript:

> "Begin counting from 1."

The initialization step executes **only once**, before the loop starts.

If the loop never executes, the initialization still occurs.

---

### Why Initialization Is Important

Without a starting value, JavaScript would not know where to begin.

For example:

```javascript
for (let i = 1; i <= 10; i++) {
    console.log(i);
}
```

The first value printed is:

```text
1
```

If you change the initialization:

```javascript
for (let i = 50; i <= 55; i++) {
    console.log(i);
}
```

The output becomes:

```text
50
51
52
53
54
55
```

The initialization determines the starting point of the iteration.

---

## Component 2: Condition

The condition determines whether another iteration should occur.

Example:

```javascript
i <= 5
```

JavaScript evaluates this condition before each iteration.

If it evaluates to:

- `true` → execute the loop body.
- `false` → terminate the loop.

This condition acts as the loop's stopping rule.

---

### Visualizing the Condition

Imagine a security guard checking whether visitors are allowed to enter a building.

Each visitor is asked:

> "Do you have authorization?"

If the answer is **Yes**, the visitor enters.

If the answer is **No**, entry stops.

A loop behaves in the same way.

Before every repetition, JavaScript asks:

> "Is the condition still true?"

If yes, execution continues.

Otherwise, the loop ends.

---

## Component 3: Update

The update changes the loop variable after each iteration.

Example:

```javascript
i++
```

This means:

```javascript
i = i + 1;
```

After each iteration, the value of `i` increases by one.

The update prevents the loop from repeating forever.

---

### Other Update Expressions

Increase by 2:

```javascript
i += 2;
```

Decrease by 1:

```javascript
i--;
```

Decrease by 5:

```javascript
i -= 5;
```

Multiply by 2:

```javascript
i *= 2;
```

Any valid expression that updates the loop variable may be used.

---

## Component 4: Loop Body

The loop body contains the statements that execute repeatedly.

Example:

```javascript
{
    console.log(i);
}
```

Everything inside the curly braces belongs to the loop body.

Each iteration executes every statement inside these braces.

Example:

```javascript
for (let i = 1; i <= 3; i++) {
    console.log("Iteration");
    console.log(i);
}
```

Output:

```text
Iteration
1
Iteration
2
Iteration
3
```

Every statement inside the loop body repeats.

---

## How the Components Work Together

Consider this loop again:

```javascript
for (let i = 1; i <= 3; i++) {
    console.log(i);
}
```

Execution proceeds as follows.

### Step 1

Initialization:

```javascript
i = 1
```

---

### Step 2

Condition:

```javascript
1 <= 3
```

Result:

```text
true
```

---

### Step 3

Execute loop body:

```text
1
```

---

### Step 4

Update:

```javascript
i++
```

Now:

```text
i = 2
```

---

### Step 5

Condition:

```javascript
2 <= 3
```

Result:

```text
true
```

Execute body.

Output:

```text
2
```

Update:

```javascript
i = 3
```

---

### Step 6

Condition:

```javascript
3 <= 3
```

Result:

```text
true
```

Output:

```text
3
```

Update:

```javascript
i = 4
```

---

### Step 7

Condition:

```javascript
4 <= 3
```

Result:

```text
false
```

The loop terminates.

---

## Execution Flow Diagram

The process can be summarized as:

```text
Initialization

↓

Condition

↓

True?

↓

Execute Loop Body

↓

Update

↓

Back to Condition

↓

False?

↓

Loop Ends
```

This sequence is common to every JavaScript loop.

---

## Common Beginner Misunderstanding

Many beginners think the update happens before the loop body.

It does **not**.

The correct order is:

1. Initialize
2. Check condition
3. Execute loop body
4. Update
5. Repeat

Remembering this sequence will help you debug loops more easily.

---

## Why Understanding Loop Anatomy Matters

Whether you are using:

- `for`
- `while`
- `do...while`

these same four concepts always apply.

Once you understand the anatomy of a loop, learning different loop types becomes much easier because only the syntax changes—the underlying logic remains the same.

---

> **Figure 6.3**
>
> **Anatomy of a JavaScript Loop**
>
> *(Insert a flowchart showing Initialization → Condition → Loop Body → Update → back to Condition, with the loop ending when the condition becomes false.)*

---

> **CodeTales Insight**
>
> Many loop-related bugs occur because one of the four components is missing or incorrect. For example, forgetting to update the loop variable can create an infinite loop, while using the wrong condition may cause the loop to stop too early or continue for too long. When debugging a loop, always inspect these four components first.

---

## Section Summary

Every JavaScript loop consists of four essential components: **initialization**, **condition**, **update**, and **loop body**. These components work together to control when a loop starts, how long it continues, what it does during each iteration, and when it stops. Although different loop types use different syntax, they all follow this same underlying execution process.

In the next section, you will learn the most commonly used loop in JavaScript—the **`for` loop**—and discover why it is often the best choice when the number of iterations is known in advance.

## 6.4 The `for` Loop

The **`for` loop** is one of the most commonly used looping structures in JavaScript. It is ideal when you know in advance how many times a block of code should execute.

Because the `for` loop places the initialization, condition, and update in one concise statement, it is easy to read and understand. For this reason, it is often the first loop beginners learn and one of the most frequently used loops in professional software development.

---

## Syntax of the `for` Loop

The general syntax of a `for` loop is:

```javascript
for (initialization; condition; update) {
    // code to repeat
}
```

Let's examine each part:

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

- **Initialization:** `let i = 1`
- **Condition:** `i <= 5`
- **Update:** `i++`
- **Loop Body:** `console.log(i)`

Each part has a specific responsibility, and together they control the execution of the loop.

---

## How a `for` Loop Executes

Consider the following program:

```javascript
for (let i = 1; i <= 3; i++) {
    console.log(i);
}
```

The execution proceeds as follows:

### First Iteration

Initialization:

```javascript
i = 1
```

Condition:

```javascript
1 <= 3
```

Result:

```text
true
```

Output:

```text
1
```

Update:

```javascript
i++
```

Now:

```text
i = 2
```

---

### Second Iteration

Condition:

```javascript
2 <= 3
```

Result:

```text
true
```

Output:

```text
2
```

Update:

```javascript
i = 3
```

---

### Third Iteration

Condition:

```javascript
3 <= 3
```

Result:

```text
true
```

Output:

```text
3
```

Update:

```javascript
i = 4
```

---

### Final Check

Condition:

```javascript
4 <= 3
```

Result:

```text
false
```

The loop terminates.

---

## Example 1: Display Numbers 1 to 10

```javascript
for (let number = 1; number <= 10; number++) {
    console.log(number);
}
```

Output:

```text
1
2
3
4
5
6
7
8
9
10
```

---

## Example 2: Count Backwards

Loops can also count downward.

```javascript
for (let number = 10; number >= 1; number--) {
    console.log(number);
}
```

Output:

```text
10
9
8
7
6
5
4
3
2
1
```

---

## Example 3: Counting by Twos

The update expression is not limited to increasing by one.

```javascript
for (let number = 2; number <= 20; number += 2) {
    console.log(number);
}
```

Output:

```text
2
4
6
8
10
12
14
16
18
20
```

---

## Example 4: Multiplication Table

```javascript
let multiplier = 5;

for (let i = 1; i <= 12; i++) {
    console.log(`${multiplier} × ${i} = ${multiplier * i}`);
}
```

Output (partial):

```text
5 × 1 = 5
5 × 2 = 10
5 × 3 = 15
...
5 × 12 = 60
```

This demonstrates how loops can automate repetitive calculations.

---

## Example 5: Display a Message Multiple Times

```javascript
for (let count = 1; count <= 5; count++) {
    console.log("Welcome to CodeTales Africa!");
}
```

Output:

```text
Welcome to CodeTales Africa!
Welcome to CodeTales Africa!
Welcome to CodeTales Africa!
Welcome to CodeTales Africa!
Welcome to CodeTales Africa!
```

---

## Choosing Meaningful Loop Variables

Although `i` is commonly used as a loop counter, descriptive names often improve readability.

Instead of:

```javascript
for (let i = 1; i <= 12; i++) {
    console.log(i);
}
```

You might write:

```javascript
for (let month = 1; month <= 12; month++) {
    console.log(month);
}
```

Or:

```javascript
for (let studentNumber = 1; studentNumber <= 30; studentNumber++) {
    console.log(studentNumber);
}
```

Meaningful variable names make code easier to understand, especially in larger programs.

---

## Common Uses of the `for` Loop

The `for` loop is commonly used to:

- Display numbered lists.
- Generate multiplication tables.
- Process arrays (covered in a later chapter).
- Repeat calculations.
- Validate repeated inputs.
- Create patterns.
- Iterate through collections of data.

Whenever the number of repetitions is known in advance, a `for` loop is often the best choice.

---

## Common Beginner Mistakes

### Mistake 1: Forgetting the Update

```javascript
for (let i = 1; i <= 5;) {
    console.log(i);
}
```

Because `i` never changes, the condition remains true, creating an **infinite loop**.

---

### Mistake 2: Incorrect Condition

```javascript
for (let i = 1; i < 5; i++) {
    console.log(i);
}
```

Output:

```text
1
2
3
4
```

If your intention was to include `5`, the correct condition is:

```javascript
i <= 5
```

---

### Mistake 3: Wrong Starting Value

```javascript
for (let i = 0; i <= 5; i++) {
    console.log(i);
}
```

Output:

```text
0
1
2
3
4
5
```

If you intended to start from `1`, initialize `i` accordingly.

---

## Best Practices

When writing `for` loops:

- Initialize variables clearly.
- Write conditions that are easy to understand.
- Ensure the update moves the loop toward termination.
- Use meaningful variable names when appropriate.
- Keep the loop body focused on one task.
- Avoid unnecessarily complex conditions.

Following these practices makes loops easier to read, maintain, and debug.

---

> **Figure 6.4**
>
> **Execution of a `for` Loop**
>
> *(Insert a diagram showing the execution cycle: Initialization → Condition → Loop Body → Update → Condition, repeating until the condition becomes false.)*

---

> **CodeTales Insight**
>
> A `for` loop is most effective when you know exactly how many iterations are required. As a general rule, if you can answer the question *"How many times should this repeat?"* before writing the code, a `for` loop is often the right choice.

---

## Section Summary

The `for` loop is a powerful and versatile control structure used to repeat a block of code a known number of times. It combines initialization, condition checking, and updating into a single statement, making programs concise and easy to understand. By mastering the `for` loop, you can automate repetitive tasks, generate sequences, perform calculations, and prepare for more advanced programming concepts such as arrays and nested loops.

In the next section, you will learn about **nested `for` loops** and discover how one loop can operate inside another to solve more complex problems, such as creating tables, grids, and patterns.

## 6.5 Nested `for` Loops

As programs become more sophisticated, a single loop is sometimes not enough to solve a problem. There are situations where one repetitive task must occur inside another repetitive task.

JavaScript allows you to place one loop inside another. This is known as a **nested loop**.

Nested loops are commonly used to:

- Display tables.
- Create patterns.
- Process rows and columns of data.
- Work with two-dimensional arrays.
- Generate game boards and grids.
- Build calendars and schedules.

Understanding nested loops is an essential step toward solving more advanced programming problems.

---

## What Is a Nested Loop?

A **nested loop** is simply a loop placed inside the body of another loop.

The outer loop controls how many times the inner loop executes.

General syntax:

```javascript
for (initialization1; condition1; update1) {

    for (initialization2; condition2; update2) {

        // code

    }

}
```

The outer loop begins first.

For every iteration of the outer loop, the inner loop executes completely before the outer loop continues to its next iteration.

---

## Visualizing Nested Loops

Imagine a school with five classrooms.

Each classroom contains thirty students.

The principal visits:

- Classroom 1 → every student
- Classroom 2 → every student
- Classroom 3 → every student
- Classroom 4 → every student
- Classroom 5 → every student

The principal does not move to the next classroom until every student in the current classroom has been visited.

Nested loops work in exactly the same way.

---

## Example 1: Simple Nested Loop

```javascript
for (let row = 1; row <= 3; row++) {

    console.log(`Row ${row}`);

    for (let column = 1; column <= 4; column++) {

        console.log(`Column ${column}`);

    }

}
```

Output:

```text
Row 1
Column 1
Column 2
Column 3
Column 4

Row 2
Column 1
Column 2
Column 3
Column 4

Row 3
Column 1
Column 2
Column 3
Column 4
```

Notice that the inner loop restarts from **1** every time the outer loop moves to the next row.

---

## Understanding the Execution

Consider:

```javascript
for (let row = 1; row <= 2; row++) {

    for (let column = 1; column <= 3; column++) {

        console.log(row, column);

    }

}
```

Execution occurs in this order:

Outer loop:

```text
row = 1
```

Inner loop:

```text
(1,1)
(1,2)
(1,3)
```

Outer loop updates:

```text
row = 2
```

Inner loop starts again:

```text
(2,1)
(2,2)
(2,3)
```

The inner loop always completes before the outer loop continues.

---

## Example 2: Multiplication Table

Nested loops make multiplication tables very easy to generate.

```javascript
for (let row = 1; row <= 5; row++) {

    for (let column = 1; column <= 5; column++) {

        console.log(`${row} × ${column} = ${row * column}`);

    }

}
```

Partial output:

```text
1 × 1 = 1
1 × 2 = 2
...

2 × 1 = 2
2 × 2 = 4
...
```

Without nested loops, this task would require a large amount of repetitive code.

---

## Example 3: Printing a Square Pattern

```javascript
for (let row = 1; row <= 4; row++) {

    let stars = "";

    for (let column = 1; column <= 4; column++) {

        stars += "* ";

    }

    console.log(stars);

}
```

Output:

```text
* * * *
* * * *
* * * *
* * * *
```

The outer loop creates the rows.

The inner loop creates the columns.

---

## Example 4: Number Grid

```javascript
for (let row = 1; row <= 5; row++) {

    let output = "";

    for (let column = 1; column <= 5; column++) {

        output += column + " ";

    }

    console.log(output);

}
```

Output:

```text
1 2 3 4 5
1 2 3 4 5
1 2 3 4 5
1 2 3 4 5
1 2 3 4 5
```

---

## Real-World Applications

Nested loops appear in many software systems.

Examples include:

### Spreadsheet Software

Processing:

- Rows
- Columns
- Cells

---

### Games

Creating:

- Chess boards
- Sudoku grids
- Tile maps
- Game worlds

---

### School Management Systems

Processing:

- Classes
- Students
- Subjects
- Examination scores

---

### E-commerce

Displaying:

- Product categories
- Products within each category

---

### Data Analysis

Processing:

- Tables
- Matrices
- Scientific data

Nested loops make these applications possible.

---

## Time Complexity

Notice that nested loops perform more work than a single loop.

Example:

Outer loop:

```javascript
5 iterations
```

Inner loop:

```javascript
5 iterations
```

Total executions:

```text
25
```

If each loop executes 100 times:

```text
100 × 100 = 10,000
```

As the number of nested loops increases, the amount of work grows rapidly.

Professional developers therefore avoid unnecessary nesting whenever possible.

---

## Common Beginner Mistakes

### Mistake 1: Using the Same Variable

Incorrect:

```javascript
for (let i = 1; i <= 3; i++) {

    for (let i = 1; i <= 3; i++) {

        console.log(i);

    }

}
```

Although JavaScript allows block-scoped variables with `let`, reusing the same variable name in nested loops can make the code confusing.

Better:

```javascript
for (let row = 1; row <= 3; row++) {

    for (let column = 1; column <= 3; column++) {

        console.log(row, column);

    }

}
```

Descriptive variable names improve readability.

---

### Mistake 2: Forgetting Which Loop Is Which

Many beginners accidentally modify the wrong loop variable.

Always remember:

- Outer loop controls rows.
- Inner loop controls columns.

---

### Mistake 3: Excessive Nesting

Three or four nested loops are sometimes necessary.

However, deeply nested loops often make programs difficult to understand.

Whenever possible:

- simplify the logic,
- divide the problem into functions,
- or use more appropriate data structures.

---

## Best Practices

When writing nested loops:

- Use descriptive variable names such as `row` and `column`.
- Keep nesting as shallow as practical.
- Indent code consistently.
- Add comments for complex logic.
- Avoid unnecessary work inside the inner loop.
- Test the loops with small values before increasing the number of iterations.

---

> **Figure 6.5**
>
> **Execution of Nested Loops**
>
> *(Insert a diagram showing an outer loop controlling rows and an inner loop controlling columns. Illustrate that the inner loop completes all its iterations before the outer loop advances.)*

---

> **CodeTales Insight**
>
> Beginners often think of nested loops as "a loop inside another loop." Professional developers think of them as a way to process **two dimensions**. Whenever you encounter rows and columns, grids, tables, calendars, seating arrangements, or matrices, consider whether nested loops provide the simplest solution.

---

## Section Summary

Nested `for` loops allow one loop to execute inside another, making it possible to process two-dimensional data and solve more complex problems. The outer loop controls the overall repetitions, while the inner loop completes all its iterations during each cycle of the outer loop. Mastering nested loops prepares you for working with tables, arrays of arrays, game boards, and many real-world programming tasks.

In the next section, you will explore the **`while` loop**, which is particularly useful when the number of iterations is **not known in advance**.

## 6.6 The `while` Loop

The **`while` loop** repeatedly executes a block of code **as long as a specified condition remains true**.

Unlike the `for` loop, the `while` loop is most useful when the number of iterations is **not known in advance**. Instead of asking, *"How many times should this repeat?"*, you ask, *"Should this continue?"*

As long as the answer is **yes**, the loop keeps running.

---

## Syntax of the `while` Loop

The general syntax is:

```javascript
while (condition) {
    // code to repeat
}
```

The loop works as follows:

1. Evaluate the condition.
2. If the condition is `true`, execute the loop body.
3. Return to the condition.
4. Repeat until the condition becomes `false`.

---

## A Simple Example

```javascript
let count = 1;

while (count <= 5) {
    console.log(count);
    count++;
}
```

Output:

```text
1
2
3
4
5
```

Let's examine the code:

```javascript
let count = 1;
```

The counter begins at **1**.

Next:

```javascript
while (count <= 5)
```

JavaScript checks whether the condition is true.

If it is, the statements inside the loop execute.

Finally:

```javascript
count++;
```

The counter increases by one before the next iteration.

---

## How the `while` Loop Executes

Consider:

```javascript
let number = 1;

while (number <= 3) {

    console.log(number);

    number++;

}
```

Execution proceeds as follows.

### First Iteration

Condition:

```javascript
1 <= 3
```

Result:

```text
true
```

Output:

```text
1
```

Update:

```text
number = 2
```

---

### Second Iteration

Condition:

```javascript
2 <= 3
```

Result:

```text
true
```

Output:

```text
2
```

Update:

```text
number = 3
```

---

### Third Iteration

Condition:

```javascript
3 <= 3
```

Result:

```text
true
```

Output:

```text
3
```

Update:

```text
number = 4
```

---

### Final Check

Condition:

```javascript
4 <= 3
```

Result:

```text
false
```

The loop terminates.

---

## Example 1: Countdown

```javascript
let countdown = 10;

while (countdown >= 1) {

    console.log(countdown);

    countdown--;

}

console.log("Blast Off!");
```

Output:

```text
10
9
8
7
6
5
4
3
2
1
Blast Off!
```

---

## Example 2: Display Even Numbers

```javascript
let even = 2;

while (even <= 20) {

    console.log(even);

    even += 2;

}
```

Output:

```text
2
4
6
8
10
12
14
16
18
20
```

---

## Example 3: Password Verification

Suppose a program continues asking for a password until the correct one is entered.

Conceptually:

```javascript
while (passwordIsIncorrect) {

    // Ask the user for another password

}
```

The program does **not** know how many attempts the user will make.

This is an ideal situation for a `while` loop.

---

## Example 4: Filling a Water Tank

Imagine filling a water tank.

The pump continues running **while** the tank is not full.

Conceptually:

```javascript
while (tankIsNotFull) {

    fillTank();

}
```

Once the tank becomes full, the condition changes, and the loop stops.

---

## When Should You Use a `while` Loop?

A `while` loop is a good choice when:

- The number of repetitions is unknown.
- The loop depends on user input.
- The loop depends on external data.
- The stopping condition may change while the program is running.

Examples include:

- Login systems
- ATM menus
- Reading files
- Waiting for a network connection
- Game loops
- Sensor monitoring

---

## Comparison with the `for` Loop

Consider:

### `for` Loop

```javascript
for (let i = 1; i <= 5; i++) {

    console.log(i);

}
```

The number of iterations is known.

---

### `while` Loop

```javascript
let i = 1;

while (i <= 5) {

    console.log(i);

    i++;

}
```

The result is the same.

However, the initialization and update occur outside the loop declaration.

---

## Common Beginner Mistakes

### Mistake 1: Forgetting the Update

```javascript
let count = 1;

while (count <= 5) {

    console.log(count);

}
```

The value of `count` never changes.

The condition always remains true.

This creates an **infinite loop**.

Correct:

```javascript
count++;
```

must appear inside the loop.

---

### Mistake 2: Incorrect Condition

```javascript
let number = 10;

while (number < 5) {

    console.log(number);

    number++;

}
```

Since the condition is already false, the loop never executes.

Output:

```text
(no output)
```

Always verify the initial value and the condition work together.

---

### Mistake 3: Updating the Wrong Variable

If multiple variables exist, beginners sometimes update the wrong one.

Example:

```javascript
let count = 1;
let total = 0;

while (count <= 5) {

    total++;

}
```

Because `count` never changes, the loop never ends.

---

## Best Practices

When writing `while` loops:

- Initialize variables before the loop.
- Ensure the condition eventually becomes false.
- Update the loop variable inside the loop.
- Keep conditions simple and readable.
- Avoid unnecessarily complicated logic.

---

## Real-World Applications

`while` loops appear in many professional applications.

Examples include:

- Login authentication
- ATM transaction processing
- Reading files until the end
- Download progress monitoring
- Chat applications waiting for new messages
- Monitoring sensors in industrial systems
- Online multiplayer games
- Network communication

In these situations, the program cannot predict exactly how many iterations will be required.

---

> **Figure 6.6**
>
> **Execution of a `while` Loop**
>
> *(Insert a flowchart showing: Condition → Loop Body → Update → back to Condition. If the condition is false initially, the loop body is skipped entirely.)*

---

> **CodeTales Insight**
>
> The most common cause of infinite loops is forgetting to change the condition that controls the loop. Whenever you write a `while` loop, immediately ask yourself: **"What causes this loop to stop?"** If you cannot answer that question clearly, your loop may never terminate.

---

## Section Summary

The `while` loop repeatedly executes a block of code **while** a specified condition remains true. It is especially useful when the number of iterations cannot be determined in advance and repetition depends on changing conditions such as user input, file contents, or external events. By understanding how the condition, loop body, and update work together, you can use `while` loops to solve many real-world programming problems.

In the next section, you will learn about the **`do...while` loop**, which guarantees that the loop body executes **at least once**, even if the condition is initially false.

## 6.7 The `do...while` Loop

The **`do...while` loop** is similar to the `while` loop, but it has one important difference:

> **The loop body executes at least once before the condition is evaluated.**

This means the statements inside the loop are guaranteed to run one time, even if the condition is initially `false`.

This behavior makes the `do...while` loop useful in situations where an operation must occur before deciding whether to repeat it.

---

## Syntax of the `do...while` Loop

The general syntax is:

```javascript
do {
    // code to repeat
} while (condition);
```

Notice the order:

1. Execute the loop body.
2. Evaluate the condition.
3. If the condition is `true`, repeat.
4. If the condition is `false`, terminate the loop.

Unlike the `for` and `while` loops, the condition appears **after** the loop body.

---

## A Simple Example

```javascript
let count = 1;

do {
    console.log(count);
    count++;
} while (count <= 5);
```

Output:

```text
1
2
3
4
5
```

The loop executes the body first and checks the condition afterward.

---

## Understanding the Execution

Consider:

```javascript
let number = 1;

do {

    console.log(number);

    number++;

} while (number <= 3);
```

Execution proceeds as follows.

### First Iteration

Execute loop body:

```text
1
```

Update:

```text
number = 2
```

Condition:

```javascript
2 <= 3
```

Result:

```text
true
```

---

### Second Iteration

Output:

```text
2
```

Update:

```text
number = 3
```

Condition:

```javascript
3 <= 3
```

Result:

```text
true
```

---

### Third Iteration

Output:

```text
3
```

Update:

```text
number = 4
```

Condition:

```javascript
4 <= 3
```

Result:

```text
false
```

The loop terminates.

---

## The Unique Feature of `do...while`

Suppose the initial value is:

```javascript
let number = 10;
```

Now consider:

```javascript
do {

    console.log(number);

} while (number < 5);
```

Output:

```text
10
```

Although the condition:

```javascript
number < 5
```

is false from the beginning, the loop body still executes once.

This is the defining characteristic of the `do...while` loop.

---

## Comparing `while` and `do...while`

### Example Using `while`

```javascript
let number = 10;

while (number < 5) {

    console.log(number);

}
```

Output:

```text
(no output)
```

The condition is checked before the loop begins.

---

### Example Using `do...while`

```javascript
let number = 10;

do {

    console.log(number);

} while (number < 5);
```

Output:

```text
10
```

The body executes first, then the condition is checked.

---

## Example 1: Menu-Driven Program

Imagine a program that displays a menu.

The menu must appear at least once.

Conceptually:

```javascript
do {

    // Display menu

    // Get user's choice

} while (userWantsToContinue);
```

The user cannot decide whether to continue until they have first seen the menu.

---

## Example 2: User Input Validation

Suppose a user must enter a number between 1 and 10.

Conceptually:

```javascript
do {

    // Ask for input

} while (inputIsInvalid);
```

The program must request input at least once before it can determine whether the input is valid.

---

## Example 3: Simple Countdown

```javascript
let countdown = 5;

do {

    console.log(countdown);

    countdown--;

} while (countdown >= 1);
```

Output:

```text
5
4
3
2
1
```

---

## When Should You Use a `do...while` Loop?

Use a `do...while` loop when:

- The code must execute at least once.
- The stopping condition depends on user interaction.
- You are creating menus.
- You are validating user input.
- You are prompting users repeatedly until valid data is entered.

---

## Real-World Applications

Examples include:

- ATM transaction menus.
- Login prompts.
- Customer surveys.
- Game menus.
- Password confirmation.
- PIN verification.
- Command-line applications.
- Data entry forms.

In each case, the user must interact with the program before the loop decides whether another iteration is needed.

---

## Common Beginner Mistakes

### Mistake 1: Forgetting the Semicolon

Incorrect:

```javascript
do {

    console.log("Hello");

} while (false)
```

Correct:

```javascript
do {

    console.log("Hello");

} while (false);
```

A semicolon is required after the condition.

---

### Mistake 2: Forgetting the Update

```javascript
let count = 1;

do {

    console.log(count);

} while (count <= 5);
```

Because `count` never changes, the condition always remains true.

This creates an infinite loop.

Correct:

```javascript
count++;
```

---

### Mistake 3: Using `do...while` Unnecessarily

Sometimes beginners use a `do...while` loop when a `for` or `while` loop would be simpler.

Choose the loop that best matches the problem.

---

## Best Practices

When writing `do...while` loops:

- Use them only when at least one execution is required.
- Keep the condition easy to understand.
- Update variables correctly.
- Avoid unnecessary nesting.
- Test the loop with both true and false conditions.

---

## Choosing Between the Three Loop Types

A quick guideline:

### Use a `for` loop when:

- The number of iterations is known.

### Use a `while` loop when:

- The repetition depends on a condition.
- The number of iterations is unknown.

### Use a `do...while` loop when:

- The code must execute at least once before checking the condition.

Choosing the appropriate loop improves both readability and maintainability.

---

> **Figure 6.7**
>
> **Comparison of `while` and `do...while` Execution**
>
> *(Insert a side-by-side flowchart. The `while` loop checks the condition before executing the body, while the `do...while` loop executes the body first and checks the condition afterward.)*

---

> **CodeTales Insight**
>
> Many developers use the `do...while` loop less frequently than `for` and `while`, but it remains an important tool. Whenever your program must perform an action before deciding whether to repeat it—such as displaying a menu or requesting user input—the `do...while` loop often provides the clearest solution.

---

## Section Summary

The `do...while` loop guarantees that its body executes at least once before the condition is evaluated. This makes it particularly useful for interactive programs, menus, and input validation. Although it shares many characteristics with the `while` loop, its unique execution order makes it the preferred choice whenever an initial execution is required.

In the next section, you will compare the **`for`**, **`while`**, and **`do...while`** loops and learn how to choose the most appropriate looping structure for different programming scenarios.

## 6.8 Choosing Between `for`, `while`, and `do...while`

JavaScript provides three primary looping structures:

- `for`
- `while`
- `do...while`

All three loops can perform repetitive tasks, and in many cases, the same problem can be solved using any of them.

However, experienced programmers choose the loop that best matches the nature of the problem. Selecting the appropriate loop improves readability, maintainability, and makes your intentions clearer to other developers.

This section explains when each loop should be used and how to decide which one is most appropriate.

---

## The Right Tool for the Right Job

Think of loops as different tools in a toolbox.

A hammer, a screwdriver, and a wrench can all help you build something, but each tool is designed for a particular purpose.

Similarly:

- A `for` loop is ideal when you know the number of iterations.
- A `while` loop is useful when repetition depends on a condition.
- A `do...while` loop is appropriate when the code must execute at least once.

Choosing the correct loop makes your programs easier to understand.

---

## When to Use a `for` Loop

Use a `for` loop when the number of repetitions is known before the loop begins.

Examples include:

- Displaying numbers from 1 to 100.
- Printing multiplication tables.
- Processing every item in an array.
- Repeating an action a fixed number of times.
- Generating reports with a known number of records.

Example:

```javascript
for (let i = 1; i <= 10; i++) {
    console.log(i);
}
```

In this example, it is clear that the loop will execute ten times.

The `for` loop expresses this intention directly.

---

## When to Use a `while` Loop

Use a `while` loop when you do not know in advance how many times the loop should execute.

Instead, the loop continues while a condition remains true.

Examples include:

- Waiting for a user to enter the correct password.
- Monitoring a sensor.
- Reading data until the end of a file.
- Processing messages from a queue.
- Waiting for a network connection.

Example:

```javascript
while (connectionLost) {
    reconnect();
}
```

The number of repetitions depends entirely on when the connection is restored.

---

## When to Use a `do...while` Loop

Use a `do...while` loop when the code must execute at least once before the condition is checked.

Examples include:

- Displaying menus.
- Requesting user input.
- Confirming user choices.
- Running setup procedures.

Example:

```javascript
do {
    console.log("Main Menu");
} while (userChoosesToContinue);
```

The menu must appear at least one time.

---

## Comparing the Three Loops

| Feature | `for` | `while` | `do...while` |
|---------|-------|----------|--------------|
| Best when the number of iterations is known | ✅ | ❌ | ❌ |
| Best when iterations depend on a condition | ⚠️ Possible | ✅ | ✅ |
| Executes at least once | ❌ | ❌ | ✅ |
| Initialization included in loop declaration | ✅ | ❌ | ❌ |
| Update usually included in loop declaration | ✅ | ❌ | ❌ |
| Condition checked before first iteration | ✅ | ✅ | ❌ |

Although these loops can sometimes be used interchangeably, choosing the most suitable one makes your code easier to read.

---

## Solving the Same Problem with Different Loops

Suppose you want to display the numbers from 1 to 5.

### Using a `for` Loop

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

---

### Using a `while` Loop

```javascript
let i = 1;

while (i <= 5) {
    console.log(i);
    i++;
}
```

---

### Using a `do...while` Loop

```javascript
let i = 1;

do {
    console.log(i);
    i++;
} while (i <= 5);
```

All three programs produce the same output.

The difference lies in readability and suitability for the task.

---

## Decision Guide

Ask yourself these questions before choosing a loop.

### Question 1

Do I know exactly how many times the loop should execute?

If **Yes**, use:

```text
for
```

---

### Question 2

Will the loop continue until some condition changes?

If **Yes**, use:

```text
while
```

---

### Question 3

Must the loop body execute at least once?

If **Yes**, use:

```text
do...while
```

---

## Real-World Examples

### Example 1: Student Attendance

A teacher marks attendance for exactly 30 students.

Best choice:

```text
for
```

The number of students is known.

---

### Example 2: ATM PIN Verification

A customer keeps entering a PIN until it is correct.

Best choice:

```text
while
```

The number of attempts is unknown.

---

### Example 3: Restaurant Ordering System

The menu appears first.

After ordering, the customer decides whether to place another order.

Best choice:

```text
do...while
```

The menu must appear at least once.

---

### Example 4: Processing Monthly Salaries

A company has exactly 250 employees.

Best choice:

```text
for
```

The number of employees is known.

---

### Example 5: Waiting for Internet Connectivity

The application keeps checking until a connection becomes available.

Best choice:

```text
while
```

The number of checks cannot be predicted.

---

## Common Beginner Mistakes

### Mistake 1: Using `while` Instead of `for`

Sometimes beginners write:

```javascript
let i = 1;

while (i <= 10) {

    console.log(i);

    i++;

}
```

Although correct, a `for` loop expresses the intention more clearly because the number of iterations is known.

---

### Mistake 2: Using `do...while` Without Needing the First Execution

If the loop body should not execute when the condition is false, a `while` loop is usually the better choice.

---

### Mistake 3: Choosing Based on Habit

Some programmers always use the same loop regardless of the problem.

Professional developers choose the loop that best communicates the program's logic.

---

## Best Practices

When selecting a loop:

- Choose the simplest solution.
- Let the problem determine the loop type.
- Keep loop conditions readable.
- Avoid converting one loop into another without a good reason.
- Prioritize clarity over cleverness.

Readable code is easier to maintain and debug.

---

> **Figure 6.8**
>
> **Choosing the Appropriate Loop**
>
> *(Insert a decision tree starting with the question "Do you know the number of iterations?" Branch to `for` if yes. If no, ask "Must the code execute at least once?" Branch to `do...while` if yes, otherwise branch to `while`.)*

---

> **CodeTales Insight**
>
> One hallmark of experienced programmers is that they choose control structures intentionally. When another developer reads your code, the type of loop you selected should immediately communicate how the repetition works. Good code is not only correct—it also explains itself.

---

## Section Summary

Although the `for`, `while`, and `do...while` loops can often accomplish the same tasks, each is designed for different situations. The `for` loop is ideal for a known number of iterations, the `while` loop is best when repetition depends on a changing condition, and the `do...while` loop is appropriate when the code must execute at least once before checking the condition. Choosing the right loop makes your programs clearer, easier to maintain, and more closely aligned with professional programming practices.

In the next section, you will learn about **loop control statements**, including **`break`** and **`continue`**, which allow you to alter the normal flow of loop execution.

## 6.9 Loop Control Statements (`break` and `continue`)

By default, a loop continues executing until its condition becomes `false`.

However, there are situations where you may want to:

- Stop a loop immediately before it reaches its normal end.
- Skip one particular iteration and continue with the next.

JavaScript provides two special statements for this purpose:

- `break`
- `continue`

These are known as **loop control statements** because they alter the normal flow of loop execution.

---

## The `break` Statement

The **`break`** statement immediately terminates the current loop.

When JavaScript encounters a `break` statement inside a loop, it exits the loop immediately and continues executing the first statement after the loop.

General syntax:

```javascript
break;
```

---

## Example 1: Stopping a Loop Early

```javascript
for (let i = 1; i <= 10; i++) {

    if (i === 6) {
        break;
    }

    console.log(i);

}
```

Output:

```text
1
2
3
4
5
```

Notice that the loop stops as soon as `i` becomes `6`.

Numbers `6` through `10` are never printed.

---

## How `break` Works

Execution proceeds as follows:

```
i = 1 → print

i = 2 → print

i = 3 → print

i = 4 → print

i = 5 → print

i = 6 → break

Loop Ends
```

Once `break` executes, the remaining iterations are skipped completely.

---

## Example 2: Searching for a Value

Suppose you are searching for a specific product ID.

```javascript
for (let id = 100; id <= 200; id++) {

    if (id === 145) {

        console.log("Product Found");

        break;

    }

}
```

Once the product is found, there is no need to continue searching.

The `break` statement improves efficiency by stopping the loop immediately.

---

## Real-World Uses of `break`

Examples include:

- Finding a product in a database.
- Locating a student's record.
- Searching a list of contacts.
- Detecting an error.
- Finding the first matching result.
- Stopping when a winning condition is reached in a game.

Whenever the remaining iterations are unnecessary, `break` is often the right choice.

---

# The `continue` Statement

The **`continue`** statement skips the current iteration and moves directly to the next iteration of the loop.

Unlike `break`, it **does not terminate the loop**.

General syntax:

```javascript
continue;
```

---

## Example 3: Skipping One Number

```javascript
for (let i = 1; i <= 5; i++) {

    if (i === 3) {
        continue;
    }

    console.log(i);

}
```

Output:

```text
1
2
4
5
```

Notice that:

```
3
```

is skipped, but the loop continues normally.

---

## How `continue` Works

Execution:

```
i = 1 → print

i = 2 → print

i = 3 → continue

Skip console.log()

Move to next iteration

i = 4 → print

i = 5 → print
```

Only one iteration is skipped.

The loop itself continues.

---

## Example 4: Display Only Odd Numbers

```javascript
for (let number = 1; number <= 10; number++) {

    if (number % 2 === 0) {

        continue;

    }

    console.log(number);

}
```

Output:

```text
1
3
5
7
9
```

Whenever the number is even, the loop skips printing it.

---

## Example 5: Display Only Even Numbers

```javascript
for (let number = 1; number <= 10; number++) {

    if (number % 2 !== 0) {

        continue;

    }

    console.log(number);

}
```

Output:

```text
2
4
6
8
10
```

---

## Comparing `break` and `continue`

| Feature | `break` | `continue` |
|----------|----------|------------|
| Stops the loop completely | ✅ | ❌ |
| Skips only the current iteration | ❌ | ✅ |
| Continues with the next iteration | ❌ | ✅ |
| Executes statements after the loop | ✅ | Only after the loop finishes normally |

Understanding this distinction is important.

Many beginners confuse these two statements.

---

## Visual Comparison

Consider this loop.

### Using `break`

```javascript
for (let i = 1; i <= 5; i++) {

    if (i === 3) {

        break;

    }

    console.log(i);

}
```

Output:

```text
1
2
```

The loop stops completely.

---

### Using `continue`

```javascript
for (let i = 1; i <= 5; i++) {

    if (i === 3) {

        continue;

    }

    console.log(i);

}
```

Output:

```text
1
2
4
5
```

Only the current iteration is skipped.

---

## Common Beginner Mistakes

### Mistake 1: Confusing `break` and `continue`

Some beginners expect:

```javascript
continue;
```

to stop the loop.

It does not.

It only skips one iteration.

---

### Mistake 2: Using `break` Too Early

```javascript
for (let i = 1; i <= 100; i++) {

    break;

}
```

The loop executes only once.

Always ensure `break` appears only when you truly intend to terminate the loop.

---

### Mistake 3: Overusing `continue`

Sometimes an `if...else` statement makes the logic clearer than repeatedly using `continue`.

Choose whichever approach improves readability.

---

## Best Practices

When using `break` and `continue`:

- Use `break` only when terminating the loop is the correct behavior.
- Use `continue` only when skipping specific iterations improves clarity.
- Avoid excessive use of either statement, as it can make loops harder to follow.
- Add comments if the reason for breaking or continuing is not obvious.
- Keep loop logic simple and easy to understand.

---

## Real-World Applications

### Using `break`

- Stop searching when an item is found.
- Exit a game when the player wins.
- Stop processing when an error occurs.
- Terminate a download when the user cancels it.

---

### Using `continue`

- Ignore invalid records.
- Skip inactive users.
- Process only approved transactions.
- Ignore empty input fields.
- Skip weekends when generating a work schedule.

---

> **Figure 6.9**
>
> **Difference Between `break` and `continue`**
>
> *(Insert a flowchart comparing the two statements. Show `break` exiting the loop entirely, while `continue` skips the remainder of the current iteration and returns directly to the loop condition.)*

---

> **CodeTales Insight**
>
> Professional developers often use `break` to improve efficiency. For example, if you're searching through thousands of records and find the one you need, there's no benefit in checking the remaining records. On the other hand, `continue` is useful for filtering data by skipping records that don't meet certain conditions while continuing to process the rest.

---

## Section Summary

The `break` and `continue` statements provide greater control over loop execution. The `break` statement immediately terminates a loop, while the `continue` statement skips the current iteration and proceeds to the next one. Understanding when to stop a loop entirely and when to skip only specific iterations allows you to write more efficient, readable, and maintainable programs.

In the next section, you will explore **infinite loops**, learn why they occur, understand the problems they cause, and discover practical techniques for preventing them.

## 6.10 Infinite Loops and How to Avoid Them

Loops are designed to repeat a block of code until a specified condition becomes `false`.

But what happens if that condition **never becomes false**?

The answer is an **infinite loop**.

An infinite loop is one of the most common programming mistakes, especially among beginners. It occurs when a loop continues to execute indefinitely because there is no valid way for it to terminate.

Understanding why infinite loops occur—and how to prevent them—is an essential programming skill.

---

## What Is an Infinite Loop?

An **infinite loop** is a loop whose termination condition is never satisfied.

As a result, the loop continues executing forever (or until the program is manually stopped).

Consider the following example:

```javascript
let count = 1;

while (count <= 5) {
    console.log(count);
}
```

At first glance, this may seem correct.

However, there is a problem.

The value of `count` never changes.

Since `count` remains equal to `1`, the condition:

```javascript
count <= 5
```

is always `true`.

The program never exits the loop.

---

## Correcting the Problem

The solution is simple.

Update the loop variable:

```javascript
let count = 1;

while (count <= 5) {

    console.log(count);

    count++;

}
```

Output:

```text
1
2
3
4
5
```

The update allows the condition to eventually become `false`.

---

## Infinite Loop Example Using a `for` Loop

Although `for` loops often reduce the likelihood of infinite loops, they are not immune.

Incorrect:

```javascript
for (let i = 1; i <= 5;) {

    console.log(i);

}
```

Because the update expression is missing, `i` never changes.

The condition remains true forever.

Correct:

```javascript
for (let i = 1; i <= 5; i++) {

    console.log(i);

}
```

---

## Infinite Loop Example Using `do...while`

```javascript
let number = 1;

do {

    console.log(number);

} while (number <= 5);
```

Again, the value of `number` never changes.

The loop continues indefinitely.

Correct:

```javascript
let number = 1;

do {

    console.log(number);

    number++;

} while (number <= 5);
```

---

## Common Causes of Infinite Loops

### 1. Forgetting to Update the Loop Variable

This is the most common cause.

Incorrect:

```javascript
while (count <= 10) {

    console.log(count);

}
```

Correct:

```javascript
count++;
```

---

### 2. Using the Wrong Condition

Example:

```javascript
let number = 10;

while (number >= 1) {

    console.log(number);

    number++;

}
```

Notice the problem.

The condition requires the number to become **less than 1**.

However, the update makes the number larger.

The condition never becomes false.

Correct:

```javascript
number--;
```

---

### 3. Accidentally Resetting the Loop Variable

Incorrect:

```javascript
let count = 1;

while (count <= 5) {

    console.log(count);

    count = 1;

}
```

Every iteration resets the variable back to `1`.

The loop can never terminate.

---

### 4. Always-True Conditions

Example:

```javascript
while (true) {

    console.log("Running");

}
```

The condition is permanently `true`.

Unless a `break` statement exists inside the loop, it will never end.

---

## Intentional Infinite Loops

Not every infinite loop is a programming mistake.

Professional developers sometimes create intentional infinite loops.

Example:

```javascript
while (true) {

    // Wait for incoming requests

}
```

Examples include:

- Web servers.
- Operating systems.
- Game engines.
- Chat applications.
- Background services.

These programs are designed to run continuously.

They usually contain a `break` statement or another mechanism to stop execution when necessary.

---

## Consequences of Infinite Loops

Infinite loops can cause serious problems.

Examples include:

- High CPU usage.
- Excessive memory consumption.
- Unresponsive programs.
- Frozen browsers.
- Battery drain on mobile devices.
- Poor user experience.

Because the computer never exits the loop, system resources continue to be consumed.

---

## Detecting Infinite Loops

Some warning signs include:

- The program never finishes.
- The browser becomes unresponsive.
- The terminal continuously displays output.
- CPU usage increases dramatically.
- The fan on your computer runs continuously.

If these symptoms occur immediately after writing a loop, an infinite loop is a likely cause.

---

## Debugging Infinite Loops

When debugging a loop, ask yourself the following questions:

### Question 1

Does the loop variable change?

---

### Question 2

Will the condition eventually become false?

---

### Question 3

Am I updating the correct variable?

---

### Question 4

Did I accidentally reset the variable?

---

### Question 5

Can I print the loop variable during each iteration?

Example:

```javascript
while (count <= 5) {

    console.log(count);

    count++;

}
```

Printing the variable often reveals where the problem occurs.

---

## Preventing Infinite Loops

Professional developers follow several simple practices.

### Always update loop variables.

### Verify the condition carefully.

### Test loops with small values first.

### Use meaningful variable names.

### Review the execution order.

### Add comments for complex loops.

### Trace the first few iterations manually.

These habits significantly reduce loop-related errors.

---

## Best Practices

When writing loops:

- Ensure every loop has a clear termination condition.
- Avoid unnecessarily complex conditions.
- Keep updates simple and predictable.
- Test edge cases.
- Use a debugger or `console.log()` when troubleshooting.

Good programming is not about avoiding mistakes—it is about recognizing and correcting them efficiently.

---

> **Figure 6.10**
>
> **How Infinite Loops Occur**
>
> *(Insert a flowchart showing a loop repeatedly checking a condition that never becomes false because the loop variable is not updated. Include a corrected version where the update allows the loop to terminate.)*

---

> **CodeTales Insight**
>
> One of the first questions experienced developers ask when reviewing a loop is: **"What guarantees that this loop will eventually stop?"** If there is no clear answer, the loop deserves closer inspection. Developing this habit early will help you write more reliable and efficient programs.

---

## Section Summary

An infinite loop occurs when a loop's termination condition never becomes false. Common causes include forgetting to update the loop variable, using an incorrect condition, resetting variables unintentionally, or creating always-true conditions. While some infinite loops are intentional in systems such as web servers and game engines, most are programming errors. By understanding how loops terminate and following good debugging practices, you can prevent infinite loops and build more reliable JavaScript programs.

In the next section, you will explore **common looping patterns**—reusable techniques that programmers apply repeatedly to solve everyday programming problems.

## 6.11 Common Looping Patterns

By now, you have learned how to use the `for`, `while`, and `do...while` loops.

However, writing loops is only part of programming. The real skill lies in recognizing **patterns**—common techniques that can be applied to solve many different problems.

Professional developers rarely write loops from scratch. Instead, they identify the problem and apply a familiar looping pattern.

This section introduces some of the most frequently used looping patterns in JavaScript.

---

## Pattern 1: Counting

The simplest use of a loop is counting.

Example:

```javascript
for (let number = 1; number <= 10; number++) {
    console.log(number);
}
```

Output:

```text
1
2
3
4
5
6
7
8
9
10
```

Counting is useful for:

- Numbering items.
- Displaying page numbers.
- Generating reports.
- Creating IDs.

---

## Pattern 2: Accumulating a Total

Sometimes you need to calculate a running total.

Example:

Find the sum of the numbers from 1 to 5.

```javascript
let total = 0;

for (let number = 1; number <= 5; number++) {
    total += number;
}

console.log(total);
```

Output:

```text
15
```

The variable `total` is called an **accumulator** because it stores the running total.

This pattern is commonly used in:

- Payroll systems.
- Shopping carts.
- Banking applications.
- Grade calculations.

---

## Pattern 3: Counting Specific Items

Suppose you want to count only even numbers.

```javascript
let evenCount = 0;

for (let number = 1; number <= 10; number++) {

    if (number % 2 === 0) {

        evenCount++;

    }

}

console.log(evenCount);
```

Output:

```text
5
```

This pattern is useful for counting:

- Passed students.
- Active users.
- Successful transactions.
- Available products.

---

## Pattern 4: Finding the Largest Value

Loops are often used to compare values.

Example:

```javascript
let numbers = [12, 7, 25, 19, 30];

let largest = numbers[0];

for (let i = 1; i < numbers.length; i++) {

    if (numbers[i] > largest) {

        largest = numbers[i];

    }

}

console.log(largest);
```

Output:

```text
30
```

---

## Pattern 5: Finding the Smallest Value

The logic is similar.

```javascript
let numbers = [12, 7, 25, 19, 30];

let smallest = numbers[0];

for (let i = 1; i < numbers.length; i++) {

    if (numbers[i] < smallest) {

        smallest = numbers[i];

    }

}

console.log(smallest);
```

Output:

```text
7
```

---

## Pattern 6: Searching

Sometimes you need to determine whether an item exists.

Example:

```javascript
let numbers = [10, 20, 30, 40, 50];

let found = false;

for (let i = 0; i < numbers.length; i++) {

    if (numbers[i] === 30) {

        found = true;

        break;

    }

}

console.log(found);
```

Output:

```text
true
```

Notice the use of `break` to stop searching once the value is found.

---

## Pattern 7: Filtering

A loop can process only items that satisfy a condition.

Example:

Display numbers greater than 5.

```javascript
for (let number = 1; number <= 10; number++) {

    if (number > 5) {

        console.log(number);

    }

}
```

Output:

```text
6
7
8
9
10
```

Filtering is widely used in:

- Search engines.
- Online shopping.
- Employee records.
- Reports.

---

## Pattern 8: Building Strings

Loops can combine text.

Example:

```javascript
let word = "";

for (let i = 1; i <= 5; i++) {

    word += "JavaScript ";

}

console.log(word);
```

Output:

```text
JavaScript JavaScript JavaScript JavaScript JavaScript
```

---

## Pattern 9: Generating Patterns

Loops can generate visual patterns.

Example:

```javascript
for (let row = 1; row <= 5; row++) {

    let stars = "";

    for (let column = 1; column <= row; column++) {

        stars += "* ";

    }

    console.log(stars);

}
```

Output:

```text
*
* *
* * *
* * * *
* * * * *
```

Pattern generation is commonly used for learning nested loops and improving logical thinking.

---

## Pattern 10: Processing Collections

One of the most important uses of loops is processing collections of data.

Example:

```javascript
let fruits = ["Apple", "Banana", "Orange"];

for (let i = 0; i < fruits.length; i++) {

    console.log(fruits[i]);

}
```

Output:

```text
Apple
Banana
Orange
```

In later chapters, you will learn more advanced ways of processing arrays, but traditional loops remain an important skill.

---

## Why These Patterns Matter

Although the examples in this section are simple, they represent the foundation of many real-world applications.

For example:

- Banking software accumulates account balances.
- Schools calculate examination results.
- Hospitals process patient records.
- E-commerce websites search product catalogs.
- Social media platforms filter posts.
- Data analysis software identifies maximum and minimum values.

The same looping patterns appear repeatedly in professional software development.

---

## Common Beginner Mistakes

### Mistake 1: Forgetting to Initialize Variables

Incorrect:

```javascript
let total;

for (let i = 1; i <= 5; i++) {

    total += i;

}
```

Because `total` was never initialized, the result is:

```text
NaN
```

Correct:

```javascript
let total = 0;
```

---

### Mistake 2: Starting at the Wrong Index

When processing arrays, remember that JavaScript arrays start at index `0`.

Incorrect:

```javascript
for (let i = 1; i < fruits.length; i++)
```

This skips the first element.

---

### Mistake 3: Forgetting `break` During Searches

If only one result is needed, forgetting to use `break` causes unnecessary iterations.

---

## Best Practices

When writing looping patterns:

- Choose meaningful variable names.
- Initialize variables correctly.
- Use `break` when searching for a single item.
- Keep the loop body focused on one responsibility.
- Test with small datasets before using larger ones.
- Avoid repeating logic unnecessarily.

---

> **Figure 6.11**
>
> **Common Looping Patterns**
>
> *(Insert a diagram showing the relationship between common looping tasks: Counting, Accumulating, Searching, Filtering, Finding Maximum/Minimum, Pattern Generation, and Processing Collections.)*

---

> **CodeTales Insight**
>
> Experienced programmers often recognize problems by their looping pattern rather than by the programming language. Whether you're using JavaScript, Python, Java, or C#, the same core patterns—counting, accumulating, searching, filtering, and processing collections—appear again and again. Mastering these patterns will make learning other programming languages much easier.

---

## Section Summary

Loops are more than repetition—they are tools for solving recurring programming problems. By learning common looping patterns such as counting, accumulating totals, searching, filtering, finding maximum and minimum values, generating patterns, and processing collections, you build a toolkit that can be applied to a wide range of real-world software applications. Recognizing these patterns will help you write more efficient, organized, and maintainable code.

In the next section, you will explore **practical examples** that combine the techniques you've learned throughout this chapter to solve realistic programming problems.

## 6.12 Practical Examples

Throughout this chapter, you have learned about the `for`, `while`, and `do...while` loops, loop control statements, common looping patterns, and techniques for avoiding infinite loops.

In this section, you will apply these concepts to solve practical programming problems. These examples are similar to tasks that software developers encounter in real-world applications.

---

## Example 1: Calculating the Sum of Numbers

Suppose you need to calculate the sum of the numbers from **1 to 100**.

```javascript
let total = 0;

for (let number = 1; number <= 100; number++) {
    total += number;
}

console.log("Total:", total);
```

Output:

```text
Total: 5050
```

### How It Works

- `total` starts at `0`.
- Each number from `1` to `100` is added to `total`.
- After the loop finishes, `total` contains the final sum.

This pattern is useful for:

- Calculating totals.
- Summing sales.
- Computing account balances.
- Generating reports.

---

## Example 2: Displaying a Multiplication Table

```javascript
let number = 7;

for (let i = 1; i <= 12; i++) {

    console.log(`${number} × ${i} = ${number * i}`);

}
```

Output (partial):

```text
7 × 1 = 7
7 × 2 = 14
...
7 × 12 = 84
```

Multiplication tables are commonly used in educational software.

---

## Example 3: Counting Even Numbers

Display the even numbers between 1 and 20.

```javascript
for (let number = 1; number <= 20; number++) {

    if (number % 2 === 0) {

        console.log(number);

    }

}
```

Output:

```text
2
4
6
8
10
12
14
16
18
20
```

This technique is often used when filtering data.

---

## Example 4: Countdown Timer

```javascript
let countdown = 10;

while (countdown >= 1) {

    console.log(countdown);

    countdown--;

}

console.log("Time's up!");
```

Output:

```text
10
9
8
7
6
5
4
3
2
1
Time's up!
```

Applications include:

- Game timers.
- Examination timers.
- Event countdowns.

---

## Example 5: Finding the Largest Number

```javascript
let scores = [67, 82, 91, 74, 88];

let highest = scores[0];

for (let i = 1; i < scores.length; i++) {

    if (scores[i] > highest) {

        highest = scores[i];

    }

}

console.log("Highest Score:", highest);
```

Output:

```text
Highest Score: 91
```

This pattern is commonly used in:

- Student grading systems.
- Sports statistics.
- Sales reporting.

---

## Example 6: Searching for an Item

```javascript
let products = ["Laptop", "Phone", "Printer", "Monitor"];

let found = false;

for (let i = 0; i < products.length; i++) {

    if (products[i] === "Printer") {

        found = true;

        break;

    }

}

console.log(found);
```

Output:

```text
true
```

Notice that `break` prevents unnecessary iterations after the item is found.

---

## Example 7: Printing a Triangle Pattern

```javascript
for (let row = 1; row <= 5; row++) {

    let pattern = "";

    for (let column = 1; column <= row; column++) {

        pattern += "* ";

    }

    console.log(pattern);

}
```

Output:

```text
*
* *
* * *
* * * *
* * * * *
```

Pattern generation helps strengthen logical thinking and nested loop skills.

---

## Example 8: Processing Student Scores

Suppose a teacher wants to calculate the total score of a class.

```javascript
let scores = [75, 82, 90, 68, 85];

let total = 0;

for (let i = 0; i < scores.length; i++) {

    total += scores[i];

}

console.log("Total Score:", total);
```

Output:

```text
Total Score: 400
```

This same approach can be extended to calculate averages.

---

## Example 9: Simple Password Attempts

The following example simulates allowing three password attempts.

```javascript
let attempts = 1;

while (attempts <= 3) {

    console.log(`Attempt ${attempts}`);

    attempts++;

}

console.log("Maximum attempts reached.");
```

Output:

```text
Attempt 1
Attempt 2
Attempt 3
Maximum attempts reached.
```

Real authentication systems use a similar concept, although they involve user input and password validation.

---

## Example 10: Menu Simulation

```javascript
let option = 1;

do {

    console.log("Main Menu");

    option++;

} while (option <= 3);
```

Output:

```text
Main Menu
Main Menu
Main Menu
```

This demonstrates how a `do...while` loop ensures the menu is displayed before checking whether another iteration is needed.

---

## Lessons from These Examples

Although these programs are relatively simple, they demonstrate techniques that appear in professional software development.

Notice how loops are used to:

- Process collections of data.
- Perform repeated calculations.
- Search for information.
- Display structured output.
- Control repeated operations.
- Generate reports.
- Automate repetitive tasks.

As your programming skills grow, these same techniques will become building blocks for more advanced applications.

---

## Common Beginner Mistakes

When solving practical problems with loops, beginners often:

- Forget to initialize accumulator variables.
- Update the wrong variable.
- Use incorrect loop conditions.
- Forget to terminate loops.
- Choose the wrong loop type for the problem.
- Misplace `break` or `continue` statements.

Always test your program with small datasets before working with larger ones.

---

## Best Practices

When solving problems with loops:

- Break large problems into smaller steps.
- Choose descriptive variable names.
- Keep loop bodies focused on one task.
- Test your logic with simple examples.
- Use comments to explain complex sections.
- Review your loop conditions carefully.

These habits improve code quality and make debugging easier.

---

> **Figure 6.12**
>
> **Real-World Applications of Loops**
>
> *(Insert an illustration showing loops being used in different domains such as education, banking, e-commerce, gaming, and inventory management. Include icons connected to a central "Loop" concept.)*

---

> **CodeTales Insight**
>
> Professional software is built from simple programming techniques combined in powerful ways. The examples in this section may appear straightforward, but they represent the same logical patterns used in financial systems, social media platforms, e-commerce websites, scientific applications, and enterprise software. Mastering these fundamentals is the key to solving increasingly complex programming challenges.

---

## Section Summary

Practical programming involves applying loops to solve real-world problems rather than simply repeating code. In this section, you explored examples involving calculations, searching, filtering, countdowns, pattern generation, data processing, and menu systems. These examples demonstrate how loops form the foundation of many software applications and prepare you for more advanced programming concepts in later chapters.

In the next section, you will review the **best practices for writing efficient and readable loops**, helping you develop coding habits used by professional JavaScript developers.

## 6.13 Best Practices for Writing Loops

Writing a loop that works is only the first step.

Professional developers also strive to write loops that are:

- Correct
- Readable
- Efficient
- Easy to maintain
- Easy to debug

Following established best practices helps reduce errors, improve performance, and make your code easier for others—and your future self—to understand.

This section presents practical guidelines that every JavaScript programmer should follow when working with loops.

---

## 1. Choose the Right Loop

Different loops are designed for different situations.

Use:

- `for` when the number of iterations is known.
- `while` when repetition depends on a changing condition.
- `do...while` when the code must execute at least once.

Choosing the appropriate loop communicates your intent clearly.

Good example:

```javascript
for (let i = 1; i <= 10; i++) {
    console.log(i);
}
```

---

## 2. Use Meaningful Variable Names

Avoid vague variable names such as:

```javascript
let x;
let a;
let temp;
```

Instead, choose names that describe their purpose.

Better:

```javascript
for (let student = 1; student <= 30; student++) {
    console.log(student);
}
```

Descriptive names make programs easier to understand.

---

## 3. Keep Loop Bodies Simple

A loop should perform one primary task.

Avoid placing large amounts of unrelated code inside a single loop.

Poor example:

```javascript
for (...) {

    // Calculate salary

    // Print receipt

    // Send email

    // Save to database

    // Generate report

}
```

A better approach is to divide the work into separate functions.

---

## 4. Avoid Infinite Loops

Every loop should have a clear exit condition.

Always ask:

> **"What causes this loop to stop?"**

Ensure that:

- the loop variable changes,
- the condition eventually becomes `false`,
- and the update moves toward termination.

---

## 5. Avoid Unnecessary Nesting

Nested loops are sometimes necessary, but excessive nesting makes code difficult to read.

Instead of deeply nested loops:

```javascript
for (...) {

    for (...) {

        for (...) {

            // code

        }

    }

}
```

Consider breaking the logic into smaller functions when appropriate.

---

## 6. Use `break` and `continue` Carefully

These statements are powerful but should be used only when they improve clarity.

Example:

```javascript
for (let i = 1; i <= 10; i++) {

    if (i === 5) {

        break;

    }

    console.log(i);

}
```

Avoid overusing them, as excessive control flow changes can make loops difficult to follow.

---

## 7. Initialize Variables Properly

Accumulator variables should always be initialized.

Correct:

```javascript
let total = 0;
```

Incorrect:

```javascript
let total;

total += 5;
```

The second example produces unexpected results because `total` is `undefined`.

---

## 8. Avoid Repeating Expensive Operations

Suppose an array contains one thousand elements.

Less efficient:

```javascript
for (let i = 0; i < numbers.length; i++) {

    console.log(numbers[i]);

}
```

Although modern JavaScript engines optimize many cases, repeatedly evaluating complex expressions inside loops can still be inefficient.

If a value does not change, consider storing it before the loop.

Example:

```javascript
let length = numbers.length;

for (let i = 0; i < length; i++) {

    console.log(numbers[i]);

}
```

This technique can improve readability and may offer performance benefits in certain situations.

---

## 9. Test with Small Data Sets

Before processing thousands of records, test your loop with a few items.

Example:

Instead of testing:

```text
10,000 records
```

Start with:

```text
5 records
```

Smaller tests make errors easier to identify.

---

## 10. Add Comments When Necessary

Simple loops usually do not require comments.

However, complex logic benefits from explanation.

Example:

```javascript
// Skip inactive users

for (let i = 0; i < users.length; i++) {

    if (!users[i].active) {

        continue;

    }

}
```

Comments should explain **why** the code exists, not merely restate **what** it does.

---

## 11. Format Your Code Consistently

Consistent formatting improves readability.

Example:

```javascript
for (let i = 1; i <= 5; i++) {

    console.log(i);

}
```

Avoid inconsistent indentation.

Readable code reduces debugging time.

---

## 12. Think Before You Loop

Before writing a loop, ask yourself:

- What is the goal?
- Which loop is most appropriate?
- What causes the loop to stop?
- Do I need `break` or `continue`?
- Can the problem be simplified?

A few moments of planning often prevent hours of debugging.

---

## Professional Example

Suppose you need to process only active users.

```javascript
let users = [
    { name: "Alice", active: true },
    { name: "Brian", active: false },
    { name: "Grace", active: true }
];

for (let i = 0; i < users.length; i++) {

    if (!users[i].active) {

        continue;

    }

    console.log(users[i].name);

}
```

Output:

```text
Alice
Grace
```

Notice that:

- meaningful variable names are used,
- the logic is straightforward,
- inactive users are skipped,
- the code is easy to read.

---

## Common Beginner Mistakes

Avoid these common mistakes:

- Choosing the wrong loop type.
- Forgetting to update loop variables.
- Writing unnecessarily complex conditions.
- Using vague variable names.
- Creating deeply nested loops.
- Forgetting to initialize accumulators.
- Overusing `break` and `continue`.
- Ignoring code formatting.

Recognizing these mistakes early will help you become a more confident programmer.

---

## Checklist Before Finishing a Loop

Before considering a loop complete, verify that:

- ✅ The correct loop type was chosen.
- ✅ Variables are initialized.
- ✅ The condition is correct.
- ✅ The update is present.
- ✅ The loop eventually terminates.
- ✅ Variable names are meaningful.
- ✅ Formatting is consistent.
- ✅ The logic is easy to understand.

This checklist can save considerable debugging time.

---

> **Figure 6.13**
>
> **Professional Loop Writing Checklist**
>
> *(Insert an infographic showing a checklist with items such as Choose the Right Loop, Initialize Variables, Update Variables, Clear Exit Condition, Readable Names, Proper Formatting, and Test with Small Data Sets.)*

---

> **CodeTales Insight**
>
> Experienced developers understand that code is read far more often than it is written. A well-written loop should not only produce the correct result but also make its purpose immediately clear to anyone reading the program. Clear, maintainable code is a hallmark of professional software development.

---

## Section Summary

Writing effective loops involves more than making them work correctly. By choosing the appropriate loop type, using meaningful variable names, keeping loop bodies simple, preventing infinite loops, formatting code consistently, and testing thoroughly, you can create programs that are easier to understand, maintain, and extend. These best practices form the foundation of professional JavaScript programming and will serve you well throughout your software development journey.

In the next section, you will complete this chapter with a comprehensive review, helping you consolidate everything you have learned about loops before moving on to the next topic.

# 6.14 Chapter Summary

In this chapter, you explored one of the most powerful concepts in programming: **loops**. Loops allow programs to execute a block of code repeatedly, eliminating unnecessary repetition and enabling developers to solve complex problems efficiently.

You began by learning why loops are important and how they help automate repetitive tasks. Instead of writing the same statements multiple times, you discovered how a loop can perform the work with a concise and organized structure.

Next, you examined the three primary looping constructs in JavaScript:

- The **`for` loop**, which is best suited for situations where the number of iterations is known in advance.
- The **`while` loop**, which continues executing as long as a specified condition remains true.
- The **`do...while` loop**, which guarantees that the loop body executes at least once before the condition is evaluated.

You also learned the anatomy of a loop, including:

- Initialization
- Condition
- Update
- Loop body

Understanding these four components helps you design loops that are both correct and efficient.

As the chapter progressed, you explored nested loops and saw how one loop can exist inside another to solve more complex problems, such as generating tables, processing rows and columns, and creating visual patterns.

You then learned how to control loop execution using the **`break`** and **`continue`** statements. The `break` statement immediately terminates a loop, while the `continue` statement skips the current iteration and proceeds to the next one. These control statements provide greater flexibility when solving real-world programming problems.

Another important topic was **infinite loops**. You discovered how they occur, why they are problematic, and how careful planning of loop conditions and updates prevents programs from running indefinitely. You also learned that some infinite loops are intentional and are used in applications such as web servers, operating systems, and game engines.

The chapter also introduced common looping patterns, including:

- Counting
- Accumulating totals
- Searching
- Filtering
- Finding maximum and minimum values
- Processing collections
- Generating patterns

These patterns form the foundation of countless software applications and are used across virtually every programming language.

Through practical examples, you applied these concepts to solve realistic problems involving calculations, searching, countdowns, menu systems, pattern generation, and data processing. These exercises demonstrated how loops are used in everyday software development.

Finally, you explored professional best practices for writing loops. You learned the importance of selecting the appropriate loop type, using meaningful variable names, writing clear conditions, avoiding unnecessary complexity, preventing infinite loops, and testing your code carefully.

By mastering the concepts in this chapter, you have developed the ability to write programs that automate repetitive tasks efficiently and accurately. Loops are one of the fundamental building blocks of programming, and they will appear repeatedly throughout the remainder of this book.

As you continue your JavaScript journey, you will build upon these skills to work with arrays, objects, functions, the Document Object Model (DOM), asynchronous programming, and many other advanced topics. A solid understanding of loops will make these future concepts much easier to learn and apply.

---

## Key Takeaways

After completing this chapter, you should be able to:

- Explain the purpose and benefits of loops.
- Differentiate between `for`, `while`, and `do...while` loops.
- Identify the four essential components of a loop.
- Write `for`, `while`, and `do...while` loops correctly.
- Create nested loops to solve multidimensional problems.
- Use the `break` and `continue` statements appropriately.
- Recognize and prevent infinite loops.
- Apply common looping patterns such as counting, accumulating, searching, and filtering.
- Solve practical programming problems using loops.
- Follow professional best practices for writing readable and maintainable loops.

---

> **Figure 6.14**
>
> **Chapter 6 Mind Map**
>
> *(Insert a concept map with "Loops" at the center. Branches should include `for`, `while`, `do...while`, Nested Loops, `break`, `continue`, Infinite Loops, Looping Patterns, Practical Examples, and Best Practices. This visual serves as a one-page recap of the entire chapter.)*

---

> **CodeTales Insight**
>
> Every experienced programmer reaches a point where loops become second nature. Instead of thinking about the syntax, they focus on solving problems. That is the goal of this chapter—not simply to memorize loop structures, but to develop the ability to recognize repetition, choose the appropriate loop, and express solutions clearly. These skills will continue to grow as you tackle larger and more challenging programming projects throughout this book.

# Key Terms

The following terms were introduced or reinforced in this chapter. Understanding these concepts will help you read, write, and discuss JavaScript programs more confidently.

---

## Accumulator

A variable that stores a running total as a loop executes.

Example:

```javascript
let total = 0;

for (let i = 1; i <= 5; i++) {
    total += i;
}
```

---

## Body of a Loop

The block of code that executes repeatedly while the loop is running.

Example:

```javascript
for (let i = 1; i <= 3; i++) {

    console.log(i);

}
```

The statement:

```javascript
console.log(i);
```

is the loop body.

---

## `break`

A loop control statement that immediately terminates the current loop.

Example:

```javascript
if (score === 100) {
    break;
}
```

---

## Condition

A logical expression that determines whether a loop should continue executing.

Example:

```javascript
i <= 10
```

---

## `continue`

A loop control statement that skips the current iteration and proceeds to the next iteration.

Example:

```javascript
if (number % 2 === 0) {
    continue;
}
```

---

## Counter

A variable used to keep track of the number of loop iterations.

Example:

```javascript
let count = 1;
```

---

## `do...while` Loop

A loop that executes its body first and checks its condition afterward.

It always runs at least once.

---

## Filtering

Selecting only the data that satisfies a specified condition.

Example:

Displaying only students who passed an examination.

---

## `for` Loop

A loop commonly used when the number of iterations is known before execution begins.

Example:

```javascript
for (let i = 1; i <= 10; i++) {

    console.log(i);

}
```

---

## Infinite Loop

A loop that never terminates because its condition never becomes false.

Example:

```javascript
while (true) {

    console.log("Running");

}
```

---

## Initialization

The step where loop variables receive their starting values before the first iteration.

Example:

```javascript
let i = 1;
```

---

## Iteration

A single execution of a loop body.

If a loop runs five times, it performs five iterations.

---

## Loop

A programming structure that repeatedly executes a block of code while a specified condition remains true.

---

## Loop Body

The collection of statements repeated during each iteration of a loop.

---

## Loop Control Statement

A statement that changes the normal execution of a loop.

Examples include:

- `break`
- `continue`

---

## Loop Variable

A variable whose value changes during each iteration and helps control the loop.

Example:

```javascript
for (let i = 0; i < 5; i++)
```

The variable:

```javascript
i
```

is the loop variable.

---

## Nested Loop

A loop contained inside another loop.

Nested loops are commonly used for:

- Tables
- Grids
- Pattern generation
- Matrix processing

---

## Pattern Generation

Using loops to create repeated visual output.

Example:

```text
*
* *
* * *
```

---

## Searching

Using a loop to locate a particular value within a collection of data.

---

## Termination Condition

The condition that causes a loop to stop executing.

---

## Update Expression

The statement that changes the loop variable after each iteration.

Example:

```javascript
i++
```

---

## `while` Loop

A loop that evaluates its condition before executing the loop body.

If the condition is initially false, the loop body never executes.

---

## Quick Reference Table

| Term | Meaning |
|------|---------|
| Loop | Repeats code |
| Iteration | One execution of a loop |
| Counter | Tracks loop progress |
| Initialization | Starting value |
| Condition | Determines whether the loop continues |
| Update | Changes the loop variable |
| `for` | Best when the number of iterations is known |
| `while` | Best when repetition depends on a condition |
| `do...while` | Executes at least once |
| `break` | Exits a loop immediately |
| `continue` | Skips the current iteration |
| Infinite Loop | A loop that never ends |
| Nested Loop | A loop inside another loop |
| Accumulator | Stores a running total |
| Searching | Finds a value |
| Filtering | Selects values that meet a condition |
| Pattern Generation | Creates repeated visual output |

---

> **CodeTales Tip**
>
> Programming is much easier when you understand the language developers use. Review these key terms regularly. As you continue through this book, you'll encounter them repeatedly in discussions about arrays, functions, objects, algorithms, and data structures. Becoming comfortable with this vocabulary will make learning advanced JavaScript concepts significantly easier.

# Review Questions

Use the following questions to test your understanding of the concepts covered in this chapter. Try to answer them without referring back to the chapter. If you find any question difficult, revisit the relevant section before continuing.

---

## Part A: Multiple Choice Questions

Choose the best answer for each question.

### 1. What is the primary purpose of a loop?

A. To store data

B. To repeat a block of code

C. To declare variables

D. To create functions

---

### 2. Which loop is most appropriate when you know the exact number of iterations?

A. `while`

B. `do...while`

C. `for`

D. `switch`

---

### 3. Which loop always executes its body at least once?

A. `for`

B. `while`

C. `do...while`

D. None of the above

---

### 4. Which statement immediately terminates a loop?

A. `continue`

B. `return`

C. `break`

D. `stop`

---

### 5. Which statement skips the current iteration and continues with the next one?

A. `break`

B. `continue`

C. `exit`

D. `skip`

---

### 6. Which component of a loop determines whether the loop continues?

A. Initialization

B. Update

C. Condition

D. Counter

---

### 7. Which of the following is an example of an accumulator?

A.

```javascript
let total = 0;
```

B.

```javascript
let name = "John";
```

C.

```javascript
const PI = 3.14;
```

D.

```javascript
let city = "Lagos";
```

---

### 8. What is an infinite loop?

A. A loop that runs only once

B. A loop that never stops

C. A loop inside another loop

D. A loop that contains a function

---

### 9. What is a nested loop?

A. A loop with multiple conditions

B. A loop inside another loop

C. A loop without a condition

D. A loop that uses `break`

---

### 10. Which loop is generally preferred when processing a known range of numbers?

A. `while`

B. `do...while`

C. `for`

D. `switch`

---

## Part B: Short Answer Questions

Answer each question in one or two sentences.

1. What is a loop?

2. Why are loops important in programming?

3. What are the four main components of a `for` loop?

4. What is the difference between a `while` loop and a `do...while` loop?

5. Explain the purpose of the `break` statement.

6. Explain the purpose of the `continue` statement.

7. What causes an infinite loop?

8. What is the role of a loop variable?

9. What is an accumulator?

10. Why are meaningful variable names important?

---

## Part C: Explain the Difference

Briefly explain the difference between the following pairs.

1. `for` loop vs. `while` loop

2. `while` loop vs. `do...while` loop

3. `break` vs. `continue`

4. Counter vs. accumulator

5. Searching vs. filtering

6. Condition vs. update expression

---

## Part D: Predict the Output

Without running the code, determine the output.

### 1.

```javascript
for (let i = 1; i <= 3; i++) {
    console.log(i);
}
```

---

### 2.

```javascript
let i = 3;

while (i > 0) {
    console.log(i);
    i--;
}
```

---

### 3.

```javascript
for (let i = 1; i <= 5; i++) {

    if (i === 3) {
        break;
    }

    console.log(i);

}
```

---

### 4.

```javascript
for (let i = 1; i <= 5; i++) {

    if (i === 3) {
        continue;
    }

    console.log(i);

}
```

---

### 5.

```javascript
let number = 5;

do {

    console.log(number);

} while (number < 5);
```

---

## Part E: Find the Error

Identify and correct the mistake.

### 1.

```javascript
let count = 1;

while (count <= 5) {

    console.log(count);

}
```

---

### 2.

```javascript
for (let i = 1; i <= 5;) {

    console.log(i);

}
```

---

### 3.

```javascript
let total;

for (let i = 1; i <= 5; i++) {

    total += i;

}
```

---

### 4.

```javascript
let number = 10;

while (number >= 1) {

    console.log(number);

    number++;

}
```

---

### 5.

```javascript
do {

    console.log("Hello");

} while (false)
```

---

## Part F: Reflection Questions

These questions encourage deeper thinking about how loops are used in software development.

1. Why is choosing the correct loop important?

2. How can poorly written loops affect software performance?

3. Why do professional developers value readable loops?

4. In what real-world situations would you use a `do...while` loop?

5. How can testing with small datasets help prevent programming errors?

6. Why is it important to avoid infinite loops?

7. Which looping pattern do you think is used most frequently in business software? Explain your answer.

8. How might loops be used in a banking application?

9. How could loops improve the efficiency of an inventory management system?

10. Which topic in this chapter did you find most interesting, and why?

---

> **CodeTales Reflection**
>
> Understanding loops is not just about memorizing syntax. It is about developing the ability to recognize repetition in real-world problems and expressing those solutions clearly through code. As you continue learning JavaScript, you'll discover that loops are everywhere—from processing arrays and handling user input to managing data and powering complex applications.

# Hands-on Exercises

The following exercises are designed to help you apply the concepts learned in this chapter. Complete each exercise by writing and testing your own JavaScript code.

Work through the exercises in order. Each one builds upon the skills developed in the previous exercises.

---

# Beginner Exercises

### Exercise 1: Print Numbers

Write a `for` loop that displays the numbers from **1 to 20**.

Expected Output:

```text
1
2
3
...
20
```

---

### Exercise 2: Even Numbers

Display all even numbers between **1 and 50**.

---

### Exercise 3: Odd Numbers

Display all odd numbers between **1 and 50**.

---

### Exercise 4: Countdown

Use a `while` loop to display a countdown from **20 to 1**.

After the countdown, display:

```text
Lift Off!
```

---

### Exercise 5: Multiplication Table

Write a program that displays the multiplication table for **9**.

Example:

```text
9 × 1 = 9

9 × 2 = 18

...

9 × 12 = 108
```

---

# Intermediate Exercises

### Exercise 6: Sum of Numbers

Calculate the sum of all numbers from **1 to 100**.

Display the result.

---

### Exercise 7: Factorial

Write a program that calculates:

```text
5!
```

Expected Output:

```text
120
```

*Hint:* Use a loop and an accumulator variable.

---

### Exercise 8: Count Multiples

Display how many numbers between **1 and 100** are divisible by **3**.

---

### Exercise 9: Largest Number

Given the following array:

```javascript
let numbers = [45, 72, 18, 91, 63, 27];
```

Write a program to determine the largest value.

---

### Exercise 10: Smallest Number

Using the same array, determine the smallest value.

---

# Loop Control Exercises

### Exercise 11: Skip Multiples of Five

Display the numbers from **1 to 30**.

Skip every number that is divisible by **5**.

Use:

```javascript
continue
```

---

### Exercise 12: Stop at 25

Display numbers beginning at **1**.

Stop the loop immediately when the number reaches **25**.

Use:

```javascript
break
```

---

### Exercise 13: Password Attempts

Simulate three password attempts using a loop.

Display:

```text
Attempt 1

Attempt 2

Attempt 3

Access Denied
```

---

# Nested Loop Exercises

### Exercise 14: Square Pattern

Produce the following output:

```text
* * * *

* * * *

* * * *

* * * *
```

---

### Exercise 15: Right Triangle

Produce:

```text
*

* *

* * *

* * * *

* * * * *
```

---

### Exercise 16: Number Triangle

Produce:

```text
1

1 2

1 2 3

1 2 3 4

1 2 3 4 5
```

---

# Problem-Solving Exercises

### Exercise 17: Sum of Even Numbers

Calculate the sum of all even numbers from **1 to 100**.

---

### Exercise 18: Sum of Odd Numbers

Calculate the sum of all odd numbers from **1 to 100**.

---

### Exercise 19: Count Positive Numbers

Given:

```javascript
let numbers = [-2, 8, -5, 14, 0, 11, -9];
```

Count how many numbers are positive.

---

### Exercise 20: Count Negative Numbers

Using the same array, count how many numbers are negative.

---

# Real-World Exercises

### Exercise 21: Student Grades

The following scores are stored in an array:

```javascript
let scores = [82, 65, 91, 47, 76, 88, 59];
```

Write a program that:

- Calculates the total score.
- Calculates the average score.
- Displays the highest score.
- Displays the lowest score.

---

### Exercise 22: Inventory Search

Given:

```javascript
let products = [
    "Laptop",
    "Keyboard",
    "Mouse",
    "Printer",
    "Monitor"
];
```

Determine whether:

```text
Printer
```

exists in the array.

Display:

```text
Product Found
```

or

```text
Product Not Found
```

---

### Exercise 23: Employee IDs

Display employee IDs from:

```text
EMP001
```

to

```text
EMP100
```

---

### Exercise 24: ATM Simulation

Simulate an ATM that allows a maximum of **three PIN attempts**.

Display each attempt number.

After the third unsuccessful attempt, display:

```text
Card Blocked
```

---

### Exercise 25: Restaurant Menu

Use a `do...while` loop to simulate displaying a restaurant menu until the customer chooses to exit.

For this exercise, you may simulate the customer's choice using a variable.

---

# Challenge Exercises

### Exercise 26

Print all numbers between **1 and 100** that are divisible by both **3** and **5**.

---

### Exercise 27

Calculate the sum of the squares of the numbers from **1 to 20**.

---

### Exercise 28

Reverse Countdown

Display:

```text
100

90

80

70

...

10

0
```

---

### Exercise 29

Generate the following pattern:

```text
1

2 2

3 3 3

4 4 4 4

5 5 5 5 5
```

---

### Exercise 30

Write a program that counts how many vowels appear in the following string:

```javascript
"JavaScript Programming"
```

---

# Reflection Activity

After completing the exercises, answer the following questions in your own words.

1. Which exercise did you find the easiest?

2. Which exercise challenged you the most?

3. Which type of loop did you use most frequently?

4. Did you use `break` or `continue` in any solution? Why?

5. Which looping pattern appeared most often?

6. If you repeated these exercises one month from now, which would you expect to solve more quickly?

7. Which real-world application of loops interests you most?

8. What is one thing you learned from making mistakes during these exercises?

---

> **CodeTales Practice Tip**
>
> Reading code helps you understand programming, but writing code builds programming skill. Do not simply read these exercises—type each solution yourself, run it, experiment with different inputs, and observe the results. The more you practice, the more naturally loops will become part of your problem-solving toolkit.

# Coding Challenges

The following challenges are designed to strengthen your problem-solving skills. Unlike the Hands-on Exercises, these activities provide fewer hints and encourage you to plan your own solutions.

Think carefully before writing code. Break each problem into smaller steps, test your logic with simple examples, and refine your solution as needed.

---

# Challenge 1: FizzBuzz

Write a program that displays the numbers from **1 to 100**.

However:

- Display **"Fizz"** for numbers divisible by **3**.
- Display **"Buzz"** for numbers divisible by **5**.
- Display **"FizzBuzz"** for numbers divisible by **both 3 and 5**.
- Otherwise, display the number itself.

Example (partial output):

```text
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
FizzBuzz
```

---

# Challenge 2: Prime Number Detector

Write a program that determines whether a given number is prime.

Example:

```text
Input:
29

Output:
29 is a prime number.
```

Test your program with several values, including:

- 2
- 7
- 10
- 17
- 25
- 31

---

# Challenge 3: Multiplication Tables

Generate multiplication tables from **1 to 12**.

Each table should contain values from **1 × 1** through **12 × 12**.

Use nested loops.

---

# Challenge 4: Number Guessing Simulation

Simulate a simple guessing game.

Requirements:

- Store a secret number in a variable.
- Use a loop to simulate repeated guesses.
- Stop when the correct guess is reached.
- Display the number of attempts.

You may simulate the guesses using predefined values.

---

# Challenge 5: Student Result Analysis

Given:

```javascript
let scores = [78, 91, 64, 88, 55, 72, 96, 81];
```

Write a program that displays:

- Highest score
- Lowest score
- Average score
- Number of passing students (50 or above)
- Number of failing students

---

# Challenge 6: Inventory Report

Given:

```javascript
let stock = [12, 0, 18, 5, 0, 27, 3, 14];
```

Display:

- Total number of products
- Number of out-of-stock products
- Number of products currently available
- Total stock quantity

---

# Challenge 7: Pyramid Pattern

Generate the following pattern:

```text
        *
       ***
      *****
     *******
    *********
```

Use nested loops.

---

# Challenge 8: Reverse a String

Given:

```javascript
let word = "JavaScript";
```

Write a program that prints the characters in reverse order.

Expected output:

```text
tpircSavaJ
```

Do not use the built-in `reverse()` method.

---

# Challenge 9: Password Validator Simulation

Simulate a login system.

Requirements:

- Allow a maximum of **three attempts**.
- Display the attempt number.
- Stop immediately if the correct password is entered.
- Display **"Access Granted"** or **"Account Locked"**.

You may simulate password entries using variables.

---

# Challenge 10: Character Counter

Given:

```javascript
let sentence = "Learning JavaScript is fun!";
```

Count:

- Total characters
- Total spaces
- Total vowels
- Total consonants

Display all four values.

---

# Bonus Challenge 1: Chessboard Pattern

Generate an **8 × 8** chessboard pattern using nested loops.

Example:

```text
# # # # # # # #

 # # # # # # # #

# # # # # # # #

 # # # # # # # #
```

Use alternating characters to represent the board.

---

# Bonus Challenge 2: Multiplication Grid

Display a formatted multiplication grid for the numbers **1 through 10**.

Example:

```text
1   2   3   4 ...

2   4   6   8 ...

3   6   9  12 ...
```

Ensure the output is neatly aligned.

---

# Bonus Challenge 3: Number Statistics

Generate the numbers from **1 to 100**.

Display:

- Count of even numbers
- Count of odd numbers
- Sum of even numbers
- Sum of odd numbers
- Largest number
- Smallest number

---

# Thinking Like a Programmer

Before writing your solution, ask yourself:

1. What is the problem asking me to do?
2. Which loop is most appropriate?
3. Will I need nested loops?
4. Do I need an accumulator?
5. Will `break` or `continue` simplify the solution?
6. How can I test my program with small values first?

Planning your approach before coding often leads to simpler and more reliable solutions.

---

# Self-Evaluation Checklist

After completing each challenge, verify that:

- ✅ The program produces the correct output.
- ✅ Variables have meaningful names.
- ✅ The loop terminates correctly.
- ✅ The code is properly indented.
- ✅ Unnecessary repetition has been avoided.
- ✅ The solution is easy to read.
- ✅ Edge cases have been considered.

---

> **CodeTales Challenge Tip**
>
> Don't be discouraged if you cannot solve every challenge on your first attempt. Professional developers frequently experiment, debug, and revise their solutions before arriving at the final version. The goal is not perfection on the first try—it is to strengthen your ability to analyze problems, develop logical solutions, and improve through practice.

# Mini Project

# Student Grade Analyzer

## Project Overview

In this project, you will build a simple **Student Grade Analyzer** using the looping concepts learned in this chapter.

The program will process a list of student scores and generate a summary report.

Although the project is relatively small, it introduces the same logical thinking used in school management systems, examination software, and educational platforms.

---

# Project Objectives

By completing this project, you will practice how to:

- Use loops to process data
- Traverse an array
- Use accumulators
- Find the highest score
- Find the lowest score
- Count passing students
- Count failing students
- Calculate an average
- Produce formatted output

---

# Scenario

A teacher has recorded the following student scores:

```javascript
let scores = [
    75,
    82,
    61,
    95,
    48,
    73,
    89,
    54,
    67,
    91
];
```

Your task is to write a program that analyzes these scores.

---

# Program Requirements

Your program should display:

### 1. Total Number of Students

Example:

```text
10
```

---

### 2. Highest Score

Example:

```text
95
```

---

### 3. Lowest Score

Example:

```text
48
```

---

### 4. Total Score

Example:

```text
735
```

---

### 5. Average Score

Display the average score.

---

### 6. Number of Passing Students

Assume:

```text
Pass Mark = 50
```

---

### 7. Number of Failing Students

Students scoring below 50 are considered to have failed.

---

### 8. Display All Scores

Example:

```text
Student 1: 75

Student 2: 82

Student 3: 61
...
```

---

# Expected Output

A possible output is shown below.

```text
========== STUDENT REPORT ==========

Total Students: 10

Highest Score: 95

Lowest Score: 48

Total Score: 735

Average Score: 73.5

Passed: 9

Failed: 1

------------ Scores ------------

Student 1: 75

Student 2: 82

Student 3: 61

...

===================================
```

Your formatting does not have to match this example exactly, but all required information should be displayed clearly.

---

# Suggested Steps

If you are unsure where to begin, follow this plan.

### Step 1

Create the array.

---

### Step 2

Initialize variables.

Example:

```javascript
let total = 0;

let highest = scores[0];

let lowest = scores[0];

let passed = 0;

let failed = 0;
```

---

### Step 3

Loop through the array.

---

### Step 4

Inside the loop:

- Update the total.
- Check for highest score.
- Check for lowest score.
- Count passing students.
- Count failing students.

---

### Step 5

Calculate the average.

---

### Step 6

Display the report.

---

# Extension Activities

Once your program works correctly, try adding the following features.

### Extension 1

Display the class grade.

Example:

```text
Average >= 70

Excellent Class
```

---

### Extension 2

Display the names of students instead of numbers.

Example:

```javascript
let students = [
    "Alice",
    "David",
    "Grace",
    "John"
];
```

---

### Extension 3

Display the grade for each score.

Example:

```text
90–100 → A

80–89 → B

70–79 → C

60–69 → D

Below 60 → F
```

---

### Extension 4

Display only students who passed.

---

### Extension 5

Display only students who scored above the class average.

---

# Skills Used

This project combines many concepts from this chapter.

- Variables
- Arrays
- `for` loops
- Conditional statements
- Comparison operators
- Accumulators
- Searching
- Counting
- Maximum and minimum values
- Formatted output

---

# Common Mistakes

While completing this project, watch out for these common errors.

- Forgetting to initialize variables.
- Starting the loop at the wrong index.
- Using the wrong comparison operator.
- Dividing by the wrong number when calculating the average.
- Forgetting to update the highest or lowest score.
- Miscounting passing and failing students.

Test your program carefully.

---

# Challenge Yourself

Can you modify the program to:

- Analyze **100 students** instead of 10?
- Accept different passing scores?
- Count grades A, B, C, D, and F?
- Display the percentage of students who passed?
- Identify students with the top three scores?

These improvements are excellent preparation for later chapters.

---

> **CodeTales Project Insight**
>
> This project demonstrates how several simple programming concepts can be combined to solve a practical problem. Professional software is rarely built from one advanced idea; instead, it is created by combining fundamental techniques—such as loops, variables, conditionals, and arrays—in a logical and organized way. As your knowledge grows, you'll continue building larger applications using the same principles introduced here.

# Chapter Quiz

**Instructions**

- Answer all questions without referring to the chapter.
- Choose the **one best answer** for each question.
- Each question carries **1 mark**.
- Total: **30 marks**

---

## Multiple-Choice Questions

### 1. What is the main purpose of a loop?

A. To create variables

B. To repeat a block of code

C. To define functions

D. To store arrays

---

### 2. Which loop is best when the number of iterations is known?

A. `while`

B. `do...while`

C. `for`

D. `switch`

---

### 3. Which loop guarantees that its body executes at least once?

A. `for`

B. `while`

C. `do...while`

D. `if`

---

### 4. Which part of a `for` loop is evaluated before each iteration?

A. Initialization

B. Update expression

C. Condition

D. Loop body

---

### 5. Which statement immediately exits a loop?

A. `continue`

B. `break`

C. `return`

D. `stop`

---

### 6. Which statement skips the remainder of the current iteration?

A. `continue`

B. `break`

C. `exit`

D. `return`

---

### 7. What is an iteration?

A. A variable declaration

B. A single execution of the loop body

C. A function call

D. An array element

---

### 8. Which variable is commonly used to store a running total?

A. Counter

B. Constant

C. Accumulator

D. Index

---

### 9. Which of the following can cause an infinite loop?

A. Updating the loop variable correctly

B. Forgetting to update the loop variable

C. Using meaningful variable names

D. Initializing variables

---

### 10. Which loop is most suitable when the stopping condition depends on user input?

A. `for`

B. `while`

C. `switch`

D. `if`

---

### 11. A loop inside another loop is called a:

A. Conditional loop

B. Nested loop

C. Infinite loop

D. Recursive loop

---

### 12. Which operator is commonly used to increment a counter?

A. `--`

B. `+=`

C. `++`

D. `==`

---

### 13. Which keyword starts a `while` loop?

A. `loop`

B. `repeat`

C. `while`

D. `iterate`

---

### 14. Which keyword starts a `do...while` loop?

A. `repeat`

B. `loop`

C. `do`

D. `start`

---

### 15. Which loop is often preferred for traversing arrays using an index?

A. `for`

B. `while`

C. `do...while`

D. `switch`

---

### 16. Which of the following is a valid `for` loop update expression?

A. `i++`

B. `i==`

C. `i===`

D. `i&&`

---

### 17. What is the purpose of the loop condition?

A. To declare variables

B. To determine whether the loop continues

C. To print output

D. To define functions

---

### 18. Which looping pattern is used to compute a total?

A. Filtering

B. Searching

C. Accumulating

D. Sorting

---

### 19. Which looping pattern is used to locate a specific value?

A. Counting

B. Searching

C. Pattern generation

D. Accumulating

---

### 20. What is the output of the following code?

```javascript
for (let i = 1; i <= 3; i++) {
    console.log(i);
}
```

A.

```text
1
2
3
```

B.

```text
0
1
2
```

C.

```text
1
2
```

D.

```text
3
2
1
```

---

### 21. What happens if the condition in a `while` loop is initially false?

A. The loop runs once.

B. The loop runs twice.

C. The loop body does not execute.

D. An error occurs.

---

### 22. Which statement about `do...while` is true?

A. The condition is checked before the loop body.

B. The loop body always executes at least once.

C. It cannot contain `break`.

D. It cannot contain `continue`.

---

### 23. Which practice improves loop readability?

A. Using single-letter variable names everywhere

B. Writing long, complex conditions

C. Using meaningful variable names

D. Omitting indentation

---

### 24. Why should you test loops with small datasets first?

A. To reduce debugging time

B. To make the code longer

C. To increase memory usage

D. To avoid using variables

---

### 25. Which statement is true about `break`?

A. It skips only the current iteration.

B. It exits the loop immediately.

C. It restarts the loop.

D. It changes the loop condition.

---

### 26. Which statement is true about `continue`?

A. It exits the loop.

B. It skips the current iteration.

C. It stops the program.

D. It resets the loop variable.

---

### 27. Which of the following is an example of filtering?

A. Printing only even numbers

B. Calculating a total

C. Displaying every item

D. Finding the largest value

---

### 28. Which looping pattern is commonly used to create star patterns?

A. Counting

B. Searching

C. Nested loops

D. Filtering

---

### 29. What is the greatest advantage of loops?

A. They eliminate all programming errors.

B. They reduce repetitive code.

C. They replace variables.

D. They eliminate conditions.

---

### 30. Which statement best summarizes this chapter?

A. Loops are useful only for mathematical calculations.

B. Loops automate repetitive tasks and are fundamental to programming.

C. Loops replace arrays and functions.

D. Loops are used only in games.

---

# Scoring Guide

| Score | Performance |
|--------|-------------|
| **27–30** | Excellent – You have a strong understanding of JavaScript loops. |
| **23–26** | Very Good – You understand the concepts well with only minor gaps. |
| **18–22** | Good – Review a few topics before moving to the next chapter. |
| **12–17** | Fair – Revisit the chapter and complete more exercises. |
| **0–11** | Needs Improvement – Study the chapter again and practice the Hands-on Exercises before continuing. |

---

> **CodeTales Assessment Tip**
>
> A quiz measures what you remember at a particular moment, but real programming ability comes from consistent practice. If you miss a question, don't simply memorize the correct answer. Revisit the concept, write a small program that demonstrates it, and explain it in your own words. Understanding is far more valuable than memorization.

# Answers to Selected Exercises

This section provides answers to selected review questions, quiz questions, and programming exercises. Use these solutions to verify your understanding after attempting the questions on your own.

> **Important:** Try every question before consulting the answers. Learning happens through the process of thinking, experimenting, and debugging.

---

# Part A – Review Questions (Selected Answers)

### 1. What is a loop?

**Answer:**

A loop is a programming structure that repeatedly executes a block of code while a specified condition is true or until a stopping condition is reached.

---

### 2. Why are loops important?

**Answer:**

Loops eliminate repetitive code, automate repetitive tasks, improve program efficiency, and make programs easier to maintain.

---

### 3. What are the four components of a `for` loop?

**Answer:**

- Initialization
- Condition
- Update expression
- Loop body

---

### 4. Difference between `while` and `do...while`

**Answer:**

A `while` loop checks its condition before executing the loop body, while a `do...while` loop executes the body first and checks the condition afterward. Therefore, a `do...while` loop always runs at least once.

---

### 5. Purpose of `break`

**Answer:**

The `break` statement immediately terminates the current loop.

---

### 6. Purpose of `continue`

**Answer:**

The `continue` statement skips the remainder of the current iteration and proceeds to the next iteration.

---

# Part B – Predict the Output

### Question 1

```javascript
for (let i = 1; i <= 3; i++) {
    console.log(i);
}
```

**Output**

```text
1
2
3
```

---

### Question 2

```javascript
let i = 3;

while (i > 0) {
    console.log(i);
    i--;
}
```

**Output**

```text
3
2
1
```

---

### Question 3

```javascript
for (let i = 1; i <= 5; i++) {

    if (i === 3) {
        break;
    }

    console.log(i);

}
```

**Output**

```text
1
2
```

---

### Question 4

```javascript
for (let i = 1; i <= 5; i++) {

    if (i === 3) {
        continue;
    }

    console.log(i);

}
```

**Output**

```text
1
2
4
5
```

---

### Question 5

```javascript
let number = 5;

do {

    console.log(number);

} while (number < 5);
```

**Output**

```text
5
```

---

# Part C – Find the Error

### Question 1

**Incorrect**

```javascript
let count = 1;

while (count <= 5) {

    console.log(count);

}
```

**Problem**

The loop variable is never updated, causing an infinite loop.

**Correct**

```javascript
let count = 1;

while (count <= 5) {

    console.log(count);

    count++;

}
```

---

### Question 2

**Incorrect**

```javascript
for (let i = 1; i <= 5;) {

    console.log(i);

}
```

**Problem**

The update expression is missing.

**Correct**

```javascript
for (let i = 1; i <= 5; i++) {

    console.log(i);

}
```

---

### Question 3

**Incorrect**

```javascript
let total;

for (let i = 1; i <= 5; i++) {

    total += i;

}
```

**Problem**

`total` is undefined.

**Correct**

```javascript
let total = 0;

for (let i = 1; i <= 5; i++) {

    total += i;

}
```

---

# Selected Hands-on Exercises

## Exercise 1

```javascript
for (let i = 1; i <= 20; i++) {

    console.log(i);

}
```

---

## Exercise 2

```javascript
for (let i = 2; i <= 50; i += 2) {

    console.log(i);

}
```

---

## Exercise 6

```javascript
let total = 0;

for (let i = 1; i <= 100; i++) {

    total += i;

}

console.log(total);
```

---

## Exercise 7

```javascript
let factorial = 1;

for (let i = 1; i <= 5; i++) {

    factorial *= i;

}

console.log(factorial);
```

**Output**

```text
120
```

---

## Exercise 11

```javascript
for (let i = 1; i <= 30; i++) {

    if (i % 5 === 0) {

        continue;

    }

    console.log(i);

}
```

---

## Exercise 12

```javascript
for (let i = 1; i <= 30; i++) {

    if (i === 25) {

        break;

    }

    console.log(i);

}
```

---

# Selected Coding Challenge Hints

## Challenge 1 – FizzBuzz

Think about the order of your conditions.

Check:

```text
Divisible by both 3 and 5
```

before checking:

```text
Divisible by 3
```

or

```text
Divisible by 5
```

---

## Challenge 2 – Prime Number

A number is prime if it has exactly two positive divisors:

- 1
- itself

Use a loop to test divisibility from `2` up to the square root of the number.

---

## Challenge 7 – Pyramid Pattern

Hint:

Use:

- one loop for spaces
- one loop for stars

This is a classic nested loop problem.

---

# Chapter Quiz Answer Key

| Question | Answer | Question | Answer |
|-----------|:------:|-----------|:------:|
| 1 | B | 16 | A |
| 2 | C | 17 | B |
| 3 | C | 18 | C |
| 4 | C | 19 | B |
| 5 | B | 20 | A |
| 6 | A | 21 | C |
| 7 | B | 22 | B |
| 8 | C | 23 | C |
| 9 | B | 24 | A |
| 10 | B | 25 | B |
| 11 | B | 26 | B |
| 12 | C | 27 | A |
| 13 | C | 28 | C |
| 14 | C | 29 | B |
| 15 | A | 30 | B |

---

# Final Words

Congratulations!

You have successfully completed **Chapter 6: Loops and Iteration**. By working through the explanations, examples, exercises, coding challenges, mini project, and assessments, you have built a strong foundation in one of the most important concepts in programming.

Loops are used in almost every software application—from processing user input and managing data to powering games, websites, financial systems, and artificial intelligence. The skills you developed in this chapter will continue to appear throughout the remainder of this book.

As you move forward, remember that mastering programming is not about memorizing syntax—it is about learning to think logically, solve problems systematically, and improve through consistent practice.

Keep experimenting, keep building, and keep writing code. Every program you create brings you one step closer to becoming a confident and professional JavaScript developer.

Happy coding!

— **The CodeTales Africa Team**
