---
image: "/assets/default-social-image.png"
title: JavaScript Array find() function
categories: JavaScript-array
---

The method arr.find() is used to find the first element from the array that fulfills the function's condition. If the condition is satisfied by more than one element, the first element that meets the requirement is returned. Suppose you want the first odd number in the array to be found. The function of the argument checks whether or not the argument passed to it is odd or it isn't. The find() method calls the function of the argument for each array element. The first odd number that returns true for the argument function is identified as the response by find() method. The feature syntax is the following:

**Syntax:**

`arr.find(function(element, index, array), thisValue)`

**Arguments**

Another function that defines the condition to be checked for each element in the array is the argument for this function. There are three arguments for this function itself:

**array:**

This is the list that has been called to the.filter() function.

**index:**

This is the index of the current element that the function is processing.

**element:**

This is the current element that the function processes.

Another argument thisValue is used when running the argument method to tell the function to use this value.

**Return value**

This function returns the first value that meets the condition from the array. If no value fulfills the condition, the response will be undefined.

Example 1:

```
function isOdd(element, index, array) {
  return (element%2 == 1);
}

print([4, 6, 8, 12].find(isOdd));
```

Output:

`undefined`

The find() method identifies all the odd numbers in the array in this case. Since there are no odd numbers, it returns undefined.

Example 2:

```
function isOdd(element, index, array) {
  return (element%2 == 1);
}

print([4, 5, 8, 11].find(isOdd));
```

Output:

`5`

The find() function determines the first occurrence of odd number in the array in this case. So, since the first odd number is 5, it returns it.

Program 1:

```
// JavaScript to illustrate find() function 
  
<script> 
function isOdd(element, index, array)  
{  
  return (element % 2 == 1);  
} 
  
function func()  
{ 
  var array = [ 4, 6, 8, 12 ]; 
  
  // Checking for odd numbers and  
  // reporting the first odd number 
  document.write(array.find(isOdd)); 
}  
func(); 
</script> 
```

Output:

`undefined`

Program 2:

```
<script> 
// JavaScript to illustrate find() function 
  
function isOdd(element, index, array) 
{  
   return (element % 2 == 1);  
} 
  
function func()  
{ 
  var array = [ 4, 5, 8, 11 ]; 
  
  // Checking for odd numbers and  
  // reporting the first odd number 
  document.write(array.find(isOdd)); 
}  
func(); 
</script> 
```

Output:

`5`

**Application:**

If we need to get the value of the first element in the array that satisfies the testing function given that we use the JavaScript method of Array.find().

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