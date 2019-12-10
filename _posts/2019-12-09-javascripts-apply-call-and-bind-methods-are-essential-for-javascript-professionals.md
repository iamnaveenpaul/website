---
title: JavaScript’s Apply, Call, and Bind Methods are Essential for JavaScript Professionals
image: "/assets/default-social-image.png"
categories: JavaScript
---

Essential for JavaScript Professionals are Apply, Call, and Bind Methods.

Prerequisite:
— [Understand JavaScript’s “this” with clarity, and Master It](http://70.32.104.226/~javascriptissexy/understand-javascripts-this-with-clarity-and-master-it/).
— [JavaScript Objects in detail](http://70.32.104.226/~javascriptissexy/javascript-objects-in-detail/).
— [Understand JavaScript Closures with ease](http://70.32.104.226/~javascriptissexy/understand-javascript-closures-with-ease/).

Functions are objects in JavaScript, as you ought to understand now, once you have read any of the prerequisite sources. Yet functions include methods as objects including the efficient methods of Apply, Call and Bind methods. On the one side, Apply and Call are almost similar and are often used for borrowing methods in JavaScript and specifically attempting to set 'this' value. We also use Apply for functions of variable-arity; you'll learn a bit more about this.

On the other side, we use Bind in methods and currying functions to set 'this' value.

We're going to discuss any situation in which JavaScript utilizes these three approaches. While ECMAScript 3 (available on IE 6, 7, 8, and modern browsers) comes with Apply and Call, ECMAScript 5 (available only on modern browsers) introduced the Bind method. All three methods of operation are workhorses, and sometimes one of them is absolutely necessary. Let's start with the method 'Bind'.

**JavaScript’s Bind Method**

The Bind () method is mainly used to directly call a function with 'this' value set. In terms, bind () helps us to set quickly what particular object will be bound to when invoking a function or procedure.

This may seem fairly simple, but it is often necessary to set 'this' value specifically in methods and functions when you need a particular object linked to 'this' value of the function.

Normally the need for 'bind' arises while we use 'this' keyword in a method and we call the method from a receiver object; in such situations 'this' is sometimes not bound to the object we want to be bound to, and likely to result in errors in our applications. Do not concern if the previous paragraph is not fully understood. In a second, it will become transparent as a dewdrop.

We will grasp 'this' keyword in JavaScript before we look at the script for this chapter. If in JavaScript you don't already understand 'this', read: Understand JavaScript's "this" With Clarity, and Master It. If you don't grasp this well, some of the terms mentioned below will be having trouble understanding it. In fact, It also addressed several of the principles about setting 'this' value.

JavaScript’s Bind Allows Us to Set the 'this' Value on Methods

```
When the button below is clicked, the text field is populated with a random name.

    <pre><code data-language="javascript">
// Get Random Person
// 

var user = {
data :[
{name:”T. Woods”, age:37},
{name:”P. Mickelson”, age:43}
],
clickHandler:function (event) {
var randomNum = ((Math.random () * 2 | 0) + 1) – 1; // random number between 0 and 1

    // This line is adding a random person from the data array to the text field
    $ ("input").val (this.data[randomNum].name + " " + this.data[randomNum].age);
}
}

// Assign an eventHandler to the button’s click event
$ (“button”).click (user.clickHandler);
```

You get an error here when you click the button because 'this' is linked to the HTML element button in the clickHandler () method, since that is the object on which the clickHandler method is executed.

The particular issue is quite popular in JavaScript, since JavaScript frameworks such as Backbone.js and libraries such as jQuery do the bindings for us automatically, so 'this' is often bound to the object we want to be bound to.

In the example above, we can use the bind method to fix the problem:

Rather than this line:

` $ ("button").click (user.clickHandler);`

Just like this, we need to bind the clickHandler method to the 'user' object:

` $ ("button").click (user.clickHandler.bind (user));`

Remember another way of fixing 'this' value: you may pass an anonymous callback function to the click() method and jQuery binds 'this' to the button object within the anonymous function.

Due to the introduction of the Bind method by ECMAScript 5, that (Bind) is not usable in IE<9 and Firefox 3.x.

If you are targeting older browsers, include this Bind functionality in your code:

```
    <pre><code data-language="javascript">
        // Credit to Douglas Crockford for this bind method
        if (!Function.prototype.bind) {
            Function.prototype.bind = function (oThis) {
                if (typeof this !== "function") {
                    // closest thing possible to the ECMAScript 5 internal IsCallable function
                    throw new TypeError ("Function.prototype.bind - what is trying to be bound is not callable");
                }

                var aArgs = Array.prototype.slice.call (arguments, 1),
                        fToBind = this,
                        fNOP = function () {
                        },
                        fBound = function () {
                            return fToBind.apply (this instanceof fNOP && oThis
                                    ? this
                                    : oThis,
                                    aArgs.concat (Array.prototype.slice.call (arguments)));
                        };

                fNOP.prototype = this.prototype;
                fBound.prototype = new fNOP ();

                return fBound;
            };
        }
    </code></pre>
```

Let's proceed with the same illustration we used above. The 'this' value is also bound to another object if we allocate the method (where 'this' is defined) to a variable. This shows the following:

```
    <pre><code data-language="javascript">
        // This data variable is a global variable
        var data = [
            {name:"Samantha", age:12},
            {name:"Alexis", age:14}
        ]

        var user = {
            // local data variable
            data    :[
                {name:"T. Woods", age:37},
                {name:"P. Mickelson", age:43}
            ],
            showData:function (event) {
                var randomNum = ((Math.random () * 2 | 0) + 1) - 1; // random number between 0 and 1

                console.log (this.data[randomNum].name + " " + this.data[randomNum].age);
            }

        }

        // Assign the showData method of the user object to a variable
        var showDataVar = user.showData;

        showDataVar (); // Samantha 12 (from the global data array, not from the local data array)

    </code></pre>
```

When the showDataVar() function is executed, the values printed on the console are from the global data array and not the user object data array. That's due to the execution of showDataVar() as a global function and the use of this within showDataVar() is bound to the global scope, which is the browser window object.

Again, by setting the "this" value explicitly with the bind procedure, we can fix this issue:

```
    <pre><code data-language="javascript">
        // Bind the showData method to the user object
        var showDataVar = user.showData.bind (user);

        // Now the we get the value from the user object because the this keyword is bound to the user object
        showDataVar (); // P. Mickelson 43
    </code></pre>
```

**Bind () Allows us to Borrow Methods**

Through JavaScript, we can pass, return, borrow, etc for functions around. And the process of bind() renders the borrow methods fairly easy.

Here is an example to borrow a method using bind ():

```
    <pre><code data-language="javascript">
        // Here we have a cars object that does not have a method to print its data to the console
        var cars = {
            data:[
                {name:"Honda Accord", age:14},
                {name:"Tesla Model S", age:2}
            ]

        }

        // We can borrow the showData () method from the user object we defined in the last example.
        // Here we bind the user.showData method to the cars object we just created.
        cars.showData = user.showData.bind (cars);
        cars.showData (); // Honda Accord 14

    </code></pre>
```

The issue with this instance is that we are adding a new method (showData) to the object of the cars and we may not want to do this just to steal a method because the object of the cars may already have a property or the name of the method showData. We don't want to mistakenly overwrite it. It is best to borrow a method using either the Apply or Call method, as we will see in our discussion of Apply and Call below.

**JavaScript’s Bind Allows Us to Curry a Function**

Function Currying is the use of a function (which accepts one or more arguments) which returns a new function with some of the arguments already set, it is also known as also known as 'partial function application'. The returning function has access to the outer function's stored arguments and variables. It seems much more complicated than it is, so let's code it.

```
    Let's use the <em>bind ()</em> method for currying. First we have a simple greet () function that accepts 3 parameters:

    <pre><code data-language="javascript">
        function greet (gender, age, name) {
            // if a male, use Mr., else use Ms.
            var salutation = gender === "male" ? "Mr. " : "Ms. ";

            if (age > 25) {
                return "Hello, " + salutation + name + ".";
            }
            else {
                return "Hey, " + name + ".";
            }
        }
    </code></pre>

    And we use the bind () method to curry (preset one or more of the parameters) our greet () function. The first argument of the bind () method sets the <em>this</em> value, as we discussed earlier:
    <pre><code data-language="javascript">
    // So we are passing null because we are not using the "this" keyword in our greet function.
    var greetAnAdultMale = greet.bind (null, "male", 45);

    greetAnAdultMale ("John Hartlove"); // "Hello, Mr. John Hartlove."

    var greetAYoungster = greet.bind (null, "", 16);
    greetAYoungster ("Alex"); // "Hey, Alex."
    greetAYoungster ("Emma Waterloo"); // "Hey, Emma Waterloo."
    </code></pre>
```

When using the currying form of bind(), all parameters of the greet() function are preset except for the last (right side) statement. So it's the rightmost argument when we call the new functions curried from the greet() function that we're changing. Finally, I'm thinking about currying lengthily in a different article, and you'll see how we can easily create really efficient functions with two simple JavaScript techniques, Currying and Compose.

Therefore, we may explicitly set this value with the bind() method to invoke methods on objects, borrow and duplicate methods, and allocate methods to the attribute to be executed as functions. And as described earlier in the Currying Tip, you can use bind to curry.

**JavaScript’s Apply and Call Methods**

Apply and Call methods are two of JavaScript's most commonly used function methods, and for logical reason: they allow us to borrow functions and set this value to function declaration. However, the apply feature in particular helps us to implement a function with a set of parameters, so that each parameter is passed on to the function independently when the method is implemented— perfect for variadic functions; a variadic function requires a range of arguments, not a fixed number of arguments as most functions do.

**Set the this value with Apply or Call**

Like in the bind() example, we can also set this value by using the Apply or Call methods when invoking functions. In the call and apply methods, the first parameter sets 'this' value to the object on which the function is invoked.

Here's a very simple illustrative example to begin before we get into Apply and Call's more complicated uses:

```
        // global variable for demonstration
        var avgScore = "global avgScore";

        //global function
        function avg (arrayOfScores) {
            // Add all the scores and return the total
            var sumOfScores = arrayOfScores.reduce (function (prev, cur, index, array) {
                return prev + cur;
            });

            // The "this" keyword here will be bound to the global object, unless we set the "this" with Call or Apply
            this.avgScore = sumOfScores / arrayOfScores.length;
        }

        var gameController = {
            scores  :[20, 34, 55, 46, 77],
            avgScore:null
        }

        // If we execute the avg function thus, "this" inside the function is bound to the global window object:
        avg (gameController.scores);
        // Proof that the avgScore was set on the global window object
        console.log (window.avgScore); // 46.4
        console.log (gameController.avgScore); // null

        // reset the global avgScore
        avgScore = "global avgScore";

        // To set the "this" value explicitly, so that "this" is bound to the gameController,
        // We use the call () method:
        avg.call (gameController, gameController.scores);

        console.log (window.avgScore); //global avgScore
        console.log (gameController.avgScore); // 46.4
```
    
Note that 'this' value is set with the first argument to call(). In the example above, it is set to the object of the gameController. The other arguments were passed to the avg () function as parameters after the first argument.

When setting 'this' value, the apply and call methods are almost similar except that you pass the function parameters to apply() as an array while listing the parameters individually to pass them to the call() process.While, the apply() method also has another feature that the call() method does not have. More details on this to follow.

**Use Call or Apply To Set 'this' in Callback Functions**

This section is from the article: [Understand JavaScript Callback Functions and Use Them](http://70.32.104.226/~javascriptissexy/understand-javascript-callback-functions-and-use-them/).

```
    // Define an object with some properties and a method
    // We will later pass the method as a callback function to another function
    var clientData = {
    id: 094545,
    fullName: "Not Set",
    // setUserName is a method on the clientData object
    setUserName: function (firstName, lastName)  {
    // this refers to the fullName property in this object
    this.fullName = firstName + " " + lastName;
    }
    }
```
```

        function getUserInput (firstName, lastName, callback, callbackObj) {
            // The use of the Apply method below will set the "this" value to callbackObj
            callback.apply (callbackObj, [firstName, lastName]);
        }
```
    
This value is set by the Apply method to callbackObj. This allows us to execute the callback function explicitly with the setting of this value so that the parameters passed to the callback function are set to the object clientData:

```

    // The clientData object will be used by the Apply method to set the "this" value
    getUserInput ("Barack", "Obama", clientData.setUserName, clientData);
    // the fullName property on the clientData was correctly set
    console.log (clientData.fullName); // Barack Obama
```
    
Apply, Call, and Bind methods are all included when invoking a method to set 'this' value, but they do so in slightly different ways to allow direct control and flexibility to be used in our JavaScript code. The meaning of JavaScript is as critical as any other aspect of the language, and we have the three above-mentioned methods as the essential tools for efficient and properly establishing and making use of 'this'.

**Borrowing Functions with Apply and Call (A Must Know)**

Probably the most common use in JavaScript's Apply and call methods is to borrow functions. With the Apply and Call methods, we can borrow functions just like with the bind method, albeit in a more flexible way.

Consider the following examples:

**#1. Borrowing Array Methods**

Arrays come with such a number of useful methods to iterate and modify it, but unfortunately there are not as many native methods for objects. Nonetheless, because an object could be displayed in an Array-like fashion (referred as an array-like object), or most importantly since all the Array strategies are generic (except toString and toLocaleString), we can borrow Array methods and use them on array-like objects.

An array-like object is an object defined as non-negative integers by its keys. It is best to specifically add a length property to the object that has the object's length, since there is no length property on objects that it might on Arrays.

I must mention (for clarification, especially for younger JavaScript developers) that in the illustrations below, when we call Array.prototype, we enter the Array object and its prototype (where all of its inheritance methods are defined). And it's from there, the origin, that we borrow the methods of the Array. Hence the use of software such as Array.prototype.slice— the slice method specified on the prototype of the Array

Let's create an array-like object and borrow methods for the array-like object to operate on. Please note that the array-like object is a real object, it is by no means an array:

```
                // An array-like object: note the non-negative integers used as keys
                var anArrayLikeObj = {0:"Martin", 1:78, 2:67, 3:["Letta", "Marieta", "Pauline"], length:4 };
```
            
We could do this, if one of the common Array methods on our object is to be used:

```
                // Make a quick copy and save the results in a real array:
                // First parameter sets the "this" value
                var newArray = Array.prototype.slice.call (anArrayLikeObj, 0);

                console.log (newArray); // ["Martin", 78, 67, Array[3]]

                // Search for "Martin" in the array-like object
                console.log (Array.prototype.indexOf.call (anArrayLikeObj, "Martin") === -1 ? false : true); // true

                // Try using an Array method without the call () or apply ()
                console.log (anArrayLikeObj.indexOf ("Martin") === -1 ? false : true); // Error: Object has no method 'indexOf'

                // Reverse the object:
                console.log (Array.prototype.reverse.call (anArrayLikeObj));
                // {0: Array[3], 1: 67, 2: 78, 3: "Martin", length: 4}

                // Sweet. We can pop too:
                console.log (Array.prototype.pop.call (anArrayLikeObj));
                console.log (anArrayLikeObj); // {0: Array[3], 1: 67, 2: 78, length: 3}

                // What about push?
                console.log (Array.prototype.push.call (anArrayLikeObj, "Jackie"));
                console.log (anArrayLikeObj); // {0: Array[3], 1: 67, 2: 78, 3: "Jackie", length: 4}
```

If we set up object entity as an array-like object and borrow the Array methods, we get all the great benefits of an object and are still free to use Array methods on our object. All this is made possible by the call or apply method virtue.

The object of arguments which is a property of all JavaScript functions is an array-like object, and therefore one of the most popular uses of call() and apply() methods is to extract the parameters passed from the object of arguments into a function.

Here is an instance I have taken from the source of Ember.js:

```
                function transitionTo (name) {
                    // Because the arguments object is an array-like object
                    // We can use the slice () Array method on it
                    // The number "1" parameter means: return a copy of the array from index 1 to the end. Or simply: skip the first item

                    var args = Array.prototype.slice.call (arguments, 1);

                    // I added this bit so we can see the args value
                    console.log (args);

                    // I commented out this last line because it is beyond this example
                    //doTransition(this, name, this.updateURL, args);
                }

                // Because the slice method copied from index 1 to the end, the first item "contact" was not returned
                transitionTo ("contact", "Today", "20"); // ["Today", "20"]
```
            
The variable of args is a real array. It has a list of all the transitionTo function parameters passed on.

We learn from this illustration that a simple way to get all the arguments passed to a function (as an array) is:

```
                // We do not define the function with any parameters, yet we can get all the arguments passed to it
                function doSomething () {
                    var args = Array.prototype.slice.call (arguments);
                    console.log (args);
                }

                doSomething ("Water", "Salt", "Glue"); // ["Water", "Salt", "Glue"]
```
            
We will examine again how to use the apply method for variadic functions with the array-like object arguments. More about that later.

**#2. Borrowing String Methods with Apply and Call**

Like the previous case, to borrow String methods, we can also use apply() and call(). Because strings are immutable, they only work with non-manipulative arrays, so you can't use 'reverse', 'pop', and so forth.

**#3. Borrow Other Methods and Functions**

Because we borrow, let's borrow something from our own unique methods and functions, not just from Array and String:

```
							var gameController = {
									scores  :[20, 34, 55, 46, 77],
									avgScore:null,
									players :[
											{name:"Tommy", playerID:987, age:23},
											{name:"Pau", playerID:87, age:33}
									]
							}

							var appController = {
									scores  :[900, 845, 809, 950],
									avgScore:null,
									avg     :function () {

											var sumOfScores = this.scores.reduce (function (prev, cur, index, array) {
													return prev + cur;
											});

											this.avgScore = sumOfScores / this.scores.length;
									}
							}

							// Note that we are using the apply () method, so the 2nd argument has to be an array
							appController.avg.apply (gameController);
							console.log (gameController.avgScore); // 46.4

							// appController.avgScore is still null; it was not updated, only gameController.avgScore was updated
							console.log (appController.avgScore); // null
```

Of course, borrowing our own custom methods and functions is just as easy and even recommended. The property of the gameController borrows the avg() method of the appController object. The 'this' value defined in the avg() method is set to the gameController object, the first parameter.

You may wonder what will happen if changes are made to the original definition of the system we borrow. Will the borrowed (copied) method also change, or is the copied method a complete copy not referring back to the original method? Let's take a quick, illustrative example to answer these questions:

```
        appController.maxNum = function () {
            this.avgScore = Math.max.apply (null, this.scores);
        }

        appController.maxNum.apply (gameController, gameController.scores);
        console.log (gameController.avgScore); // 77
```
    
When we modify the original system as intended, the modifications will be mirrored in that method's borrowed instances. With good reason, this is expected: we never made a complete copy of the process, we only borrowed it (referred to its current implementation directly).

**Use Apply () to Execute Variable-Arity Functions**

To finalize our conversation on the versatility and usefulness of the Apply, Call, and Bind methods, we will discuss the Apply method's nice, small feature: execute functions with an array of arguments.

We may pass an array of arguments to a function and the function will execute the objects in the list as if we were calling the feature like this by using the apply() method:

```
    createAccount (arrayOfItems[0], arrayOfItems[1], arrayOfItems[2], arrayOfItems[3]);
```

In specific, this method is used to construct variable-arity, also known as variadic functions.

These are functions that accept as many arguments as possible rather than a fixed number of arguments. A function's arity determines the number of arguments to be defined by the function to accept.

The method Math.max() is an instance of a popular JavaScript variable-arity function:

```
    // We can pass any number of arguments to the Math.max () method
    console.log (Math.max (23, 11, 34, 56)); // 56
```

What if we have to pass to Math.max, an array of numbers? We can't do:

```
    var allNumbers = [23, 11, 34, 56];
    // We cannot pass an array of numbers to the the Math.max method like this
    console.log (Math.max (allNumbers)); // NaN
```

This is where the method of apply () helps us to perform variable functions. Instead of the above, we need to use apply() to pass the array of numbers:

```
    var allNumbers = [23, 11, 34, 56];
    // Using the apply () method, we can pass the array of numbers:
    console.log (Math.max.apply (null, allNumbers)); // 56
```

The fist argument to apply() sets the 'this' value, as we have learned earlier, but 'this' is not used in the Math.max() rule, so we pass null.

Here is an illustration of our own variadic feature to demonstrate in this resource the principle of using the request() method:

```
    var students = ["Peter Alexander", "Michael Woodruff", "Judy Archer", "Malcolm Khan"];

    // No specific parameters defined, because ANY number of parameters are accepted
    function welcomeStudents () {
        var args = Array.prototype.slice.call (arguments);

        var lastItem = args.pop ();
        console.log ("Welcome " + args.join (", ") + ", and " + lastItem + ".");
    }

    welcomeStudents.apply (null, students);
    // Welcome Peter Alexander, Michael Woodruff, Judy Archer, and Malcolm Khan.
```

**Final Words**

The Call, Apply and Bind methods are indeed powerhouses and must be part in your JavaScript repertoire to set this value into functions, construct and execute variadic functions, and borrow methods and functions. You are likely to experience and use these features as a JavaScript programmer over and over again. So be sure that you know them well.