---
image: "/assets/default-social-image.png"
title: JavaScript Array fill() function
categories: JavaScript-array
---

The function Array.fill() is used to fill the static value of the array. The value can be used to fill the whole array or even a portion of the array.

**Syntax:**

`arr.fill(value, start, end)`

Here is the array with the static value to be filled in.

**Arguments**

There are three arguments for this function to take.

**value**

It defines the static value to be used to replace the array elements.

**start (Optional)**

Defines the starting index from which the static representation of the array is to be filled. The starting index will be taken as 0 if this value is not specified. The net start index is length+start if start is negative.

**end (Optional)**

This argument specifies the last index to which the static value of the array is to be filled. If this value is not set, the last index of the i.e. arr.length -1 is taken as the end value by default. The net end is defined as length+end if the end is negative.

**Return value**

A new array is not returned by this function. Alternatively, the array on which this function is implemented is modified.

Example 1:

```
var arr = [1, 23, 46, 58];
arr.fill(87); 
```

Output:

`[87, 87, 87, 87]`

The function fill() fills the whole array with 87 in this case, replacing all the initial values in the array.

Example 2:

```
var arr = [1, 23, 46, 58];
arr.fill(87, 1, 3); 
```

Output:

`[1, 87, 87, 58]`

In this case, the fill() function fills the index 1 to 2 array less than the upper index by 87, replacing all the original values in the array.

Example 3:

```
var arr = [1, 23, 46, 58];
arr.fill(87, 2); 
```

Output:

`[1, 23, 87, 87]`

The function fill() fills the index 1 to 3 array with 87 in this case, replacing all the initial values in the array.

Program 1:

```
<script> 
// JavaScript code for fill() function 
function func() 
{ 
  var arr = [ 1, 23, 46, 58 ]; 
  
  // fill array with 87 
  arr.fill(87); 
  document.write(arr); 
}  
func(); 
</script> 
```

Output:

`[87, 87, 87, 87]`

Program 2:

```
<script> 
// JavaScript code for fill() function 
function func()  
{ 
    var arr = [1, 23, 46, 58]; 
      
    // here value = 87, start index=1 and 
    // and last index = 3  
    arr.fill(87, 1, 3); 
    document.write(arr); 
} 
  
func(); 
</script> 
```

Output:

`[1, 87, 87, 58]`

Program 3:

```
<script> 
// JavaScript code for fill() function 
function func()  
{ 
  var arr = [ 1, 23, 46, 58 ]; 
  
  // here value = 87, start index=1  
  arr.fill(87, 2); 
  document.write(arr); 
} 
  
func(); 
</script> 
```

Output:

`[1, 23, 87, 87]`