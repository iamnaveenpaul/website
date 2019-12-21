---
image: "/assets/default-social-image.png"
title: Object.is() in JavaScript
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

**Object.is() Method**

The method of Object.is() is used to evaluate whether or not two values are the same.

If they posses one of the following properties, two values can be the same:

* If both have undefined values.
* If both have null values.
* If both have true or false values.
* If both strings are of the same length and in the same order with the same characters.
* If both have “+0”, which are numbered values.
* If both have “-0”, which are numbered values.
* If both are numbers, and both are either "NaN" or non-zero, and both are not NaN, and both have the same value.

Object.is() takes two arguments and returns a boolean showing whether the two arguments are the same or not, because the arguments are values to be compared.

**Difference between Object.is() method and “==” operator**

The operator "==" and "===" considers the numerical values "+0" and "-0" as equivalent, while they are handled as not equal by the rule Object.is(). Other than that, the operator "==" and "===" will not consider Number. Nan equal to Nan.

**Applications:**

* Object.is() is used when two strings are needed to compare.
* Object.is() is used when two numbers are needed to compare.
* Object.is() is used when polarity of two numbers are needed to compare.
* Object.is() is used when two objects are needed to compare.

**Syntax:**

`Object.is(value1, value2)`

**Parameters Used:**

value1 : It is used to compare the first value.
value2 : It is used to compare the second value.

**Return Value:**

Object.is() returns a boolean that shows whether or not the two arguments are the same.

Examples:

```
Input : Object.is('thisIsMyWorld', 'thisIsMyWorld');
Output: true
```

Explanation: The Object.is() function returns true in the above case because the two strings provided as an argument are of the same length with the same characters and in the same manner.

```
Input : Object.is('thisIsMyWorld', 'timw');
Output : false
```

Explanation: The Object.is() function returns false in the above case because the two strings provided as an argument are not of the same length with the same characters and in the same manner.

```
Input : Object.is(0,-0);
Output: false
```

Explanation: The Object.is() function returns false in the above case because the two numbers presented as an argument are of opposite polarity.

```
Input : var check = { a: 100 };
        Object.is(check, check);  
Output: true
```

Explanation: an object "check" was generated in the above example and passed to the Object.is() method as a parameter. This returns valid as both parameters are a single object and are related, hence rendering true as output.

**Code 1:**

```
<script> 
  
// Comparing strings of the same length  
// with the same characters in the same order   
Object.is('thisIsMyWorld', 'thisIsMyWorld'); 
  
</script> 
```

OUTPUT :

`true`

**Code 2:**

```
<script> 
  
// Comapring two different strings 
Object.is('thisIsMyWorld', 'timw'); 
  
</script> 
```

OUTPUT :

`false`

**Code 3:**

```
<script> 
  
// Comapring 0 and -0  
Object.is(0,-0); 
  
</script> 
```

OUTPUT :

`false`

**Code 4:**

```
<script> 
  
// Comparing a variable with itself 
var check = { a: 100 }; 
Object.is(check, check);   
  
</script> 
```

OUTPUT :

`false`

**Exceptions :**

* The operator "==" and "===" considers the numerical values "+0" and "-0" as equivalent, but they are treated differently by the object.is() method.
* The Object.is() method does not coerce values before comparison even if they are of different data types.

Reference: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/is](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/is)