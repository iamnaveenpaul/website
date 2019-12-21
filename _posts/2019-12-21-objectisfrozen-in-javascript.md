---
title: Object.isFrozen() In JavaScript
image: "/assets/default-social-image.png"
categories: JavaScript-objects
---

**Object and Object Constructor in JavaScript?**

The standard way to use the Object Constructor function is to build an object "type" that can be used multiple times without needing to redefine the object each time to meet the needs of each particular instance.

An object constructor is simply a standard JavaScript feature, which is as versatile in general as specifying parameters, calling certain functions, etc. Object constructors construct the object's blueprints, not the object itself.

Let's use as an illustration an actual-world object called "dog". A dog's property may be its color or name, and "bark" may be a method. An interesting thing to note is that each dog is going to have a different name and even the type of bark. We use an object constructor to build an object type that will satisfy this need for versatility. The dog will therefore be an object constructor and its properties (color, name) and methods (bark noise) will be stated in it using the keyword "this". The new keyword will then be used to instantiate objects defined using an object constructor.

It helps to define several dog instances (an object constructor) effectively, each with its own name- which is the flexibility object constructor that carries custom objects.

**Object.isFrozen() Method**

Among the functions of the object constructor is an Object.isFrozen() that is used to evaluate whether or not an object is frozen.

If all of the following requirements hold true, an object will be frozen:

If it can't be extended.
If all of the properties can't be configured.
If all the properties of its data are unwritable.

Object.isFrozen() takes the object as a verified (that has to be checked) argument and returns a boolean describing whether or not the object is frozen.

**Applications:**

Object.isfrozen() is used to test whether or not an object has been frozen.

**Syntax:**

`Object.isFrozen(obj)`

**Parameters Used:**

obj: This is the object to be tested.

**Return Value:**

Object.isFrozen() returns a boolean that indicates whether or not the object is frozen.

Examples:

```
Input : const object = {
        property: 'hi myWorld'
        };
        console.log(Object.isFrozen(object));
Output : false

Input : const object = {
        property: 'hi myWorld'
        };
        Object.freeze(object);
        console.log(Object.isFrozen(object));
Output : true
```

**Code 1:**

```
<script> 
  
<!-- creating an object constructor and assigning values to it -->
const object = { 
property: 'hi myWorld' 
}; 
  
<!-- checking whether the object is frozen or not -->
console.log(Object.isFrozen(object)); 
  
</script> 
```

OUTPUT :

`false`

**Code 2:**

```
<script> 
  
<!-- creating an object constructor and assigning values to it -->
const object = { 
property: 'hi myWorld' 
}; 
  
<!-- Using freeze() method to freeze the object -->
Object.freeze(object); 
  
<!-- checking whether the object is frozen or not -->
console.log(Object.isFrozen(object)); 
  
</script> 
```

OUTPUT :

`true`

**Exceptions :**

It will trigger a TypeError if the passed argument is not an object.