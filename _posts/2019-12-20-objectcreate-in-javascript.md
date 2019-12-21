---
title: Object.create() In JavaScript
image: "/assets/default-social-image.png"
categories: JavaScript-objects
---

**Object and Object Constructors in JavaScript?**

We already understand the importance of classes and objects in the living world of object-oriented programming, but unlike most programming languages, JavaScript has no conventional classes like in many languages. But JavaScript has objects and constructors that work often in the the same way to tackle the same type of operations.

The Constructors are general features in JavaScript that are used with the "new" keyword. Constructors are built-in constructors (array and object) and unique constructors (defining properties and methods for specific objects) of two kinds in JavaScript.

Constructors can be helpful if we need a way to create a "type" of the object that can be used repeatedly without needing to redefine the object at any point, and it can be done with the Object Constructor function.

To order to differentiate these from regular functions, it is a norm to capitalize the name for constructors.

Consider the following code for illustration:

```
function Automobile(color) {
  this.color=color;
}

var vehicle1 = new Automobile ("red");
```

The "Automobile()" feature is an object constructor as well as its properties and methods, i.e. "color," are declared in it by prefixing that with the keyword "this". Then objects identified by an object constructor are rendered instants using the "new" keyword.

By calling new Automobile(), JavaScript will do two tasks:

* It generates and assigns a new object(instance) Automobile() to a variable.
* It sets to Automobile for the constructor property i.e. the object's "color".

**Object.create() Method**

The method object.create() is used to establish a new object, with the object and property of the given prototype.

**Applications:**

Object.create() is used for inheritance implementation.

**Syntax:**

`Object.create(prototype[, propertiesObject])`

**Parameters Used:**

* **prototype:** it is a prototype object to create a new object
* **propertiesObject:** This parameter is optional. This defines the properties that can be applied to the newly created object.

**Return Value:**

Object.create() returns the object and property of a new object with a specified prototype.

Examples:

```
Input : function fruits() {
        this.name = 'fruit 1';
        }

        function apple() {
        fruits.call(this);
        }

        apple.prototype = Object.create(fruits.prototype);
        const app = new apple();
        console.log(app.name);

Output : "fruit 1"
```

Explanation: There are two "fruits" and "apple" functions in this case. A new apple instance is generated that is named "app" and has been defined with the "fruits" prototype and properties, i.e. this.name = ‘fruit 1’.

```
Input : function fruits() {
        this.name = 'fruit 1';
        this.season = 'summer';
        }

        function apple() {
        fruits.call(this);
        }

        apple.prototype = Object.create(fruits.prototype);
        const app = new apple();
        console.log(app.name);
        console.log(app.season);

Output : "fruit 1"
         "summer"
```

Explanation: There are two "fruits" and "apple" functions in this case. A new apple instance is generated that is labeled "app" and has been specified with the prototype and property of “fruits” i.e. this.name = ‘fruit 1’ and this .season = ‘summer’.

**Code 1:**

```
<script> 
// creating a function which will be the  
//prototype for the object to be created later 
function fruits() { 
    this.name = 'fruit 1'; 
} 
  
// creating a function to whose object will  
// inherit properties from the prototype  
// using object.create() method 
function
apple() { 
    fruits.call(this); 
} 
  
// creating an object of the apple function which 
// will have properties of the prototype  
// object i.e. fruits 
apple.prototype = Object.create(fruits.prototype); 
const app = new apple(); 
  
// Displaying the created object 
console.log(app.name); 
< /script> 
```

OUTPUT :

`"fruit 1"`

**Code 2:**

```
<script> 
    // creating a function which will be the 
    // prototype for the object to be created later 
    function fruits() { 
        this.name = 'fruit 1'; 
        this.season = 'summer'; 
    } 
  
// creating a function to whose object  
// will inherit properties from the    
// prototype using object.create() method 
function apple() { 
    fruits.call(this); 
} 
  
// creating an object of the apple function which 
// will have properties of the prototype  
// object i.e. fruits 
apple.prototype 
    = Object.create(fruits.prototype); 
const app = new apple(); 
  
// Displaying the created object 
console.log(app.name); 
console.log(app.season); 
< /script> 
```

OUTPUT :

```
"fruit 1"
"summer"
```

**Exceptions :**

* The function Object.create() throws an exception to TypeError if the parameter propertiesObject is not null.
* The function Object.create() throws an exception to TypeError if the parameter propertiesObject is a non-primitive object.

Reference: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create)