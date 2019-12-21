---
image: "/assets/default-social-image.png"
title: Object.keys() In JavaScript
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

**Object.keys() Method**

The method Object.keys() is used to return an array whose elements are strings referring to the properties contained directly on an object. The ordering of the properties is the same as being added to the property by the object manually in a loop.

Object.keys() takes the object as an argument for returning the enumerable properties and returns a string array containing all the enumerable properties of the given object.

**Applications:**

Object.keys() is used to retrieve a simple array's enumerable properties.
Object.keys() is used to retrieve an array of object's enumerable properties.
Object.keys() is used with random key ordering to return enumerable properties of an array like object.

**Syntax:**

`Object.keys(obj)`

Parameters Used:

obj : It is the object to retrieve the enumerable properties.

Return Value:

Object.keys() returns a string array that describes all of the provided object's enumerable properties.

Examples:

```
Input : var check = ['x', 'y', 'z'];
        console.log(Object.keys(check));
Output : ['0', '1', '2']
```

Explanation: In this case, a "check" array has three property values [‘x’, ‘y’, ‘z’] and the object.keys() method returns this array's enumerable properties. The property ordering is the same as manually provided by the object.

```
Input : var object = { 0: 'x', 1: 'y', 2: 'z' };
        console.log(Object.keys(object));
Output : ['0', '1', '2']
```

Explanation: In this case, an array-like "check" object has three property values { 0: ‘x’, 1: ‘y’, 2: ‘z’ } and the object.keys() method returns this array's enumerable properties. The property ordering is the same as manually provided by the object.

```
Input : var object = { 70: 'x', 21: 'y', 35: 'z' };
        console.log(Object.keys(object));
Output : ['21', '35', '70']
```

Explanation: In this case, an array-like "check" object has three property values { 70: ‘x’, 21: ‘y’, 35: ‘z’ } in randomized order and the object.keys() method returns the enumerable properties of such an array in the increasing order of the indices value.

**Code 1:**

```
<script> 
  
// Returning enumerable properties 
// of a simple array  
var check = ['x', 'y', 'z']; 
console.log(Object.keys(check)); 
  
</script> 
```

OUTPUT :

`['0', '1', '2']`

**Code 2:**

```
<script> 
  
// Returning enumerable properties 
// of an array like object. 
var object = { 0: 'x', 1: 'y', 2: 'z' }; 
console.log(Object.keys(object)); 
  
</script> 
```

OUTPUT :

`['0', '1', '2']`

**Code 3:**

```
<script> 
  
// Returning enumerable properties of an array 
// like object with random key ordering. 
var object = { 70: 'x', 21: 'y', 35: 'z' }; 
console.log(Object.keys(object)); 
  
</script> 
```

OUTPUT :

`['21', '35', '70']`

**Exceptions :**

* It will trigger a TypeError if the passed argument is not an object.
* If an object is not passed to the method as an argument, it will persuade it and handles it as an object.

Reference: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys)