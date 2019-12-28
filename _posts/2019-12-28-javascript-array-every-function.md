---
image: "/assets/default-social-image.png"
title: JavaScript Array every() function
categories: JavaScript-array
---

The function Array.every() (tests whether or not all of the array elements meet the requirement provided by a function passed on to it as the argument.

**Syntax:**

`arr.every(function[, This_arg])`

**Argument**

The function that defines the condition to be verified for each element in the array is the argument for this method. There are three reasons for this function argument itself:

**array (optional)**

This is the array that has been called to the.every() function.

**index (optional)**

This is the index of the current element that the function is processing.

**element (Compulsory)**

This is the current element that the function processes.

**Another argument**

This_arg is used when executing the argument function to tell the function to use this value.

**Return value**

This method returns the value of Boolean true if all array elements obey the condition introduced by the function of the argument. If the argument function is not satisfied by one of the array elements, then this function returns false.

Example 1:

```
function ispositive(element, index, array) {
  return element > 0;
}
print([11, 89, 23, 7, 98].every(ispositive)); 
```

Output:

`true`

In this example, the every() function checks if each element of the array has a positive number. Therefore this function returns true as the answer because the array does not contain negative elements.

Example 2:

```
function isodd(element, index, array) {
  return (element % 2 == 1);
}
print([56, 91, 18, 88, 12].every(isodd)); 
```

Output:

`false`

In this example, the every() function checks whether or not each number in the array is odd. Therefore this method returns false as some of the numbers are even.

Program 1:

```
<script> 
// JavaScript code for every() function 
function ispositive(element, index, array)  
{ 
   return element > 0;  
} 
  
function func() { 
  var arr = [ 11, 89, 23, 7, 98 ]; 
    
  // check for positive  
  // number 
  var value = arr.every(ispositive); 
  document.write(value); 
} 
func(); 
</script> 
```

Output:

`true`

Program 2:

```
<script> 
// JavaScript code for every() function 
function isodd(element, index, array) 
{  
   return (element % 2 == 1);  
} 
  
function func()  
{ 
   var arr = [ 56, 91, 18, 88, 12 ]; 
    
   // check for odd number 
   var value = arr.every(isodd); 
   document.write(value); 
} 
func(); 
</script> 
```

Output:

`false`