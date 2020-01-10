---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.subarray()
categories: JavaScript-typedArray
---

The typedArray.subarray() is a built-in function in JavaScript that is used to return some of the object typedArray.

**Syntax:**

`typedarray.subarray(begin, end)`

**Parameters:**

This acknowledges two parameters listed below:

* **begin:** It stipulates the starting element index upon which to start the part of the given array. It's optional and inclusive.
* **end:** It stipulates the ending element index up to which the part to be included in the given array. It's optional and exclusive.

**Return value:**

It returns a new array formed by the given object typedArray.

Code #1:

```
<script> 
  
   // Creating a new typedArray Uint8Array() object 
   const A = new Uint8Array([5, 10, 15, 20, 25, 30, 35 ]); 
  
   // Calling subarray() functions 
   B = A.subarray(1, 3) 
   C = A.subarray(1) 
   D = A.subarray(3) 
   E = A.subarray(0, 6) 
   F = A.subarray(0) 
     
   // Printing some new typedArray which are 
   // the part of the given input typedArray 
   document.write(B +"<br>"); 
   document.write(C +"<br>"); 
   document.write(D +"<br>"); 
   document.write(E +"<br>"); 
   document.write(F +"<br>"); 
  
</script> 
```

Output:

```
10,15
10,15,20,25,30,35
20,25,30,35
5,10,15,20,25,30
5,10,15,20,25,30,35
```

Code #2:

When index is negative, elements are accessed from the end of the object typedArray.

Code that illustrates this negative indexing concept.

```
<script> 
  
   // Creating a new typedArray Uint8Array() object 
   const A = new Uint8Array([5, 10, 15, 20, 25, 30, 35 ]); 
  
   // Calling subarray() functions 
   B = A.subarray(-1) 
   C = A.subarray(-2) 
   D = A.subarray(-3) 
   E = A.subarray(3) 
   F = A.subarray(0) 
     
   // Printing some new typedArray which are 
   // the part of the given input typedArray 
   document.write(B +"<br>"); 
   document.write(C +"<br>"); 
   document.write(D +"<br>"); 
   document.write(E +"<br>"); 
   document.write(F +"<br>"); 
  
</script> 
```

Output:

```
35
30,35
25,30,35
20,25,30,35
5,10,15,20,25,30,35
```