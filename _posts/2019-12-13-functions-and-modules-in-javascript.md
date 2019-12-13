---
title: Functions, Callbacks and Modules in JavaScript
image: "/assets/default-social-image.png"
categories: JavaScript-basics
---

**Functions in JavaScript**

A function is a collection of assertions that take inputs, perform certain specific calculations, and generate output. Generally, a function is a set of statements performing certain tasks or executing some calculations and then returning the outcome to the user.

The idea is to put together a specific or repetitive process to render a feature so that we can call the method rather than writing the same code over and over for different inputs.

JavaScript also supports the use of functions like other programming languages. You have already seen several widely used functions like alert() in JavaScript, it is a built-in JavaScript function. Nevertheless, JavaScript also allows us to build user-defined functions.

With the keyword function, we may generate functions in JavaScript. Below is shown the simple syntax for constructing a function in JavaScript.

**Syntax:**

```
function functionName(Parameter1, Parameter2, ..)
{
    // Function body
}
```

We must first use the keyword function to create a function in JavaScript, separated by function name and parameters within parenthesis. The structure part within the curly braces {} is the function's body.

**Function Definition**

Before, we need to develop this using a user-defined function in JavaScript. We could use the syntax above to create a JavaScript function. Function definition is also sometimes referred to as declaration of function or statement of function.

The rules for creating a JavaScript function are as follows:

* Each function should start with the function keyword followed by,
* A function name defined by the user that should be unique,
* A collection of parameters in parenthesis, distinguished by commas,
* Statement collections containing within the function's body inside curly braces {}.

Example:

```
function calcAddition(number1, number2)  
{  
    return number1 + number2;  
} 
```

We generated a function called calcAddition with the above instance, this function recognizes two numbers as variables and reverts these two numbers to be added.

**Function Parameters**

We've heard a lot about function parameters so far but we have not yet spoke about them in detail. Additional information is passed to a function by parameters. For example, the function calcAddition's job in the above illustration is to compute the addition of two figures.

These two numbers are carried to this function as parameters on which we want to conduct the addition operation. After the name of the function, the parameters are transferred to the function under parentheses and split by commas. A JavaScript function can have a number of parameters but can not have a single parameter at the same time.


**Calling Functions:** The next task is to call them to make use of the function after describing a function. By using the function name differentiated by the parameter value between parenthesis and a semicolon at the end, we may call a function in this manner. The syntax below illustrates how to label JavaScript functions:

`functionName( Value1, Value2, ..);`

Here is a sample program which shows how JavaScript functions operate:

```
<script type = "text/javascript"> 
  
// Function definition 
function welcomeMsg(name) { 
   document.write("Hello " + name + " welcome to World"); 
} 
  
// creating a variable 
var nameVal = "Admin"; 
  
// calling the function 
welcomeMsg(nameVal); 
  
</script> 
```

Output:

`Hello Admin welcome to World`

**Return Statement:** There are some cases where, after some operations, we want to return any values from a function. We can use the return statement in JavaScript in such cases. This is an optional statement in a JavaScript function and most of the times, the last statement. Look at our first instance with the calcAddition function. This function calculates two amounts and returns the outcome thereafter. Using the return declaration is the most fundamental syntax:

`return value;`

The return declaration starts with the return keyword distinguished by the value we want to return from it. We can also use an expression rather than returning the value directly.

**JavaScript Callbacks**

After something else has been completed, callbacks are a great way to handle something. We mean an execution of function by saying as something here. If we want a function to be implemented right after some other function is returned, callbacks can be used.

JavaScript functions have the object type. So, like any other objects (string, arrays, etc.), they can be passed on to any other function as an argument during the call.

**Code to display callback work:**

Code #1:

```
<script> 
  
   // add() function is called with arguments a, b 
   // and callback, callback will be executed just  
   // after ending of add() function 
   function add(a, b , callback){ 
   document.write(`The sum of ${a} and ${b} is ${a+b}.` +"<br>"); 
   callback(); 
   } 
     
   // disp() function is called just 
   // after the ending of add() function  
   function disp(){ 
   document.write('This must be printed after addition'); 
   } 
     
   // Calling add() function 
   add(5,6,disp);     
     
</script> 
```

Output:

```
The sum of 5 and 6 is 11.
This must be printed after addition
```

**Explanation:**

Here are the add (a, b, callback) and disp() functions. Here add() is called with the disp() function, i.e. passed in together with two numbers as the third argument to the add function.

Consequently, add() is invoked with 1, 2 and disp() is the callback. The add() prints the number after adding the two numbers and the callback function will be fired as soon as that is done! Therefore, we see what is inside the disp() as the output below, is the output of the addition.

**Code #2:**

An alternative method of applying the code above is shown below for passing anonymous functions.

```
<script> 
  
   // add() function is called with arguments a, b 
   // and callback, callback will be executed just  
   // after ending of add() function 
   function add(a, b , callback){ 
   document.write(`The sum of ${a} and ${b} is ${a+b}.` +"<br>"); 
   callback(); 
   } 
   
   // add() function is called with arguments given below 
   add(5,6,function disp(){ 
   document.write('This must be printed after addition.'); 
   }); 
     
</script> 
```

Output:

```
The sum of 5 and 6 is 11.
This must be printed after addition.
```

Callbacks are primarily used when handling asynchronous operations, such as requesting an API to the Google Maps, fetching/writing data from/to a file, registering listeners for events and related material. All of the above operations use callbacks. This way, once the asynchronous operation data/error is returned, the callbacks are used in our code to do something with.

**JavaScript Modules**

Closure is one of Javascript's most essential yet most misunderstood concepts. The closure is a technique where a child function should retain the parent scope environment even after the parent function has already been performed, otherwise we can claim to recall or replicate the scope and its members that have already been completed once.

JavaScript modules are now Closure's finest implementations. Modules are small units of distinct, reusable code to be used as the building blocks to generate a non-trivial Javascript program. Modules enable the programmer to identify private and public members independently, making it one of JavaScript's very anticipated development patterns. As in any other object-oriented programming language, you could see modules as classes.

Note that in ES2015, the class keyword was used to define JavaScript classes, but while JavaScript is still more of a classless programming language, ES2015 classes are essentially unique functions.

Moving to Modules, let's just get to see an illustration in seeing what Modules could do, we'll try to recreate the activity of a given two-sided lengths of rectangle class and returning the area.

```
<script> 
// This is a Rectangle Module.  
function Rectangle()  
{  
    var length, width;  
  
    function create(l, w)  
    {  
        length = l;  
        width = w;  
    }  
  
    function getArea()  
    {  
        return (length * width);  
    }  
  
    function getPerimeter()  
    {  
        return (2 * (length + width));  
    }  
  
    // This is the object to consist public members.  
    // The rest are private members.  
    var publicAPI = {  
        create : create,  
        getArea : getArea,  
        getPerimeter : getPerimeter  
    };  
  
    // To be returned upon creation of a new instance.  
    return publicAPI;  
}  
  
// create a Rectangle module instance  
var myRect = Rectangle();  
myRect.create(5, 4);  
document.write("Area: " + myRect.getArea());  
document.write("<br> Perimeter: " + myRect.getPerimeter()); </script> 
```

Output:

```
Area: 20
Perimeter: 18
```

The Rectangle() function here serves as an outer scope containing the required variables, i.e. length, width, and the create(), getArea(), and getPerimeter() functions. All of these together are the private information which can not be accessed/modified from the outside of this rectangle module.

On the other side, as the name suggests, the public API is an object made up of three functional members and will be returned once the execution of the rectangle function is finished. Using the methodology of the API, we can build and obtain the value of the rectangle area and perimeter.

Note that as we previously mentioned that modules are the closest class concepts in any other OOP language, several programmers may want to use the 'new' keyword when building a new Rectangle Module instance. Rectangle() is just a function to instantiate and not a formal class, so it's only called normally. It would be inappropriate and would waste resources to use the new.

Performing Rectangle() function generates an instance of the rectangle module which produces and allocates a whole new scope to the function thereby creating a new instance of the function member since we allocated it to a variable, now the variable has a reference to the allowed members of the public API. Therefore, we could see that executing the Rectangle() function produces a completely separate new instance from any previous instance.

All the member functions have a length and width closure, which ensures that even after the execution of the Rectangle() function finished its execution, such functions can access them.

Which sums up how JavaScript modules operate. On JavaScript, we will discover more interesting topics and make relevant projects to refine our newly learned abilities in the near term.

**Importing and Exporting Modules**

JavaScript modules are essentially libraries included in the program in consideration. These are used to link two JavaScript programs to access the functions written in one program without writing the function body itself in another one.

**Importing a library:** this ensures that a library is included in a program to define the function in that library. Use the feature 'require' to pass the library name with its relative path for this purpose.

Example: Suppose a library with the file name library.js is created in the same directory, then include the file with the function require:

`const lib = require('./library') `

This will return the library's reference. Now, if the library has a defined area function, use it as lib.area().

**Exporting a library:** JavaScript contains a special object called module.exports. This object will be exposed if some program includes or imports this module (program). Hence, all the functions which need to be exposed or be accessible in order to be used in some other file defined in module.exports.

Expample : Compose two separate programs just to see how to use the functions defined in the program's library (Module). Define two basic functions in the library while provided with length and breadth to calculate and print the area and perimeter of a rectangle. And after that, export the functions so that they can be imported and used by other programs if needed.

**Exporting Module Example : library.js**

```
<script> 
// Area function 
let area = function (length, breadth) { 
    let a = length * breadth; 
    console.log('Area of the rectangle is ' + a + ' square unit'); 
} 
  
// Perimeter function 
let perimeter = function (length, breadth) { 
    let p = 2 * (length + breadth); 
    console.log('Perimeter of the rectangle is ' + p + ' unit'); 
} 
  
// Making all functions available in this 
// module to exports that we have made 
// so that we can import this module and 
// use these functions whenever we want. 
module.exports = { 
    area, 
    perimeter 
} 
</script> 
```

**Importing Module Example**

Use a function called 'Require' to import any module which takes the name of the module and if the module is defined by its user then use its relative path as an argument and return its reference.

The JavaScript module (library.js) above is included in the script.js.

**Script.js**

```
<script> 
// Importing the module library containing 
// area and perimeter functions. 
// " ./ " is used if both the files are in the same folder. 
const lib =  require('./library'); 
  
let length = 10; 
let breadth = 5; 
  
// Calling the functions  
// defined in the lib module 
lib.area(length, breadth); 
lib.perimeter(length, breadth); 
</script> 
```

Output:

```
Area of the rectangle is 50 square unit
Perimeter of the rectangle is 30 unit
```

Note: Create all files in the same directory to execute the script first and use script.js using the terminal NodeJs interpreter.