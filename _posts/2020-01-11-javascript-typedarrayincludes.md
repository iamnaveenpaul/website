---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.includes()
categories: JavaScript-typedArray
---

The typedArray.includes() is a built-in function in JavaScript that is used to test whether or not the specified typedArray contains a specific element and produces true and false as a consequence.

**Syntax:**

`typedarray.includes(Element, Index);`

**Parameters:**

It acknowledges two parameters indicated below.

* **element:** This is the search element in the typedArray.
* **index:** This is optional and is the element index of the form typedArray where search should begin. The predefined value is zero (0).

**Return value:** If the element is found in the specified typedArray, it returns a boolean value true, or else it will revert false.

Code #1:

```
<script> 
  
    // Creating some typedArrays 
    const A = new Uint8Array([ 1, 2, 3, 4, 5 ]); 
    const B = new Uint8Array([ 5, 10, 15, 20 ]); 
    const C = new Uint8Array([ 0, 2, 4, 6,, 8, 10 ]); 
    const D = new Uint8Array([ 1, 3, 5, 7, 9 ]); 
  
    // Calling include() function 
    a = A.includes(2) 
    b = B.includes(15, 1) 
    c = C.includes(6) 
    d = D.includes(9, 1) 
  
    // Printing true or false, either the element 
    // is present in the typedArray or not 
    document.write(a + "<br>"); 
    document.write(b + "<br>"); 
    document.write(c + "<br>"); 
    document.write(d); 
  
</script> 
```

Output:

```
true
true
true
true
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
    a = A.includes(6) 
    b = B.includes(21, 1) 
    c = C.includes(6, 4) 
    d = D.includes(0) 
  
    // Printing true or false, either the element 
    // is present in the typedArray or not 
    document.write(a + "<br>"); 
    document.write(b + "<br>"); 
    document.write(c + "<br>"); 
    document.write(d); 
  
</script> 
```

Output:

```
false
false
false
false
```