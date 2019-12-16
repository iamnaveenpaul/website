---
image: "/assets/default-social-image.png"
title: Type Conversion, Error and Exceptional Handling and Strict Modes in JavaScript
categories: JavaScript-basics
---

**JavaScript Type Conversion**

JavaScript is dynamically typed language and most often operators automatically convert a value to the correct type, but there are also situations when converts of type have to be rendered explicitly.

Although JavaScript offers several ways to convert information from one form to another, there are two popular conversions of data:

* **Converting Values to String**
* **Converting Values to Numbers**

**Implicit Conversion:**

Throughout JavaScript, there are various operators and functions that automatically convert a value to the right type, as the alert() function in JavaScript takes each value and transforms it to a string. Yet different operators create an operator problem like the '+'.

Example:

```
Input: "2" + "3"
Output: "23"
here + operator stands for string concatenation in this case.
But "3" - "1" gives output 2 by using Implicit Conversion.
```

**Code #1:**

This script demonstrates JavaScript's implicit type conversion.

```
<script>
  
  document.write('("3" - "1") = ' + ("3" - "1") + "<br>"); 
  document.write('("3" - 1) = ' + ("3" - 1) + "<br>"); 
  document.write('("3" * "2") = ' + ("3" * "2") + "<br>"); 
  document.write('("3" % "2") = ' + ("3" % "2") + "<br>"); 
  document.write('("3" + null) = ' + ("3" + null) + "<br>"); 
    
</script>
```

Output:

```
("3" - "1") = 2
("3" - 1) = 2
("3" * "2") = 6
("3" % "2") = 1
("3" + null) = 3null
```

**Converting Values to Strings:**

In JavaScript, the function **String()** or **toString()** can be used to transform a value to a string.

**Syntax of String() function:**

`String(value)`

Example:

```
Input:
var v = 1555;
var s = String(v);
Output:
now s contains "1555".
```

**Syntax of toString() function:**

`variableName.toString(base)`

Example:

```
Input:
var v = 1555;
var s = v.toString();
Output:
now s contains "1555".
```

**Code #2:**

Given below, the number will be translated to string, the boolean value to string and the dates to string.

```
<script> 
    
  // Number and date has been assigned 
  // to variable v and d respectively 
  var v = 123; 
  var d = new Date('1995-12-17T03:24:00'); 
    
  // Conversion of number to string 
  document.write(" String(v) = " + String(v) + "<br>");  
    
  // Conversion of number to string 
  document.write(" String(v + 11) = " + String(v + 11) + "<br>"); 
  document.write(" String( 10 + 10) = " + String(10 + 10) + "<br>");  
    
  // Conversion of boolean value to string 
  document.write(" String(false) = " + String(false) + "<br>");  
    
  // Conversion of Date to string 
  document.write(" String(d) = " + String(d) + "<br>");  
    
</script> 
```

Output:

```
String(v) = 123
String(v + 11) = 134
String( 10 + 10) = 20
String(false) = false
String(d) = Sun Dec 17 1995 03:24:00 GMT+0530 (India Standard Time)
```

**Converting Values to Numbers:**

In JavaScript, we can use **Number()** to convert a value to a number. Every numerical text and boolean value can be transformed to a number. It will convert it to a **NaN** (Not a Number) in non-number strings.

**Syntax:**

`Number(valueToConvert)`

Example:

```
Input:
var s = "144";
var n = Number(s);
Output:
now n contain 144(Number).
```

**Code #3:**

The code below converts to a number from a numerical text, dates and boolean values.

```
<script> 
    
  // Number and date has been assigned 
  // to variable v and d respectively 
  var v = "144"; 
  var d = new Date('1995-12-17T03:24:00'); 
    
  // Conversion of string to number 
  document.write(" Number(v) = " + Number(v) + "<br>");  
    
  //Conversion of boolean value to number 
  document.write(" Number(false) = " + Number(false) + "<br>");  
  document.write(" Number(true) = " + Number(true) + "<br>"); 
    
  // Conversion of date to number 
  document.write(" Number(d) = " + Number(d) + "<br>"); 
    
</script> 
```

Output:

```
Number(v) = 144
Number(false) = 0
Number(true) = 1
Number(d) = 819150840000
```

**code #4:**

If the string is non-number, it is converted to NaN and white space strings or empty strings are converted to 0.

```
<script> 
  
    // Empty string assigned 
    var v = ""; 
      
    // White space assigned 
    var d = " "; 
      
    // Non-number string assigned 
    var s = "GeeksforGeeks"; 
      
    // Printing converted values of number 
    document.write(" Number(v) = " + Number(v) + "<br>"); 
    document.write(" Number(d) = " + Number(d) + "<br>"); 
    document.write(" Number(s) = " + Number(s) + "<br>"); 
      
</script>
``` 

Output:

```
Number(v) = 0
Number(d) = 0
Number(s) = NaN
```

**Javascript Error and Exceptional Handling With Examples**

An error is an inaccurate or wrong behavior due to an action.. There are three types of programming errors that are listed below:

* **Syntax error**
* **Logical error**
* **Runtime error**

**Syntax error:** As per computer engineering, a syntax error is an error in the syntax of a sequence of characters or tokens intended to be transcribed in a specific programming language, as well as it is also the compile-time error if the syntax is incorrect, this will give an error message.

Example:

```
<script type="text/javascript"> 
  
      // Here the semicolon after the printing statement 
      //  is missing and it is a syntax error 
      window.print()   
  
</script> 
```

Since the syntax of the JavaScript is not appropriate, only the thread under this JavaScript will be impacted and the remainder of the code in other threads will be implemented as nothing in them will depend on the code involving the error.

**Logical error:** It is the most challenging error to detect because the mistake on the logical aspect of the coding or logical error is a bug in a program that allows it to function inappropriately and fail (or crash) abnormally.

**Runtime Error:** An error that happens while program execution, often known as the exceptions. In the instance below the syntax is right, but at runtime it tends to call a non-existent method.

Example:

```
<script type="text/javascript"> 
  
      // An runtime error here  
      window.printme();  
  
</script> 
```

There are exceptions as in the runtime error, and this exception is valid by using the try and catch method.

**try..catch method:** JavaScript uses the try..catch and finally handle the exception and the throw operator is also used to handle the exception. Try is to run the main code and give the exception statement to all the things related to the exception in the, catch.

**Syntax:**

```
<script type="text/javascript"> 
   <!-- 
          try 
          { 
            // Here the main Code run  
            [break;] 
          }  
        
          catch ( exception e )  
          { 
             // The code will run when there is an exception  
             [break;] 
         }  
   //--> 
</script> 
```

Example 1:

```
<html> 
    <head> 
        <title>Error and Exception handling</title> 
        <script type="text/javascript"> 
            function First() { 
                var a = 123; 
                var b = 145; 
                var c = a + b; 
                alert("Value of a: " + a ); 
                alert("Value of b: " + b ); 
                alert("Sum of a and b: " + c); 
            } 
        </script> 
    </head> 
          
    <body> 
        <p>Click the GfG button to see the result:</p> 
          
        <form> 
            <input type="button" value="Click GfG" onclick="First();" /> 
        </form> 
          
    </body> 
</html> 
```

Use the method that will always execute unconditionally after the try/catch in this example.

Example 2:

```
<html> 
    <head> 
        <title>Error and Exception handling</title> 
        <script type="text/javascript"> 
            function First() { 
                var a = 123; 
                var b = 145; 
                var c = a + b; 
                try { 
                    alert("Value of a: " + a ); 
                    alert("Value of b: " + b ); 
                    alert("Sum of a and b: " + c); 
                } 
                catch ( e ) { 
                    alert("Error: " + e.description ); 
                } 
                finally { 
                    alert("Finally block will always execute!" ); 
                } 
            } 
        </script> 
    </head> 
          
    <body> 
        <p>Click the GfG button to see the result:</p> 
          
        <form> 
            <input type="button" value="Click GfG" onclick="First();" /> 
        </form> 
          
    </body> 
</html> 
```

**Strict mode in JavaScript**

In ECMAScript 5, Strict Mode is a new option which allows you to put a program or function in a "strict" operational sense. A stringent scope forbids the execution of certain actions and generates further exceptions. The sentence "use strict"; instructs the browser to use JavaScript's Strict mode, a reduced and safer set of features.

**Benifits of using ‘use strict’**

Strict mode makes a number of changes to normal semantics of JavaScript.

* Strict mode prevents certain silent errors from JavaScript by modifying them to throw errors.
* Strict mode addresses defects that render optimization difficult for JavaScript engines: often strict mode coding can be made to run quicker than the same code that is not strict mode.
* Strict mode prohibits certain syntax that will likely be defined in future ECMAScript versions.
* When relatively "unsafe" actions (such as gaining access to the global object) are taken, it prevents or throws errors.
* It disables confusing or poorly thought-out features.
* Strict mode makes "secure" JavaScript writing easier.

**How to use strict mode**

Strict mode can be used for the entire script in two ways, and can be applied to individual functions in global scope. Strict mode does not work within {} braces containing block statements.

**Using Strict mode for the entire script**

Put the exact statement "use strict"; (or 'use strict';) before any other statements to invoke strict mode for a whole script.

```
// Whole-script strict mode syntax
'use strict';
 let v = "strict mode script!";
```

NOTE: This syntax has a flow, non-conflicting scripts can't be blindly concatenated. Consider combining a strict mode script with a non-strict mode script: it looks strict for the whole concatenation! The opposite is also true: non-strict plus strict looks non-strict. It is good to concatenate strict mode scripts with each other, and it is also good to concatenate non-strict mode scripts. It is only problematic to concatenate strict and non-strict scripts. It is therefore recommended that you enable strict mode (at least during the transition period) on a function-by-function premise.

**Using Strict mode for the entire script**

Similarly, to induce strict mode to a function, put that exact statement "use strict"; (or 'use strict;') before any other statements in the body of the function.

```
function strict() {

  // Function-level strict mode syntax
  'use strict';

  function nested() { return 'Javascript on GeeksforGeeks'; }

  return "strict mode function!  " + nested();
}
function notStrict() { return "non strict function"; }
```

**Examples of using Strict mode**

* Mistyping a variable name in normal JavaScript creates a new global variable. This will trigger an error in strict mode, making it impossible to create a global variable accidentally
* Do not allow a variable to be used in strict mode without declaring it

```
// Using a variable, without declaring it, is not allowed: 
'use strict'; 
 x = 3.14;  // will throw an error 
```

```
// Objects are variables too. 
// Using an object, without declaring it, is not allowed: 
'use script'; 
  x = {p1:10, p2:20}; // will throw an error 
```

* It is not allowed to delete a variable (or object) and a function.

```
'use strict'; 
 let x = 3.14; 
  
// Deleting a function is also not allowed 
'use strict'; 
 function x(p1, p2) {};  
 delete x;     // will throw an error  
```

* It is not allowed to duplicate a parameter name

```
'use strict'; 
 function x(p1, p1) {};   // will throw an error 
```

* It is not allowed to use Octal numeric literals.

```
'use strict'; 
 let x = 010;       // will throw an error 
```

* It is not allowed to use Escape characters.

```
'use strict'; 
 let x = \010;     // will throw an error 
```

* It is not allowed to write to a read-only property

```
'use strict'; 
 let obj = {}; 
 Object.defineProperty(obj, "x", {value:0, writable:false}); 
  
 obj.x = 3.14;     //will throw an error 
```

* It is not allowed to write to a get-only property

```
'use strict'; 
 let obj = {get x() {return 0} }; 
  
 obj.x = 3.14;     // will throw an error 
```

* It is not allowed to Delete an undeletable property

```
'use strict'; 
 delete Object.prototype; // will throw an error 
```

* It is not allowed touse the string "test" as a parameter

```
'use strict'; 
 let eval = 3.14;  // will throw an error 
```

* It is not allowed to use the string “arguments” as a variable

```
'use strict'; 
 let arguments = 3.14;    // will throw an error 
```

* It is not allowed to use the with statement

```
'use strict'; 
 with (Math){x = cos(2)}; // will throw an error 
```

* This value was the global object in function calls such as f(). It's now undefined in strict mode
* A developer will not receive error feedback in normal JavaScript assigning values to non-writable properties

**Strict Mode**

JavaScript is a dynamic language, i.e. each element of JavaScript is dynamic from variables to the script itself. With JavaScript, you can build variables in runtime, change the type of data, create new functions or replace existing logic or in other words, while using JavaScript, the programmer is in almost complete control. Why is it that? There is a well-known saying, “With great power comes great responsibility.”

JavaScript embraces this concept very deeply, though JavaScript works as one of the strongest programming languages out there in a marksman coder project, it can function completely randomly in a novice's eyes. While being an essential part of building the desire to learn JavaScript inside-out, this spontaneous behaviour may build up some complications, especially when used in a project.

JavaScript programmers added a new feature to ES5 known as the Strict-Mode, which is intended to disallow certain language actions to decrease unpredictable activity and improve poorly written software detectability. These set of restrictions have made the code much more secure and generally maintain a high coding standard. Until execution by the computer, JavaScript codes are optimized, developers were now able to write highly optimized programs using the strict mode. An inclusion was for the industrial coding standards, not only recommended but was made mandatory by developers.

**Syntax:** In order to use strict mode in your script, we just need to exercise the following line below, the strict mode also known as strict mode pragma has its own scope and depending on the same can affect the entire file or individual methods.

`"use strict";`

**Functionalities:** We now know that strict mode is basically a JavaScript mode that is much more obsessed with correct syntax and other logical paradigms which is used to allow without much examination. But what are the syntax and logical errors that are no longer permitted in the strict mode? The following is a short list of some important ones.

**Auto-Global Variable Declaration:** This is one of JavaScript's biggest problems, without using the strict mode if you accidentally use a variable without its definition, JavaScript does not throw an error but defines the variable in global scope, which often amounts to randomness and unintended outputs. It will throw a regular reference error with strict mode enabled to notify that the variable to be used has never been defined.

Source:

```
"use strict"; // Turn on strict mode.
a = 1;  
```

Output:

`Uncaught ReferenceError: a is not defined`

Note: There are variables in JavaScript objects, so defining one also requires the keyword 'var', 'let' or 'const'.

**Deletion of any JavaScript element:** This is a big change from regular mode as the removal of any variable or function is disallowed in the strict mode. This makes the code much more optimizable as the scope is static and does not change throughout the lifetime.

Source:

```
"use strict"; // Turn on strict mode.
var a = 1;
delete a;  
```

Output:

`Uncaught SyntaxError: Delete of an unqualified identifier in strict mode.`

Note: you might ask as to why the error says unqualified? JavaScript provides the functionality where a property of an object can be defined as deletable, qualifying the property to be deleted in strict mode.

**Using reserved keyword as variable names:** Unlike most other JavaScript applications, reserved keywords can be used as the names of the variable that are disallowed in the strict mode.

Source:

```
"use strict"; // Turn on strict mode.
var eval = 5; 
```

Output:

`Uncaught SyntaxError: Unexpected eval or arguments in strict mode.`

**Duplication of parameter names:** Unlike most other JavaScript applications, identical parameter names that are disallowed in the strict mode can be used.

Source:

```
"use strict"; // Turn on strict mode.
var eval = 5; 
```

Output:

`Uncaught SyntaxError: Unexpected eval or arguments in strict mode.`

**References:**

* [https://es5.github.io/](https://es5.github.io/)
* [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode)