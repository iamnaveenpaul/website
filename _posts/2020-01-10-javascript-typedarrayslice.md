---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.slice()
categories: JavaScript-typedArray
---

The typedArray.slice() is an built-in function in JavaScript that is used to return the part of the typedArray elements.

**Syntax:**

`typedArray.slice(begin, end)`

**Parameters:**

It needs two parameters described below.

**begin:** It's the index that begins with, and it can also be negative.
**end:** It is the ending index and here slice extracts elements up to the end index but not including it.

**Return value:**

It returns a new typedArray that contains the elements extracted.

Example:

```
<script> 
  
  // Creating some typedArray containing same values 
  const A = new Uint8Array([ 5, 10, 15, 20, 25 ]); 
  const B = new Uint8Array([ 5, 10, 15, 20, 25 ]); 
  const C = new Uint8Array([ 5, 10, 15, 20, 25 ]); 
  const D = new Uint8Array([ 5, 10, 15, 20, 25 ]); 
  const E = new Uint8Array([ 5, 10, 15, 20, 25 ]); 
  const F = new Uint8Array([ 5, 10, 15, 20, 25 ]); 
  
  // Calling slice function with starting and ending index 
  var a = A.slice(1, 2); 
  var b = B.slice(0, 3); 
  var c = C.slice(4); 
  var d = D.slice(0 
    
  // Here index is negative so it extract element 
  // from the end of the typedArray 
  var e = E.slice(-2); 
  var f = F.slice(); 
  
  // Printing the extracted arrays 
  document.write(a +"<br>"); 
  document.write(b +"<br>"); 
  document.write(c +"<br>"); 
  document.write(d +"<br>"); 
  document.write(e +"<br>"); 
  document.write(f); 
    
</script> 
```

Output:

```
10
5,10,15
25
5,10,15,20,25
20,25
5,10,15,20,25
```