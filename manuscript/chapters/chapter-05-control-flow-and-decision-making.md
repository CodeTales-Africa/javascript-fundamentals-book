# Chapter 5: Control Flow and Decision-Making in JavaScript

## 5.1 Introduction to Control Flow

Imagine you are approaching a traffic light while driving. If the light is green, you continue driving. If it is yellow, you slow down and prepare to stop. If it is red, you stop and wait until it changes. Each action depends on a specific condition.

Computer programs behave in much the same way. Rather than making decisions on their own, they evaluate conditions and follow instructions based on the results. This process is known as **control flow**.

Control flow determines the order in which a program executes its statements. While some programs execute instructions one after another in a simple sequence, most real-world applications must make decisions based on user input, calculations, or other conditions.

For example, an online banking application may check whether an account has enough funds before approving a withdrawal. An e-commerce website may verify whether a product is in stock before allowing a customer to complete a purchase. A learning platform may display different content depending on whether a learner has completed a prerequisite lesson.

In each case, the program evaluates one or more conditions and decides what action to take.

JavaScript provides several control flow structures that allow developers to create dynamic and interactive applications. Throughout this chapter, you will learn how to use these structures to build programs that respond intelligently to different situations.

---

### Why Control Flow Matters

Without control flow, every JavaScript program would execute the same sequence of instructions regardless of the data it receives. This would make software unable to adapt to different users, inputs, or circumstances.

Control flow enables programs to:

- Make decisions based on conditions.
- Respond to user input.
- Validate information before processing it.
- Display different messages for different situations.
- Execute specific blocks of code only when required.
- Improve the overall user experience by making applications interactive.

---

### Everyday Examples of Control Flow

You encounter decision-making processes every day. Consider the following examples:

- **ATM:** Dispense cash only if the account balance is sufficient.
- **Online Store:** Apply a discount if the customer meets the promotion requirements.
- **School Portal:** Display examination results only after the student logs in successfully.
- **Social Media Platform:** Show different content based on a user's interests and preferences.
- **Weather App:** Recommend carrying an umbrella if rain is forecast.

Each example follows the same pattern:

1. Evaluate a condition.
2. Decide which action to perform.
3. Execute the appropriate instructions.

This is the essence of control flow in programming.

---

### Building on Previous Knowledge

In Chapter 4, you learned how to create expressions and use comparison and logical operators to evaluate conditions. Those skills now become the foundation for decision-making.

For example:

```javascript
let score = 75;

console.log(score >= 50);
```

The expression `score >= 50` evaluates to `true`. In this chapter, you will learn how to use that result to determine which block of code should execute.

---

### What You Will Learn in This Chapter

In this chapter, you will explore:

- `if` statements
- `if...else` statements
- `else if` statements
- Nested conditional statements
- `switch` statements
- Truthy and falsy values
- Best practices for writing conditional logic
- Practical applications of decision-making in JavaScript

By the end of this chapter, you will be able to write programs that respond intelligently to different conditions and user interactions.

---

> **Figure 5.1**
>
> **Basic Control Flow**
>
> *(Insert a flowchart showing: Start → Evaluate Condition → True Path / False Path → End.)*

---

> **CodeTales Insight**
>
> Every interactive application—from online banking systems to video games—depends on control flow. Learning how to make decisions in your programs transforms them from simple calculators into software that can respond to users, solve problems, and automate real-world tasks.

---

### Section Summary

In this section, you learned that control flow determines the order in which a JavaScript program executes its statements. You explored why decision-making is essential in software development and how conditional structures enable programs to respond dynamically to different situations. In the next section, you will examine the Boolean logic that powers every conditional statement in JavaScript.

## 5.2 Understanding Boolean Logic

Before a JavaScript program can make a decision, it must evaluate a condition. Every condition ultimately produces one of two possible Boolean values: `true` or `false`.

Boolean logic forms the foundation of decision-making in programming. Whether you are checking a user's password, validating a payment, or determining whether a student has passed an examination, the program first evaluates a condition and then decides what to do based on the result.

In this section, you will explore how Boolean values work and how they are used to control the flow of a JavaScript program.

---

### What Is a Boolean Value?

A **Boolean** is a data type that has only two possible values:

- `true`
- `false`

Unlike numbers or strings, Booleans represent the result of a logical evaluation.

Example:

```javascript
let isLoggedIn = true;
let hasPaid = false;

console.log(isLoggedIn);
console.log(hasPaid);
```

Output:

```text
true
false
```

These values are commonly used to represent states such as:

- On or off
- Yes or no
- Success or failure
- Logged in or logged out
- Approved or rejected

---

### Boolean Values from Comparisons

Most Boolean values are produced by comparison operators.

Example:

```javascript
let age = 20;

console.log(age >= 18);
```

Output:

```text
true
```

Another example:

```javascript
let score = 45;

console.log(score >= 50);
```

Output:

```text
false
```

The comparison operator evaluates the expression and returns a Boolean value.

---

### Boolean Values from Logical Operators

Logical operators combine or modify Boolean expressions.

Example:

```javascript
let hasID = true;
let isAdult = true;

console.log(hasID && isAdult);
```

Output:

```text
true
```

Example:

```javascript
let hasTicket = false;
let isVIP = true;

console.log(hasTicket || isVIP);
```

Output:

```text
true
```

Logical operators allow programs to evaluate more complex conditions.

---

### Using Boolean Variables

Boolean values are often stored in variables for later use.

Example:

```javascript
let isMember = true;
let hasDiscount = false;

console.log(isMember);
console.log(hasDiscount);
```

Meaningful variable names make your code easier to understand.

---

### Boolean Expressions

A **Boolean expression** is any expression that evaluates to either `true` or `false`.

Examples:

```javascript
10 > 5
```

Result:

```text
true
```

```javascript
8 === "8"
```

Result:

```text
false
```

```javascript
25 <= 30
```

Result:

```text
true
```

Boolean expressions are used in every conditional statement.

---

### Why Boolean Logic Matters

Without Boolean logic, programs would not be able to make decisions.

For example:

- Is the password correct?
- Is the user at least 18 years old?
- Is the shopping cart empty?
- Has the payment been approved?
- Is the product available?

Each question produces a Boolean answer that determines what the program does next.

---

### Real-World Example

Consider a library management system.

A member can borrow a book only if:

- The book is available.
- The member's account is active.

Example:

```javascript
let bookAvailable = true;
let accountActive = true;

let canBorrow = bookAvailable && accountActive;

console.log(canBorrow);
```

Output:

```text
true
```

If either condition is false, the member cannot borrow the book.

---

### Boolean Logic in Everyday Software

Boolean logic appears in almost every application you use.

Examples include:

- Logging into websites.
- Making online payments.
- Unlocking smartphones.
- Booking airline tickets.
- Registering for courses.
- Submitting online forms.
- Filtering search results.

Every one of these tasks depends on conditions that evaluate to `true` or `false`.

---

> **Figure 5.2**
>
> **Boolean Logic in Decision-Making**
>
> *(Insert a simple diagram showing a condition being evaluated to either `true` or `false`, with each outcome leading to a different action.)*

---

### Best Practices

When working with Boolean logic:

- Use descriptive Boolean variable names such as `isLoggedIn`, `hasPermission`, or `isAvailable`.
- Write conditions that are simple and easy to read.
- Avoid unnecessary comparisons such as `isLoggedIn === true`; simply use `isLoggedIn` when appropriate.
- Test your conditions with different input values to ensure they behave as expected.

---

> **CodeTales Insight**
>
> Boolean logic may seem simple because it has only two possible values, but it powers nearly every decision a computer makes. From validating user input to controlling access to sensitive information, Boolean expressions are at the heart of modern software development.

---

### Section Summary

In this section, you learned that Boolean logic provides the foundation for decision-making in JavaScript. You explored Boolean values, Boolean expressions, and how comparison and logical operators produce `true` or `false` results. In the next section, you will use these Boolean values to control the execution of code with the `if` statement.

## 5.3 The `if` Statement

The **`if` statement** is the simplest form of decision-making in JavaScript. It allows a program to execute a block of code **only when a specified condition evaluates to `true`**.

If the condition is `false`, the program skips the block and continues executing the next statement.

This enables programs to respond dynamically to different situations instead of always performing the same actions.

---

### Syntax of the `if` Statement

The general syntax of an `if` statement is:

```javascript
if (condition) {
    // Code to execute if the condition is true
}
```

The statement consists of two parts:

- **Condition:** An expression that evaluates to either `true` or `false`.
- **Code Block:** The statements enclosed within curly braces `{}` that execute only if the condition is `true`.

---

### How the `if` Statement Works

The JavaScript engine follows these steps:

1. Evaluate the condition.
2. If the condition is `true`, execute the code inside the braces.
3. If the condition is `false`, skip the code block.
4. Continue executing the rest of the program.

---

### Example 1: Checking Age

```javascript
let age = 20;

if (age >= 18) {
    console.log("You are eligible to vote.");
}
```

Output:

```text
You are eligible to vote.
```

Since `age >= 18` evaluates to `true`, the message is displayed.

---

### Example 2: Condition Is False

```javascript
let age = 15;

if (age >= 18) {
    console.log("You are eligible to vote.");
}

console.log("Program finished.");
```

Output:

```text
Program finished.
```

The condition evaluates to `false`, so the code inside the `if` block is skipped.

---

### Example 3: Student Pass Check

```javascript
let score = 72;

if (score >= 50) {
    console.log("Congratulations! You passed the examination.");
}
```

Output:

```text
Congratulations! You passed the examination.
```

---

### Example 4: Bank Withdrawal

```javascript
let balance = 80000;
let withdrawal = 25000;

if (balance >= withdrawal) {
    console.log("Withdrawal approved.");
}
```

Output:

```text
Withdrawal approved.
```

The transaction proceeds only because the account has sufficient funds.

---

### Example 5: Product Availability

```javascript
let stock = 12;

if (stock > 0) {
    console.log("Product is available.");
}
```

Output:

```text
Product is available.
```

---

### Using Logical Operators in an `if` Statement

Conditions can combine multiple expressions using logical operators.

```javascript
let age = 25;
let hasLicense = true;

if (age >= 18 && hasLicense) {
    console.log("You may drive the vehicle.");
}
```

Output:

```text
You may drive the vehicle.
```

Both conditions must be true before the message is displayed.

---

### Using Boolean Variables

You can use Boolean variables directly without comparing them to `true`.

Preferred:

```javascript
let isLoggedIn = true;

if (isLoggedIn) {
    console.log("Welcome back!");
}
```

Avoid:

```javascript
if (isLoggedIn === true) {
    console.log("Welcome back!");
}
```

The first version is shorter, cleaner, and more idiomatic.

---

### Flow of an `if` Statement

The execution of an `if` statement can be visualized as follows:

```text
Start
   │
   ▼
Evaluate Condition
   │
 ┌─┴─┐
 │   │
True False
 │    │
 ▼    ▼
Execute
Code
 │
 ▼
Continue Program
```

---

### Practical Example: Online Course Enrollment

```javascript
let completedPrerequisite = true;

if (completedPrerequisite) {
    console.log("Enrollment successful.");
}
```

Output:

```text
Enrollment successful.
```

---

### Common Beginner Mistakes

Beginners often make mistakes such as:

- Using `=` instead of `===` in conditions.
- Forgetting parentheses around the condition.
- Omitting curly braces for multi-line code blocks.
- Assuming the `if` block runs when the condition is `false`.
- Writing conditions that are unnecessarily complex.

Example of an incorrect condition:

```javascript
if (age = 18) {
    console.log("Adult");
}
```

Correct version:

```javascript
if (age === 18) {
    console.log("Adult");
}
```

---

### Best Practices

When using `if` statements:

- Keep conditions simple and readable.
- Use meaningful variable names.
- Prefer `===` over `==` for comparisons.
- Use curly braces even for a single statement to improve readability and reduce future errors.
- Test both `true` and `false` outcomes.

---

> **Figure 5.3**
>
> **Execution Flow of an `if` Statement**
>
> *(Insert a flowchart showing: Start → Evaluate Condition → If True: Execute Code → Continue Program; If False: Skip Code → Continue Program.)*

---

> **CodeTales Insight**
>
> The `if` statement is the first step toward creating intelligent software. Whether you're checking login credentials, validating user input, or processing online payments, nearly every interactive application uses `if` statements to decide what should happen next.

---

### Section Summary

In this section, you learned how the `if` statement enables JavaScript programs to execute code only when a specified condition evaluates to `true`. You explored its syntax, execution flow, practical examples, common mistakes, and best practices. In the next section, you will expand this concept by learning the `if...else` statement, which allows a program to choose between two alternative actions.

## 5.4 The `if...else` Statement

In the previous section, you learned that an `if` statement executes a block of code only when a condition is `true`. But what happens when the condition is `false`?

In many real-world situations, a program should perform one action when a condition is true and a different action when it is false. The **`if...else` statement** makes this possible.

The `if...else` statement allows a program to choose between two alternative paths of execution.

---

### Syntax of the `if...else` Statement

The general syntax is:

```javascript
if (condition) {
    // Code executed if the condition is true
} else {
    // Code executed if the condition is false
}
```

The program first evaluates the condition.

- If the condition is `true`, the code inside the `if` block executes.
- If the condition is `false`, the code inside the `else` block executes.

Only **one** of the two blocks is executed.

---

### How the `if...else` Statement Works

The JavaScript engine follows these steps:

1. Evaluate the condition.
2. If the condition is `true`, execute the `if` block.
3. Otherwise, execute the `else` block.
4. Continue executing the remaining program.

---

### Example 1: Voting Eligibility

```javascript
let age = 20;

if (age >= 18) {
    console.log("You are eligible to vote.");
} else {
    console.log("You are not eligible to vote.");
}
```

Output:

```text
You are eligible to vote.
```

If `age` were `16`, the output would be:

```text
You are not eligible to vote.
```

---

### Example 2: Student Examination Result

```javascript
let score = 48;

if (score >= 50) {
    console.log("Pass");
} else {
    console.log("Fail");
}
```

Output:

```text
Fail
```

---

### Example 3: ATM Withdrawal

```javascript
let balance = 50000;
let withdrawal = 60000;

if (balance >= withdrawal) {
    console.log("Withdrawal approved.");
} else {
    console.log("Insufficient funds.");
}
```

Output:

```text
Insufficient funds.
```

---

### Example 4: Login Verification

```javascript
let passwordCorrect = false;

if (passwordCorrect) {
    console.log("Login successful.");
} else {
    console.log("Invalid password.");
}
```

Output:

```text
Invalid password.
```

---

### Example 5: Product Availability

```javascript
let stock = 0;

if (stock > 0) {
    console.log("Product available.");
} else {
    console.log("Out of stock.");
}
```

Output:

```text
Out of stock.
```

---

### Using Logical Operators

Conditions can include logical operators to evaluate multiple requirements.

```javascript
let age = 22;
let hasTicket = true;

if (age >= 18 && hasTicket) {
    console.log("Entry granted.");
} else {
    console.log("Entry denied.");
}
```

Output:

```text
Entry granted.
```

---

### Using Comparison Operators

You can compare numbers, strings, or other values.

```javascript
let temperature = 32;

if (temperature > 30) {
    console.log("It's a hot day.");
} else {
    console.log("The weather is pleasant.");
}
```

---

### Flow of an `if...else` Statement

```text
Start
   │
   ▼
Evaluate Condition
   │
 ┌─┴─────────┐
 │           │
True       False
 │           │
 ▼           ▼
Execute     Execute
if Block    else Block
      │
      ▼
Continue Program
```

---

### Real-World Example: Online Shopping

```javascript
let cartTotal = 120000;

if (cartTotal >= 100000) {
    console.log("Free shipping applied.");
} else {
    console.log("Shipping charges apply.");
}
```

Output:

```text
Free shipping applied.
```

---

### Common Beginner Mistakes

Be careful to avoid these common errors:

**Using assignment instead of comparison**

Incorrect:

```javascript
if (age = 18) {
    console.log("Adult");
}
```

Correct:

```javascript
if (age === 18) {
    console.log("Adult");
}
```

---

**Forgetting Curly Braces**

Although JavaScript allows braces to be omitted for a single statement, always include them.

Recommended:

```javascript
if (loggedIn) {
    console.log("Welcome!");
} else {
    console.log("Please log in.");
}
```

---

**Writing Complex Conditions**

Instead of:

```javascript
if ((score >= 50 && attendance >= 75) || isAdministrator) {
```

Consider using intermediate Boolean variables:

```javascript
let passedCourse = score >= 50 && attendance >= 75;

if (passedCourse || isAdministrator) {
    console.log("Access granted.");
}
```

This improves readability.

---

### Best Practices

When writing `if...else` statements:

- Keep conditions short and meaningful.
- Use `===` instead of `==`.
- Write descriptive variable names.
- Always use curly braces.
- Test both the `true` and `false` branches.
- Keep indentation consistent.

---

> **Figure 5.4**
>
> **Execution Flow of an `if...else` Statement**
>
> *(Insert a flowchart showing one decision splitting into two branches: the `if` block for `true` and the `else` block for `false`, both joining before the program continues.)*

---

> **CodeTales Insight**
>
> The `if...else` statement mirrors many decisions we make every day. Whether approving a bank transaction, checking examination results, or validating a user's login credentials, software constantly chooses between two possible outcomes based on a condition.

---

### Section Summary

In this section, you learned how the `if...else` statement enables JavaScript programs to choose between two alternative actions. You explored its syntax, execution flow, practical examples, common mistakes, and best practices. In the next section, you will learn how to handle situations involving more than two possible outcomes using the `else if` statement.

## 5.5 The `else if` Statement

In the previous section, you learned how the `if...else` statement allows a program to choose between two possible actions. However, many real-world situations involve more than two possible outcomes.

For example:

- A student's grade could be **A, B, C, D, or F**.
- A traffic light could be **green, yellow, or red**.
- A weather application could display **Sunny, Cloudy, Rainy, or Stormy**.
- An online shopping system might assign different discount levels based on the customer's purchase amount.

To handle multiple conditions efficiently, JavaScript provides the **`else if` statement**.

The `else if` statement allows a program to test several conditions in sequence. As soon as one condition evaluates to `true`, the corresponding block of code executes, and the remaining conditions are skipped.

---

### Syntax of the `else if` Statement

The general syntax is:

```javascript
if (condition1) {
    // Executes if condition1 is true
} else if (condition2) {
    // Executes if condition2 is true
} else if (condition3) {
    // Executes if condition3 is true
} else {
    // Executes if none of the conditions are true
}
```

JavaScript evaluates the conditions from top to bottom.

- If `condition1` is `true`, its block executes.
- Otherwise, JavaScript checks `condition2`.
- This process continues until a condition evaluates to `true`.
- If none of the conditions are `true`, the `else` block executes (if present).

Only **one** block executes.

---

### Example 1: Student Grade

```javascript
let score = 82;

if (score >= 70) {
    console.log("Grade: A");
} else if (score >= 60) {
    console.log("Grade: B");
} else if (score >= 50) {
    console.log("Grade: C");
} else {
    console.log("Grade: F");
}
```

Output:

```text
Grade: A
```

---

### Example 2: Time of Day

```javascript
let hour = 15;

if (hour < 12) {
    console.log("Good morning!");
} else if (hour < 18) {
    console.log("Good afternoon!");
} else {
    console.log("Good evening!");
}
```

Output:

```text
Good afternoon!
```

---

### Example 3: Internet Signal Strength

```javascript
let signal = 3;

if (signal >= 5) {
    console.log("Excellent signal");
} else if (signal >= 3) {
    console.log("Good signal");
} else if (signal >= 1) {
    console.log("Weak signal");
} else {
    console.log("No signal");
}
```

Output:

```text
Good signal
```

---

### Example 4: Shopping Discount

```javascript
let purchaseAmount = 120000;

if (purchaseAmount >= 200000) {
    console.log("20% discount");
} else if (purchaseAmount >= 100000) {
    console.log("10% discount");
} else if (purchaseAmount >= 50000) {
    console.log("5% discount");
} else {
    console.log("No discount");
}
```

Output:

```text
10% discount
```

---

### Why Order Matters

JavaScript evaluates conditions from top to bottom. Therefore, place the most specific or highest-priority conditions first.

Incorrect:

```javascript
let score = 95;

if (score >= 50) {
    console.log("Pass");
} else if (score >= 90) {
    console.log("Excellent");
}
```

Output:

```text
Pass
```

The second condition is never reached because the first condition is already true.

Correct:

```javascript
if (score >= 90) {
    console.log("Excellent");
} else if (score >= 50) {
    console.log("Pass");
}
```

Output:

```text
Excellent
```

---

### Flow of an `else if` Statement

```text
Start
   │
   ▼
Condition 1?
   │
 ┌─┴─┐
 │   │
Yes  No
 │    │
 ▼    ▼
Block 1
      │
      ▼
Condition 2?
      │
   ┌──┴──┐
   │     │
  Yes    No
   │      │
   ▼      ▼
 Block 2  ...
      │
      ▼
   Else Block
      │
      ▼
 Continue Program
```

---

### Real-World Example: Loan Approval

```javascript
let creditScore = 720;

if (creditScore >= 800) {
    console.log("Excellent credit");
} else if (creditScore >= 700) {
    console.log("Good credit");
} else if (creditScore >= 600) {
    console.log("Fair credit");
} else {
    console.log("Poor credit");
}
```

---

### Common Beginner Mistakes

**Placing conditions in the wrong order**

Always check more restrictive conditions before broader ones.

---

**Using separate `if` statements unnecessarily**

Incorrect:

```javascript
if (score >= 70) {
    console.log("A");
}

if (score >= 60) {
    console.log("B");
}
```

A score of `75` prints both `A` and `B`.

Correct:

```javascript
if (score >= 70) {
    console.log("A");
} else if (score >= 60) {
    console.log("B");
}
```

Only one grade is displayed.

---

**Forgetting the final `else`**

While optional, a final `else` helps handle unexpected cases gracefully.

---

### Best Practices

- Arrange conditions from most specific to most general.
- Use meaningful comparison values.
- Avoid deeply nested `else if` chains when another structure (such as `switch`) would be clearer.
- Keep each condition simple and readable.
- Test boundary values (for example, `49`, `50`, `69`, `70`) to ensure your logic works correctly.

---

> **Figure 5.5**
>
> **Decision Tree Using `else if`**
>
> *(Insert a flowchart showing multiple conditions evaluated sequentially until one matches, followed by a default `else` path.)*

---

> **CodeTales Insight**
>
> Many real-world systems classify information into categories. Whether assigning grades, determining tax brackets, or calculating discounts, `else if` statements provide a clear and efficient way to evaluate multiple possibilities while ensuring that only one outcome is selected.

---

### Section Summary

In this section, you learned how the `else if` statement enables JavaScript programs to evaluate multiple conditions in sequence. You explored its syntax, execution flow, practical examples, common mistakes, and best practices. In the next section, you will learn how to create **nested conditional statements**, allowing you to place one decision inside another for more complex program logic.

## 5.6 Nested Conditional Statements

As your JavaScript programs become more sophisticated, you may encounter situations where a single decision depends on the outcome of another decision. In such cases, you can place one conditional statement inside another. This is known as **nesting**.

A **nested conditional statement** is simply an `if`, `if...else`, or `else if` statement placed inside another conditional statement.

Nested conditionals allow you to evaluate additional conditions only after an initial condition has been satisfied. This approach is useful when decisions naturally occur in stages.

---

### Syntax of a Nested `if` Statement

```javascript
if (condition1) {
    if (condition2) {
        // Code executes if both conditions are true
    }
}
```

The inner `if` statement is evaluated only if the outer `if` condition is `true`.

---

### How Nested Conditionals Work

The JavaScript engine follows these steps:

1. Evaluate the outer condition.
2. If the outer condition is `false`, skip the entire nested block.
3. If the outer condition is `true`, evaluate the inner condition.
4. Execute the inner block only if its condition is also `true`.
5. Continue with the rest of the program.

---

### Example 1: Driving Eligibility

A person must:

- Be at least 18 years old.
- Have a valid driver's license.

```javascript
let age = 22;
let hasLicense = true;

if (age >= 18) {
    if (hasLicense) {
        console.log("You are allowed to drive.");
    }
}
```

Output:

```text
You are allowed to drive.
```

The second condition is checked only because the first condition is true.

---

### Example 2: School Admission

```javascript
let applicationSubmitted = true;
let passedEntranceExam = true;

if (applicationSubmitted) {
    if (passedEntranceExam) {
        console.log("Admission granted.");
    }
}
```

Output:

```text
Admission granted.
```

---

### Example 3: Online Banking

```javascript
let loggedIn = true;
let accountVerified = false;

if (loggedIn) {
    if (accountVerified) {
        console.log("Transfer approved.");
    } else {
        console.log("Please verify your account.");
    }
}
```

Output:

```text
Please verify your account.
```

Notice that the `else` belongs to the inner `if`.

---

### Example 4: Employee Bonus

```javascript
let yearsWorked = 6;
let performanceRating = "Excellent";

if (yearsWorked >= 5) {
    if (performanceRating === "Excellent") {
        console.log("Bonus approved.");
    } else {
        console.log("No performance bonus.");
    }
} else {
    console.log("Employee not yet eligible.");
}
```

Output:

```text
Bonus approved.
```

---

### Visualizing Nested Decisions

```text
Start
   │
   ▼
Age ≥ 18?
   │
 ┌─┴─┐
 │   │
Yes  No
 │    │
 ▼    ▼
Has License?   Stop
 │
┌┴┐
│ │
Y N
│ │
▼ ▼
Drive  Cannot Drive
```

The second decision is evaluated only if the first one succeeds.

---

### Nested `if...else` Statements

You can also nest complete `if...else` structures.

```javascript
let loggedIn = true;
let isAdmin = true;

if (loggedIn) {
    if (isAdmin) {
        console.log("Welcome, Administrator.");
    } else {
        console.log("Welcome, User.");
    }
} else {
    console.log("Please log in.");
}
```

Output:

```text
Welcome, Administrator.
```

---

### When to Use Nested Conditionals

Nested conditionals are useful when:

- A second decision depends on the first.
- You need to perform additional validation.
- A process naturally occurs in stages.
- Different permissions depend on earlier checks.

Examples include:

- User authentication.
- ATM transactions.
- Online examination systems.
- Loan approval systems.
- Hospital patient registration.
- Access control systems.

---

### Common Beginner Mistakes

#### Excessive Nesting

Avoid deeply nested code such as:

```javascript
if (a) {
    if (b) {
        if (c) {
            if (d) {
                // Code
            }
        }
    }
}
```

Deep nesting makes code difficult to read and maintain.

---

#### Incorrect Indentation

Poor indentation makes it difficult to determine which `if` an `else` belongs to.

Always indent nested blocks consistently.

Correct:

```javascript
if (loggedIn) {
    if (isAdmin) {
        console.log("Admin");
    }
}
```

---

#### Forgetting That Inner Conditions Depend on Outer Conditions

The inner condition is never evaluated if the outer condition is false.

---

### Best Practices

- Keep nesting as shallow as possible.
- Use meaningful variable names.
- Maintain consistent indentation.
- Consider combining conditions with logical operators when appropriate.
- Refactor overly complex nested logic into separate functions as your programs grow.

---

### Comparing Nested Conditionals and Logical Operators

Sometimes nested conditionals can be simplified.

Nested version:

```javascript
if (age >= 18) {
    if (hasLicense) {
        console.log("Drive");
    }
}
```

Equivalent version:

```javascript
if (age >= 18 && hasLicense) {
    console.log("Drive");
}
```

The second version is shorter and often easier to read.

Choose the approach that best communicates your program's logic.

---

> **Figure 5.6**
>
> **Nested Conditional Flow**
>
> *(Insert a flowchart illustrating an outer decision leading to a second decision before reaching the final outcome.)*

---

> **CodeTales Insight**
>
> Real-world software rarely makes just one decision. Banking systems, educational platforms, healthcare applications, and e-commerce websites often perform a series of related checks before completing an action. Nested conditional statements help organize these layered decisions in a logical and structured way.

---

### Section Summary

In this section, you learned how nested conditional statements allow one decision to be placed inside another. You explored their syntax, execution flow, practical examples, common mistakes, and best practices. You also learned when nested conditionals are appropriate and when combining conditions with logical operators can produce cleaner code. In the next section, you will explore the `switch` statement, an alternative decision-making structure that is often more suitable when comparing a single value against many possible options.

## 5.7 The `switch` Statement

In the previous sections, you learned how to make decisions using `if`, `if...else`, and `else if` statements. While these structures are suitable for many situations, there are times when you need to compare **one expression** against several possible values.

For example, you might want to:

- Display the name of a month based on its number.
- Show the day of the week.
- Process menu selections.
- Handle user roles.
- Respond to different application states.

Writing many `else if` statements for these situations can make your code longer and harder to read.

JavaScript provides the **`switch` statement** as a cleaner alternative when comparing a single value against multiple possible cases.

---

## Syntax of the `switch` Statement

The general syntax is:

```javascript
switch (expression) {
    case value1:
        // Code
        break;

    case value2:
        // Code
        break;

    case value3:
        // Code
        break;

    default:
        // Code
}
```

The `switch` statement evaluates the expression once and compares its value with each `case`.

If a matching case is found, JavaScript executes that block of code.

If no case matches, the `default` block executes.

---

## How the `switch` Statement Works

JavaScript performs the following steps:

1. Evaluate the expression.
2. Compare it with each `case`.
3. Execute the first matching case.
4. Continue until a `break` statement is encountered.
5. If no match exists, execute the `default` block.

---

## Example 1: Day of the Week

```javascript
let day = 3;

switch (day) {
    case 1:
        console.log("Monday");
        break;

    case 2:
        console.log("Tuesday");
        break;

    case 3:
        console.log("Wednesday");
        break;

    case 4:
        console.log("Thursday");
        break;

    case 5:
        console.log("Friday");
        break;

    default:
        console.log("Weekend");
}
```

Output:

```text
Wednesday
```

---

## Example 2: User Role

```javascript
let role = "admin";

switch (role) {
    case "admin":
        console.log("Full access granted.");
        break;

    case "editor":
        console.log("Edit access granted.");
        break;

    case "viewer":
        console.log("Read-only access.");
        break;

    default:
        console.log("Unknown role.");
}
```

Output:

```text
Full access granted.
```

---

## Example 3: Traffic Light

```javascript
let light = "yellow";

switch (light) {
    case "green":
        console.log("Go");
        break;

    case "yellow":
        console.log("Slow down");
        break;

    case "red":
        console.log("Stop");
        break;

    default:
        console.log("Invalid signal");
}
```

Output:

```text
Slow down
```

---

## The Importance of `break`

The `break` statement tells JavaScript to exit the `switch` statement after executing the matching case.

Without `break`, execution continues into the next case. This behavior is known as **fall-through**.

Example:

```javascript
let grade = "A";

switch (grade) {
    case "A":
        console.log("Excellent");

    case "B":
        console.log("Very Good");

    case "C":
        console.log("Good");
}
```

Output:

```text
Excellent
Very Good
Good
```

Since there are no `break` statements, execution continues through the remaining cases.

Correct version:

```javascript
switch (grade) {
    case "A":
        console.log("Excellent");
        break;

    case "B":
        console.log("Very Good");
        break;

    case "C":
        console.log("Good");
        break;
}
```

Output:

```text
Excellent
```

---

## The `default` Case

The `default` block runs when none of the cases match.

```javascript
let month = 15;

switch (month) {
    case 1:
        console.log("January");
        break;

    case 2:
        console.log("February");
        break;

    default:
        console.log("Invalid month.");
}
```

Output:

```text
Invalid month.
```

Although optional, including a `default` case is considered a best practice because it helps handle unexpected input.

---

## Grouping Multiple Cases

Sometimes several cases should perform the same action.

```javascript
let day = "Saturday";

switch (day) {
    case "Saturday":
    case "Sunday":
        console.log("Weekend");
        break;

    default:
        console.log("Weekday");
}
```

Output:

```text
Weekend
```

This technique avoids repeating identical code.

---

## Flow of a `switch` Statement

```text
Start
   │
   ▼
Evaluate Expression
   │
   ▼
Compare with Cases
   │
 ┌─┼───────────────┐
 │ │               │
 ▼ ▼               ▼
Case 1         Case 2 ... Default
   │               │
   └──────┬────────┘
          ▼
     Continue Program
```

---

## When to Use a `switch` Statement

A `switch` statement is a good choice when:

- Comparing one variable against many fixed values.
- Creating menus.
- Handling commands.
- Processing application states.
- Selecting options from a list.

Examples include:

- ATM menu options.
- Navigation menus.
- User roles.
- Language selection.
- Day and month names.
- Product categories.

---

## Common Beginner Mistakes

### Forgetting `break`

This often causes unintended fall-through.

---

### Omitting the `default` Case

Unexpected input should be handled gracefully.

---

### Using Complex Conditions

A `switch` statement compares a single expression against values. It is **not** intended for complex logical expressions.

Poor choice:

```javascript
switch (score >= 50) {
```

Better:

```javascript
if (score >= 50) {
    console.log("Pass");
}
```

---

### Mixing Data Types

Remember that `switch` uses **strict comparison (`===`)**.

Example:

```javascript
let value = "1";

switch (value) {
    case 1:
        console.log("Number");
        break;

    default:
        console.log("No match");
}
```

Output:

```text
No match
```

The string `"1"` is not strictly equal to the number `1`.

---

## Best Practices

- Always include `break` unless fall-through is intentional.
- Include a `default` case.
- Keep each case concise.
- Use meaningful case values.
- Choose `switch` only when comparing one expression against multiple fixed values.

---

> **Figure 5.7**
>
> **Execution Flow of a `switch` Statement**
>
> *(Insert a flowchart showing an expression being evaluated, matched against several cases, executing one matching case, and then exiting the `switch` statement.)*

---

> **CodeTales Insight**
>
> Many professional applications use `switch` statements to process menus, user roles, commands, and application states. Choosing `switch` when appropriate makes code easier to read, maintain, and extend, especially when many fixed options must be handled.

---

### Section Summary

In this section, you learned how the `switch` statement provides an efficient way to compare a single expression against multiple possible values. You explored its syntax, execution flow, the purpose of `break` and `default`, grouping cases, common mistakes, and best practices. In the next section, you will learn how to decide between using `if...else` statements and `switch` statements by understanding the strengths and limitations of each approach.

## 5.8 Choosing Between `if...else` and `switch`

JavaScript provides both `if...else` statements and `switch` statements for making decisions. Since both can be used to control the flow of a program, beginners often wonder which one they should choose.

The answer depends on the type of decision your program needs to make.

Although there is some overlap between these two structures, each has situations where it is the better choice.

---

## Understanding the Difference

An `if...else` statement evaluates **Boolean expressions**.

A `switch` statement compares **one expression** against several possible values.

This distinction is the key to deciding which structure to use.

---

## When to Use `if...else`

Choose an `if...else` statement when:

- Comparing ranges of values.
- Evaluating multiple logical conditions.
- Using comparison operators such as `>`, `<`, `>=`, or `<=`.
- Combining conditions with logical operators (`&&`, `||`, `!`).
- Writing conditions that involve calculations or expressions.

### Example: Age Verification

```javascript
let age = 17;

if (age >= 18) {
    console.log("Adult");
} else {
    console.log("Minor");
}
```

The decision depends on whether the age falls within a range.

---

### Example: Loan Approval

```javascript
let income = 250000;
let creditScore = 730;

if (income >= 200000 && creditScore >= 700) {
    console.log("Loan Approved");
} else {
    console.log("Loan Rejected");
}
```

This decision depends on multiple conditions, making `if...else` the appropriate choice.

---

## When to Use `switch`

Choose a `switch` statement when:

- Comparing one variable against many fixed values.
- Building menus.
- Processing user commands.
- Working with predefined options.
- Selecting actions based on categories.

### Example: User Role

```javascript
let role = "editor";

switch (role) {
    case "admin":
        console.log("Administrator");
        break;

    case "editor":
        console.log("Editor");
        break;

    case "viewer":
        console.log("Viewer");
        break;

    default:
        console.log("Unknown Role");
}
```

Since one variable is compared against several known values, `switch` is clearer than multiple `else if` statements.

---

## Side-by-Side Comparison

### Using `if...else`

```javascript
let day = 2;

if (day === 1) {
    console.log("Monday");
} else if (day === 2) {
    console.log("Tuesday");
} else if (day === 3) {
    console.log("Wednesday");
} else {
    console.log("Other Day");
}
```

---

### Using `switch`

```javascript
let day = 2;

switch (day) {
    case 1:
        console.log("Monday");
        break;

    case 2:
        console.log("Tuesday");
        break;

    case 3:
        console.log("Wednesday");
        break;

    default:
        console.log("Other Day");
}
```

Both programs produce the same result, but the `switch` version is easier to read when there are many fixed options.

---

## Comparison Table

| Feature | `if...else` | `switch` |
|---------|-------------|----------|
| Evaluates Boolean expressions | ✅ | ❌ |
| Compares one value against many fixed values | ❌ | ✅ |
| Handles value ranges | ✅ | ❌ |
| Supports logical operators | ✅ | ❌ |
| Suitable for complex conditions | ✅ | ❌ |
| Suitable for menus and commands | ❌ | ✅ |
| Requires `break` statements | ❌ | ✅ |
| Includes a `default` option | ❌ (`else`) | ✅ (`default`) |

---

## Real-World Examples

### Use `if...else` for:

- Age verification
- Exam grading based on ranges
- Banking transactions
- Login validation
- Weather alerts
- Loan approval
- Payment verification

---

### Use `switch` for:

- ATM menu selection
- Navigation menus
- User roles
- Product categories
- Language selection
- Day of the week
- Month names
- Game difficulty levels

---

## Common Beginner Mistakes

### Using `switch` for Ranges

Incorrect:

```javascript
switch (score) {
    case score >= 70:
        console.log("A");
}
```

A `switch` statement compares values, not range expressions.

Use `if...else` instead:

```javascript
if (score >= 70) {
    console.log("A");
}
```

---

### Writing Long `else if` Chains for Fixed Values

Instead of:

```javascript
if (role === "admin") {
    ...
} else if (role === "editor") {
    ...
} else if (role === "viewer") {
    ...
}
```

A `switch` statement is usually cleaner.

---

### Choosing Based on Habit

Don't use `if...else` or `switch` simply because you're more familiar with one of them. Select the structure that best communicates your program's intent.

---

## Best Practices

- Use `if...else` for comparisons, ranges, and logical conditions.
- Use `switch` for one expression with multiple fixed values.
- Keep conditions readable and straightforward.
- Include a `default` case in every `switch` statement.
- Avoid forcing one structure to solve problems better suited to the other.

---

> **Figure 5.8**
>
> **Choosing the Right Decision Structure**
>
> *(Insert a decision diagram: "Are you comparing one value against many fixed options?" → Yes: Use `switch`; No: Use `if...else`.)*

---

> **CodeTales Insight**
>
> Good programmers don't just know the syntax of control structures—they know when each one is appropriate. Choosing the right structure improves readability, reduces bugs, and makes your code easier for others to understand and maintain.

---

### Section Summary

In this section, you learned the strengths and limitations of both `if...else` and `switch` statements. You discovered that `if...else` is best suited for Boolean expressions, ranges, and complex conditions, while `switch` excels at comparing a single value against multiple fixed options. Making the right choice between these structures is an important skill in writing clean and maintainable JavaScript code.

In the next section, you will revisit the **conditional (ternary) operator** and see how it provides a concise alternative to simple `if...else` statements.

## 5.9 Conditional (Ternary) Operator Revisited

In Chapter 4, you learned about the **conditional (ternary) operator**, a compact way to choose between two values based on a condition.

Now that you understand `if...else` statements, it is the perfect time to revisit the ternary operator and see how it fits into JavaScript's control flow mechanisms.

The ternary operator is not a replacement for every `if...else` statement. Instead, it provides a concise and readable alternative for **simple decisions**.

---

## What Is the Ternary Operator?

The ternary operator is JavaScript's only operator that takes **three operands**:

1. A condition
2. The value or expression returned if the condition is `true`
3. The value or expression returned if the condition is `false`

Its general syntax is:

```javascript
condition ? expressionIfTrue : expressionIfFalse;
```

If the condition evaluates to `true`, the first expression is returned.

Otherwise, the second expression is returned.

---

## Comparing `if...else` and the Ternary Operator

### Using `if...else`

```javascript
let age = 20;
let message;

if (age >= 18) {
    message = "Adult";
} else {
    message = "Minor";
}

console.log(message);
```

Output:

```text
Adult
```

---

### Using the Ternary Operator

```javascript
let age = 20;

let message = age >= 18 ? "Adult" : "Minor";

console.log(message);
```

Output:

```text
Adult
```

Both examples produce the same result, but the second version is shorter.

---

## Example 1: Pass or Fail

```javascript
let score = 68;

let result = score >= 50 ? "Pass" : "Fail";

console.log(result);
```

Output:

```text
Pass
```

---

## Example 2: Even or Odd

```javascript
let number = 15;

let type = number % 2 === 0 ? "Even" : "Odd";

console.log(type);
```

Output:

```text
Odd
```

---

## Example 3: Product Availability

```javascript
let stock = 8;

let status = stock > 0 ? "Available" : "Out of Stock";

console.log(status);
```

Output:

```text
Available
```

---

## Example 4: User Login

```javascript
let isLoggedIn = true;

let greeting = isLoggedIn
    ? "Welcome back!"
    : "Please log in.";

console.log(greeting);
```

Output:

```text
Welcome back!
```

---

## Example 5: Free Shipping

```javascript
let total = 125000;

let shipping =
    total >= 100000
        ? "Free Shipping"
        : "Shipping Charges Apply";

console.log(shipping);
```

Output:

```text
Free Shipping
```

---

## Nested Ternary Operators

It is possible to nest ternary operators.

Example:

```javascript
let score = 82;

let grade =
    score >= 70
        ? "A"
        : score >= 60
            ? "B"
            : score >= 50
                ? "C"
                : "F";

console.log(grade);
```

Output:

```text
A
```

Although this works, nested ternary operators can quickly become difficult to read.

For complex decisions, prefer an `if...else if` structure.

---

## When to Use the Ternary Operator

The ternary operator works best when:

- Choosing between two values.
- Assigning a value to a variable.
- Returning a value from a function.
- Writing concise expressions.
- Improving readability for simple conditions.

Examples include:

- Displaying "Pass" or "Fail"
- Showing "Online" or "Offline"
- Choosing between light and dark themes
- Selecting shipping options
- Displaying login messages

---

## When Not to Use the Ternary Operator

Avoid using the ternary operator when:

- There are many conditions.
- Multiple statements need to execute.
- Readability becomes difficult.
- The expression spans several complex conditions.

Instead, use `if...else` or `switch`.

---

## Common Beginner Mistakes

### Forgetting the `:` Symbol

Incorrect:

```javascript
let result = score >= 50 ? "Pass";
```

Correct:

```javascript
let result = score >= 50 ? "Pass" : "Fail";
```

---

### Overusing Nested Ternary Operators

Difficult to read:

```javascript
let message =
    age >= 18
        ? income >= 50000
            ? "Approved"
            : "Income Too Low"
        : "Underage";
```

For this type of logic, `if...else if` is usually clearer.

---

### Using the Ternary Operator for Side Effects

The ternary operator is designed to produce a value. Avoid using it to perform multiple unrelated actions.

Poor example:

```javascript
isLoggedIn
    ? console.log("Welcome")
    : console.log("Login Required");
```

Clearer version:

```javascript
if (isLoggedIn) {
    console.log("Welcome");
} else {
    console.log("Login Required");
}
```

---

## Best Practices

- Use the ternary operator only for simple decisions.
- Keep expressions short and readable.
- Avoid deeply nested ternary operators.
- Use `if...else` when readability is more important than brevity.
- Format long ternary expressions across multiple lines.

---

> **Figure 5.9**
>
> **Equivalent Decision Structures**
>
> *(Insert a side-by-side comparison showing an `if...else` statement and its equivalent ternary operator expression.)*

---

> **CodeTales Insight**
>
> Professional developers value code that is both concise and readable. The ternary operator is an excellent tool for simple decisions, but clarity should always take priority over writing fewer lines of code.

---

### Section Summary

In this section, you revisited the conditional (ternary) operator and learned how it serves as a concise alternative to simple `if...else` statements. You explored its syntax, practical applications, common mistakes, and best practices. You also learned that while the ternary operator is powerful, it should be used thoughtfully to maintain code readability.

In the next section, you will explore **truthy and falsy values in conditions**, an essential JavaScript concept that explains how values other than `true` and `false` influence decision-making.

## 5.10 Truthy and Falsy Values in Conditions

So far in this chapter, the conditions used in `if` statements have evaluated to either `true` or `false`. However, JavaScript allows many other values to be used in conditional expressions.

When a value is evaluated in a Boolean context, JavaScript automatically determines whether it should be treated as **truthy** or **falsy**.

Understanding this behavior is essential because it appears throughout modern JavaScript code.

---

## What Are Truthy and Falsy Values?

A **truthy value** is any value that JavaScript treats as `true` when evaluated in a Boolean context.

A **falsy value** is any value that JavaScript treats as `false` when evaluated in a Boolean context.

For example:

```javascript
if ("Hello") {
    console.log("This code executes.");
}
```

Output:

```text
This code executes.
```

Although `"Hello"` is not the Boolean value `true`, JavaScript treats it as truthy.

---

## The Falsy Values in JavaScript

JavaScript has only a small number of falsy values.

| Value | Description |
|--------|-------------|
| `false` | The Boolean value `false` |
| `0` | The number zero |
| `-0` | Negative zero |
| `0n` | BigInt zero |
| `""` | An empty string |
| `null` | Absence of a value |
| `undefined` | A variable with no assigned value |
| `NaN` | Not-a-Number |

Every other value is considered truthy.

---

## Common Truthy Values

Examples include:

```javascript
true
```

```javascript
1
```

```javascript
-10
```

```javascript
"JavaScript"
```

```javascript
"0"
```

```javascript
[]
```

```javascript
{}
```

```javascript
function() {}
```

Notice that even an empty array (`[]`) and an empty object (`{}`) are truthy.

---

## Example 1: Using a Number

```javascript
let count = 5;

if (count) {
    console.log("Count has a value.");
}
```

Output:

```text
Count has a value.
```

Because `5` is truthy.

---

## Example 2: Using Zero

```javascript
let count = 0;

if (count) {
    console.log("Count has a value.");
}
```

Output:

```text
(No output)
```

Zero is falsy.

---

## Example 3: Using Strings

```javascript
let username = "Ada";

if (username) {
    console.log("Username entered.");
}
```

Output:

```text
Username entered.
```

A non-empty string is truthy.

---

Empty string:

```javascript
let username = "";

if (username) {
    console.log("Username entered.");
}
```

Output:

```text
(No output)
```

---

## Example 4: Using `null`

```javascript
let user = null;

if (user) {
    console.log("User found.");
}
```

Output:

```text
(No output)
```

---

## Example 5: Using Arrays

```javascript
let items = [];

if (items) {
    console.log("Array exists.");
}
```

Output:

```text
Array exists.
```

An empty array is still truthy because it is an object.

---

## Example 6: Using Objects

```javascript
let student = {};

if (student) {
    console.log("Object exists.");
}
```

Output:

```text
Object exists.
```

Even an empty object is truthy.

---

## Why Truthy and Falsy Values Matter

Truthy and falsy values allow developers to write shorter and more readable code.

Instead of writing:

```javascript
if (username !== "") {
    console.log("Welcome");
}
```

You can simply write:

```javascript
if (username) {
    console.log("Welcome");
}
```

This is a common pattern in modern JavaScript.

---

## Explicit Boolean Conversion

JavaScript provides the `Boolean()` function to show how a value is interpreted.

Examples:

```javascript
Boolean(0)
```

Result:

```text
false
```

---

```javascript
Boolean(100)
```

Result:

```text
true
```

---

```javascript
Boolean("")
```

Result:

```text
false
```

---

```javascript
Boolean("Hello")
```

Result:

```text
true
```

---

```javascript
Boolean([])
```

Result:

```text
true
```

---

```javascript
Boolean({})
```

Result:

```text
true
```

---

## Real-World Applications

Truthy and falsy values are commonly used in:

- Login forms
- Search boxes
- Online shopping carts
- Form validation
- API responses
- Configuration settings
- Feature toggles

Example:

```javascript
let searchQuery = "";

if (!searchQuery) {
    console.log("Please enter a search term.");
}
```

---

## Common Beginner Mistakes

### Assuming Empty Arrays Are Falsy

Incorrect assumption:

```javascript
if ([]) {
    // This DOES execute
}
```

An empty array is truthy.

---

### Assuming Empty Objects Are Falsy

Incorrect assumption:

```javascript
if ({}) {
    // This DOES execute
}
```

An empty object is also truthy.

---

### Confusing `"0"` with `0`

```javascript
Boolean("0")
```

Result:

```text
true
```

```javascript
Boolean(0)
```

Result:

```text
false
```

The string `"0"` is truthy, while the number `0` is falsy.

---

### Forgetting About `undefined`

Using an uninitialized variable in a condition evaluates to `false`.

---

## Best Practices

- Understand the complete list of falsy values.
- Use truthy and falsy checks to simplify code where appropriate.
- Be careful when checking arrays and objects.
- Use explicit comparisons when your program requires precision.
- Use `Boolean()` while learning to verify how values are evaluated.

---

> **Figure 5.10**
>
> **Truthy vs. Falsy Values**
>
> *(Insert a table or diagram separating common truthy values from the eight falsy values, with examples of each.)*

---

> **CodeTales Insight**
>
> Experienced JavaScript developers rely heavily on truthy and falsy values to write clean, expressive code. Understanding how JavaScript evaluates different values allows you to simplify conditional logic while avoiding subtle bugs caused by incorrect assumptions.

---

### Section Summary

In this section, you learned how JavaScript evaluates values as truthy or falsy when they appear in conditional expressions. You explored the complete list of falsy values, examined common truthy values, learned how to convert values using `Boolean()`, and discovered how truthy and falsy checks are used in real-world applications. Mastering this concept will help you write more concise, idiomatic, and reliable JavaScript code.

In the next section, you will apply everything you have learned by working through a collection of practical decision-making examples drawn from real-world programming scenarios.

## 5.11 Practical Examples

The best way to understand control flow is to apply it to realistic programming problems. In this section, you will explore practical examples that combine the concepts covered throughout this chapter, including `if`, `if...else`, `else if`, nested conditionals, `switch`, the ternary operator, and truthy/falsy values.

---

## Example 1: Age Verification

Determine whether a person is eligible to vote.

```javascript
let age = 20;

if (age >= 18) {
    console.log("You are eligible to vote.");
} else {
    console.log("You are not eligible to vote.");
}
```

Output:

```text
You are eligible to vote.
```

---

## Example 2: Student Grading System

Assign a letter grade based on a student's score.

```javascript
let score = 76;

if (score >= 70) {
    console.log("Grade: A");
} else if (score >= 60) {
    console.log("Grade: B");
} else if (score >= 50) {
    console.log("Grade: C");
} else {
    console.log("Grade: F");
}
```

Output:

```text
Grade: A
```

---

## Example 3: ATM Withdrawal

Allow a withdrawal only if the account balance is sufficient.

```javascript
let balance = 85000;
let withdrawal = 25000;

if (balance >= withdrawal) {
    balance -= withdrawal;
    console.log("Withdrawal successful.");
    console.log(`Remaining balance: ₦${balance}`);
} else {
    console.log("Insufficient funds.");
}
```

Output:

```text
Withdrawal successful.
Remaining balance: ₦60000
```

---

## Example 4: User Authentication

```javascript
let username = "admin";
let password = "password123";

if (username === "admin" && password === "password123") {
    console.log("Login successful.");
} else {
    console.log("Invalid username or password.");
}
```

Output:

```text
Login successful.
```

---

## Example 5: Online Shopping Discount

```javascript
let purchaseAmount = 125000;

if (purchaseAmount >= 100000) {
    console.log("10% discount applied.");
} else {
    console.log("No discount available.");
}
```

Output:

```text
10% discount applied.
```

---

## Example 6: Day Selection Using `switch`

```javascript
let day = 6;

switch (day) {
    case 1:
        console.log("Monday");
        break;

    case 2:
        console.log("Tuesday");
        break;

    case 3:
        console.log("Wednesday");
        break;

    case 4:
        console.log("Thursday");
        break;

    case 5:
        console.log("Friday");
        break;

    case 6:
        console.log("Saturday");
        break;

    case 7:
        console.log("Sunday");
        break;

    default:
        console.log("Invalid day.");
}
```

Output:

```text
Saturday
```

---

## Example 7: Traffic Light Controller

```javascript
let light = "red";

switch (light) {
    case "green":
        console.log("Go");
        break;

    case "yellow":
        console.log("Slow down");
        break;

    case "red":
        console.log("Stop");
        break;

    default:
        console.log("Invalid signal");
}
```

Output:

```text
Stop
```

---

## Example 8: Product Availability

```javascript
let stock = 15;

let status = stock > 0
    ? "Product Available"
    : "Out of Stock";

console.log(status);
```

Output:

```text
Product Available
```

---

## Example 9: Course Registration

A student can register only if they have completed the prerequisite course and paid their registration fees.

```javascript
let completedPrerequisite = true;
let feesPaid = true;

if (completedPrerequisite) {
    if (feesPaid) {
        console.log("Course registration successful.");
    } else {
        console.log("Please pay your registration fees.");
    }
} else {
    console.log("Complete the prerequisite course first.");
}
```

Output:

```text
Course registration successful.
```

---

## Example 10: Search Validation

```javascript
let searchQuery = "";

if (!searchQuery) {
    console.log("Please enter a search term.");
} else {
    console.log(`Searching for "${searchQuery}"...`);
}
```

Output:

```text
Please enter a search term.
```

---

## Example 11: Electricity Billing Category

```javascript
let units = 280;

if (units >= 500) {
    console.log("Premium tariff");
} else if (units >= 200) {
    console.log("Standard tariff");
} else {
    console.log("Basic tariff");
}
```

Output:

```text
Standard tariff
```

---

## Example 12: Weather Recommendation

```javascript
let weather = "Rainy";

switch (weather) {
    case "Sunny":
        console.log("Wear sunglasses.");
        break;

    case "Rainy":
        console.log("Carry an umbrella.");
        break;

    case "Cold":
        console.log("Wear a jacket.");
        break;

    default:
        console.log("Check today's forecast.");
}
```

Output:

```text
Carry an umbrella.
```

---

## Key Lessons from These Examples

These examples demonstrate several important principles:

- Choose the appropriate control structure for the problem.
- Keep conditions clear and easy to understand.
- Use meaningful variable names.
- Test both expected and unexpected inputs.
- Keep code properly indented and consistently formatted.
- Prefer readability over unnecessary complexity.

As your programs become larger, these practices will make your code easier to debug, maintain, and extend.

---

> **Figure 5.11**
>
> **Control Flow in Real-World Applications**
>
> *(Insert an infographic showing common applications of control flow, such as banking, education, e-commerce, healthcare, transportation, and authentication systems.)*

---

> **CodeTales Insight**
>
> Control flow is one of the foundations of software development. Every interactive application—from online banking platforms and mobile apps to e-commerce websites and games—depends on conditional logic to respond intelligently to user actions and changing conditions.

---

### Section Summary

In this section, you explored a variety of practical JavaScript programs that demonstrated how conditional statements are used in real-world applications. These examples combined the concepts introduced throughout the chapter and illustrated how thoughtful control flow leads to reliable, maintainable, and user-friendly software.

In the next section, you will examine common beginner mistakes related to conditional statements and learn how to avoid them.

## 5.12 Common Beginner Mistakes

Learning conditional statements is an important milestone in becoming a JavaScript developer. However, beginners often encounter mistakes that can lead to incorrect program behavior or difficult-to-find bugs.

Understanding these common pitfalls will help you write cleaner, more reliable code and improve your debugging skills.

---

## Mistake 1: Using Assignment (`=`) Instead of Comparison (`===`)

One of the most common errors is accidentally using the assignment operator (`=`) inside a condition.

Incorrect:

```javascript
let age = 20;

if (age = 18) {
    console.log("Adult");
}
```

In this example, `18` is assigned to `age`, and the expression evaluates to a truthy value.

Correct:

```javascript
let age = 20;

if (age === 18) {
    console.log("Adult");
}
```

Always use `===` when comparing values.

---

## Mistake 2: Forgetting Curly Braces

JavaScript allows braces to be omitted when only one statement follows an `if`.

Example:

```javascript
if (isLoggedIn)
    console.log("Welcome");
```

Although this is valid, adding another statement later can introduce bugs.

Recommended:

```javascript
if (isLoggedIn) {
    console.log("Welcome");
}
```

Using braces consistently improves readability and reduces mistakes.

---

## Mistake 3: Misunderstanding Truthy and Falsy Values

Some beginners believe only `true` and `false` can appear in conditions.

Example:

```javascript
let username = "";

if (username) {
    console.log("Welcome");
}
```

Nothing is displayed because an empty string is falsy.

Understanding truthy and falsy values helps explain this behavior.

---

## Mistake 4: Forgetting the `break` Statement in `switch`

Without `break`, execution continues into the next case.

Incorrect:

```javascript
let day = 1;

switch (day) {
    case 1:
        console.log("Monday");

    case 2:
        console.log("Tuesday");
}
```

Output:

```text
Monday
Tuesday
```

Correct:

```javascript
switch (day) {
    case 1:
        console.log("Monday");
        break;

    case 2:
        console.log("Tuesday");
        break;
}
```

---

## Mistake 5: Writing Conditions in the Wrong Order

Conditions should usually be arranged from the most specific to the most general.

Incorrect:

```javascript
let score = 95;

if (score >= 50) {
    console.log("Pass");
} else if (score >= 90) {
    console.log("Excellent");
}
```

Output:

```text
Pass
```

Correct:

```javascript
if (score >= 90) {
    console.log("Excellent");
} else if (score >= 50) {
    console.log("Pass");
}
```

---

## Mistake 6: Overusing Nested Conditionals

Deep nesting makes code difficult to read.

Example:

```javascript
if (a) {
    if (b) {
        if (c) {
            if (d) {
                console.log("Done");
            }
        }
    }
}
```

When appropriate, combine conditions:

```javascript
if (a && b && c && d) {
    console.log("Done");
}
```

---

## Mistake 7: Using `switch` for Range Comparisons

Incorrect:

```javascript
switch (score) {
    case score >= 70:
        console.log("A");
}
```

A `switch` statement compares values, not ranges.

Use `if...else` instead.

---

## Mistake 8: Overusing the Ternary Operator

Nested ternary operators quickly become difficult to understand.

Difficult to read:

```javascript
let grade =
    score >= 70
        ? "A"
        : score >= 60
            ? "B"
            : score >= 50
                ? "C"
                : "F";
```

For multiple conditions, `if...else if` is usually a better choice.

---

## Mistake 9: Ignoring Unexpected Input

Programs should be prepared for invalid or unexpected values.

Example:

```javascript
let role = "manager";

switch (role) {
    case "admin":
        console.log("Admin");
        break;

    case "editor":
        console.log("Editor");
        break;

    default:
        console.log("Unknown role.");
}
```

Including a `default` case improves reliability.

---

## Mistake 10: Not Testing Both Outcomes

Many beginners test only the expected result.

Always test:

- Conditions that evaluate to `true`
- Conditions that evaluate to `false`
- Boundary values
- Unexpected input

Testing both success and failure cases helps uncover hidden bugs.

---

## Tips for Avoiding These Mistakes

- Use `===` instead of `==` whenever possible.
- Always include curly braces, even for a single statement.
- Keep conditions simple and readable.
- Arrange `else if` conditions carefully.
- Use `switch` only when comparing one expression against fixed values.
- Avoid unnecessary nesting.
- Include `break` statements in every `switch` case unless fall-through is intentional.
- Test your code with different inputs before considering it complete.

---

> **Figure 5.12**
>
> **Common Conditional Programming Mistakes**
>
> *(Insert a table with two columns: "Mistake" and "Recommended Solution," summarizing the issues discussed in this section.)*

---

> **CodeTales Insight**
>
> Every programmer makes mistakes, especially while learning. The key difference between beginners and experienced developers is not that professionals avoid errors entirely, but that they recognize common patterns, test their code thoroughly, and continually refine their solutions.

---

### Section Summary

In this section, you examined the most common mistakes beginners make when writing conditional statements in JavaScript. You learned how to identify these errors, understand why they occur, and apply practical techniques to avoid them. Developing these habits early will help you write more reliable, maintainable, and professional JavaScript programs.

In the next section, you will explore best practices for writing clean, readable, and efficient conditional logic.

## 5.13 Best Practices

Writing code that works is only the first step in becoming a proficient JavaScript developer. Professional developers also strive to write code that is **readable, maintainable, efficient, and easy to debug**.

The following best practices will help you create conditional logic that is clear, reliable, and easy for others—including your future self—to understand.

---

## 1. Write Clear and Readable Conditions

A condition should communicate its purpose immediately.

Instead of writing complicated expressions, keep them as simple as possible.

Poor example:

```javascript
if ((score >= 50 && attendance >= 75) || isAdministrator) {
    console.log("Access granted.");
}
```

Improved example:

```javascript
let passedCourse = score >= 50 && attendance >= 75;

if (passedCourse || isAdministrator) {
    console.log("Access granted.");
}
```

Descriptive variables make conditions easier to understand.

---

## 2. Use Meaningful Variable Names

Avoid generic names such as:

```javascript
let x = true;
```

Instead, choose names that describe the condition:

```javascript
let isLoggedIn = true;
let hasPermission = false;
let paymentSuccessful = true;
```

Well-named variables reduce the need for comments.

---

## 3. Prefer Strict Equality (`===`)

Use strict equality whenever possible.

Recommended:

```javascript
if (age === 18) {
    console.log("Exactly eighteen.");
}
```

Avoid:

```javascript
if (age == 18) {
    console.log("Exactly eighteen.");
}
```

Strict equality avoids unexpected type coercion.

---

## 4. Always Use Curly Braces

Although braces are optional for single statements, always include them.

Recommended:

```javascript
if (isLoggedIn) {
    console.log("Welcome!");
}
```

Consistent use of braces improves readability and helps prevent future bugs.

---

## 5. Avoid Deeply Nested Conditionals

Deep nesting makes programs difficult to follow.

Instead of:

```javascript
if (loggedIn) {
    if (hasPermission) {
        if (accountActive) {
            console.log("Access granted.");
        }
    }
}
```

Consider:

```javascript
if (loggedIn && hasPermission && accountActive) {
    console.log("Access granted.");
}
```

When appropriate, combine related conditions using logical operators.

---

## 6. Choose the Right Control Structure

Use the structure that best fits the problem.

Use `if...else` when:

- Comparing ranges
- Combining logical conditions
- Evaluating expressions

Use `switch` when:

- Comparing one value against many fixed options
- Building menus
- Processing commands

Selecting the appropriate structure improves readability.

---

## 7. Keep Conditions Focused

Avoid placing too many unrelated checks inside a single condition.

Instead of:

```javascript
if (loggedIn && hasPermission && balance > 0 && age >= 18 && accountVerified) {
    console.log("Approved");
}
```

Consider breaking the logic into smaller parts:

```javascript
let canAccess = loggedIn && hasPermission;
let canProceed = balance > 0 && age >= 18 && accountVerified;

if (canAccess && canProceed) {
    console.log("Approved");
}
```

---

## 8. Use the Ternary Operator Wisely

The ternary operator is ideal for short, simple decisions.

Good example:

```javascript
let result = score >= 50 ? "Pass" : "Fail";
```

For more complex logic, use `if...else` to improve readability.

---

## 9. Always Include a `default` Case

Every `switch` statement should include a `default` block to handle unexpected values.

```javascript
switch (role) {
    case "admin":
        console.log("Administrator");
        break;

    default:
        console.log("Unknown role.");
}
```

This makes programs more robust.

---

## 10. Test All Possible Outcomes

Don't test only the expected result.

Verify:

- True conditions
- False conditions
- Boundary values
- Invalid input
- Unexpected values

Thorough testing improves software reliability.

---

## 11. Maintain Consistent Indentation

Consistent formatting makes code easier to read.

Example:

```javascript
if (loggedIn) {
    console.log("Welcome");
} else {
    console.log("Please log in.");
}
```

Proper indentation clearly shows program structure.

---

## 12. Write Code for Humans

Computers execute code exactly as written, but people must read and maintain it.

Favor clarity over cleverness.

A straightforward solution is usually better than a shorter but confusing one.

---

## Professional Checklist

Before completing a conditional statement, ask yourself:

- Are the conditions easy to understand?
- Have I used meaningful variable names?
- Did I choose the appropriate control structure?
- Have I avoided unnecessary nesting?
- Did I use strict equality where appropriate?
- Are braces used consistently?
- Have I tested all possible outcomes?
- Would another developer understand this code quickly?

If the answer to each question is "Yes," your code is likely to be clear and maintainable.

---

> **Figure 5.13**
>
> **Characteristics of High-Quality Conditional Logic**
>
> *(Insert a diagram highlighting readability, simplicity, maintainability, correctness, consistency, and testability as the key qualities of well-written conditional code.)*

---

> **CodeTales Insight**
>
> Great developers are recognized not by how much code they write, but by how clearly they express their ideas through code. Readable, well-structured conditional logic is easier to debug, easier to extend, and far more valuable than overly clever solutions.

---

### Section Summary

In this section, you learned a collection of best practices for writing clean and professional conditional logic in JavaScript. These practices include choosing meaningful variable names, preferring strict equality, avoiding deep nesting, selecting the appropriate control structure, testing thoroughly, and writing code that is easy to read and maintain. By adopting these habits early, you will develop programming skills that scale well as your applications become more complex.

In the next section, you will explore real-world applications of conditional statements and see how control flow powers the behavior of modern software systems.

## 5.14 Real-World Applications

Conditional statements are among the most frequently used programming constructs in software development. Nearly every modern application relies on decision-making to respond to user input, validate data, enforce security rules, and automate business processes.

Whether you are developing a simple website or a large enterprise application, control flow enables your software to make intelligent decisions.

This section explores several real-world scenarios where conditional statements play a critical role.

---

## 1. User Authentication

Most applications require users to log in before accessing protected resources.

A typical authentication process checks:

- Whether the username exists.
- Whether the password is correct.
- Whether the account is active.
- Whether two-factor authentication has been completed.

Example:

```javascript
let username = "admin";
let password = "password123";
let accountActive = true;

if (
    username === "admin" &&
    password === "password123" &&
    accountActive
) {
    console.log("Login successful.");
} else {
    console.log("Access denied.");
}
```

Without conditional statements, secure authentication would not be possible.

---

## 2. Online Banking Systems

Banks constantly evaluate conditions before processing transactions.

Examples include:

- Is the account active?
- Is there enough money?
- Has the daily withdrawal limit been reached?
- Is the transaction suspicious?

Example:

```javascript
let balance = 50000;
let withdrawal = 15000;

if (balance >= withdrawal) {
    balance -= withdrawal;
    console.log("Transaction successful.");
} else {
    console.log("Insufficient funds.");
}
```

---

## 3. E-Commerce Websites

Online stores use conditional logic throughout the shopping experience.

Examples include:

- Product availability
- Discount eligibility
- Free shipping qualification
- Coupon validation
- Payment verification

Example:

```javascript
let orderTotal = 120000;

if (orderTotal >= 100000) {
    console.log("Free shipping applied.");
} else {
    console.log("Shipping charges apply.");
}
```

---

## 4. Educational Platforms

Learning management systems use conditional statements to:

- Determine whether students passed an examination.
- Unlock the next lesson.
- Award certificates.
- Restrict access until prerequisites are completed.

Example:

```javascript
let finalScore = 84;

if (finalScore >= 50) {
    console.log("Course completed.");
} else {
    console.log("Course not completed.");
}
```

---

## 5. Healthcare Applications

Medical software evaluates conditions to improve patient care.

Examples include:

- Determining emergency priority.
- Checking appointment availability.
- Validating patient information.
- Triggering alerts for abnormal test results.

Example:

```javascript
let temperature = 39.2;

if (temperature >= 38) {
    console.log("Possible fever detected.");
} else {
    console.log("Temperature is within the normal range.");
}
```

---

## 6. Transportation Systems

Conditional logic powers many transportation services.

Examples include:

- Traffic light controllers
- Ride-booking applications
- Airline booking systems
- Train scheduling
- Navigation software

Example:

```javascript
let trafficLight = "Red";

switch (trafficLight) {
    case "Green":
        console.log("Proceed");
        break;

    case "Yellow":
        console.log("Prepare to stop");
        break;

    case "Red":
        console.log("Stop");
        break;

    default:
        console.log("Signal unavailable");
}
```

---

## 7. Social Media Platforms

Social networking applications make thousands of decisions every second.

Conditional statements determine:

- Which posts appear in a user's feed.
- Whether comments are permitted.
- Which notifications should be displayed.
- Whether content violates community guidelines.

Example:

```javascript
let isLoggedIn = true;

if (isLoggedIn) {
    console.log("Display personalized news feed.");
} else {
    console.log("Show login page.");
}
```

---

## 8. Smart Home Systems

Smart devices automatically respond to environmental conditions.

Examples include:

- Turning lights on at night.
- Adjusting room temperature.
- Locking doors automatically.
- Detecting motion.

Example:

```javascript
let motionDetected = true;
let isNight = true;

if (motionDetected && isNight) {
    console.log("Turn on outdoor lights.");
}
```

---

## 9. Mobile Applications

Mobile apps use conditional logic for many everyday features.

Examples include:

- Internet connection checks.
- Permission requests.
- Battery-saving mode.
- GPS availability.
- Push notifications.

Example:

```javascript
let internetAvailable = false;

if (internetAvailable) {
    console.log("Synchronizing data...");
} else {
    console.log("Working offline.");
}
```

---

## 10. Artificial Intelligence Applications

AI systems rely heavily on decision-making.

Examples include:

- Chatbots selecting appropriate responses.
- Recommendation systems suggesting products or videos.
- Spam email detection.
- Fraud detection.
- Image classification.

Although modern AI uses advanced algorithms, many systems still rely on conditional logic to guide workflows, validate results, and handle exceptional situations.

---

## Why Control Flow Is Essential

Conditional statements allow software to:

- Adapt to user input.
- Enforce business rules.
- Improve security.
- Prevent invalid operations.
- Automate repetitive decisions.
- Create personalized user experiences.
- Respond intelligently to changing conditions.

Without control flow, software would execute the same instructions regardless of the situation, making it impossible to build interactive applications.

---

> **Figure 5.14**
>
> **Control Flow Across Industries**
>
> *(Insert an infographic illustrating the use of conditional logic in banking, healthcare, education, e-commerce, transportation, social media, smart homes, and artificial intelligence.)*

---

> **CodeTales Insight**
>
> Every time you withdraw money from an ATM, shop online, unlock your smartphone, stream a movie, or interact with a chatbot, conditional statements are working behind the scenes. Mastering control flow is one of the most important steps toward becoming a professional software developer because it enables programs to respond intelligently to real-world situations.

---

### Section Summary

In this section, you explored how conditional statements are applied across a wide range of real-world systems, including banking, healthcare, education, transportation, e-commerce, mobile applications, and artificial intelligence. These examples demonstrate that control flow is not merely a programming concept—it is a fundamental building block of modern software that enables applications to make decisions, enforce rules, and respond dynamically to users and their environments.

## 5.15 Chapter Summary

In this chapter, you explored **control flow**, one of the fundamental concepts in JavaScript programming. Control flow enables programs to make decisions by executing different blocks of code based on specific conditions. Without control flow, every JavaScript program would execute statements sequentially, making it impossible to build interactive, responsive, and intelligent applications.

You began by learning how Boolean values (`true` and `false`) form the foundation of decision-making in JavaScript. You then explored how comparison operators and logical operators produce Boolean expressions that can be evaluated in conditional statements.

Next, you learned how to use the `if` statement to execute code only when a condition is true. You expanded this knowledge by studying the `if...else` statement, which allows programs to choose between two alternative execution paths, and the `else if` statement, which enables programs to evaluate multiple conditions efficiently.

You also examined nested conditional statements, where one decision is placed inside another, making it possible to model more sophisticated decision-making processes.

The chapter introduced the `switch` statement as an alternative to long `else if` chains when comparing a single expression against multiple fixed values. You learned the purpose of the `break` statement, the importance of the `default` case, and situations where `switch` statements improve readability.

You revisited the conditional (ternary) operator and discovered how it provides a concise alternative to simple `if...else` statements while recognizing the importance of maintaining readability.

Another essential concept covered in this chapter was **truthy and falsy values**. You learned that JavaScript evaluates many non-Boolean values in conditional expressions and identified the complete set of falsy values along with examples of common truthy values.

Through numerous practical examples, you applied conditional logic to realistic programming scenarios, including authentication systems, grading applications, banking transactions, shopping systems, and search validation. These examples demonstrated how control flow is used in real-world software.

You also explored common beginner mistakes, such as confusing assignment with comparison, forgetting `break` statements, overusing nested conditionals, and misunderstanding truthy and falsy values. Understanding these pitfalls will help you avoid bugs and write more reliable programs.

Finally, you examined professional best practices for writing clean, maintainable conditional logic and discovered how conditional statements power applications across industries such as finance, healthcare, education, transportation, e-commerce, social media, and artificial intelligence.

By completing this chapter, you have developed a strong foundation in JavaScript decision-making. These skills will continue to play an important role throughout the remainder of this book as you learn about loops, functions, objects, asynchronous programming, and modern JavaScript application development.

---

### What You Learned

By the end of this chapter, you should now be able to:

- Explain the purpose of control flow in JavaScript.
- Write Boolean expressions using comparison and logical operators.
- Use `if`, `if...else`, and `else if` statements effectively.
- Create and understand nested conditional statements.
- Use the `switch` statement appropriately.
- Decide when to use `if...else` versus `switch`.
- Apply the conditional (ternary) operator correctly.
- Distinguish between truthy and falsy values.
- Write conditional logic for real-world applications.
- Recognize and avoid common programming mistakes.
- Apply professional best practices when writing conditional statements.

These learning outcomes prepare you for the next major topic in JavaScript: **iteration**, where programs perform tasks repeatedly using loops.

## 5.16 Looking Ahead

Congratulations on completing Chapter 5!

You have taken an important step in your JavaScript journey by learning how programs make decisions. Control flow is one of the core building blocks of programming, enabling software to respond intelligently to user input, validate data, enforce business rules, and automate complex processes.

Throughout this chapter, you learned how to use conditional statements such as `if`, `if...else`, `else if`, and `switch` to direct the flow of program execution. You also explored the conditional (ternary) operator, truthy and falsy values, practical programming examples, common mistakes, and professional best practices.

These concepts will continue to appear throughout the rest of this book. Whether you are validating user input, handling application states, processing data, or building interactive user interfaces, conditional logic will remain one of your most valuable programming tools.

However, making decisions is only part of the story.

Many programming tasks require the same operation to be performed repeatedly. Imagine displaying every item in a shopping cart, processing thousands of records in a database, validating every field in a form, or generating reports from large datasets. Writing the same code repeatedly would be inefficient, error-prone, and difficult to maintain.

This is where **loops** become essential.

In the next chapter, you will learn how JavaScript performs repetitive tasks efficiently using iteration. You will explore several looping structures, understand how they work, and discover when each one is most appropriate.

Among the topics you will study are:

- The purpose of loops and iteration
- The `for` loop
- The `while` loop
- The `do...while` loop
- Loop control statements such as `break` and `continue`
- Nested loops
- Common looping mistakes
- Best practices for writing efficient loops
- Real-world applications of iteration

By combining the decision-making skills from this chapter with the iteration techniques in the next, you will be able to build programs that are not only intelligent but also efficient and scalable.

As you continue your JavaScript journey, remember that becoming a skilled developer is not about memorizing syntax—it is about understanding how to solve problems logically and writing code that is clear, reliable, and maintainable.

Take time to complete the review questions, programming exercises, and mini project at the end of this chapter before moving on. Practicing what you have learned is the most effective way to strengthen your programming skills.

The next chapter awaits—let's learn how to make JavaScript repeat tasks efficiently and unlock another essential programming technique.

# Chapter 5 – Key Takeaways

This chapter introduced **control flow**, the mechanism that enables JavaScript programs to make decisions based on conditions. By mastering conditional statements, you can create applications that respond intelligently to user input, enforce business rules, and adapt to different situations.

The most important ideas from this chapter are summarized below.

---

## Control Flow

- Control flow determines the order in which JavaScript executes statements.
- Conditional statements allow programs to make decisions.
- Most interactive applications rely on conditional logic.

---

## Boolean Logic

- Boolean values have only two possible states: `true` and `false`.
- Comparison operators produce Boolean results.
- Logical operators combine or modify Boolean expressions.
- Every conditional statement depends on Boolean evaluation.

---

## The `if` Statement

- Executes code only when a condition evaluates to `true`.
- Ideal for single-condition decisions.
- Keeps decision-making simple and straightforward.

Example:

```javascript
if (age >= 18) {
    console.log("Adult");
}
```

---

## The `if...else` Statement

- Chooses between two possible execution paths.
- Executes one block when the condition is true and another when it is false.

Example:

```javascript
if (loggedIn) {
    console.log("Welcome!");
} else {
    console.log("Please log in.");
}
```

---

## The `else if` Statement

- Evaluates multiple conditions in sequence.
- Only the first matching condition executes.
- Arrange conditions from the most specific to the most general.

---

## Nested Conditional Statements

- Allow one decision to be placed inside another.
- Useful when a second condition depends on the first.
- Avoid excessive nesting to keep code readable.

---

## The `switch` Statement

- Best suited for comparing one expression against multiple fixed values.
- Always include `break` statements unless fall-through is intentional.
- Include a `default` case to handle unexpected values.

---

## Choosing Between `if...else` and `switch`

Use **`if...else`** when:

- Comparing ranges.
- Combining logical conditions.
- Evaluating complex expressions.

Use **`switch`** when:

- Comparing one variable against many fixed values.
- Creating menus.
- Processing commands.
- Handling predefined categories.

---

## Conditional (Ternary) Operator

- Provides a concise alternative to simple `if...else` statements.
- Best used for short, readable expressions.
- Avoid deeply nested ternary operators.

Example:

```javascript
let result = score >= 50 ? "Pass" : "Fail";
```

---

## Truthy and Falsy Values

Falsy values include:

- `false`
- `0`
- `-0`
- `0n`
- `""` (empty string)
- `null`
- `undefined`
- `NaN`

All other values are truthy.

Understanding truthy and falsy values allows you to write more concise and idiomatic JavaScript code.

---

## Common Beginner Mistakes

Avoid:

- Using `=` instead of `===`.
- Forgetting `break` in `switch`.
- Writing conditions in the wrong order.
- Overusing nested conditionals.
- Misunderstanding truthy and falsy values.
- Omitting the `default` case in `switch`.
- Testing only one outcome.

---

## Best Practices

- Prefer strict equality (`===`).
- Use meaningful variable names.
- Always include curly braces.
- Keep conditions simple.
- Avoid unnecessary nesting.
- Choose the appropriate control structure.
- Test both expected and unexpected inputs.
- Prioritize readability over cleverness.

---

## Real-World Applications

Conditional logic powers applications such as:

- Authentication systems
- Banking software
- E-commerce platforms
- Educational systems
- Healthcare applications
- Transportation systems
- Mobile applications
- Artificial intelligence systems

---

## Chapter Review Checklist

Before moving to the next chapter, make sure you can confidently:

- Explain control flow.
- Write Boolean expressions.
- Use `if`, `if...else`, and `else if` statements.
- Create nested conditional statements.
- Use `switch` statements effectively.
- Decide when to use `if...else` versus `switch`.
- Apply the ternary operator appropriately.
- Identify truthy and falsy values.
- Debug common conditional logic errors.
- Write readable and maintainable conditional code.

If you can confidently complete each item on this checklist, you are well prepared to begin **Chapter 6: Loops and Iteration**, where you will learn how to execute code repeatedly and efficiently.

# Glossary

This glossary defines the key terms introduced in Chapter 5. Review these definitions whenever you need a quick refresher on JavaScript control flow and conditional statements.

---

## Assignment Operator (`=`)

An operator used to assign a value to a variable. It should not be confused with comparison operators such as `===`.

Example:

```javascript
let age = 20;
```

---

## Boolean

A data type with only two possible values: `true` and `false`. Boolean values are the foundation of conditional logic.

---

## Boolean Expression

An expression that evaluates to either `true` or `false`.

Example:

```javascript
age >= 18
```

---

## Comparison Operator

An operator used to compare two values. Common comparison operators include:

- `===`
- `!==`
- `>`
- `<`
- `>=`
- `<=`

Comparison operators return Boolean values.

---

## Condition

A Boolean expression evaluated to determine which block of code should execute.

---

## Conditional Logic

Programming logic that allows a program to make decisions based on one or more conditions.

---

## Conditional (Ternary) Operator

A compact operator that chooses between two expressions based on a condition.

Syntax:

```javascript
condition ? valueIfTrue : valueIfFalse
```

---

## Control Flow

The order in which JavaScript executes statements. Conditional statements and loops are both examples of control flow mechanisms.

---

## `default`

The optional block executed in a `switch` statement when no case matches the evaluated expression.

---

## `else`

The block executed when the condition of an `if` statement evaluates to `false`.

---

## `else if`

A conditional statement used to evaluate additional conditions after a previous condition evaluates to `false`.

---

## Falsy Value

A value that JavaScript treats as `false` in a Boolean context.

Falsy values include:

- `false`
- `0`
- `-0`
- `0n`
- `""`
- `null`
- `undefined`
- `NaN`

---

## `if` Statement

A conditional statement that executes code only when a specified condition evaluates to `true`.

---

## Logical Operator

An operator used to combine or modify Boolean expressions.

Common logical operators include:

- `&&` (AND)
- `||` (OR)
- `!` (NOT)

---

## Nested Conditional

A conditional statement placed inside another conditional statement.

---

## `switch` Statement

A control flow statement that compares one expression against multiple possible values using `case` labels.

---

## `break`

A statement that immediately exits a `switch` statement after a matching case has executed.

---

## Case

A labeled branch inside a `switch` statement that executes when its value matches the evaluated expression.

---

## Strict Equality (`===`)

A comparison operator that checks both the value and the data type of two operands.

Example:

```javascript
5 === "5"
```

Result:

```text
false
```

---

## Truthy Value

Any value that JavaScript treats as `true` when evaluated in a Boolean context.

Examples include:

- Non-zero numbers
- Non-empty strings
- Arrays
- Objects
- Functions

---

## Type Coercion

The automatic conversion of one data type to another during certain operations. Using strict equality (`===`) helps avoid unexpected results caused by type coercion.

---

## Flowchart

A diagram that visually represents the sequence of decisions and actions in a program. Flowcharts are commonly used to illustrate the behavior of conditional statements.

---

## Branch

One possible execution path chosen by a conditional statement based on the result of a condition.

---

## Readability

The ease with which humans can understand source code. Readable code uses meaningful variable names, consistent formatting, and clear conditional logic.

---

## Maintainability

The quality of code that makes it easy to modify, debug, extend, and understand over time.

---

## Decision Structure

A programming construct that determines which block of code executes based on one or more conditions. Examples include `if`, `if...else`, `else if`, and `switch`.

---

## Boundary Value

A value at the edge of a valid range that should be tested to ensure conditional logic behaves correctly.

Example:

If the passing score is `50`, important boundary values include `49`, `50`, and `51`.

---

## Expression

A combination of values, variables, operators, and function calls that JavaScript evaluates to produce a single value.

Example:

```javascript
score >= 50
```

---

## Statement

A complete instruction that JavaScript executes.

Example:

```javascript
console.log("Hello, World!");
```

---

## Summary

The concepts introduced in this chapter form the foundation of decision-making in JavaScript. A solid understanding of these terms will make it easier to write, debug, and maintain conditional logic throughout the rest of this book and in your own software projects.

# Review Questions

The following questions are designed to help you assess your understanding of the concepts covered in this chapter. Try to answer each question without referring to the chapter first. If you struggle with a question, revisit the relevant section before continuing.

---

## Part A – Conceptual Questions

1. What is control flow, and why is it important in JavaScript programming?

2. What is a Boolean value?

3. What is a Boolean expression?

4. What is the difference between the assignment operator (`=`) and the strict equality operator (`===`)?

5. What is the purpose of an `if` statement?

6. When should you use an `if...else` statement instead of a simple `if` statement?

7. How does an `else if` statement differ from multiple separate `if` statements?

8. What is a nested conditional statement?

9. What is the purpose of the `switch` statement?

10. Why is the `break` statement important inside a `switch` statement?

11. What happens if no case matches in a `switch` statement?

12. What is the purpose of the `default` case?

13. When is a `switch` statement preferable to an `if...else if` chain?

14. What is the conditional (ternary) operator?

15. When should you use the ternary operator?

16. What is the difference between truthy and falsy values?

17. List all the falsy values in JavaScript.

18. Why are empty arrays (`[]`) considered truthy?

19. Why are empty objects (`{}`) considered truthy?

20. Why is readability important when writing conditional logic?

---

## Part B – Understanding Code

Study each code snippet and predict its output before running it.

### Question 21

```javascript
let age = 16;

if (age >= 18) {
    console.log("Adult");
} else {
    console.log("Minor");
}
```

What will be displayed?

---

### Question 22

```javascript
let score = 65;

if (score >= 70) {
    console.log("A");
} else if (score >= 60) {
    console.log("B");
} else {
    console.log("F");
}
```

What is the output?

---

### Question 23

```javascript
let role = "editor";

switch (role) {
    case "admin":
        console.log("Administrator");
        break;

    case "editor":
        console.log("Editor");
        break;

    default:
        console.log("Unknown");
}
```

What will be printed?

---

### Question 24

```javascript
let username = "";

if (username) {
    console.log("Welcome");
} else {
    console.log("Enter username");
}
```

What is the output?

---

### Question 25

```javascript
let number = 0;

if (number) {
    console.log("Truthy");
} else {
    console.log("Falsy");
}
```

Explain the result.

---

## Part C – Short Answer Questions

26. Explain the difference between `==` and `===`.

27. Why is strict equality generally recommended?

28. Give three examples of situations where nested conditionals are useful.

29. Describe two situations where a `switch` statement improves code readability.

30. Why is testing both true and false conditions important?

31. What problems can arise from deeply nested conditional statements?

32. Why is using meaningful variable names considered a best practice?

33. Explain why the following code may produce unexpected results:

```javascript
if (age = 18) {
    console.log("Adult");
}
```

34. Give two examples of real-world software that relies heavily on conditional logic.

35. Why should every `switch` statement include a `default` case?

---

## Part D – Critical Thinking

36. Suppose you are developing an online banking application. Which conditional statements would you use to verify:

- A valid username
- A correct password
- Sufficient account balance
- Daily withdrawal limit

Explain your reasoning.

---

37. Imagine you are building an online learning platform.

List at least five decisions the software would need to make using conditional statements.

---

38. Explain why conditional statements are essential for creating interactive applications.

---

39. Describe how truthy and falsy values simplify JavaScript code.

---

40. In your own words, summarize what you learned in this chapter and explain how conditional statements contribute to modern software development.

# Programming Exercises

Complete the following exercises without looking at the sample solutions in the chapter. Practice is essential for developing confidence in writing conditional logic.

---

## Beginner Exercises

### Exercise 1: Even or Odd

Write a program that determines whether a number is even or odd.

Example:

```text
Input: 14
Output: Even
```

---

### Exercise 2: Voting Eligibility

Write a program that checks whether a person is eligible to vote.

Assume the voting age is **18 years**.

Example:

```text
Input: 22
Output: Eligible to vote
```

---

### Exercise 3: Positive, Negative, or Zero

Write a program that determines whether a number is:

- Positive
- Negative
- Zero

---

### Exercise 4: Pass or Fail

Write a program that accepts a student's score.

If the score is **50 or above**, display:

```text
Pass
```

Otherwise display:

```text
Fail
```

---

### Exercise 5: Largest Number

Write a program that compares two numbers and displays the larger one.

---

## Intermediate Exercises

### Exercise 6: Grade Calculator

Write a program that assigns grades using the following scale:

| Score | Grade |
|--------|-------|
| 70–100 | A |
| 60–69 | B |
| 50–59 | C |
| Below 50 | F |

---

### Exercise 7: Leap Year Checker

Write a program that determines whether a given year is a leap year.

Research the leap year rules if necessary.

---

### Exercise 8: Login Validation

Create a simple login program.

Requirements:

- Verify username.
- Verify password.
- Display an appropriate success or error message.

---

### Exercise 9: ATM Withdrawal

Given:

- Account balance
- Withdrawal amount

Display whether the withdrawal is successful or rejected due to insufficient funds.

---

### Exercise 10: Day of the Week

Use a `switch` statement to display the day of the week for numbers **1–7**.

Example:

```text
Input: 5
Output: Friday
```

---

## Advanced Exercises

### Exercise 11: Electricity Billing

Write a program that assigns customers to one of the following tariff categories:

| Units Consumed | Tariff |
|----------------|---------|
| Below 200 | Basic |
| 200–499 | Standard |
| 500 and above | Premium |

---

### Exercise 12: Shipping Cost Calculator

Requirements:

- Orders of **₦100,000 or more** receive free shipping.
- Otherwise charge **₦5,000**.

Display both the shipping cost and the total amount payable.

---

### Exercise 13: Simple Calculator

Use a `switch` statement to perform:

- Addition
- Subtraction
- Multiplication
- Division

The user selects the operation.

---

### Exercise 14: Movie Ticket Pricing

Ticket prices:

- Child (under 13): ₦2,000
- Teen (13–17): ₦3,000
- Adult (18–59): ₦5,000
- Senior (60+): ₦2,500

Write a program that determines the correct ticket price.

---

### Exercise 15: Student Admission

A student is admitted only if:

- Score ≥ 70
- Required documents submitted
- Registration fee paid

Display the appropriate admission decision.

---

## Debugging Exercises

Identify and correct the errors in the following programs.

---

### Exercise 16

```javascript
let age = 20;

if (age = 18) {
    console.log("Adult");
}
```

---

### Exercise 17

```javascript
let role = "admin";

switch (role) {
    case "admin":
        console.log("Administrator");

    case "editor":
        console.log("Editor");
}
```

---

### Exercise 18

```javascript
let score = 90;

if (score >= 50) {
    console.log("Pass");
} else if (score >= 90) {
    console.log("Excellent");
}
```

---

### Exercise 19

```javascript
let username = "";

if (username === true) {
    console.log("Welcome");
}
```

---

### Exercise 20

```javascript
let stock = 10

if (stock > 0)
console.log("Available")
else
console.log("Out of Stock")
```

Rewrite the code using recommended formatting and best practices.

---

## Reflection Questions

After completing the exercises, consider the following:

1. Which exercise did you find most challenging?

2. Which conditional statement did you use most frequently?

3. When did you choose `switch` instead of `if...else`?

4. Did you encounter any bugs? How did you debug them?

5. How could you improve the readability of your solutions?

6. Which real-world application from this chapter inspired your solutions?

---

## Stretch Goal

Choose **three** of the programs above and improve them by:

- Validating user input.
- Handling invalid values gracefully.
- Using meaningful variable names.
- Adding helpful comments where appropriate.
- Testing both valid and invalid inputs.

This extra practice will help you develop habits that professional JavaScript developers use every day.

# Challenge Exercises

The following exercises are more open-ended than the programming exercises. They are designed to strengthen your problem-solving skills by requiring you to combine multiple concepts from this chapter. In many cases, there is more than one correct solution.

Before writing any code:

1. Read the problem carefully.
2. Identify the conditions that must be checked.
3. Decide which control structure (`if...else`, `switch`, or the ternary operator) is most appropriate.
4. Test your solution with different inputs, including invalid values.

---

## Challenge 1: Nigerian University Grade Classification

Write a program that accepts a student's score (0–100).

Display:

| Score | Grade |
|--------|-------|
| 70–100 | A |
| 60–69 | B |
| 50–59 | C |
| 45–49 | D |
| 40–44 | E |
| Below 40 | F |

Additional Requirements:

- Reject scores less than 0 or greater than 100.
- Display an appropriate error message for invalid input.

---

## Challenge 2: ATM Transaction Simulator

Create a simple ATM program.

Requirements:

- Verify the correct PIN.
- Check that the withdrawal amount is greater than zero.
- Ensure the account has enough money.
- Reject withdrawals above the daily limit.
- Display the remaining balance after a successful withdrawal.

---

## Challenge 3: Online Shopping Checkout

Create a checkout system.

Requirements:

- Validate the shopping cart is not empty.
- Apply a **10% discount** for purchases of ₦100,000 or more.
- Apply free shipping for orders above ₦150,000.
- Display:
  - Original total
  - Discount
  - Shipping fee
  - Final amount payable

---

## Challenge 4: Student Admission Decision

Determine whether a student should be admitted.

Admission Requirements:

- Score ≥ 70
- Required documents submitted
- Registration fee paid
- Minimum age of 16 years

Display an explanation if admission is denied.

---

## Challenge 5: Weather Advisory System

Write a program that recommends what a user should do based on the weather.

Possible weather conditions:

- Sunny
- Rainy
- Windy
- Cold
- Hot
- Stormy

Provide a suitable recommendation for each condition using a `switch` statement.

---

## Challenge 6: Cinema Ticket System

Determine ticket prices using the following rules:

| Age | Price |
|-----|-------|
| Under 13 | ₦2,000 |
| 13–17 | ₦3,000 |
| 18–59 | ₦5,000 |
| 60+ | ₦2,500 |

Additional Requirements:

- Apply a 20% discount on Wednesdays.
- Display both the original price and the discounted price (if applicable).

---

## Challenge 7: Password Strength Checker

Classify passwords as:

- Weak
- Moderate
- Strong

Consider:

- Minimum length
- Uppercase letters
- Lowercase letters
- Numbers
- Special characters

*Hint:* At this stage, focus on conditional logic. You will learn more advanced string processing techniques in later chapters.

---

## Challenge 8: Electricity Billing Assistant

Determine a customer's electricity tariff.

Requirements:

- Classify usage as Basic, Standard, or Premium.
- Apply a surcharge if consumption exceeds 800 units.
- Display a warning for unusually high consumption.

---

## Challenge 9: Mobile Data Bundle Recommendation

Recommend a mobile data plan based on monthly usage.

Example categories:

- Light User
- Moderate User
- Heavy User
- Power User

Explain why each recommendation was made.

---

## Challenge 10: Simple Loan Eligibility Checker

Determine whether an applicant qualifies for a loan.

Requirements:

- Minimum age of 21 years
- Stable monthly income
- Credit score above a specified threshold
- Employment status verified

Display a clear approval or rejection message explaining the decision.

---

## Bonus Challenge: Build a Decision Dashboard

Create a menu-driven application using a `switch` statement.

The menu should allow the user to choose one of several features, such as:

1. Grade Calculator
2. Age Checker
3. ATM Withdrawal
4. Weather Advisor
5. Ticket Price Calculator
6. Exit

Each option should call the appropriate conditional logic.

This challenge combines everything you learned in this chapter into a single interactive program.

---

## Tips for Success

As you work through these challenges:

- Break large problems into smaller steps.
- Validate user input whenever possible.
- Choose the simplest appropriate control structure.
- Write descriptive variable names.
- Keep your code properly indented.
- Test normal, boundary, and invalid inputs.
- Refactor your solution if you discover a clearer approach.

Remember that there is rarely only one correct solution. Focus on writing code that is **correct, readable, and maintainable**.

---

## Self-Evaluation Checklist

After completing the challenge exercises, ask yourself:

- Did I choose the correct conditional structure?
- Is my code easy to read?
- Have I handled invalid input?
- Did I test multiple scenarios?
- Can another developer understand my solution without explanation?
- Could I simplify any of my conditions?

If you can answer **"Yes"** to these questions, you are developing the habits of a professional JavaScript programmer.

# Mini Project

## Student Management and Result Evaluation System

### Project Overview

In this mini project, you will build a **Student Management and Result Evaluation System** using the conditional statements covered in this chapter.

The program will determine whether a student has passed, assign a grade, decide admission eligibility, and display personalized messages based on the student's information.

This project combines many of the concepts you have learned, including:

- Boolean expressions
- `if` statements
- `if...else`
- `else if`
- Nested conditionals
- `switch`
- Conditional (ternary) operator
- Truthy and falsy values
- Input validation
- Best practices

---

## Learning Objectives

By completing this project, you will learn how to:

- Combine multiple conditional statements.
- Solve a real-world programming problem.
- Organize program logic into manageable sections.
- Validate input before processing data.
- Produce meaningful output for users.

---

## Project Requirements

Your program should collect or define the following information:

```javascript
studentName
studentAge
studentScore
department
registrationPaid
documentsSubmitted
```

---

## Functional Requirements

Your application should perform the following tasks.

### Task 1: Validate Input

Check that:

- Student name is not empty.
- Age is greater than zero.
- Score is between 0 and 100.
- Department has a value.

Display an appropriate error message if any input is invalid.

---

### Task 2: Determine Pass or Fail

Rules:

- Score ≥ 50 → Pass
- Otherwise → Fail

---

### Task 3: Assign Grade

Use the grading scale:

| Score | Grade |
|--------|-------|
| 70–100 | A |
| 60–69 | B |
| 50–59 | C |
| 45–49 | D |
| 40–44 | E |
| Below 40 | F |

---

### Task 4: Admission Decision

A student is admitted only if:

- Age ≥ 16
- Registration fee paid
- Required documents submitted

Display the reason if admission is denied.

---

### Task 5: Department Information

Use a `switch` statement.

Example departments:

- Computer Science
- Mathematics
- Physics
- Chemistry
- Biology

Display a welcome message specific to the selected department.

---

### Task 6: Scholarship Eligibility

Award a scholarship if:

- Grade is A
- Registration fee has been paid
- Documents have been submitted

Display an appropriate message.

---

### Task 7: Graduation Status

Use the ternary operator.

Example:

```javascript
let graduationStatus =
    studentScore >= 50
        ? "Eligible"
        : "Not Eligible";
```

Display the result.

---

## Expected Output

Example:

```text
========================================
 Student Evaluation Report
========================================

Student: Ada Okafor

Department: Computer Science

Age: 19

Score: 84

Grade: A

Result: PASS

Admission Status: Approved

Scholarship: Awarded

Graduation Status: Eligible

Welcome to the Department of Computer Science!

========================================
```

---

## Suggested Program Structure

```
Start

│

├── Validate Input

│

├── Determine Pass/Fail

│

├── Assign Grade

│

├── Check Admission

│

├── Department Switch

│

├── Scholarship Decision

│

├── Graduation Status

│

└── Display Final Report
```

---

## Extension Ideas

After completing the project, try adding the following features:

### Level 1

- Display student remarks.
- Count distinctions.
- Calculate percentage.
- Add student ID.

---

### Level 2

- Allow multiple students.
- Store results in an array.
- Display class statistics.
- Determine the best-performing student.

---

### Level 3

After learning loops and functions in later chapters:

- Process many students automatically.
- Convert repeated code into reusable functions.
- Read student records from a file or database.
- Build a simple web interface using HTML, CSS, and JavaScript.

---

## Reflection Questions

After completing the project, answer the following:

1. Which conditional statement did you use most frequently?

2. Where did you use nested conditionals?

3. Why did you choose a `switch` statement for department selection?

4. How did you validate user input?

5. What additional features would improve this application?

6. Which concepts from this chapter were the most useful?

---

## Project Checklist

Before considering the project complete, verify that:

- [ ] All inputs are validated.
- [ ] Grades are calculated correctly.
- [ ] Admission decisions are accurate.
- [ ] Department messages use a `switch` statement.
- [ ] Scholarship decisions are correct.
- [ ] The ternary operator is used appropriately.
- [ ] Code is properly indented.
- [ ] Variable names are meaningful.
- [ ] The program has been tested with valid and invalid inputs.
- [ ] Output is clear and user-friendly.

---

> **CodeTales Project Challenge**
>
> Once you have completed this project, publish your solution to GitHub with a descriptive `README.md`. Explain the purpose of the application, the conditional structures you used, and include sample output. As you progress through later chapters, revisit this project and enhance it with loops, functions, objects, and a graphical user interface. This approach will help you see how your programming skills grow over time.

# Further Reading

Learning JavaScript is an ongoing journey. This chapter introduced the fundamentals of control flow and conditional statements, but there are many opportunities to deepen your understanding through books, official documentation, interactive tutorials, and coding practice.

The resources below are recommended for readers who want to strengthen their JavaScript skills.

---

## Official Documentation

### MDN Web Docs

The Mozilla Developer Network (MDN) provides one of the most comprehensive and trusted references for JavaScript.

Topics worth exploring include:

- `if...else` statements
- `switch` statements
- Comparison operators
- Logical operators
- Truthy and falsy values
- Conditional (ternary) operator

MDN combines detailed explanations with practical examples and is an excellent reference throughout your JavaScript journey.

---

## ECMAScript Language Specification

The ECMAScript specification defines the official JavaScript language standard.

Although it is intended primarily for experienced developers and language implementers, it provides precise definitions of the language's behavior.

---

## Recommended Books

### *Eloquent JavaScript* (Marijn Haverbeke)

A highly regarded book that explains JavaScript fundamentals with clear examples and practical exercises.

Recommended chapters:

- Program Structure
- Functions
- Objects
- Bugs and Errors

---

### *JavaScript: The Definitive Guide* (David Flanagan)

A comprehensive reference covering both the JavaScript language and web APIs.

Recommended for readers who want an in-depth understanding of JavaScript.

---

### *You Don't Know JS Yet* (Kyle Simpson)

A multi-volume series that explores JavaScript in greater depth.

Recommended volumes include:

- *Get Started*
- *Scope & Closures*
- *Objects & Classes*

---

## Interactive Learning Platforms

Practice is one of the best ways to strengthen your programming skills.

Consider exploring platforms such as:

- freeCodeCamp
- Codecademy
- Scrimba
- Exercism
- HackerRank

These platforms provide hands-on exercises and immediate feedback.

---

## Coding Practice

To become comfortable with conditional statements:

- Solve one programming problem every day.
- Rewrite your solutions using different conditional structures.
- Experiment with edge cases and invalid input.
- Refactor your code to improve readability.

Consistent practice is more effective than memorizing syntax.

---

## Build Small Projects

Apply what you learned by creating small applications such as:

- Grade calculator
- Age checker
- ATM simulator
- Login system
- Shopping discount calculator
- Weather advisor
- Ticket pricing system
- Simple menu-driven applications

Each project reinforces the concepts introduced in this chapter.

---

## Explore Open-Source Projects

Reading other developers' code helps you learn new techniques and coding styles.

When exploring open-source JavaScript projects, pay attention to:

- How conditions are written
- Variable naming conventions
- Code organization
- Error handling
- Readability

---

## Prepare for the Next Chapter

Before beginning Chapter 6, make sure you can confidently:

- Write `if` statements.
- Use `if...else` and `else if`.
- Create `switch` statements.
- Apply the ternary operator.
- Explain truthy and falsy values.
- Debug common conditional logic errors.

A strong understanding of these topics will make learning loops much easier.

---

## Continue Learning

Programming is a practical skill developed through consistent application.

Remember these principles:

- Read code regularly.
- Write code every day.
- Debug patiently.
- Learn from mistakes.
- Build increasingly challenging projects.
- Revisit earlier concepts as your understanding grows.

Each chapter builds upon the previous one. The knowledge you gained about conditional statements will continue to support your progress as you explore loops, functions, arrays, objects, asynchronous programming, and modern JavaScript development.

---

> **CodeTales Learning Tip**
>
> Don't aim to memorize every piece of syntax. Instead, focus on understanding the underlying concepts and applying them through regular practice. The ability to solve problems is far more valuable than memorizing language features.

# References

The following references were consulted during the preparation of this chapter. They provide authoritative information on JavaScript, programming fundamentals, software engineering principles, and language specifications.

---

## Books

Flanagan, D. (2025). *JavaScript: The Definitive Guide* (8th ed.). O'Reilly Media.

Haverbeke, M. (2018). *Eloquent JavaScript* (3rd ed.). No Starch Press.

Simpson, K. (2020). *You Don't Know JS Yet: Get Started* (2nd ed.). Independently Published.

Simpson, K. (2020). *You Don't Know JS Yet: Scope & Closures* (2nd ed.). Independently Published.

Crockford, D. (2008). *JavaScript: The Good Parts*. O'Reilly Media.

Freeman, E., & Robson, E. (2014). *Head First JavaScript Programming*. O'Reilly Media.

---

## Official Documentation

ECMA International. (2024). *ECMAScript® 2024 Language Specification.*

Mozilla. *MDN Web Docs – JavaScript Guide.*

Mozilla. *MDN Web Docs – Control Flow and Error Handling.*

Mozilla. *MDN Web Docs – if...else Statement.*

Mozilla. *MDN Web Docs – switch Statement.*

Mozilla. *MDN Web Docs – Conditional (Ternary) Operator.*

Mozilla. *MDN Web Docs – Truthy.*

Mozilla. *MDN Web Docs – Falsy.*

---

## Educational Resources

freeCodeCamp. *JavaScript Algorithms and Data Structures.*

The Odin Project. *JavaScript Curriculum.*

Scrimba. *Learn JavaScript.*

Codecademy. *Learn JavaScript.*

HackerRank. *JavaScript Practice Problems.*

Exercism. *JavaScript Track.*

---

## Web Standards

World Wide Web Consortium (W3C). *Web Standards.*

WHATWG. *HTML Living Standard.*

ECMA International. *ECMAScript Language Specifications.*

---

## Recommended Reading for Further Study

- *JavaScript Patterns* — Stoyan Stefanov
- *Programming JavaScript Applications* — Eric Elliott
- *Secrets of the JavaScript Ninja* — John Resig & Bear Bibeault
- *Effective JavaScript* — David Herman
- *Maintainable JavaScript* — Nicholas C. Zakas

---

## Acknowledgement of Sources

The explanations, examples, best practices, and programming techniques presented in this chapter were developed through the author's original writing while drawing upon established JavaScript language standards, official documentation, and widely respected educational resources. Every effort has been made to ensure technical accuracy, clarity, and alignment with modern JavaScript development practices.

Readers are encouraged to consult the official ECMAScript specification and MDN Web Docs for the most current language features and updates as JavaScript continues to evolve.
