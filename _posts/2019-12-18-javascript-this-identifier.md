---
title: JavaScript 'this' Identifier
image: "/assets/default-social-image.png"
categories: JavaScript-basics
---

'This' attribute can be used in various contexts and scopes of JavaScript. Let's go over each one to evaluate what 'this' is like and how it's determined.

**Global Scope**

Whenever in the global context 'this' keyword is used, i.e. not as a part of function or object declaration, it always applies to the Global object. 'this' action will be highlighted in the following scenario.

```
// Declaring variable in global context. 
var a = "WAP"; 
console.log(a); 
  
// Using this we refer to the Global Context. 
// And update the value of a we declared previously. 
this.a = "WeAreProgrammers"; 
console.log(a); 
```

Output:

```
WAP
WeAreProgrammers
```

**Functional Scope**

If a function has within it a 'this' connection, it can be said that this applies to an object, not to the function itself (which is normally the most frequent mistake developers do).

This relies on how the function was first defined to decide which object the 'this' refers to. The illustration below will shed some light on the situation.

```
// Function that contains this. 
function myFunc() { 
  console.log( this.a ); 
} 
  
var a = "Global"; 
  
// Owner of the function. 
var myObj1 = { 
  a: "myObj1", 
  myFunc: myFunc 
}; 
  
// Object other than the owner. 
var myObj2 = { 
  a: "myObj2"
}; 
  
// Call the function in Global Scope. 
myFunc(); 
  
// Call the function from the reference of owner.  
myObj1.myFunc(); 
  
// Call the function from the reference 
// of object other than the owner. 
myFunc.call( myObj2 ); 
  
// Create a new undefined object. 
new myFunc(); 
```

Output:

```
Global
myObj1
myObj2
undefined
```

You could see four various ways in which we can evaluate what 'this' leads to. For how 'this' is organized, there are four principles, let's clarify such four for ourselves.

* In the first call, myFunc() finishes setting this in non-strict mode to the Global object. While 'this' would be undefined in strict mode, JavaScript would dump an error in the property's access.
* MyObj1.myFunc() sets 'this' to the myObj1 object, here myObj1 is the holder of the myFunc method, so we call the object relation function itself with reference, so it relates to the owner object in such situations.
* 'ihis' is provided by myFunc.call(myObj2) to the myObj2 object. It indicates that this does not necessarily refer to the object of the owner, but rather to the object under whose scope the feature is called.
* New myFunc() sets 'this' to a brand new empty object, so in the console log, we get undefined.

Note: Through using this simple method, we could decide whom corresponds to 'this'. Whenever a function of 'this' is called, we can glance at the parentheses pair's immediately left of it. When there is a relation on the left side of the parentheses, then "this" is the object to which it refers, otherwise it is the global object. Assuming no unique function has been used to invoke the function.

**Inside an Event Handler**

'this' always relates to the component on which it was triggered within an event handler. Let's see an illustration showing the same issue.

```
<div id="clickMe">Welcome to World!</div> 
  
function clickedMe() {  
    console.log(this.innerHTML);  
}  
  
clickedMe(); // undefined because global object.  
  
var myElem = document.getElementById('clickMe');  
myElem.onclick = clickedMe;  
   
myElem.onclick(); // Welcome to World! 
```

Output:

```
undefined
Welcome to World!
```

Here we can see that the first call was made throughout the Global scope and therefore 'this' applied to the Global Object and was logged for undefined. So we copied the function to myElem.onclick event so whenever you activate the onclick function, 'this' refers to the myElem component which is the div with id clickMe, so 'Welcome to World!' is registered.

As we can state we know how to set 'this' to a specific object and we have to worry about one less misconception now.

The JavaScript 'this' keyword seems to have become a cause of great confusion to the language for newcomers. Most of this misunderstanding arises from the fact that 'this' is treated differently in JavaScript relative to other languages such as Java or Python's self.

Understanding 'this' is absolutely imperative to comprehend more complex JavaScript concepts or for reading and writing JavaScript code, that's why we're going to spend this post trying to illustrate what JavaScript 'this' really means.

We're going to spend a lot of the topic studying about 'this' with respect to JavaScript functions, which is why we're going to first glance at a detail about JavaScript functions to make us get there easier.

**this and Functions**

Functions are simply objects of JavaScript. They can be allocated to parameters like objects, moved on to other functions and retrieved from functions. And they have their own property, much like objects. 'this' is one of those properties.

The information 'this' holds is the actual execution context of the JavaScript code. 'this' meaning can change based on how that function is defined, how it is called, and the standard execution context when used within a function.

Note: 'this' always includes a relation to a single object, which determines the scope of execution of the current line of code.

Before we go into how 'this' plays, let's look at how it operates outside of functions:

**Global Context:**

It is said that a line of code written outside a function belongs to the global context, and in this global context, its value is the same as the global object.

If you launched your browser console and wrote by pressing return/enter console.log(this)

You'd seeing the Window object loaded into the console. This is because the Window object is the Window object in a browser run-time like the run-time in Chrome.

The global context may no longer be present within a function though, and the function may have its own established context and thus a separate value of it. Let's turn our attention back to functions to grasp it:

Through JavaScript, functions can be invoked in several ways:

1. Function invocation
2. Method invocation
3. Constructor invocation

**'this' with function invocation:**

Function invocation refers to the practice of invoking a function using its name or an expression that executes the function object accompanied by a series of first brackets opening and closing (including brackets means that we request the JavaScript engine to run the function instantly).

Example:

```
<!DOCTYPE html> 
<html> 
<body> 
<script> 
    function doSomething() { 
        // do something here 
    } 
  
// function invocation 
doSomething();  
</script>                     
</body> 
</html> 
```

'this inside the doSomething function has the value of the global object, which is the window object in the browser environment if triggered by the function invocation as above:

```
<!DOCTYPE html> 
<html> 
<body> 
<script> 
    function doSomething(a, b) { 
  
       // adds a propone property to the Window object 
        this.propone = "test value";  
    } 
  
// function invocation 
doSomething();  
document.write(window.propone); 
</script> 
</body> 
</html>  
```

Output:

`test value `

If the doSomething() function is operating in strict mode, it would report undefined instead of the global window object. This is because the default value for any feature object is set to undefined instead of the global object in strict mode(indicated by the line: 'use strict';).

Example :

```
<!DOCTYPE html> 
<html> 
<body> 
<script> 
    function doSomething() { 
        // enable the strict mode 
        'use strict';  
  
       // logs undefined 
        document.write(this + '<br>')  
            function innerFunction() { 
              // Also logs undefined, indicating that  
              // strict mode permeates to inner function scopes 
                document.write(this)  
            } 
        innerFunction(); 
    } 
  
// function invocation 
doSomething();  
</script> 
</body> 
</html> 
```

Output:

```
undefined
undefined 
```

**this with method invocation:**

Functions are referred to as methods as described as fields or properties of objects.

```
<!DOCTYPE html> 
<html> 
<body> 
<script> 
    let person = { 
        name : "John", 
        age : 31, 
        logInfo : function() { 
            document.write(this.name + " is " + this.age + " years old "); 
        } 
    } 
       // logs John is 31 years old 
       person.logInfo()  
                 </script> 
</body> 
</html> 
```

Output:

`John is 31 years old `

logInfo() is a method of the person object in the instance above and we invoked it using the invocation pattern.

Therefore, to reach the method that was part of the object, we used the property accessors.

Such an invocation involves the use of an expression evaluating the object of which our process is part and a property accessor (e.g. person.logInfo()) accompanied by a series of parentheses opening and closing.

Knowing how functional invocations and invocations of methods vary is important.

That in effect will help us to understand what 'this' meaning could be in any particular function, as the significance of 'this' is different in each of these invocations.


Within such a procedure, invoked using the property accessors, 'this' will have the value of the invoking object i.e. 'this' will refer to the object used to make the call in accordance with the property accessor.

Example :

```
<!DOCTYPE html> 
<html> 
<body> 
<script> 
    let add = { 
        num : 0, 
        calc : function() { 
  
            // logs the add object 
            document.write(this + ' ')  
                this.num 
                += 1; 
            return this.num; 
        } 
    }; 
  
// logs 1 
document.write(add.calc() + '<br>');  
// logs 2 
document.write(add.calc());  
</script>                     
</body> 
</html> 
```

Output:

```
[object Object] 1
[object Object] 2 
```

In the instance above, calc() is an insert object method and is thus called using the invocation rules of the method in lines 9 and 10.

So we recognize that the value of 'this' is assigned to the calling object when method invocation patterns are being used.

The value of 'this' is set within this calc() method to the calling object, which is add to our case. And so we can reach the numproperty of add effectively.

Let us first look at one major point of confusion:

What happens to 'this' in a function nestled within an object's method?

```
<!DOCTYPE html> 
<html> 
<body> 
<script> 
    let add = { 
        num : 0, 
        calc : function() { 
  
        // logs the add object 
        document.write(this + ' ')  
  
        function innerfunc() { 
            this.num += 1; 
  
        // logs the window object 
        document.write(this + ' ');  
  
        return this.num 
  
    } return innerfunc(); 
     } 
}; 
  
// logs NaN 
document.write(add.calc() + '<br>');  
  
// logs NaN 
document.write(add.calc()); 
</script> 
</body> 
</html>  
```

Output:

```
[object Object] [object Window] NaN
[object Object] [object Window] NaN 
```

Let's try to figure to see what has happened.

When calling calc() in lines 14 and 15, we use invocation method which sets 'this' to be add to calc(). Use the log statement in line 4 to check this.

Within the calc() method, however, innerfunc() is called using a simple invocation(line 11) function. This means that this is set to the global object inside innerfunc(), which has no number property, and thus the NaN outputs are received.

How can we solve this problem?How would we maintain the value of this' within the nested function from the outer method?

One alternative is to allocate this value to a variable to be used in the nested function like this from the outer function:

```
<!DOCTYPE html> 
<html> 
<body> 
<script> 
    let add = { 
        num : 0, 
        calc : function() { 
  
            // logs the add object 
            document.write(this + ' ')  
  
           // using thisreference variable to  
           // store the value of this 
           thisreference = this;  
  
            function innerfunc() 
            { 
  
             // using the variable to access the 
             // context of the outer function 
                thisreference.num += 1;  
  
               // logs the add object 
                document.write(thisreference + ' '); 
                return thisreference.num; 
            } 
            return innerfunc(); 
        } 
    }; 
  
// logs 1 
document.write(add.calc() + '<br>');  
  
// logs 2 
document.write(add.calc());  
</script> 
</body> 
</html> 
```

Output:

```
[object Object] [object Object] 1
[object Object] [object Object] 2 
```

Other approaches to this issue include bind(), call() or apply(), which we will be looking soon.

**'this' with constructor invocation:**

Constructor invocation is done when a function name and a set of parentheses (with or without arguments) are followed by a new keyword.

Example:

let person1= new People(‘John’, 21);

Here, the newly created object is person1 and the constructor function used to build this object is People.

The invocation of the constructor is one of several aspects JavaScript constructs objects.

What happens in conjunction with a function name when we use the new keyword?

Essentially, there are five phases involved in the creation of an object through this process.

```
<!DOCTYPE html> 
<html> 
<body> 
<script> 
let people = function(name, age) { 
         this.name = name; 
         this.age = age; 
  
    this.displayInfo = function() { 
       document.write(this.name + " is " + this.age + " years old"); 
      } 
    } 
  
let person1 
    = new people('John', 21); 
  
// logs John is 21 years old 
person1.displayInfo(); 
</script> 
</body> 
</html> 
```
Output:

`John is 21 years old `

* First, an empty object is generated which is an instance of the new(i.e.: people(name, age)) function name used. In other words, it sets the object's constructor property to the invocation(people(name, age)) function.
* It then connects the prototype of the constructor function(people) to the newly created object, so that this object will inherit all the constructor function properties and methods.
* Therefore, on this newly created object, the constructor function is called. When we recall the invocation process, we will see that it is identical. Hence, within the constructor function, the value of the newly created object used in the call is 'this'.
* Ultimately, the generated object is returned to person1 with all its properties and methods.

It should be remembered that the new keyword is crucial in order to set the context within the function of the constructor accurately. Without a new one, we would have a normal invocation of the function and therefore this could be wrongly set to the global object even within the constructor.

We will be covering more topics like Arrow functions, separated methods etc. related to this in JavaScript in Set-2.