---
image: "/assets/default-social-image.png"
title: JavaScript Array some() function
categories: JavaScript-array
---

**Arr.some()**

Arr.some() tests if at least one of the array elements fulfills the requirement specified by the function of the argument.

**Syntax:**

`arr.some(arg_function(element, index, array), thisArg)`

**Arguments**

The function's argument is another function that defines the condition for each element of the array to be verified. There are three arguments for this function itself:

**array**

This is the array that has been called to the.some() function.

**index**

This is the index of the current element that the function is processing.

**element**

This is the current element that the function processes.

Another argument this value is used when running the argument method to inform the function to use this value.

**Return value**

This method returns true even if one of the array elements fulfills the condition (and does not test the remaining values) enforced by the function of the argument. If the requirement is not fulfilled by any aspect of the array, it returns false.

Example 1:

```
function isGreaterThan5(element, index, array) 
{
  return element > 5;
}

print([2, 5, 8, 1, 4].some(isGreaterThan5));
```

Output:

`true`

some() tests for any number greater than 5 in this scenario. Because there are elements that meet this requirement, the function returns true.

Example 2:

```
function isGreaterThan5(element, index, array) 
{
  return element > 5;
}

print([-2, 5, 3, 1, 4].some(isGreaterThan5)); 
```

Output:

`false`

some() searches for any number greater than 5 in this case. Because there are no elements that satisfy this requirement, the function returns false.

Example 3:

```
var arr = [2, 5, 8, 1, 4]

function checkAvailability(arr, val) 
{
  return arr.some(
           function(arrVal) 
           {
             return val === arrVal;
           } );
}

print(checkAvailability(arr, 2));
print(checkAvailability(arr, 87));
```

Output:

```
true
false
```

In this case, some() checks in the array for 2 and 87. Therefore the function returns true for first query while returning false for second query since only 2 is available.

Program 1:

```
<script> 
// JavaScript to illustrate lastIndexOf() function 
  
function isGreaterThan5(element, index, array)  
{ 
   return element > 5; 
} 
function func()  
{ 
    // Original array 
    var array = [2, 5, 8, 1, 4]; 
  
    // Checking for condition in array 
    var value = array.some(isGreaterThan5); 
  
    document.write(value); 
} 
func(); 
</script> 
```

Output:

`true`

Program 2:

```
// JavaScript to illustrate lastIndexOf() function 
<script> 
function isGreaterThan5(element, index, array)  
{ 
  return element > 5; 
} 
  
function func()  
{ 
    // Original array 
    var array = [-2, 5, 3, 1, 4]; 
  
    // Checking for condition in the array 
    var value = array.some(isGreaterThan5); 
  
    document.write(value);  
} 
  
func(); 
</script> 
```

Output:

`false`

Program 3:

```
<script> 
// JavaScript to illustrate some() function 
  
function checkAvailability(arr, val)  
{ 
  return arr.some(function(arrVal)  
  { 
    return val === arrVal; 
  }); 
} 
function func()  
{ 
    // Original function 
    var arr = [2, 5, 8, 1, 4] 
  
    // Checking for condition 
    document.write(checkAvailability(arr, 2)); 
    document.write("<br>"); 
    document.write(checkAvailability(arr, 87)); 
} 
func(); 
</script> 
```

Output:

```
true
false
```