---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.every()
categories: JavaScript-typedArray
---

The typedArray.every() method is a built-in feature in JavaScript that is used to check whether the items in the typedArray satisfy a given function's requirement.

Syntax:

`typedarray.every(callback)`

**Parameters:**

As a parameter, it takes callback function.

The callback is a method to check the typedArray elements. This callback function takes the following three parameters.

**current_value:** This is the current element in the typedArray being processed.
**index:** This is the index of the current element being processed in the array being typed.
**array:** This would be the typedArray.

**Return value:**

This returns true if a true value for each and every array element present in the typedArray is returned by the callback function, otherwise which it is returned false.

Code #1:

```
<script> 
  
   // is_negative function is called to test the 
   // elements of the typedArray element. 
   function is_negative(current_value, index, array) 
   { 
    return current_value < 0; 
   } 
  
  // Creating a typedArray with some elements 
  const A = new Int8Array([ -5, -10, -15, -20, -25, -30 ]); 
  
  // Printing whether elements are satisfied by the 
  // functions or not 
  document.write(A.every(is_negative)); 
    
</script> 
```

Output:

`true`

Code #2:

```
<script> 
  
   // is_negative function is called to test the 
   // elements of the typedArray element. 
   function is_positive(current_value, index, array) 
   { 
    return current_value > 0; 
   } 
  
  // Creating a typedArray with some elements 
  const A = new Int8Array([ -5, -10, -15, -20, -25, -30 ]); 
  
  // Printing whether elements are satisfied by the 
  // functions or not 
  document.write(A.every(is_positive)); 
    
</script> 
```

Output:

`false`