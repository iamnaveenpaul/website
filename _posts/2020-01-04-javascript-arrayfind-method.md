---
image: "/assets/default-social-image.png"
title: JavaScript Array.find() Method
categories: JavaScript-array
---

**Introduction:**

The Array.find() is an inbuilt feature in JavaScript that is used to get the value of the first element in the array that fits the requirement given. This searches all the elements in the array and whatever the first element matches the condition which will be displayed.

**Syntax:**

`array.find(function(element))`

**Parameters:**

**element:**

It is the element of the array that operates on the method of array.find().

**Return value:**

If any of the elements in the array that satisfy the condition, it returns the array element value, otherwise it returns undefined.

**Browser Support:**

```
FEATURE	BASIC SUPPORT
Chrome	45
Edge	Yes
Firefox	25
Internet Explorer	No
Opera	32
Safari	8
Android webview	Yes
Chrome for Android	Yes
Edge mobile	Yes
Firefox for Android	4
Opera Android	Yes
iOS Safari	8
```

Example:

Here in JavaScript, the Array.find() method returns the value of the first element in the array that satisfies the test function given.

```
// input array contain some elements. 
var array = [10, 20, 30, 40, 50]; 
  
// Here find function returns the value of the first element 
// in the array that satisfies the provided testing 
// function (return element > 10). 
var found = array.find(function(element) { 
  return element > 20; 
}); 
  
// Printing desired values. 
console.log(found); 
```

Output:

`> 30`

**Application:**

Whenever we need to get the value of the first element in the array that satisfies the testing function provided that we use the JavaScript method of Array.find().

```
// input array contain some elements. 
var array = [2, 7, 8, 9]; 
  
// Here find function returns the value of  
// the first element in the array that satisfies  
// the provided testing function (return element > 4). 
var found = array.find(function(element) { 
  return element > 4; 
}); 
  
// Printing desired values. 
console.log(found); 
```

Output:

`> 7`