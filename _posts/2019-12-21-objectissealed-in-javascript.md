---
title: Object.isSealed() In JavaScript
image: "/assets/default-social-image.png"
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

**Object.isSealed() Method**

The function Object.isSealed() is used to evaluate whether or not an object has been sealed.

An object is sealed if all the criteria mentioned below are true:

* If it can't be extended.
* If all of the properties can't be configured.
* If it can not be removed (but not usually unwritable).

Object.isSealed() takes the object as a verified (has to be checked) argument and returns a boolean indicating whether or not the object is sealed.

**Applications:**

Object.isSealed() is used to test whether or not an object has been sealed.

**Syntax:**

`Object.isSealed(obj)`

Parameters Used:

obj : It is the object to be checked.

Return Value:

Object.isSealed() returns a boolean that indicates whether or not the object is sealed.

Examples:

```
Input : const object = {
        property: 'hi world'
        };
        console.log(Object.isSealed(object));
Output : false
```

Explanation: In the case above, the item was not sealed using the Object.seal() process, so when verified using the Object.isSealed() method, it returns false value.

```
Input : const object = {
        property: 'hi world'
        };
        Object.seal(object);
        console.log(Object.isSealed(object));
Output : true
```

Explanation: The object was sealed using the Object.seal() method in the above case, thus, when tested using the Object.isSealed() method, it returns true as output.

**Code 1:**

```
<script> 
// creating an object constructor 
// and assigning values to it  
const object = { 
property: 'hi world'
}; 
  
// checking whether the object 
// is sealed or not  
console.log(Object.isSealed(object)); 
  
</script> 
```

OUTPUT :

`false`

**Code 2:**

```
<script> 
  
// creating an object constructor 
// and assigning values to it  
const object = { 
property: 'hi world'
}; 
  
// Using seal() method to seal the object 
Object.seal(object); 
  
// checking whether the 
// object is frozen or not  
console.log(Object.isSealed(object)); 
  
</script> 
```

OUTPUT :

`true`

**Exceptions :**

It will trigger a TypeError if the passed argument is not an object.
If an object is not passed to the method as an argument, it will be regarded as a sealed object and returns true output.