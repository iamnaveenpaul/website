---
title: Variables, Datatypes and Hoisting in JavaScript
image: "/assets/default-social-image.png"
categories: JavaScript-basics
---

**Datatypes in JavaScript**

There are two main types of languages. First one is a **statically typed language** in which at the time of compilation, every parameter and form of expression is already defined. Once a variable has been declared to be of a specific type of data, it can not hold values of other type of data. Example: C, C++, Java.

```
// Java(Statically typed) 
int x = 5  // variable x is of type int and it will not store any other type. 
string y = 'abc' // type string and will only accept string values 
```

Others are **dynamically typed  languages**: these languages can receive different types of data over time. Ruby, Python etc., for example.

```
// Javascript(Dynamically typed) 
var x = 5; // can store an integer 
var name = 'string'; // can also store a string. 
```

JavaScript is a scripting language that is dynamically typed (also called loosely typed). That is, over time, different types of information can be obtained in javascript variables. Datatypes are essentially data types that can be used in a program and manipulated.

Seven types of data are specified by the new **ECMAScript(ES6) standard**: six types of data of which are primitive (predefined).

* **Numbers:** 5, 6.5, 7 etc.
* **String:** “Hello World” etc.
* **Boolean:** A logical entity is defined and can have two values: true or false.
* **Null:** This type has only one value : null.
* **Undefined:** A variable not allocated to a value is undefined
* **Object:** It is the most important data type and forms the modern JavaScript building blocks.

**Variables in JavaScript:**

JavaScript variables are containers that contain reusable data. It is the basic storage unit within a program.

* Throughout code implementation, the value contained in a variable can be modified.
* A variable is just a name given to a memory location, all the operations performed on the memory location's variable that effects it.
* Before they can be used, all variables must be defined in JavaScript.

JavaScript variables are declared exclusively using the var keyword before ES2015, accompanied by the parameter and semi-colon names. Below is the code for constructing JavaScript variables:

```
var var_name;
var x;
```

The var_name is the function name that the user should define and be distinct. Often recognized as **identifiers** that are these types of names. The guidelines for generating an identifier in JavaScript are, the identifier name should not be a predefined term (known as keywords), the first character should be a letter, an underscore `_` or a dollar sign `$`.

Remember in the code sample above that we do not allocate any values to the variables. We only state that they exist. When you check the value of each variable in the code sample above, it would be unknown or undefined.

When we want to use them, we can initialize the variables either at the time of declaration or later. Below are some instances of JavaScript variables being declared and initialized:

```
// declaring single variable
var name;

// declaring multiple variables
var name, title, num;

// initializng variables
var name = "Harish";
name = "Somesh";
```

Often recognized as **untyped** script for the language Javascript. It ensures that once the keyword var is used to construct a variable in javascript, we can store some type of attribute provided by javascript in this variable. The example below is as follows:

```
// creating variable to store a number
var num = 5;

// store string in the variable num
num = "IWroteSomethingHere";
```

The example above runs well, unlike other programming languages, without any error in JavaScript.

JavaScript variables can also evaluate and assume their value for simple mathematical expressions.

```
// storing a mathematical expression
var x = 5 + 10 + 1;
console.log(x); // 16
```

Now we have two new variable containers after ES2015: let and const. Now we're going to look at both of them one by one. The variable type **Let** has certain characteristics similar to var, but it has limits in scope unlike var. Learn more about '[Let vs var](https://www.geeksforgeeks.org/difference-between-var-and-let-in-javascript/)', Read here Let's use the variable let:

```
// let variable
let x; // undefined
let name = 'Sid';

// can also declare multiple vlaues
let a=1,b=2,c=3;

// assignment
let a = 3;
a = 4; // works same as var.
```

**Const** is another type of variable allocated to data for which the value can not and will not alter within the script.

```
// const variable
const name = 'Sid';
name = 'Mac'; // will give Assignment to constant variable error.
```

**Variable Scope in Javascript**

A variable's scope is the part of the program from which the parameter can be accessed directly.

There are two types of scope in JavaScript:

* **Global Scope:** Scope outside Window's attached outermost function.
* **Local Scope:** The function is conducted inside.

Let's see the code below. We have a global variable in global scope defined in the first line. Then we've defined a local variable within the function fun().

```
let globalVar = "This is a global variable"; 
  
function fun() { 
  let localVar = "This is a local variable"; 
  
  console.log(globalVar); 
  console.log(localVar); 
} 
  
fun(); 
```

When the function fun() is executed, the output indicates that both global and local variables can be reached within the function as we can check the output by console.log. It indicates that both global variables (declared outside of the function) and local variables (declared within the function) are accessible within the function. Let's push the statements of console.log outside of the function and place them just after the function is called.

```
let globalVar = "This is a global variable"; 
  
function fun() {  
  let localVar = "This is a local variable";  
} 
  
fun(); 
  
console.log(globalVar); 
console.log(localVar); 
```

We can still see the global variable's value. but console.log creates an error for the local variable. This is because console.log statements are now found on a global scope where they have access to global variables but are unable to reach local variables.

Additionally, any variable specified in a function with the same naming as a global variable prioritizes over the global variable, shadowing it. You could read the article [understanding variable scopes in JavaScript](https://www.geeksforgeeks.org/understanding-variable-scopes-in-javascript/).

**Understanding variable scopes in JavaScript**

If you declare variables, use the let prefix at all times. If the let keyword is not used, then the variables are created in the global scope by default. For example, let's just remove the keyword let before the localLet statement in the above example, note that we used globalLet instead of globalVar and localLet insteas of localVar, and everything would be the same as which was for the above code.

We can now console.log the local variable, because we skipped the keyword let when defining it, because the localLet is generated in the global scope. What really happened is that since we didn't use the let keyword, JavaScript searched the localLet on a local scale first, then on a global scale. Since that name did not have a current global variable, this created a new global variable.

One of the most frequently asked questions in interviews is the case where the same title is assigned to both the global and local variable. Let's see now:

```
let globalLet = "This is a global variable"; 
   
function fun() { 
  let globalLet = "This is a local variable"; 
} 
fun(); 
console.log(globalLet); // This is a global variable 
```

In this case, we proclaimed the "globalLet" as a local and global parameter. What matters here is the scope to which we access it. We view it in global scope in the above case, so it will output the global variable as the local variable is not present in its scope Let's transfer the console.log declaration within the function fun().

```
let globalLet = "This is a global variable"; 
   
function fun() { 
  let globalLet = "This is a local variable"; 
  console.log(globalLet); // This is a local variable 
} 
fun(); 
```

Both local and global variables are accessible within the function fun(). Nonetheless, once we console.log the globalLet variable, JavaScript first attempts to find a local variable in the current scope. It finds and outputs the local variable. Otherwise, in the outer scope (which in this case is global scope), it would have to search for the variable "globalLet."

What if, instead of a local, we want to access the global variable here. Well, the object of the window is coming to our rescue. All global variables are connected to the window object, and as shown in the illustration below, we may access the name of the global variable.

```
let globalLet = "This is a global variable"; 
   
function fun() { 
  let globalLet = "This is a local variable"; 
  console.log(window.globalLet); // This is a global variable 
} 
fun(); 
```

After analyzing scopes in JavaScript, it should be like walking in a park to estimate the output of fragments of the code below.

```
function fun(){ 
    function fun2(){ 
         i = 100; 
    } 
    fun2(); 
    console.log(i); // 100 
} 
fun();  
```

```
function fun(){ 
    function fun2(){ 
        let i = 100; 
    } 
    fun2(); 
    console.log(i); // i is not defined  
} 
fun(); 
```

In the first case, because we did not use the let keyword, it was presumed that the parameter "i" was defined in global scope and therefore the output would be 100. "i" became a local variable in the second example and was therefore not available outside the scope of that function.

Let's take another example

```
function fun(){ 
    if(true){ 
        let i = 100; 
    } 
    console.log(i); // i is not defined 
} 
fun(); 
```

We began using let instead of var after ES2015 to define variables and also now if block is also counted as a block scope, so we get an error instead of 100 in the above case. If we adjust the let to var, we get 100 as output as if block wasn't considered a block scope earlier, that wasconsidered only for functions.

**JavaScript Hoisting**

In JavaScript, Hoisting is the default action to move all declarations before executing code at the top of the scope. Essentially, this offers us a benefit that they are pushed to the top of their scope irrespective of whether their scope is global or local irrespective of wherever the functions and variables are declared.

This allows us to call functions before we even write them in our program.

Note: JavaScript just hoists declarations, not initializations.

Let's understand this exactly:

The following is the sequence where the declaration and initialisation of the variable occurs.

**Declaration to Initialisation/Assignment to Usage**

```
// Variable lifecycle
let a;        // Declaration
a = 100;      // Assignment
console.log(a);  // Usage
```

Because JavaScript however, helps us to seamlessly define and initialize our variables, this is the most common pattern:

`let a = 100;`

Note that the Javascript declares the variable first in the context and then initializes it. It's also good to know that before any coding is performed, variable declarations are processed.

Undeclared variables won't occur in javascript, however until code is executed to assign them. Consequently, when the assignment is executed, assigning a value to an undeclared variable implicitly creates it as a global variable. This means that the global variables are all undeclared variables.

```
// hoisting 
function codeHoist(){ 
    a = 10; 
    let b = 50; 
} 
codeHoist(); 
  
console.log(a); // 10 
console.log(b); // ReferenceError : b is not defined 
```

Explanation: We built a function called codeHoist() in the above code sample and in it, we have a variable which we did not declare using let/var/const and a let variable b. The undeclared variable is allocated by javascript to the global scope, so we can print it outside the function, but the scope is limited in the case of variable b and it is not accessible outside and we get a ReferenceError.

Note: ReferenceError is different from undefined error. If we have a variable that is either not specified or explicitly defined as type undefined, an undefined error arises. When attempting to access a previously undeclared variable, ReferenceError is returned.

**ES5**

The variable that arises into our heads is var as we speak about ES5. Var hoisting is somewhat different from let/const hoisting. Let's see how hoisting works by using the var:

```
// var code (global) 
console.log(name); // undefined 
var name = 'Michael';  
```

Explanation of the above code, we tried to console the name of the variable that was later declared and assigned then using it, the compiler provides us undefined that we didn't expect as we could have had ReferenceError as we tried to use the name variable before declaring it.

However the interpreter perceives this differently:

```
//how interpreter sees the above code 
var name; 
console.log(name); // undefined 
name = 'Michael';  
```

**Function scoped variable**

Now let us look at how variables that are scoped for function are hoisted.

```
//function scoped 
function fun(){ 
    console.log(name); 
    var name = 'Mukul Latiyan';  
} 
fun(); // undefined 
```

There is no difference here as we get undefined as the code seen by the interpreter, for when compared to the code where we declared the variable globally:

```
//function scoped 
function fun(){ 
    var name; 
    console.log(name); 
    name = 'Mukul Latiyan'; 
} 
fun(); // undefined 
```

To prevent this pitfall, we should ensure that the variable is declared and allocated at the same time before it is used. Which is something like:

```
//in order to avoid it  
function fun(){ 
    var name = 'Mukul Latiyan'; 
    console.log(name); // Mukul Latiyan 
} 
fun(); 
```

**ES6**

**Let**

We realize that the variables specified with let keywords are block scoped and not function scoped, so when it comes to hoisting it is not a concern.

Example:

```
//let example(global) 
console.log(name); 
let name='Mukul Latiyan'; // ReferencError: name is not defined 
```

As before, we consider the output of the log to be undefined for the var keyword. Nonetheless, using undeclared variables since the es6 will not take kindly on us, the interpreter should spit out a Reference error directly. This ensures that our variable is always **declared** first.

**const** acts like let when it comes to hoisting.