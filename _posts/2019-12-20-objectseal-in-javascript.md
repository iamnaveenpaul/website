---
image: "/assets/default-social-image.png"
title: Object.seal() In JavaScript
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

**Object.seal() Method**

Among the methods used to seal an object is an Object.seal() function that is used to seal an object. Sealing an object doesn't quite require the addition of new property and identifies as non-configurable for those existing properties. While current property values can be modified as long as they can be writable

The sealed object is passed as an argument and the method returns the sealed object.

**Difference between Object.freeze() Method and Object.seal() Method**

If an object becomes frozen using the Object.freeze() method, the properties are immutable and no changes can be made to it, whereas if an object becomes sealed using the Object.seal() method, the changes can be made to the object's existing properties.

**Applications:**

For seal objects and arrays, Object.seal() is used.
To make an object immutable, Object.seal() is used.

**Syntax:**

`Object.seal(obj)`

**Parameters Used:**

**obj:** It's the object that has to be sealed.

**Return Value:**

Object.sealed() returns the passed object to the function.

Examples:


```
Input : const obj1 = { property1: 'initial_data'};
        const obj2 = Object.seal(obj1);
        obj2.property1 = 'new_data';
        console.log(obj2.property1);

Output : "new_data"
```

Explanation: In this case, properties of the object "obj1" have been applied to the object "obj2" and are sealed so that new values can not be inserted. Property 1 value for obj2 has been modified as sealing an object makes it possible to change existing properties.

```
Input : var obj = { prop: function() {}, name: 'adam' };
        console.log(obj);
        obj.name = 'billy';
        delete obj.prop;
        console.log(obj);
        var o = Object.seal(obj);
        delete obj.prop;
        console.log(obj);
        obj.name = 'chris';
        console.log(obj);

Output : Object { prop: function () {}, name: "adam" }
         Object { name: "billy" }
         Object { name: "billy" }
         Object { name: "chris" }
```

Explanation: The "obj" object was allocated "prop: function" in this case, which was later removed since the "obj" object was not sealed. After that, the sealed values of "obj" were allocated to a new object "o" that stopped it from being removed but permitted changes to existing properties.

**Code 1:**

```
<script> 
// creating an object constructor and assigning values to it  
const obj1 = { property1: 'initial_data'}; 
  
// creating a second object which will seal the properties of the first object 
const obj2 = Object.seal(obj1); 
  
// Updating the properties of the frozen object 
obj2.property1 = 'new_data'; 
  
// Displaying the properties of the  frozen object  
console.log(obj2.property1); 
</script> 
```

OUTPUT :

`"new_data"`

**Code 2:**

```
<script> 
// creating an object constructor and assigning values to it  
var obj = { prop: function() {}, name: 'adam' }; 
  
// Displaying the properties of the object created  
console.log(obj); 
  
// Updating the properties of the object  
obj.name = 'billy'; 
delete obj.prop; 
  
// Displaying the updated properties of the object  
console.log(obj); 
  
// Sealing the object using object.seal() method 
var o = Object.seal(obj); 
  
// Updating the properties of the object  
delete obj.prop; 
  
// Displaying the updated properties of the object  
console.log(obj); 
  
// Updating the properties of the sealed object  
obj.name = 'chris'; 
  
// Displaying the properties of the  frozen object  
console.log(obj); 
  
</script> 
```

OUTPUT :

```
Object { prop: function () {}, name: "adam" }
Object { name: "billy" }
Object { name: "billy" }
Object { name: "chris" }
```

**Exceptions :**

* It will trigger a TypeError if the passed argument is not an object.
* Deleting or adding properties to a sealed object would fail or raise a TypeError.
* A TypeError will be thrown when a data property is transformed to an accessor or vice versa.

**Reference :**
[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/seal](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/seal)