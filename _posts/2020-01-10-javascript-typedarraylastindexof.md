---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.lastIndexOf()
categories: JavaScript-typedArray
---

The typedArray.lastIndexOf() is a built-in function in JavaScript that is used to return the last index of the typedArray that contains a specified element, or else it reverts -1 if the element is not available.

Syntax:

`typedArray.lastIndexOf(search_Element, from_Index])`

**Parameters:**

This accepts the following two parameters:

* **search_Element:** It is the element that must be searched for the last index.
* **from_Index:** It is optional and is the index to check for an element and its default value is the typedArray length.

**Return value:**

It returns the last index of the typedArray where there is a given element, else it reverts -1 if there is no element.

Code #1:

```
<script> 
  
  // Creating a typedArray with some elements 
  var A = new Uint8Array([5, 10, 15, 15, 5, 20, 10]); 
    
  // Calling lastIndexOf() function 
  b = A.lastIndexOf(10);      
  c = A.lastIndexOf(5);      
  d = A.lastIndexOf(15);   
  e = A.lastIndexOf();   
  f = A.lastIndexOf(20);  
  g = A.lastIndexOf(25);  
    
  // Printing returned values 
  document.write(b +"<br>"); 
  document.write(c +"<br>"); 
  document.write(d +"<br>"); 
  document.write(e +"<br>"); 
  document.write(f +"<br>"); 
  document.write(g +"<br>"); 
    
</script> 
```

Output:

```
6
4
3
-1
5
-1
```

Code #2:

```
<script> 
  
  // Creating a typedArray with some elements 
  var A = new Uint8Array([5, 10, 15, 15, 5, 20, 10]); 
    
  // Calling lastIndexOf() function 
  b = A.lastIndexOf(10, 1);      
  c = A.lastIndexOf(5, 2);      
  d = A.lastIndexOf(15, 3);   
  e = A.lastIndexOf(15, 1);   
  f = A.lastIndexOf(20, 1);  
  g = A.lastIndexOf(25, 3);  
    
  // Printing returned values 
  document.write(b +"<br>"); 
  document.write(c +"<br>"); 
  document.write(d +"<br>"); 
  document.write(e +"<br>"); 
  document.write(f +"<br>"); 
  document.write(g +"<br>"); 
    
</script> 
```

Output:

```
1
0
3
-1
-1
-1
```