---
image: "/assets/default-social-image.png"
title: JavaScript array.values()
categories: JavaScript-array
---

The array.values() function is a built-in function in JavaScript that is used to return a new Iterator array object that contains the values for each index in the array, i.e. it prints all of the array elements.

**Syntax:**

`arr.values()`

**Return values:**

It returns a new object of the array iterator i.e. elements of the array provided.

Examples:

Inpu```
t:
A = ['a', 'b', 'c', 'd']
Output:
a, b, c, d
Here as we see that input array contain some 
elements and in output same elements get printed.
```

// Input array contain some elements```
 
var A = [ 'Ram', 'Z', 'k', 'griva' ]; 
  
// Here array.values() function is called. 
var iterator = A.values(); 
  
// All the elements of the array the array  
// is being printed. 
console.log(iterator.next().value); 
console.log(iterator.next().value); 
console.log(iterator.next().value); 
console.log(iterator.next().value); 
```

Output:

`> Ram, z, k, griva`

**Application:**

JavaScript uses this array.values() method to print the elements of the specified array.

```
// Input array contain some elements. 
var array = [ 'a', 'gfg', 'c', 'n' ]; 
  
// Here array.values() function is called. 
var iterator = array.values(); 
  
// Here all the elements of the array is being printed. 
for (let elements of iterator) { 
  console.log(elements); 
} 
```

Output:

`> a, gfg, c, n`