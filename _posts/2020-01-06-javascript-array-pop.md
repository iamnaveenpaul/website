---
image: "/assets/default-social-image.png"
title: JavaScript Array pop()
categories: JavaScript-array
---

The feature of arr.pop() extracts the last element of the array and returns the extracted element as well. This function reduces the array length by 1.

**Syntax**

`arr.pop()`

**Arguments**

There is no argument for this function.

**Return value**

This function returns the element that has been removed. This function returns undefined if the array is empty.

Example 1:

```
var arr = [34, 234, 567, 4];
var popped = arr.pop();
print(popped);
print(arr);
```

Output:

```
4
34,234,567
```

In this case, the pop() method extracts and returns the last element from the array which is 4.

Example 2:

```
var arr = [];
var popped = arr.pop();
print(popped);
```

Output:

`undefined`

In this example, the pop() function attempts to extract the last element of the array, but as the array is empty, it returns as the answer undefined.

Program 1:

```
<script> 
// JavaScript code to illustrate pop() function 
  
function func() { 
    var arr = [34, 234, 567, 4]; 
  
    // popping the last element from the array  
    var popped = arr.pop(); 
    document.write(popped); 
    document.write("<br>"); 
    document.write(arr); 
} 
func(); 
</script> 
```

Output:

```
4
34,234,567
```

Program 2:

```
// JavaScript to illustrate pop() function 
<script> 
function func() { 
  
    var arr = []; 
  
    // popping the last element 
    var popped = arr.pop(); 
    document.write(popped); 
} 
func(); 
</script> 
```

Output:

`undefined`