---
image: "/assets/default-social-image.png"
title: JavaScript Array shift()
categories: JavaScript-array
---

Arr.shift() eliminates the first portion of the array so that the initial array size is reduced by 1.

**Syntax:**

`arr.shift()`

**Arguments**

There is no argument taken for this function.

**Return value**

* This feature returns the first element of the array that has been removed.
* This function returns undefined if the array is empty.

Note: It is also possible to use this method with other javascript objects that behave like the array.

Example 1:

```
var arr = [34, 234, 567, 4];
print(arr.shift());
print(arr);
```

Output:

```
34
234,567,4
```

In this case, the shift() function removes the array's first element, so it returns 34.

Example 2:

```
var arr = [];
print(arr.shift());
print(arr);
```

Output:

`undefined`

In this case, the shift() method attempts to remove the array's first element, but the array is empty, so it returns undefined.

Program 1:

```
// JavaScript to illustrate  
// shift() function 
importPackage(java.io); 
importPackage(java.lang); 
importPackage(java.math); 
importPackage(java.util); 
  
// Original Array 
var arr = [34, 234, 567, 4]; 
  
// Removing the first element 
var value = arr.shift(); 
print(value); 
print(arr); 
```

Output:

```
34
234,567,4
```

Program 2:

```
// JavaScript to illustrate 
// shift() function 
importPackage(java.io); 
importPackage(java.lang); 
importPackage(java.math); 
importPackage(java.util); 
  
// Original Array 
var arr = []; 
  
// Removing the first element 
var value = arr.shift(); 
print(value); 
print(arr); 
```

Output:

`undefined`