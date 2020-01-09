---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.name
categories: JavaScript-typedArray
---

The typedArray.name is a built-in property in JavaScript that is used to represent a string value of the given name of the typedArray constructor.

Below is a collection of different types of arrays.

* Int8Array();
* Uint8Array();
* Uint8ClampedArray();
* Int16Array();
* Uint16Array();
* Int32Array();
* Uint32Array();
* Float32Array();
* Float64Array();

**Syntax:**

`typedArray.name;`

**Parameters:**

It acknowledges no parameters because it is not a function but a property.

**Return value:**

It returns a string value of the name of the given array constructor.

Example:

```
<script> 
  
    // Returning the string value of the given 
    // typedArray constructor name. 
    document.write(Int8Array.name + "<br>"); 
    document.write(Uint8Array.name + "<br>"); 
    document.write(Uint8ClampedArray.name + "<br>"); 
    document.write(Int16Array.name + "<br>"); 
    document.write(Uint16Array.name + "<br>"); 
    document.write(Int32Array.name + "<br>"); 
    document.write(Uint32Array.name + "<br>"); 
    document.write(Float32Array.name + "<br>"); 
    document.write(Float64Array.name); 
  
</script> 
```

Output:

```
Int8Array
Uint8Array
Uint8ClampedArray
Int16Array
Uint16Array
Int32Array
Uint32Array
Float32Array
Float64Array
```