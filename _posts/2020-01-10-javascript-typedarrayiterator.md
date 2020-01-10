---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.@@iterator
categories: JavaScript-typedArray
---

The typedArray.@@iterator is an built-in property in JavaScript that is used to return the initial value of the element of the specified typedArray.

**Syntax:**

`arr[Symbol.iterator]()`

**Parameters:**

It accepts no parameters because it is a function, not a property.

**Return value:**

It returns the default value() function of the array iterator.

Example:

```
<script> 
  
    // Constructing a new typedArray with some elements 
    var A = new Uint8Array([ 5, 10, 15, 20, 25 ]); 
  
   // Calling iterator() function 
    var a = A[Symbol.iterator](); 
  
    // Printing each value of the typedArray 
    document.write(a.next().value + "<br>"); 
    document.write(a.next().value + "<br>"); 
    document.write(a.next().value + "<br>"); 
    document.write(a.next().value + "<br>"); 
    document.write(a.next().value); 
  
</script> 
```

Output:

```
5
10
15
20
25
```