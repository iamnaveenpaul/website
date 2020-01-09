---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.copyWithin()
categories: JavaScript-typedArray
---

The typedArray.copyWithin() is a built-in feature in JavaScript that is used in the same typedArray to copy all elements of a typedArray at the specified location.

**Syntax:**

`typedArray.copyWithin(target, start, end)`

**Parameters:**

It recognizes three parameters listed below:

**target:** This is the position of the start index from which to copy the element.
**start:** This is the starting index position from which to start copying elements and its default value starts the typedArray index.
**end:** It is optional and it is the index of the end position to copy the elements and its default value is the end of the typedArray.

**Return value:**

After copying process, this returns the modified array.

Code #1:

```
<script> 
  
   // Constructing a new typedArray "A" 
   // with some elements 
   const A = new Uint8Array([ 5, 10, 15, 20, 25, 30, 35, 40 ]); 
  
   // Calling copyWithin function to copy  
   // element from index position 0 and 
   // element from index 4 to 5 
   A.copyWithin(0, 4, 5); 
  
   // Printing a new modified array 
   document.write(A); 
     
</script> 
```

Output:

`25,10,15,20,25,30,35,40`

Code #2:

```
<script> 
  
   // Constructing some new typedArrays 
   // with some elements 
   const A = new Uint8Array([ 5, 10, 15, 20, 25, 30, 35, 40 ]); 
   const B = new Uint8Array([ 5, 10, 15, 20, 25, 30, 35, 40 ]); 
   const C = new Uint8Array([ 5, 10, 15, 20, 25, 30, 35, 40 ]); 
   const D = new Uint8Array([ 5, 10, 15, 20, 25, 30, 35, 40 ]); 
   const E = new Uint8Array([ 5, 10, 15, 20, 25, 30, 35, 40 ]); 
  
   // Calling copyWithin function with different 
   // parameters 
   a = A.copyWithin(0, 5); 
   b = B.copyWithin(1, 4); 
   c = C.copyWithin(0, 4, 5); 
   d = D.copyWithin(2, 3, 5); 
   e = E.copyWithin(0, 1, 4); 
  
   // Printing new modified arrays 
   document.write(a +"<br>"); 
   document.write(b +"<br>"); 
   document.write(c +"<br>"); 
   document.write(d +"<br>"); 
   document.write(e); 
     
</script> 
```

Output:

```
30,35,40,20,25,30,35,40
5,25,30,35,40,30,35,40
25,10,15,20,25,30,35,40
5,10,20,25,25,30,35,40
10,15,20,20,25,30,35,40
```