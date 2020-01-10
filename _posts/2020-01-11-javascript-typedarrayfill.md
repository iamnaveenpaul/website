---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.fill()
categories: JavaScript-typedArray
---

The typedArray.fill() is a JavaScript built-in function that is used to fill a value from start index to end index to typedArray.

**Syntax:**

`typedarray.fill(value, start, end)`

**Parameters:**

It enables three parameters stated below:

* **value:** It is the value to fill with the array that is typed.
* **start:** This is optional, beginning index and its default value is 0.
* **end:** This is index ending, optional and not included. The default value is the typedArray length.

**Return value:**

It returns the array that is modified.

Example:

```
// Javascript to illustrate typedArray.fill() 
<script> 
  
   // Creating some typedArrays 
   const A = new Uint8Array([ 0, 0, 0, 0 ]); 
   const B = new Uint8Array([ 0, 0, 0, 0 ]); 
   const C = new Uint8Array([ 0, 0, 0, 0 ]); 
   const D = new Uint8Array([ 0, 0, 0, 0 ]); 
  
   // Calling fill() function to fill different values 
   a = A.fill(4, 1, 3); 
   b = B.fill(5, 1); 
   c = C.fill(3); 
   d = D.fill(4, 0, 0); 
  
   // Printing modified array 
   document.write(a +"<br>"); 
   document.write(b +"<br>"); 
   document.write(c +"<br>"); 
   document.write(d +"<br>"); 
     
</script> 
```

Output:

```
0,4,4,0
0,5,5,5
3,3,3,3
0,0,0,0
```