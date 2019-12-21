---
title: Object.entries() In JavaScript
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

**Object.entries() Method**

The method Object.entries() is used to return an array comprising of the object's enumerable property [key, value] pairs passed as the parameter. The property ordering is the same as that provided by manually looping over the object's property values.

**Difference between Object.entries() and Object.values() method**

The object.entries() method in JavaScript yields an array of enumerable item property [key, value] pairs provided as the parameter while the object.values() method in JavaScript returns an array where members are the enumerable property values located on the object. For further recognizing the difference between these two functions, take the example below.

```
Input: var object = { 0: '23', 1: 'qwerty', 2: 'true' };
       console.log(Object.values(object));
       console.log(Object.entries(object));

Output: Array ["23", "qwerty", "true"]
        Array [["0", "23"],  ["1", "qwerty"],["2", "true"]]
```

Explanation: The above illustration generates an object of three [key, value] pairs and the object.entries() method returns the object's [key, value] pairs and object.values() returns the object's values.

**Applications:**

Object.entries() for an object is used for listing properties related to it.
Object.entries() for an object is used for listing all the [key,value] pairs.

**Syntax:**

`Object.entries(obj)`

**Parameters Used:**

obj : It is an object whose enumerable property [key, value] is to return pairs.

**Return Value:**

Object.entries() returns an array comprising of the passed object pairs of enumerable property [key, value].

Examples:

```
Input : const obj = { 0: 'adam', 1: 'billy', 2: 'chris' };
        console.log(Object.entries(obj)[1]);

Output : Array ["1", "billy"]
```

Explanation: An object "obj" with three property [key, value] pairs has been generated in this case, and the Object.entries() function is used to return the object's first property [key, value] pair.

```
Input : const obj = { 10: 'adam', 200: 'billy', 35: 'chris' };
        console.log(Object.entries(obj)); 

Output : Array [ ["10", "adam"], ["35", "chris"], ["200", "billy"]]
```

Explanation: An object "obj" with three property [key, value] pairs has been generated in this case, and the Object.entries() function is used to return all the object's property [key, value] pair.

**Code 1:**

```
<script> 
// creating an object constructor 
// and assigning values to it  
const obj = { 0: 'adam', 1: 'billy', 2: 'chris' }; 
  
// Displaying the enumerable property [key, value]  
// pairs of the object using object.entries() method  
console.log(Object.entries(obj)[1]); 
</script> 
```

OUTPUT :

`Array ["1", "billy"]`

**Code 2:**

```
<script> 
// creating an object constructor and  
// assigning values to it  
const obj = { 10: 'adam', 200: 'billy', 35: 'chris' }; 
  
// Displaying the enumerable property [key, value]  
// pairs of the object using object.entries() method  
console.log(Object.entries(obj));  
</script> 
```

OUTPUT :

`Array [["10", "adam"], ["35", "chris"],["200", "billy"]]`

Exceptions :

This triggers a TypeError when the passed argument is not an object.
It triggers a RangeError if the key is passed in the argument but not within the [key, value] pair's range.

Reference :[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries)