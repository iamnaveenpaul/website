---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.from()
categories: JavaScript-typedArray
---

The typedArray.from() is a built-in function in JavaScript that is used from a regular array or any iterable object to build a new typedArray.

Below is a list of different typedArrays:

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

`typedArray.from(source, mapFn, thisArg)`

**Parameters:**

It accepts three parameters specified below:

* **source:** To convert to a typedArray, it is a regular array or any iterable object.
* **mapFn:** It is optional, and calling on each element of the typedArray is a map function.
* **thisArg:** It is optional and the value to use when performing the mapFn function.

**Return value:**

It returns a new instance of typedArray.

Code #1:

```
<script> 
  
    // Constructing an iterable object 
    var a = new Set([ 5, 10, 15, 20, 25 ]); 
    var b = new Set([ 1, 2, 3, 4, 5 ]); 
    var c = new Set([ 1, 3, 5, 7, 9 ]); 
    var d = new Set([ 2, 4, 6, 8, 10 ]); 
  
    // Calling from() function 
    A = Uint8Array.from(a); 
    B = Uint8Array.from(b); 
    C = Uint8Array.from(c); 
    D = Uint8Array.from(d); 
  
   // Printing new typedArray instance 
    document.write(A + "<br>"); 
    document.write(B + "<br>"); 
    document.write(C + "<br>"); 
    document.write(D); 
  
</script> 
```

Output:

```
5, 10, 15, 20, 25
1, 2, 3, 4, 5
1, 3, 5, 7, 9
2, 4, 6, 8, 10
```

Code #2:

```
<script> 
  
    // Calling from() function 
    A = Uint16Array.from('123456'); 
    B = Uint16Array.from('80397418327'); 
  
    // Printing new typedArray instance 
    document.write(A + "<br>"); 
    document.write(B + "<br>"); 
  
</script> 
```

Output:

```
1, 2, 3, 4, 5, 6
8, 0, 3, 9, 7, 4, 1, 8, 3, 2, 7
```

Code #3:

```
<script> 
  
    // Constructing an iterable object 
    var a = new Set([ 5, 10, 15, 20, 25 ]); 
    var b = new Set([ 1, 2, 3, 4, 5 ]); 
    var c = new Set([ 1, 3, 5, 7, 9 ]); 
    var d = new Set([ 2, 4, 6, 8, 10 ]); 
  
    // Calling from() function 
    A = Uint8Array.from(a, x => x + 1); 
    B = Uint8Array.from(b, x => x + 2); 
    C = Uint8Array.from(c, x => x * 2);   
    D = Uint8Array.from(d); 
  
    // Printing new typedArray instance 
   document.write(A + "<br>"); 
   document.write(B + "<br>"); 
   document.write(C + "<br>"); 
   document.write(D); 
  
</script> 
```

Output:

```
6, 11, 16, 21, 26
3, 4, 5, 6, 7
2, 6, 10, 14, 18
2, 4, 6, 8, 10
```