---
image: "/assets/default-social-image.png"
title: Arrays in JavaScript
categories: JavaScript-array
---

Array is a single variable in JavaScript that is used to store various elements. It is often used when a set of elements is processed and accessed by a single variable. Unlike most languages where array is a multiple variable reference, there is a single variable in the JavaScript array that holds multiple elements.

**Declaration of an Array**

There are two methods to declare an array, generally.

Example:

```
var House = [ ]; // method 1
var House = new array(); // method 2
```

However method 1 is usually favored to Method 2. Let's recognize why this is so.

**Initialization of an Array**

Example (for Method 1):

```
// Initializing while declaring 
var house = ["1BHK", "2BHK", "3BHK", "4BHK"]; 
  
// Initializing after declaring 
house[0] = "1BHK";   
house[0] = "2BHK"; 
house[0] = "3BHK"; 
house[0] = "4BHK"; 
```

Example (for Method 2):

```
// Initializing while declaring 
// Creates an array having elements 10, 20, 30, 40, 50 
var house = new Array(10, 20, 30, 40, 50); 
  
//Creates an array of 5 undefined elements 
var house1 = new Array(5); 
  
//Creates an array with element 1BHK 
var home = new Array("!BHK"); 
```

As shown in the example above, the house contains 5 elements i.e. (10, 20, 30, 40, 50) whereas house1 includes 5 undefined elements rather than having a single element 5. Therefore this approach is usually not favored when working with numbers, but it works well with Strings and Boolean as shown in the example above, home contains a single 1BHK unit.

**A JavaScript array may contain various elements**

We can store in a single array: Numbers, Strings and Boolean.

Example:

```
// Storing number, boolean, strings in an Array 
var house = ["1BHK", 25000, "2BHK", 50000, "Rent", true]; 
```

**Accessing Array Elements**

JavaScript array is indexed from 0 so that the array components can be viewed as follows:

```
var house = ["1BHK", 25000, "2BHK", 50000, "Rent", true]; 
alert(house[0]+" cost= "+house[1]); 
var cost_1BHK = house[1]; 
var is_for_rent = house[5]; 
alert("Cost of 1BHK = "+ cost_1BHK); 
alert("Is house for rent = ")+ is_for_rent); 
```

**Length property of an Array**

An Array's length property returns an Array's length. The Array Length is always one more than an Array's highest index.

Example:

```
var house = ["1BHK", 25000, "2BHK", 50000, "Rent", true]; 
  
//len conatains the length of the array 
var len = house.length; 
for (var i = 0; i < len; i++) 
    alert(house[i]); 
```

Note: You can verify all the above examples by typing them in the HTML script tag.