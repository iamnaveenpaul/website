---
title: JavaScript Array.prototype.map() function
image: "/assets/default-social-image.png"
categories: JavaScript-array
---

**Array.map()**

Arr.map() creates a new array for each array element with the results of the function called. For each element of the specified array, this function calls in order the argument function once. This function's syntax is as follows:

**Syntax:**

```
var new_array = arr.map(arg_function(element[, index[, array]]) {
    // Return element for new_array
}[, thisArg])
```

**Arguments:**

Another function which performs some operation on the original array elements and returns elements to a new array is the argument for this function. There would be three arguments for this function:

* **array :** This is the array that has been named to the.map() function.
* **index :** This is the index of the current element that the function processes.
* **element :** This is the current element that the function performs.

Another argument thisValue is used when executing the argument function to instruct the function to use this value.

**Return value :** Using the value from the original array, this function returns a new array created using the values modified by the arg_function. This function does not alter the original array to implement this function.

Example 1:

```
var arr = [2, 56, 78, 34, 65];
var new_arr = arr.map(function(num) {
  return num / 2;
});
print(new_arr);
```

Output:

`[1, 28, 39, 17, 32.5]`

In this case, the map() function generates an array of numbers obtained by dividing the numbers by 2 in the original array.

Example 2:

```
var arr = [10, 64, 121, 23];
var new_arr = arr.map(Math.sqrt);
print(new_arr);
```

Output:

`[3.1622776601683795, 8, 11, 4.795831523312719]`

In this case, the map() function generates an array that includes square roots of the initial array numbers.

Program 1:

```
<script> 
// JavaScript to illustrate map() function 
  
function func()  
{ 
  // Original array 
  var arr = [ 2, 56, 78, 34, 65 ]; 
  
  // new mapped array 
  var new_arr = arr.map(function(num) { return num / 2; }); 
  
  document.write(new_arr); 
}  
func(); 
< /script> 
```

Output:

`1, 28, 39, 17, 32.5`

Program 2:

```
<script> 
//JavaScript to illustrate map() function 
  
function func()  
{ 
    //Original array 
    var arr = [10, 64, 121, 23]; 
  
    //new mapped array 
    var new_arr = arr.map(Math.sqrt); 
    document.write(new_arr); 
} 
func(); 
</script> 
```

Output:

`3.1622776601683795, 8, 11, 4.795831523312719`