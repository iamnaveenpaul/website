---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.toString()
categories: JavaScript-typedArray
---

The typedArray.toString() is a JavaScript built-in function used to convert tyepdArray content to string.

**Syntax:**

`typedarray.toString()`

**Parameters:**

No parameters are recognized by this method.

**Return value:**

It returns a string representing the typedArray elements.

Code #1:

```
<script> 
  
    // Constructing a new typedArray Uint8Array() object 
    const A = new Uint8Array([5, 10, 15, 20, 25, 30, 35]); 
  
    // Converting the elements of typedArray 
    // object into string 
    const B = A.toString(); 
  
    // Printing converted string 
    document.write(B); 
     
</script> 
```

Output:

`5,10,15,20,25,30,35`

Code #2:

```
<script> 
  
    // Constructing a new typedArray Uint8Array() object 
    const A = new Uint8Array(["Griva", "CSE", "GrivaForCoding"]); 
  
    // Converting the elements of typedArray 
    // object into string 
    const B = A.toString(); 
  
    // Printing converted string 
    document.write(B); 
     
</script> 
```

Output:

`0,0,0`

The output here is zero since the content of the typedArray shouldn't be a string, but numbers.