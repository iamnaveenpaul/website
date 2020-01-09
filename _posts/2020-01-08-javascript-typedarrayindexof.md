---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.indexOf()
categories: JavaScript-typedArray
---

The typedArray.indexOf() is a JavaScript built-in feature that is used to return the element index if it is contained in the specified typedArray otherwise which it returns -1.

**Syntax:**

`typedarray.indexOf(Element, Index);`

**Parameters:**

It accepts two parameters specified below:

* **Element:** It is the element in the typedArray that is searched for index.
* **Index:** It is the element index in the form of the typedArray where the search will commence. The default value is zero (0) and optional.

**Return value:**

If found in the given typedArray, it returns the index of the element, otherwise it returns -1.

Code #1:

```
<script> 
  
    // Creating some typedArrays 
    const A = new Uint8Array([ 1, 2, 3, 4, 5 ]); 
    const B = new Uint8Array([ 5, 10, 15, 20 ]); 
    const C = new Uint8Array([ 0, 2, 4, 6,, 8, 10 ]); 
    const D = new Uint8Array([ 1, 3, 5, 7, 9 ]); 
  
    // Calling indexOf() function 
    a = A.indexOf(2) 
    b = B.indexOf(15, 1) 
    c = C.indexOf(6) 
    d = D.indexOf(9, 1) 
  
    // Printing the index of the elements given 
    // as the parameter of the indexOf() function 
    document.write(a + "<br>"); 
    document.write(b + "<br>"); 
    document.write(c + "<br>"); 
    document.write(d); 
  
</script> 
```

Output:

```
1
2
3
4
```

Code #2:

```
<script> 
  
    // Creating some typedArrays 
    const A = new Uint8Array([ 1, 2, 3, 4, 5 ]); 
    const B = new Uint8Array([ 5, 10, 15, 20 ]); 
    const C = new Uint8Array([ 0, 2, 4, 6,, 8, 10 ]); 
    const D = new Uint8Array([ 1, 3, 5, 7, 9 ]); 
  
   // Calling include() function 
   a = A.indexOf(6) 
   b = B.indexOf(21, 1) 
   c = C.indexOf(6, 4) 
   d = D.indexOf(0) 
  
   // Printing the index of the elements given 
   // as the parameter of the indexOf() function 
   document.write(a + "<br>"); 
   document.write(b + "<br>"); 
   document.write(c + "<br>"); 
   document.write(d); 
  
</script> 
```

Output:

```
-1
-1
-1
-1
```