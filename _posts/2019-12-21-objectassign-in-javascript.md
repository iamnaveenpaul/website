---
image: "/assets/default-social-image.png"
title: Object.assign() in JavaScript
categories: JavaScript-objects
---

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

**Object.assign() Method**

There is a function Object.assign() among the methods of the object constructor that is used to transfer the values and properties from one or more origin objects to a target object. As it uses both [[Get]] on the source and [[Set]] on the goal, it invokes getters and setters. This returns the target object copied from the target object containing properties and values. Object.assign() doesn't throw source values as null or undefined.0

**Applications:**

Object.assign() will be used to clone an object.
Object.assign() is used to combine the same object having the same properties.

**Syntax:**

`Object.assign(target, ...sources)`

**Parameters Used:**

target: The target object to copy values and properties from.
sources: This is the source object to copy values and property.

**Return Value:**

Object.assign() returns the object of the target.

Examples:

```
Input : var obj1 = { a: 10 };
        var new_obj = Object.assign({}, obj1);
        console.log(new_obj);
Output : Object { a: 10 }
```

Explanation: The properties of the object "obj1" i.e. { a: 10 } are copied to the object "new_obj" in this case.

```
Input : var obj1 = { a: 10 };
        var obj2 = { b: 20 };
        var obj3 = { c: 30 };
        var new_obj = Object.assign(o1, o2, o3);
        console.log(new_obj);
Output : Object { a: 10, b: 20, c: 30 }
```

Explanation: The properties of three source objects "obj1, obj2, obj3" are copied to the object "new_obj" in this case, as they are targets.

```
Input : var obj1 = { a: 10, b: 10, c: 10 };
        var obj2 = { b: 20, c: 20 };
        var obj3 = { c: 30 };
        var new_obj = Object.assign({}, obj1, obj2, obj3);
        console.log(new_obj); 
Output : Object { a: 10, b: 20, c: 30 }
```

Explanation: In this case, the properties of three source objects "obj1, obj2, obj3" are copied to the target object "new obj" and overwritten values are provided to the target object.

**Code 1:**

```
<script> 
<!-- creating an object constructor and assigning values to it -->
const obj1 = { a: 1 }; 
  
<!--creating a target object and copying values and properties to it using object.assign() method -->
const new_obj = Object.assign({}, obj1); 
  
<!-- Displaying the target object -->
console.log(new_obj); 
</script> 
```

OUTPUT :

`Object { a: 1 }`

**Code 2:**

```
<script> 
<!-- creating 3 object constructors and assigning values to it -->
var obj1 = { a: 10 }; 
var obj2 = { b: 20 }; 
var obj3 = { c: 30 }; 
  
<!--creating a target object and copying values and properties to it using object.assign() method -->
var new_obj = Object.assign({}, obj1, obj2, obj3); 
  
<!-- Displaying the target object -->
console.log(new_obj); 
</script> 
```

OUTPUT :

`Object { a: 10, b: 20, c: 30 }`

**Code 3:**

```
<script> 
  
<!-- creating 3 object constructors and assigning values to it -->
var obj1 = { a: 10, b: 10, c: 10 }; 
var obj2 = { b: 20, c: 20 }; 
var obj3 = { c: 30 }; 
  
<!--creating a target object and copying values and properties to it using object.assign() method -->
var new_obj = Object.assign({}, obj1, obj2, obj3); 
  
<!-- Displaying the target object -->
console.log(new_obj); 
</script> 
```

OUTPUT :

`Object { a: 10, b: 20, c: 30 }`

Explanation: In the above application, certain objects that later have the same properties in the same order of parameters overwritten the properties.

**Errors and Exceptions**

* If the property is unwritable, a TypeError will be created.
* Only when the properties are inserted before the error is created could the target object be modified.
* Object.assign() does not throw source values that are null or undefined.