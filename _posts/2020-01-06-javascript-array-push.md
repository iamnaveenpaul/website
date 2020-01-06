---
image: "/assets/default-social-image.png"
title: JavaScript Array push()
categories: JavaScript-array
---

arr.push() is used to push into the array one or more values. This method adjusts the array's length by applying the number of elements to the array.

**Syntax**

`arr.push(element1[, ...[, elementN]])`

**Arguments:** Each function includes as many arguments numbers as the amount of elements to be added into the array.

**Return value:** This method returns the new array length after the arguments have been inserted into the array.

Example 1:

```
var arr = [34, 234, 567, 4];
print(arr.push(23,45,56));
print(arr);
```

Output:

```
7
34,234,567,4,23,45,56
```

The push() method adds the numbers to the end of the array in this case.

Example 2:

```
var arr = [34, 234, 567, 4];
print(arr.push('jacob',true,23.45));
print(arr);
```

Output:

```
7
34,234,567,4,jacob,true,23.45
```

The push() method adds the objects to the end of the array in this case.

Program 1:

```
// JavaScript to illustrate push() function 
<script> 
function func() { 
  
    // Original array 
    var arr = [34, 234, 567, 4]; 
  
    // Pushing the elements 
    document.write(arr.push(23,45,56)); 
    document.write("<br>"); 
    document.write(arr); 
} 
func(); 
</script> 
```

Output:

```
7
34,234,567,4,23,45,56
```

Program 2:

```
<script> 
// JavaScript to illustrate push() function 
function func() { 
  
    var arr = [34, 234, 567, 4]; 
  
    document.write(arr.push('jacob',true,23.45)); 
    document.write("<br>"); 
    document.write(arr); 
} 
func(); 
</script> 
```

Output:

```
7
34,234,567,4,jacob,true,23.45
```