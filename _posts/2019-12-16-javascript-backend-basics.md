---
title: JavaScript Backend basics
image: "/assets/default-social-image.png"
categories: JavaScript-basics
---

This article is to use JavaScript to get started with back-end development. This post will include JavaScript's basics and rules to be implemented.

**JavaScript Engine**

Every browser has its own JavaScript engine that is used to run scripts so that they can function properly. Here are the descriptions used in some of the most popular browsers out there for the JavaScript engines.

* Chrome: V8
* Firefox: SpiderMonkey
* Safari: JavaScript Core
* Microsoft Edge/ Internet Explorer: Chakra

ECMA Script Standard: The ECMA Script Standard is a trademark scripting language classification regulated by the European Computer Manufactures Association. The ECMA Script specification defines the JavaScript syntax that is used throughout the various web browsers.

**Types definitions in JavaScript**

**Dynamic Typing:** The interpreter can automatically determine the type of variable depending on certain factors.

**Primitive Data Types:** The primitive data types are the types of information that have no methods attached to them, i.e. those specified methods could not be used with them and are used in isolation. Although there are ways to use these techniques by covering certain variables of the primitive data type. The types of data in the primitive classification are as follows:

1. **undefined:** If there is a variable but it is not defined, it will be categorized as undefined.
2. **null:** If there is a variable but it is not clearly defined, the classification will be null.
3. **boolean:** The type of Boolean data is to determine whether a variable is True or False.
4. **number:** Number is the type of data that can be assigned to integer, floating point, double. The only difficulty here is that each time we specify a number, we have to assign a memory equal to a double variable.
5. **string:** It is used to determine a character's string values.
6. **symbol:** This is a special type of data that is unique to ECMA Script 6. The "symbol" data type is a primitive data type with the consistency that this sort of values can be used to make anonymous object property.

**Object**

Everything is an object in JavaScript. That's every variable, array, string or any other structure we recognize falls within the object class. The object in Java Script can be interpreted by almost every language and can be interpreted quickly.

**Creating objects:** There are three ways of creating objects.

**#1. By Using the Object() Constructor**

```
var obj = new Object(); 
obj.firstName = "How"; 
obj.middleName = "are"; 
obj.lastName = "you"; 
obj.isTeaching = "Javascipt"; 
obj.greet = function() { console.log("Hi"); } 
```

**#2. By Using Object literal**

```
var obj = {} //obj is an empty object 
obj.firstName = "How"; 
obj.middleName = "are"; 
obj.lastName = "You"; 
obj.isTeaching = "Javascipt"; 
obj.greet = function() { console.log("Hi"); } 
```

**#3.  Specifying the values directly**

```
var obj = {  
    obj.firstName = "How"; 
    obj.middleName = "are"; 
    obj.lastName = "you"; 
    obj.isTeaching = "Javascipt"; 
    obj.greet = function() { console.log("Hi"); } 
} 
```

**Coercion:** Throughout JavaScript, what we consider typecasting throughout C, C++, Java is considered coercion. They are of two types:

**Explicit Coercion**

Explicit coercion is the method by which a variable to a type of data is expressly specified.

```
var x = 42; 
var explicit = String(x); // explicit is set to "42" 
```

**Implicit Coercion**

Implicit coercion is the method by which, under certain conditions, the interpreter type casts the variable dynamically.

```
var x = 42; 
var implicit = x + " "; // interpreter automatically sets implicit as "42" 
```

**Scope**

**Variable lifetime:** The lifespan of the variable is from where it is defined until its purpose stops. If no function is specified, the variable's context is global.

**Hoisting:** Function definitions are declarations that are hoisted but not variable. This means that it can be used from anywhere in your code when a function is declared.

Hoisting example:

```
function greet(){ 
    console.log("Hi"); 
} 
greet(); 
```

Once called, the function above is performed successfully. Yet if we first call the function and then define it, it will also be implemented successfully. This is considered hoisting function.

```
greet(); 
function greet(){ 
    console.log("Hi"); 
} 
```

The initialization of the variable is not hoisted, however.

```
x(); // calling x 
var x = function(){ 
    console.log("Hi"); 
} 
/* The above is is an error since x is not a function because x is a variable initialization delegated to a function due to the current '=' operator. 
```

The illustration above is the part that proves that it is not possible to hoist the variable in JavaScript. But look at the next instance described in JavaScript, which is another form of hoisting.

```
console.log(x); 
var x = 42; 
// Output ==> undefined 
```

The above output errors are undefined, and when the variable exists but is not specified, we recognize it the undefined type. Therefore the problem here is how the variable exists even if it is later declared and initialized?

This is another hoisting type such as function hoisting, i.e. we have the variable 'x' before.

The JavaScript engine runs in two phases:

**Creation Phase:** The engine checks the entire file before running the program which, if detected, can throw a syntactic error. While it does so, it will only save any function definitions in memory. No initialization of any variable will be performed, but the names of the variable will be declared.

**Execution Phase:** The execution phase is the stage in which the program is implemented and hence the above-mentioned variable-hoisting illustration errors as undefined since the variable was stated in the creation process but not specified.

The following is a follow-up to delve deeper into some of the sophisticated JavaScript concepts that are commonly used in the industry.

**“==” vs “===”**

The "==" coerces the input types that it forces the variable to be the same and examines their equality afterwards.

In addition, the "===" demands identical types to generate a true output. The "===" is typically used more commonly, and the "==" should only be used if we really know the input type equivalence. 

Note: My advice is to use "===" at all levels unless you really know what you're doing.

**JavaScript false values**

The following values are treated as FALSE values when converted to boolean:

* **0** – This is always false, as it is the number zero.
* **undefined** – Any value is regarded as false if primitively undefined.
* **null** – Primitive null values are always false
* **+0 , -0 , NaN(not a number)** – Positive/negative or non-number value is presumed to be false

**JavaScript Truth Values**

The following values are viewed as TRUE values when translated to boolean:

* **{ }** – The empty object
* **[ ]** – The empty array
* All the rest that isn't false will be TRUE.

**Prototypical inheritance**

We recognize all that in JavaScript is an object except the primitive types, so we need a way to distinguish between objects and other types of data. Now follows the idea of inheritance as a prototype.

* The Non-Primitive types (Objects) are connected with a few properties/methods.

Example:

```
Array.prototype.push()
String.prototype.toUpperCase()
```

* Every object holds a link to its prototype, and then its prototype may also have its prototype, which could be known as prototype chaining which seems possible.
* Priority is given to the prototype/properties/methods most closely defined to the instance.

Example:

```
var arr = []; 
arr.test = 'test'; // making a property called test 
Array.prototype.test = 'test1' // making a prototype test on the array object 
```

Now, on our console if we print **“arr.test”**,

Output :

`test`

The reasoning is that the test is first bound to the array instance and has priority even though we later defined a "test1" prototype.

**Prototype Chain**

`NULL<—Object<—Array<—Instances of Array`

The above is a prototype chain instance followed in the case of objects. Just as the object array is the prototype of all array instances, the array object prototype is an object and since in JavaScript everything is an object hence its prototype is NULL.

Many methods or prototypes have a 'writable' method that is set to false i.e. they are not overwritable.

Example:

```
var arr = [1, 2, 3]; 
arr.length = 'test'; //length is also an actual property of array and not writable 
```

The above program does not cause any error, but when we print arr.length, the output is "3," which is the real property and not what we created.

Note: We know there are no methods associated with primitive types, but most primitive types have object wrappers that we can declare and then we can use those methods and properties. JavaScript can box or wrap the primitive values so that the methods used by non-primitive types can be accessed.

The following describes the different JavaScript wrappers:

* String()
* Boolean()
* Number()
* Object()
* Symbol()

Note: Please ensure that you see the difference between these and the primitive types that all the first characters of the wrapper's name are capitalized in the above wrappers.

Since 50 is a primitive type that is a 'number' and does not have any methods, hence the error.

By assuming the Number() wrapper object, the JavaScript engine wraps the primitive type 'x'. So now that it wraps the 'x' into the prototype of Number(), which is an object, and now we can use the functions which were not available to us.

**The Global Object**

All variables and functions are described on the global object as parameters and methods.

The global object is the "window" object for a browser.

The global object is referred to as 'global' itself for NodeJS.

**Execution context**

It refers to a “Stack Frame” in C.
Variables and functions wrapper are local to the creation of a function.
Execution context collection is referred to as execution stack.

**Lexical Environment**

This defines how to address variable names for nested functions in particular.
Child functions retain the parent function's scope even if the parent is returned. (This segment will be discussed in the "closures" section later)

Example:-

```
\var x = 50; 
function test() { 
      var x = 42; 
      function printvaluex(){ 
             console.log(x); 
      } 
} 
```

Even though there is a global 'x' existing, the child function is in test scope. This is because the child's lexical environment is in closure to its parent, not the global value 'x'.