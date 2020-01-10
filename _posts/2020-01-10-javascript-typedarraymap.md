---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.map()
categories: JavaScript-typedArray
---

The typedArray.map() is a built-in function in JavaScript that is used to create a new typedArray on each element of the given typedArray, resulting in a given function.

**Syntax:**

`typedArray.map(callback)`

**Parameters:**

It accepts a callback function parameter that recognizes those parameters defined below.

* **currentValue:** In the typedArray, it is the current element being handled.
* **index:** It is the index of the current element processed in the typedArray.
* **array:** It's the typedArray that's called.

**Return value:**

It returns a new typedArray on each element of the specified typedArray with the result of a provided function.

Code #1:

```
<script> 
   
  // Creating a typedArray with some elements 
  const A = new Uint8Array([4, 9, 16, 25, 36]); 
    
  // Calling map() function with the parameter 
  // Math.sqrt function which find square root  
  // of the typedArray's elements 
  const B = A.map(Math.sqrt); 
  
  // Printing the result of the function 
  document.write(B); 
  
</script> 
```

Output:

`2,3,4,5,6`

Code #2:

```
<script> 
   
  // Creating a typedArray with some elements 
  var A = new Uint8Array([1, 2, 3, 4, 5, 6]); 
    
  // Calling map() function 
  var B = A.map(function(a) { 
  return a * 5; 
  }); 
    
  // Returning the results 
  document.write(B); 
  
</script> 
```

Output:

`5,10,15,20,25,30`