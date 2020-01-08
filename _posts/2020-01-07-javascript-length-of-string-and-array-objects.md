---
image: "/assets/default-social-image.png"
title: JavaScript length of string and array objects
categories: JavaScript-array
---

The JavaScript object's length property is used to determine the object's size. This property is used with many objects such as string, array, etc. This function returns, in the case of strings the number of characters in the array. The function returns in the case of an array, the number of elements in the array.

**Syntax:**

`object.length`

Where a string object or an array object can be an object.

Examples:

```
Input : print("Griva".length)
Output :5
```

```
Input : print([1, 2, 3, 4, 5, 6, 7, 8, 9].length)
Output :9
```

Explanation:

The number of characters in the string "Griva" is in the first example 5, hence the output is 5.

And in the second example, the array length is 9, and the output is 9.

Program:

```
<script> 
// JavaScript to illustrate length property 
  
function func() { 
  
    // length property for array 
    document.write([1,2,3,4,5,6,7,8,9].length); 
    document.write("<br>"); 
  
    // length property for string 
    document.write("Griva".length) 
} 
func(); 
</script> 
```

Output:

```
9
5
```