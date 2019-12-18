---
title: JavaScript Polyfilling & Transpiling
image: "/assets/default-social-image.png"
categories: JavaScript-basics
---

Because of the rapid changes to JavaScript implementation, the syntax types and vocabulary are also changed in JavaScript, so many of the JavaScript functionality are new additions and may not even be usable in older browsers, i.e. browsers operating on older JavaScript versions.

Another concern is that some of the browsers do not find JavaScript's newest capabilities to be stable due to the extreme power it can handle, and therefore they are not included or included as an experimental mode with restrictions to prevent use. Yet why are we even going to discuss this? JavaScript is used primarily to develop client-side applications, and the successful execution of the programs depends in part on the client's machine, i.e. the JavaScript version available on the client's browser.

Now the naive method would be to run only such features that can be run in the browser of the client, although this is not really a sensible approach. A programmer can use two key strategies to "bring" the new features of JavaScript to older browsers, namely **Polyfilling** and **Transpiling**.

**Polyfilling**

Polyfilling is Remy Sharp's invented term. It is one of the tools that can be used as some kind of calculation for backward compatibility. Remy himself offers the description.

“A polyfill, or polyfiller, is a piece of code (or plugin) that provides the technology that you, the developer, expect the browser to provide natively. Flattening the API landscape if you will.”
— Remy Sharp

If we demonstrate what he meant to say, we'll get that, A polyfill or polyfiller is a script segment that should behave in the same way as a modern JavaScript feature and still be able to run on older versions. For instance, ES2015 provides a new Number.isNaN(…) functionality to provide a reliable and effective mechanism for testing the values of **NaN** or **Not a Number**. To duplicate this action, we can use polyfilling and use it on some browsers pre-ES2015. The following description of our situation will be useful.

```
// Check if Number.isNaN already exists. 
// If False then proceed. 
if (!Number.isNaN) { 
  
    // Define explicitly for older browsers. 
    Number.isNaN = function isNaN(x) { 
  
        // This is a property of NaN. 
        // No two NaN can be equal to the other. 
        // Because NaN is a concept not a comparable value. 
        return x !== x; 
    }; 
} 
```

First, we check whether the method is already present and inhibit the explicit version from being defined if so. If not present then we are certainly on an older version of JavaScript and we describe clearly one using the NaNs property that no two NaNs are equivalent to each other because NaNs is a term, not a relative attribute to be identical to the other. Therefore, if they are not identical, we will return True whereas otherwise we will return False. This is one of the simplest polyfills to be found.

Note: Some new features are not polyfillable or it is not often possible to produce polyfills without any variation, so it is advised to have complete knowledge of the function when adding polyfills directly. Nevertheless, most programmers tend to use the already usable polyfills. Some of these are listed below.

* [ES6 Shim](https://github.com/es-shims/es6-shim)
* [ES5 Shim](https://github.com/es-shims/es5-shim)

**Transpiling**

Modern JavaScript releases often include syntax changes that can't be polyfilled as they just don't get implemented and instead throw syntax errors in existing JavaScript systems, this is where a transpiler falls in. The union of two operations it executes **Transformation + Compiling** offers it its name. First, we can now describe a "Transpiler" as a method that converts modern syntax code into older syntax equivalents and this mechanism is named "Transpiling".

Through programming practice, while using Transpiling, it is important to write the code that retains the modern syntax, but using a transpiler equivalent to a minifier or linter to execute the transpiled old syntax-friendly software when deploying the design. Which raises the question why, while still retaining the older one, should we even bother writing in the current syntax form? This is a very rational question to ask, and there are many good points to offer as responses, few of which are provided below.

* This remains without saying that the new syntax has been introduced to the language in order to make the program easier to read and retain, i.e. the newer versions are simply better than the older counterparts. In order to accomplish a better result, it is advised to write newer and simpler syntax.
* We will take advantage of browser speed improvements by transpiling only for older browsers when providing the latest syntax to the new updated browsers.
* And to use the latest syntax sooner enables it to be checked more robustly in the real world, and gives better input and can be changed/fixed if found early enough before such language development bugs become unavoidable. It makes the syntax much more robust in the long run by using the older syntax.

Let's take those Transpiling instances. ES2015 has added a new default parameter value syntax function, which can be enforced using the following.

```
// Default Parameter Value Example. 
// If no parameter is passed a will be 5. 
function myFunc(a = 5) 
{ 
    console.log(a); 
} 
  
myFunc(96); // Logs 96. 
myFunc(); // Logs 5 as default. 
```

As you have seen, if the parameter is not specified, we can take into account the default parameter value, but this syntax will not be known in engines pre-ES2015. So we'll get the older equivalent as follows after transpiling.

```
// Default Parameter Value Example. 
// If no parameter is passed a will be 5. 
function myFunc() 
{ 
    // Using Ternary Operator to assign default 
    // 5 if undefined. 
    var a = (arguments[0] !== undefined) ? arguments[0] : 5; 
    console.log(a); 
} 
  
myFunc(96); // Logs 96. 
myFunc(); // Logs 5 as default. 
```

As seen in the preceding case, if the argument is found to be undefined, we can use a ternary operator to allocate the default value to the ES6 counterpart. Now let's see thick arrow methods of ES6 for another example.

```
// Function Defining is now this easy. 
var myFunc = () => { 
    console.log("This is a function."); 
} 
  
myFunc(); // This is a function. 
```

As you see in the the above illustration, we can define a function even without using the keyword function and without messing with comprehensibility, but this will not be accepted in pre-ES6 engines, so the corresponding code will be as follows.

```
// Function Defining is now this easy. 
var myFunc = function() { 
    console.log("This is a function."); 
} 
  
myFunc(); // This is a function. 
```

It will be very weird to finish this article after reading about Transpilers without understanding some of the biggest Transpilers available. The following is a short list of resources like this.

[Babel](https://babeljs.io/)
[Traceur](https://github.com/google/traceur-compiler)

Finally, we've discussed enough yet to acquire knowledge of how those techniques are and how the use of both would be essential not just to the programmer, but also to JavaScript development itself.

Reference:
[https://remysharp.com/2010/10/08/what-is-a-polyfill](https://remysharp.com/2010/10/08/what-is-a-polyfill)