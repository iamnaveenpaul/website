---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.@@species
categories: JavaScript-typedArray
---

The typedArray.@@species is a built-in attribute in JavaScript that is used to retrieve the typedArray constructor.

The typedArray is like many different types

* Int8Array
* Uint8Array
* Uint8ClampedArray
* Int16Array
* Uint16Array
* Int32Array
* Uint32Array
* Float32Array
* Float64Array

**Syntax:**

`typedArray[Symbol.species]`

**Parameters:**

It accepts no parameters because it is not a function but a property.

**Return value:**

It returns the given typedArray's constructor.

Example:

```
<script> 
  
    // Calling species property on different typedArray 
    a = Int8Array[Symbol.species]; 
    b = Uint8Array[Symbol.species]; 
    c = Uint8ClampedArray[Symbol.species]; 
    d = Int16Array[Symbol.species]; 
    e = Uint16Array[Symbol.species]; 
    f = Int32Array[Symbol.species]; 
    g = Uint32Array[Symbol.species]; 
    h = Float32Array[Symbol.species]; 
    i = Float64Array[Symbol.species]; 
  
    // Printing the constructor of the given typedArray 
    document.write(a + "<br>"); 
    document.write(b + "<br>"); 
    document.write(c + "<br>"); 
    document.write(d + "<br>"); 
    document.write(e + "<br>"); 
    document.write(f + "<br>"); 
    document.write(g + "<br>"); 
    document.write(h + "<br>"); 
    document.write(i); 
  
</script> 
```

Output:

```
function Int8Array() { [native code] }
function Uint8Array() { [native code] }
function Uint8ClampedArray() { [native code] }
function Int16Array() { [native code] }
function Uint16Array() { [native code] }
function Int32Array() { [native code] }
function Uint32Array() { [native code] }
function Float32Array() { [native code] }
function Float64Array() { [native code] }
```