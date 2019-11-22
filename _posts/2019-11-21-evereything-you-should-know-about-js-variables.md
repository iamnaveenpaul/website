---
title: Evereything you should know about JS variables
image: "/assets/default-social-image.png"
cateogories: Naveen_Paul
---

**Front Matter**

I like to make any problem work more than I want to teach the theory and concepts, so while working on that problem, the individual can learn as well as solve the problem. Check out the [deliberate practice](https://jamesclear.com/deliberate-practice-theory). But some little bit of theory is important initially as well, so let’s wrap some theory and definition of variables:

**What is a variable?**

A JavaScript variable is a predetermined name that can hold some data value and it can be changed anytime without changing the variable name. JavaScript uses reserved keyword var to declare a variable. A variable must have a unique name.

Think of this way, if you want to call your friend Paul, you don’t actually dial his number (not always, but more frequently), but you type Paul in your mobile contacts and dial it, the name Paul is a variable and the value it holds is the telephone number of him. If in case, Paul decided to change his number and no longer use the older one, you will update the number under the same name, Paul.

**Types**

In JS, we need not worry about assigning the type of data stored in a variable, because it is dynamically typed language. But it is essential to know the type of data as it makes us easier to debug. “Variables don’t have types, but the values in them do. These types define intrinsic behavior of the values”. - Kyle Simpson

There are seven built-in types in JS: null, undefined, boolean, number, string, object as well as symbol. Note that all these can be called “primitives” with the exception here being ‘object’. We will be covering about those all mentioned along with some others that you will soon see.

In JavaScript, a primitive (primitive value, primitive data type) is data that is not an object and has no methods. — MDN

**null**

Represents the intentional absence of any object value — MDN

Null is like something when we typically say ‘it has no value’.

In JS, if a variable has no value, it is ‘null’. It is used when something returning from a function doesn’t yield any results.

```
function return3 (value) {
	if(value === 3) { return value }
	else { return null }
}
return3(2) // null
```

If we don’t specify to return the value as ‘null’, it would return ‘undefined’

**undefined**

Defines a variable which has no value. The JS knows that the variable exists, but it has no value. The null is different in the sense that it is a defined value, whereas undefined is not. check [this out](https://codeburst.io/javascript-null-vs-undefined-20f955215a2) for further details.

```
let b;
console.log(b) // undefined
```

**boolean**

True or false

`let falseVariable = false`

**number**

The number in JS doesn’t need to define the type of number unlike other programming languages out there. If a particular number assigned to a variable is float or integer etc, we don’t need to specify, we just declare it whatever’s the type of number. Because JS uses the double-precision 64-bit floating point format (IEEE 754). It is generally used for a value with which you expect to do something computational like math.

```
let four = 4;
let fiveish = 5.1;
console.log(four + fiveish) // 9.1
```

**string**

A sequence of characters, like this sentence. It is used for storing information, generally to display it to the user.

`let someString = "I'm a string!"`

**object**

Initializing something with its applied property names along with their values associated with that object that are enclosed in curly braces ‘{}’. Objects can be used for any purposes where its property and their respective values can be used.

```
let car = {
	color: "red",
	miles: 400,
}
console.log(car.color) //red
```

**A note about the Array**

An Array is same as an object.

`typeof [1,2,3] === "object";`

It’s most appropriate to think of them (arrays) also as a “subtype” of object (see Chapter 3), in this case with the additional characteristics of being numerically indexed (as opposed to just being string-keyed like plain objects) and maintaining an automatically updated .length property. - Kyle Simpson

**symbol — added in ES6!**

Are unique Identifiers and no two symbols will ever be the same. In large data structures, it is useful as object keys. It avoids naming collisions. You can find an overview of symbols [here](https://www.keithcirkel.co.uk/metaprogramming-in-es6-symbols/).

**undeclared**

A variable you want to access isn’t available in the scope. The error shown is ‘ReferenceError: x is not defined’.

**Declaring variables**

var, let and const are the three different ways to declare a variable in Javascript.

**var vs const vs let**

Note: const and let are now standardized into the JS Spec.

**var**

was the usual way of defining a variable, but JS now got two new siblings to it.

* is changeable
* is used within an entire function but is scoped globally or locally regardless of block
scope.
 
**let**

* is changeable.
* is scoped to the block.
* let variables are not initialized until their definition is evaluated. — MDN

**const**

* is unchangeable after instantiation.
* is scoped to the block.
 
**when to use let vs const**

1. I don’t trust anyone

This signifies to use const first for every variable, If a situation arises where it’s needed to change already declared variable, change it to let.

1. I trust myself

This signifies to use let for everything, If a situation arises where it’s needed to make sure that the already declared variable can’t be changed, change it to const.

Point here is to not use var anymore, there might be some cases of incompatibility but it is 94% globally compatible with browsers.

**Coercion**

Let’s look at this:

```
let threeString = "3";
let threeNum = 3;
```

Now the first one is string and the other, a number. But:

`let sum = threeString + threeNum`

..doesn’t returns any error. The JS thinks that adding the two is the best idea, so it will do the math, that’s coercion. But for some cases, you might wanna keep the string stick to what it always is. Check out
[this article](https://www.freecodecamp.org/news/js-type-coercion-explained-27ba3d9a2839/) for more.

**Scope**

Scope in Javascript refers to the current context of execution. - MDN

Its meaning depends upon whether we are talking about the old var or the new const/let. There are two scopes: global and local.

**Global**

Global scope exists once in script and is visible to all functions.

```
var globalVar = "I'm global!"
let globalLet = "I'm also global!"
const globalConst = "I'm global too!"
function someFunction() {
	console.log(globalVar); // I'm global!
	console.log(globalLet); // I'm also global!
	console.log(globalConst); // I'm global too!
}
```

**Local**

Local scope depends on weather we use var or let/const.

**var (functional scope)**

If called within a function, then it is available anywhere in that function.

```
function someFunction() {
	if(true) {
	var localScope = "Yo! Call me!"
	console.log(localScope) // "Yo! Call me!"
	}
	console.log(localScope) // "Yo! Call me!"
}
```

As long as var is within a function, it’s available to be called.

**let and const (block scope)**

The new let and const are block scoped which means they are only accessible within the block.

Examples are: if/switch statements, for/while loops. Or, read [this article](https://dev.to/sandy8111112004/javascript-introduction-to-scope-function-scope-block-scope-d11):

Generally speaking, it’s a block whenever you see curly brackets ‘{}’.

Using the same example:

```
function someFunction() {
	if(true) {
	let localScope = "Yo! Call me!"
	console.log(localScope) // "Yo! Call me!"
	}
	console.log(localScope) // Uncaught ReferenceError: localScope is not defined
}
```

**Hoisting**

Because variable declarations (and declarations in general) are processed before any code is executed, declaring a variable anywhere in the code is equivalent to declaring it at the top. This also means that a variable can appear to be used before it’s declared. This behavior is called “hoisting”, as it appears that the variable declaration is moved to the top of the function or global code. - MDN

Or simply:

all declarations, both variables and functions, are processed first, before any part of your code is executed. — Kyle Simpson

When a var statement is hoisted to the top of the context, it is assigned an undefined value.

```
hoistedVar = "I've been hoisted!";
var hoistedVar;
console.log(hoistedVar) // I've been hoisted!
```

Using Tyler McGinnis [Javascript Visualizer](https://tylermcginnis.com/javascript-visualizer/)! you can see that as both variables are given an undefined value first. The compiler then assigns “I’ve been Hoisted” to any value it parses during the execution of the code.

**Let and Const Caveat**

let and const are hoisted in a different way than var. Var, when hoisted is initialized as undefined.

let/const remain uninitialized until the compiler evaluates the statement.

Using the same example:

```
hoistedVar = "I've been hoisted!";
	let hoistedVar;
	console.log(hoistedVar) // Uncaught ReferenceError:
	//Cannot access 'hoistedVar' before initialization
```

**Style Choices**

**Casing**

There’s a bunch of different options when you declare a variable. You can pick any style

But should probably prefer keeping it consistent.

**Camel Casing (Dromedary)**

`let camelCasedVar = "I'm camel cased"`

Used for common variables.

**Camel Casing (Pascal)**

`let PascalCasedVar = "I'm Pascal cased"`

I use this style for Classes or Components.

**Snake Case**

`let snake_case_var = "Sssssnake case"`

Common in PhP, but haven't seen it much in JS. I don’t really prefer it anyways.

**Kebab-case**

`<input id="kebab-case-input">`

According to StackOverflow, [this](https://stackoverflow.com/questions/11273282/whats-the-name-for-hyphen-separated-case) is a kebab-case convention. While it can’t be used by JS, it is common in HTML. I try to avoid it as I will explain below:

**What I use**

I prefer camel casing for everything (CSS, JS, HTML). One reason is that it seems to be standard, and also because it makes a little cleaner or consistent writing out the selectors.

Consider the example below:

```
<form action="/" id="form">
	<input type="text" id="kebab-case">
	<input type="text" id="camelCase">
	<button type="submit">Submit</button>
</form>
// When we submit form data, we can access it via the event parameter.
let form = document.getElementById("form")
form.addEventListener("submit", function(event) {
	event.preventDefault();
		// if we use hyphens, we have to use brackets/quotes to get the value
	const kebabInput = event.target["kebab-case"].value
		// if we use anything without special characters, we can use dot notation
	const camelInput = e.target.camelCase.value
}, false)
```

I think this would be cleaner code, but it’s up to you.

**What do I call this variable?**

Now that you know where you could access it and know if able to change it or not, the variable name is up to you. Overtime, I’ve came up with suggestions that could help save time:

**Naming it what it is**

It sounds simple, but to think what exact information is going to be assigned to this variable and how will the variable help me. Try to avoid single characters like p, i, e and use whole meaningful names, and a good text editor is always there for you to autocomplete.

**Reserved Words**

Note that there are some reserved words in JS, like var, boolean, abstract. Check them all [here](https://www.w3schools.com/js/js_reserved.asp).

**Final Thoughts**

Congratulations for making it till the end! We talked about all variable types, declaring them, coercion, scope, hoisting and style choices.

Let me know if I missed anything here.