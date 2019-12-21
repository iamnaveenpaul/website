---
image: "/assets/default-social-image.png"
title: Object.values() In JavaScript
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

**Object.values() Method**

Object.values() method is used for returning an array where elements are the values of the object's enumerable properties. The property ordering is the same as the one provided manually by the object is a loop applied to the properties.

Object.values() takes the object as an argument for returning the enumerable property values and returns an array of all of the provided object's enumerable property values.

**Applications:**

Object.values() is used to retrieve a simple array's enumerable property values.
Object.values() is used to retrieve an array of object's enumerable property values.
Object.values() is used to return an array-like object with randomized key ordering enumerable property values.

**Syntax:**

`Object.values(obj)`

**Parameters Used:**

obj: It is an object to which its enumerable properties are to be retrieved.

**Return Value:**

Object.values() returns an array that includes all of the provided object's enumerable property values.

Examples:

```
Input : var check = ['x', 'y', 'z'];
        console.log(Object.values(check));
Output : Array ["x", "y", "z"]
```

Explanation: A "check" array in this case has three property values ['x',' y','z'] and the object.values() process returns this array's enumerable property values. The property ordering is the same as manually provided by the object.

```
Input : var object = { 0: '23', 1: 'MyWorld', 2: 'true' };
        console.log(Object.values(object));
Output : Array ["23", "MyWorld", "true"]
```

Explanation: In this case, an array-like "check" object has three property values{ 0: ’23’, 1: ‘MyWorld’, 2: ‘true’ } and the object.values() method returns this array's enumerable property values. The property ordering is the same as manually provided by the object.

```
Input : var object = { 70: 'x', 21: 'y', 35: 'z' };
        console.log(Object.values(object));
Output : Array ["y", "z", "x"]
```

Explanation: In this case, an array-like "check" object has three property values { 70:‘x’,21:‘y’,35:‘z’ } in randomized order and the object.values() method returns the enumerable property values of this array in the increasing order of the indices value.

**Code 1:**

```
<script> 
  
// Returning enumerable property values of a simple array  
var check = ['x', 'y', 'z']; 
console.log(Object.values(check)); 
  
</script> 
```

OUTPUT :

`Array ["x", "y", "z"]`

**Code 2:**

```
<script> 
  
// Returning enumerable property values 
// of an array like object.  
var object = { 0: '23', 1: 'MyWorld', 2: 'true' }; 
console.log(Object.values(object)); 
  
</script> 
```

OUTPUT :

`Array ["23", "MyWorld", "true"]`

**Code 3:**

```
<script> 
  
// Returning enumerable property values 
// of an array like object.  
var object = { 70: 'x', 21: 'y', 35: 'z' }; 
console.log(Object.values(object)); 
  
</script> 
```

OUTPUT :

`Array ["y", "z", "x"]`

**Exceptions :**

It triggers a TypeError if the passed argument is not an object.
It will persuade it and handles it as an object, if a passed object is not as an argument.

Reference :[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/values
](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/values)