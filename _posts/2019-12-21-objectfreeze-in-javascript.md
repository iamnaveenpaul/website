---
image: "/assets/default-social-image.png"
title: Object.freeze() in JavaScript
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
 
**Object.freeze() Method**

There is a method Object.freeze() among the methods of the object constructor that is used for freezing an object. Freezing an object will not enable the addition of new property to an object and will prohibit the removal or modification of existing properties. Object.freeze() retains the object's enumerability, configurability, writingability, and prototype. It produces the object that was passed and does not establish a frozen duplicate.

**Applications:**

To freeze objects and arrays, Object.freeze() is used.
To make an object immutable, Object.freeze() is used.

**Syntax:**

`Object.freeze(obj)`

**Parameters Used:**

obj: This is the object to be freezed.

**Return Value:**

Object.freeze() returns the passed object to the function.

Examples:

```
Input : const obj1 = { property1: 'initial_data'};
        const obj2 = Object.freeze(obj1);
        obj2.property1 = 'new_data';
        console.log(obj2.property1);

Output : "initial_data"
```

Explanation: In this case, the object "obj2" was given property from the object "obj1" and the properties of "obj1" are frozen, thereby preventing the addition of new properties and values to "obj2."

```
Input : var obj = { prop: function() {}, name: 'adam' };
        console.log(obj);
        obj.name = 'billy';
        delete obj.prop;
        console.log(obj);
        var o = Object.freeze(obj);
        obj.name = 'chris';
        console.log(obj);

Output : Object { prop: function () {}, name: "adam" }
         Object { name: "billy" }
         Object { name: "billy" }
```

Explanation: The "obj" object was assigned "prop: function" in this case, which was later removed since the "obj" object was not frozen. After that, the frozen values of "obj" were allocated to a new object "o" that stopped any further changes.

**Code 1:**

```
<script> 
<!-- creating an object constructor and assigning values to it -->
const obj1 = { property1: 'initial_data'}; 
  
<!--creating a second object which will freeze the properties of the first object-->
const obj2 = Object.freeze(obj1); 
  
<!-- Updating the properties of the frozen object -->
obj2.property1 = 'new_data'; 
  
<!-- Displaying the properties of the  frozen object -->
console.log(obj2.property1); 
</script> 
```

OUTPUT :

`"initial_data"`

**Code 2:**

```
<script> 
<!-- creating an object constructor and assigning values to it -->
var obj = { prop: function() {}, name: 'adam' }; 
  
<!-- Displaying the properties of the object created -->
console.log(obj); 
  
<!-- Updating the properties of the object -->
obj.name = 'billy'; 
delete obj.prop; 
<!-- Displaying the updated properties of the object -->
console.log(obj); 
  
<!-- Freezing the object using object.freeze() method> 
var o = Object.freeze(obj); 
  
<!-- Updating the properties of the frozen object -->
obj.name = 'chris'; 
  
<!-- Displaying the properties of the  frozen object -->
console.log(obj); 
  
</script> 
```

OUTPUT :

```
Object { prop: function () {}, name: "adam" }
Object { name: "billy" }
Object { name: "billy" }
```

**Exceptions :**

It will trigger a TypeError if the passed argument is not an object.

Reference: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze)