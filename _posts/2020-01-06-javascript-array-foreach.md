---
image: "/assets/default-social-image.png"
title: JavaScript Array forEach()
categories: JavaScript-array
---

arr.forEach() method calls the function given once for each array element. The function provided will execute some type of operation on the elements of the specified array.

**Syntax**

```
arr.forEach(function callback(currentValue[, index[, array]]) {

}[, thisArg]);
```

**Arguments:** Another function that defines the condition to be checked for each element in the array is the argument for this function. There are three arguments for this function itself:

**array**

This is the array that has been called to the.forEach() method.

**index**

This is the index of the current element that the function is being processed.

**element**

This is the current element that the function processes.

Another argument thisValue is used when executing the argument function to tell the function to use this value.

**Return value:** This function's return value is always undefined. This function may or may not change the original array as it depends on the functionality of the function of the argument.

Example 1:

```
const items = [1, 29, 47];
const copy = [];

items.forEach(function(item){
  copy.push(item*item);
});
print(copy);
```

Output:

`1,841,2209`

In this case, the forEach() method calculates the square of each array element.

Program 1:

```
<script> 
// JavaScript to illustrate substr() function 
function func() { 
  
    // Original array 
    const items = [1, 29, 47]; 
    const copy = []; 
  
    items.forEach(function(item){ 
        copy.push(item*item); 
    }); 
  
    document.write(copy); 
} 
func(); 
</script> 
```

Output:

`1,841,2209`