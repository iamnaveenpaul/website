---
image: "/assets/default-social-image.png"
title: JavaScript Array unshift()
categories: JavaScript-array
---

Arr.unshift() is used to add to the beginning of the specified array, one or more elements. This function extends the length of the current array by applying to the array, the number of elements.

**Syntax**

`arr.unshift(element1[, ...[, elementN]])`

**Arguments**

This method has the same number of arguments as the number of elements to be inserted at the beginning of the array.

**Return value**

This method returns the array's new length after the arguments are added at the array beginning.

Example 1:

```
var arr = [23,76,19,94];
print(arr.unshift(28,65));
print(arr);
```

Output:

```
6
28,65,23,76,19,94
```

The unshift() function adds 28 and 65 to the front of the array in the above case.

Program 1:

```
// JavaScript to illustrate unshift() function 
<script> 
function sayHello() { 
    var arr = [23,76,19,94]; 
      
    // Adding elements to the front of the array 
    document.write(arr.unshift(28,65)); 
    document.write("<br>"); 
    document.write(arr); 
} 
sayHello(); 
</script> 
```

Output:

```
6
[28,65,23,76,19,94]
```