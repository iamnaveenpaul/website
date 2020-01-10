---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.forEach()
categories: JavaScript-typedArray
---

The typedArray.forEach() is a JavaScript built-in function that executes a given function once for the element of each provided typedArray.

**Syntax:**

`typedarray.forEach(callback)`

**Parameter:**

It accepts a callback function parameter that produces each element of the new typedArray and this function takes three parameters specified below:

**currentValue:** It is the value of the current element in the typedArray being processed.
**index:** It is the index of the current element in the array to be handled.
**array:** It is the array that is called to forEach() function.

**Return Value:**

It doesn't returns anything back.

Example:

```
<script> 
  
    // Constructing some typedArray 
    const A = new Uint8Array([ 1, 3, 5, 7 ]) 
    const B = new Uint8Array([ 2, 4, 6, 8 ]) 
  
      // Calling callback function 
      function callback(element, index, array) { 
          document.write('a[' + index + '] = ' + element + "<br>"); 
      } 
  
      // Calling forEach() function 
      A.forEach(callback); 
      B.forEach(callback); 
  
</script> 
```

Output:

```
a[0] = 1
a[1] = 3
a[2] = 5
a[3] = 7
a[0] = 2
a[1] = 4
a[2] = 6
a[3] = 8
```