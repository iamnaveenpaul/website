---
image: "/assets/default-social-image.png"
title: JavaScript arrayBuffer.byteLength property
categories: JavaScript-array
---

The arrayBuffer.byteLength is a JavaScript property that returns in byte the length of an ArrayBuffer. ArrayBuffer is an object that represents binary data of fixed length.

**Difference between property and function in javascript.**

JavaScript property is nothing but a value while method is a function that can be understood by using an example given below.

```
// car is an object. 
var car = {}; 
  
// car.name is a property of the given object. 
car.name = "Audi", 
  
// car.sayModel is a function of the given object. 
car.sayModel = function() { 
console.log("A8"); 
} 
      
// printing property value. 
console.log(car.name); 
  
// printing function called value. 
console.log(car.sayModel()); 
```

Output:

```
> "Audi"
> "A8"
```

Here, as we can see the object car's property, the string will be stored as "Audi" and accessed by car.name.

sayModel is a method i.e. an object function which can be accessed by car.sayModel().

It can be noted that sayModel is only a function that uses ().

**Difference between bytelength and length property**

The length property returns a string object's length i.e. the number of characters in the string object.

Example:

```
Input:- griva
Output:- 5
```

Bytelength property returns the ArrayBuffer length in byte. ArrayBuffer is an object used to represent binary data of fixed length.

Example:

```
Input:- ArrayBuffer(2)
Output:- 2
```

**Syntax:**

`arraybuffer.byteLength`

**Parameter:**

Nothing is taken here as a parameter because it is a property and not a function.

**Return Values:**

This returns an ArrayBuffer's length in byte.

Code #1:

```
// ArrayBuffer is created with  
// some size in bytes. 
var A = new ArrayBuffer(2); 
  
// Here the byteLength property  
// is used for checking the size. 
var B = A.byteLength; 
  
// Length of the ArrayBuffer in bytes is printed. 
console.log(B); 
```

Output:

`> 2`

Code #2:

```
// ArrayBuffer is created  
// with some size in bytes. 
var A = new ArrayBuffer(0); 
  
// Here the byteLength property  
// is used for checking the size. 
var B = A.byteLength; 
  
// Length of the ArrayBuffer 
// in bytes is printed. 
console.log(B); 
```

Output:

`> 0`

Code #3:

```
// ArrayBuffer is created 
// with some size in bytes. 
var A = new ArrayBuffer("geeksforgeeks"); 
  
// Here the byteLength property is  
// used for checking the size. 
var B = A.byteLength; 
  
// Length of the ArrayBuffer 
// in bytes is printed. 
console.log(B); 
```

Output:

`> 0`

Code #4:

```
// ArrayBuffer is created  
// with some size in bytes. 
var A = new ArrayBuffer(4.6); 
  
// Here the byteLength property  
// is used for checking the size. 
var B = A.byteLength; 
  
// Length of the ArrayBuffer  
// in bytes is printed. 
console.log(B); 
```

Output:

`> 4`

**Errors and Exceptions related with this function:**

Negative number can not be taken because byte sizes can only be obtained for positive integer value, even zero.

```
// ArrayBuffer is created  
// with some size in bytes. 
var A = new ArrayBuffer(-2); 
  
// Here the byteLength property is 
// used for checking the size. 
var B = A.byteLength; 
  
// Length of the ArrayBuffer  
// in bytes is printed. 
console.log(B); 
```

Output:

`Error: Invalid array buffer length`

Complex number can not be taken because byte sizes can only be obtained with positive integer value, even zero.

```
// ArrayBuffer is created with 
// some size in bytes. 
var A = new ArrayBuffer(2 + 4i); 
  
// Here the byteLength property  
// is used for checking the size. 
var B = A.byteLength; 
  
// Length of the ArrayBuffer 
// in bytes is printed. 
console.log(B); 
```

Output:

`Error: Invalid or unexpected token`

The byte sizes should be less than 2^5^3, otherwise error will be returned as: Invalid array buffer length.

```
// ArrayBuffer is created with some size in bytes. 
var A = new ArrayBuffer(2338945720394852703948572); 
  
// Here the byteLength property is 
// used for checking the size. 
var B = A.byteLength; 
  
// Length of the ArrayBuffer in bytes is printed. 
console.log(B); 
```

Output:

`Error: Invalid array buffer length`

**Application:**

To get an ArrayBuffer's length in byte.

Code #1:

```
// ArrayBuffer is created  
// with some size in bytes. 
var A = new ArrayBuffer(23); 
  
// Here the byteLength property  
// is used for checking the size. 
var B = A.byteLength; 
  
// Length of the ArrayBuffer  
// in bytes is printed. 
console.log(B); 
```

Output:

`> 23`