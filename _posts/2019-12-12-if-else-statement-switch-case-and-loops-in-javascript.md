---
title: If-else Statement, Switch-Case and Loops in JavaScript
image: "/assets/default-social-image.png"
categories: JavaScript-basics
---

**if-else Statement in JavaScript**

Programming decision-making is similar to real-life decision-making. We also face certain situations in programming where we want to execute a certain block of code when some condition is fulfilled.

A programming language uses statements of control to control the flow of program execution based on certain conditions. These are used to advance and branch the execution flow based on changes to a program's status.

**JavaScript’s conditional statements:**

**if
if-else
nested-if
if-else-if

These declarations allow you to control the movement of execution for your program based on conditions that are only considered during runtime.

**if:** If the statement is the simplest statement of decision-making. It is used to determine whether or not a certain statement or block of assertions will be executed, i.e. if a condition is true then a statement block will be executed, otherwise it won't.

**Syntax:**

```
if(condition) 
{
   // Statements to execute if
   // condition is true
}
```

Here, either true or false will be the **condition** after evaluation. If the statement acknowledges boolean values – if the value is true, the statement block under this will be executed.

If after the **if(condition)** we do not provide the curly braces '{' and '}', then by definition if statement will consider within its block for the immediate one statement.

```
if(condition)
   statement1;
   statement2;

// Here if the condition is true, if block 
// will consider only statement1 to be inside 
// its block.
```

Example:

```
<script type = "text/javaScript"> 
  
// JavaScript program to illustrate If statement 
  
var i = 10; 
  
if (i > 15) 
  document.write("10 is less than 15"); 
  
// This statement will be executed 
// as if considers one statement by default 
document.write("I am Not in if"); 
  
< /script> 
```

Output:

`I am Not in if`

**if-else:** The if statement itself informs us that it will execute a block of statements if a condition is true and if the condition is false, it will not. But what if something else we want to be done if the condition is false. The else statement comes here. We can use the else statement when the condition is false to execute a block of code, with if statement.

**Syntax:**

```
if (condition)
{
    // Executes this block if
    // condition is true
}
else
{
    // Executes this block if
    // condition is false
}
if-else-statement
```

Example:

```
<script type = "text/javaScript"> 
  
// JavaScript program to illustrate If-else statement 
  
var i = 10; 
  
if (i < 15) 
  document.write("10 is less than 15"); 
else
  document.write("I am Not in if"); 
  
< /script> 
```

Output:

`i is smaller than 15`

**nested-if:** A nested if an if argument, if or else to be of another goal. Nested if statements are inside a statement if, inside another if statement. Sure, JavaScript helps us to nest if sentences inside if statements. That is, if the assertion is inside another if statement, we could place an if inside it.

**Syntax:**

```
if (condition1) 
{
   // Executes when condition1 is true
   if (condition2) 
   {
      // Executes when condition2 is true
   }
}
```

Example:

```
<script type = "text/javaScript"> 
  
// JavaScript program to illustrate nested-if statement 
  
var i = 10; 
  
if (i == 10) { 
  
  // First if statement 
  if (i < 15) 
    document.write("i is smaller than 15"); 
  
  // Nested - if statement 
  // Will only be executed if statement above 
  // it is true 
  if (i < 12) 
    document.write("i is smaller than 12 too"); 
  else
    document.write("i is greater than 15"); 
} 
< /script> 
```

Output:

```
i is smaller than 15
i is smaller than 12 too
```

**if-else-if ladder:** A user can choose between multiple options here. If statements are performed from top to bottom. As soon as one of the conditions controlling the if is true, it bypasses the statement associated with that 'if' is executed. If none of the requirements is true, it will implement the final else statement.

```
if (condition)
    statement;
else if (condition)
    statement;
.
.
else
    statement;
```

Example:

```
<script type = "text/javaScript"> 
// JavaScript program to illustrate nested-if statement 
  
var i = 20; 
  
if (i == 10) 
  document.wrte("i is 10"); 
else if (i == 15) 
  document.wrte("i is 15"); 
else if (i == 20) 
  document.wrte("i is 20"); 
else
  document.wrte("i is not present"); 
< /script> 
```

Output:

`i is 20`

**Switch Case in JavaScript**

By using if-else statements on if-else statement in JavaScript, we read about decision making in JavaScript. We saw that if-else statements can be used to perform actions based on a particular condition. That is, if a condition is true, then perform a task, or else if the condition is false, perform another task.

The JavaScript switch case statement is also used for decision-making purposes. In some cases, it is considered more convenient to use the switch case statement over if-else statements. Imagine a case when we want to test a variable with hundreds of different values and we want to perform a task dependent on the test. It will be less effective to use if-else expressions for this reason than switch case expressions and it will also render the code look messy.

The statement of the switch case is a statement of the multiway branch. This provides an easy way to assign execution based on the value of the expression to different parts of code.

**Syntax:**

```
switch (expression)
{
    case value1:
        statement1;
        break;
    case value2:
        statement2;
        break;
    .
    .
    case valueN:
        statementN;
        break;
    default:
        statementDefault;
}
```

Explanation:

* 'expression' could be of numbers or strings type.
* Dulplicate 'case' values aren't valid.
* Optional is the 'default' statement. In any case, if the expression passed to switch does not match the value, then the default statement will be executed.
* Inside the switch, the 'break' statement is used to stop a sequence in statement.
* The statement of the 'break' is optional. If excluded, the execution in the next scenario would proceed.

**Example:**

```
<script type = "text/javascript"> 
  
    // JavaScript program to illustrate switch-case 
  
    var i = 9; 
  
    switch (i)  
    { 
       case 0: 
           document.write("i is zero."); 
           break; 
       case 1: 
           document.write("i is one."); 
           break; 
       case 2: 
           document.write("i is two."); 
           break; 
       default: 
           document.write("i is greater than 2."); 
    } 
  
</script></div> 
```

Output:

`i is greater than 2.`

**Loops in JavaScript**

Looping in programming languages is a functionality that makes it easy to repeatedly perform a series of instructions/functions while some condition evaluates to true. Assume we would like to print "Hello World," for example, 10 times. As seen below, this can be achieved in two ways:

**Iterative Method**

To do that, the Iterative method is to compose the statement document.write() 10 times.

```
<script type = "text/javascript"> 
document.write("Hello World\n"); 
document.write("Hello World\n"); 
document.write("Hello World\n"); 
document.write("Hello World\n"); 
document.write("Hello World\n"); 
document.write("Hello World\n"); 
document.write("Hello World\n"); 
document.write("Hello World\n"); 
document.write("Hello World\n"); 
document.write("Hello World\n"); 
< /script> 
```

**Using Loops**

The sentence must be wrote in Loop only once while the loop is performed 10 times as seen below:

```
<script type = "text/javascript"> 
var i; 
  
for (i = 0; i < 10; i++)  
{ 
    document.write("Hello World!\n"); 
} 
< /script> 
```

At this point in time, most issues may seem overwhelming to you in the above program, but do not doubt however, as by the end of this tutorial, you will be able to understand all about loops in JavaScript. We can see that we used the document.write statement only once in the above method utilizing loops, but still the program's output will be the same as the iterative system where we used the document.write statement 10 times.

A loop is a sequence of instructions in computer programming that is replicated until a certain state is achieved.

* An operation is performed, such as getting a data item and changing it, and then some condition such as whether a counter has reached a prescribed number, is checked.
* **Counter not Reached:** If the counter has not achieved the desired number, the next instruction in the sequence corresponds to and repeats the first instruction in the sequence.
* **Counter reached:** If the counter condition is attained, the next fall through instruction to the next sequential instruction or branches outside of the loop.

**There are mainly two types of loops:**

* **Entry Controlled loops:** the test condition is checked in this sort of loop before entering the body of the loop. Examples are the **For Loop** and the **While Loop**.
* **Exit Controlled Loops:** The test condition is checked or measured at the end of the loop body in this type of loops. The loop body will therefore run atleast once, regardless of whether the state of the experiment is true or false. Example is the **do – while loop**.

JavaScript provides three main ways to implement the loops. While all the ways offer similar basic functionality, they vary in their time for testing syntax and condition. Let us learn in detail about each of these.

**while loop:** A while loop is a statement of control flow which enables repeated execution of code based on a specified boolean condition. The while loop can be viewed as a sentence repeated if case.

**Syntax :**

```
while (boolean condition)
{
   loop statements...
}
```

* While loop begins with condition checking. If it is checked as true, then the statements of the loop body will be implemented after the loop is completed. It is also called the **Entry control loop** for this reason.
* Once the condition is determined to be true, the statements are performed in the body of the loop. The statements normally contain an update value for the next iteration variable being handled.
* The loop ends when the condition becomes false, marking the end of its life cycle.

```
<script type = "text/javaScript"> 
// JavaScript program to illustrate while loop 
  
    var x = 1; 
  
    // Exit when x becomes greater than 4 
    while (x <= 4) 
    { 
        document.write("Value of x:" + x + "<br />"); 
  
        // increment the value of x for 
        // next iteration 
        x++; 
    } 
  
< /script> 
```

Output:

```
Value of x:1
Value of x:2
Value of x:3
Value of x:4
```

**for loop:** for loop, a succinct way to compose a loop structure is provided. Unlike a while loop, a for statement consumes the initialization, condition, and increment/decrement in one line, resulting in a shorter, easy-to-debug looping structure.

**Syntax:**

```
for (initialization condition; testing condition; 
                              increment/decrement)
{
    statement(s)
}
```

* **Initialization condition:** Here, the variable in use is initialized. It marks the beginning of a loop. It can be used, for an already defined variable, or to declare a variable local to loop only.
* **Testing Condition:** It is used to test a loop's exit condition. A boolean value must be returned. It is also an Entry Control Loop as it tests the condition before the loop statements are performed.
* **Statement execution:** Once the condition is determined to be true, the statements are performed in the body of the loop.
* **Increment/ Decrement:** It is used to modify the next iteration of the variable.
* **Loop termination:** The loop ends at the end of its life cycle when the condition becomes false.

```
<script type = "text/javaScript"> 
// JavaScript program to illustrate for loop 
  
    var x; 
  
    // for loop begins when x=2 
    // and runs till x <=4 
    for (x = 2; x <= 4; x++)  
    { 
        document.write("Value of x:" + x + "<br />"); 
    } 
  
< /script> 
```

Output:

```
Value of x:2
Value of x:3
Value of x:4
```

**for…in loop**

JavaScript also features another loop variant also labeled as the for..in Loops. The loop for..in gives a simpler way of iterating through an object's property. Upon leaning objects in JavaScript, this will be simpler. But while working with objects, this loop is shown to be very helpful.

**Syntax:**

```
for (variableName in Object)
{
    statement(s)
}
```

In each step, the variable called variableName is allocated one of the properties of the object and this loop continues until all of the object's properties are handled. Let's take an example to show how to simplify the work for..in loop.

```
<script type = "text/javaScript"> 
// JavaScript program to illustrate for..in loop 
  
    // creating an Object 
    var languages = { first : "C", second : "Java",  
                      third : "Python", fourth : "PHP",  
                      fifth : "JavaScript" }; 
  
    // iterate through every property of the 
    // object languages and print all of them 
    // using for..in loops 
    for (itr in languages)  
    { 
        document.write(languages[itr] + "<br >"); 
    } 
  
< /script> 
```

Output:

```
C
Java
Python
PHP
JavaScript
```

**do while:** This is identical to while loop with the only exception that it tests for condition after performing statements and is thus an instance of exit control loop.

**Syntax:**

```
do
{
    statements..
}
while (condition);
```

* do while: the loop begins with the statement(s) execution. For the first time, there is no testing of any condition.
* After the statements are executed and the variable value is updated, true or false value is verified for the condition. If it is determined to be true, the next loop iteration starts.
* The loop ends when the condition becomes false, marking the end of its life cycle.
* It is important to note that the do-while loop must perform its atleast statements once before some condition is checked and is thus can be considered as an instance of an exit control loop.

```
<script type = "text/javaScript"> 
// JavaScript program to illustrate do-while loop 
  
    var x = 21; 
  
    do 
    { 
        // The line while be printer even 
        // if the condition is false 
        document.write("Value of x:" + x + "<br />"); 
  
        x++; 
    } while (x < 20); 
  
< /script> 
```

Output:

`Value of x: 21`

**Infinite loop**

One of the most common errors when applying any kind of looping is that it may not stop, and because of which the loop continues for infinite amount of time. It occurs because for some reason of the condition failing.

Examples:

```
<script type = "text/javaScript"> 
// JavaScript program to illustrate infinite loop 
  
    // infinite loop because condition is not apt 
    // condition should have been i>0. 
    for (var i = 5; i != 0; i -= 2) 
    { 
        document.write(i); 
    } 
      
    var x = 5; 
  
    // infinite loop because update statement 
    // is not provided. 
    while (x == 5)  
    { 
        document.write("In the loop"); 
    } 
  
< /script> 
```