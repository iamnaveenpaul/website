---
image: "/assets/default-social-image.png"
title: JavaScript Array filter()
categories: JavaScript-array
---

The function arr.filter() is used to create a new array from a given array composed of only those elements from the given array that meet the condition provided by the function of the argument.

**Syntax:**

`var newArray = arr.filter(arg_function[, this_arg])`

arr is the array that was originally given.

**Argument**

The function that defines the condition to be verified for each element in the array is the argument for this function. There are three arguments for this arg_function itself:

**array**

This is the array that has been called to the.filter() function.

**index**

This is the index of the current element that the function processes.

**element**

This is the current element that the function processes.

The argument this_arg is used when running the argument method to tell the function to use this value.

**Return value**

This method returns a new array of only those elements that fulfilled the arg_function condition.

Example 1:

```
function isPositive(value) {
  return value > 0;
}

var filtered = [112, 52, 0, -1, 944].filter(isPositive);
print(filtered);
```

Output:

`[112,52,944]`

In this case, the filter() function creates a new array consisting of only those elements that fulfill the requirement verified by the function isPositive().

Example 2:

```
function isEven(value) {
  return value % 2 == 0;
}

var filtered = [11, 98, 31, 23, 944].filter(isEven);
print(filtered);
```

Output:

`[98,944]`

In this case, the function filter() creates a new array consisting of only those elements that satisfy the condition checked by the function isPositive().

Program 1:

```
<script> 
// JavaScript to illustrate findIndex() function 
function isPositive(value) { 
  return value > 0; 
} 
  
function func() { 
    var filtered = [112, 52, 0, -1, 944].filter(isPositive); 
    document.write(filtered); 
} 
func(); 
</script> 
```

Output:

`[112,52,944]`

Program 2:

```
<script> 
// JavaScript to illustrate findIndex() function 
function isEven(value) { 
  return value%2 == 0; 
} 
  
function func() { 
    var filtered = [11, 98, 31, 23, 944].filter(isEven); 
    document.write(filtered); 
} 
func(); 
</script> 
```

Output:

`[98,944]`