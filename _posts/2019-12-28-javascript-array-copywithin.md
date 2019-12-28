---
image: "/assets/default-social-image.png"
title: JavaScript Array copyWithin()
categories: JavaScript-array
---

The copyWithin() method copies and returns part of an array to the same array without changing its size, i.e. copies array element within the same array.

**Syntax:**

`array.copyWithin(target, start, end)`

**Parameters:**

**target :** The index position to copy to (Required) the elements.

**start :** The index position to, to be used is optional. Start copying elements from  (default is 0).

**end :** The index position to, to be used is optional. Stop copying elements from (default is array.length).

**Return value:**

It returns the array that was modified.

**JavaScript Version : **

ECMAScript 6

**Browser Support:**

```
Chrome   45.0
Edge     12.0
Firefox     32.0
Opera     32.0
IE       No
```

Examples

Program 1:

```
// Input array 
var array = [ 1, 2, 3, 4, 5, 6, 7 ]; 
  
// placing at index position 0 the element  
// between index 3 and 6 
console.log(array.copyWithin(0, 3, 6)); 
Output:

Array [4, 5, 6, 4, 5, 6, 7]
```

Program 2:

```
// Input array 
var array = [ 1, 2, 3, 4, 5, 6, 7 ]; 
  
// placing from index position 0 the  
// element from index 4 
console.log(array.copyWithin(0, 4)); 
```

Output:

`Array [5, 6, 7, 4, 5, 6, 7]`

Program 3:

```
// Input array 
var array = [ 1, 2, 3, 4, 5, 6, 7 ]; 
  
// placing from index position 3  
// the element from index 0 
console.log(array.copyWithin(3)); 
```

Output:

`Array [1, 2, 3, 1, 2, 3, 4]`

**Application:**

When we use array.copyWithin() feature in javaScript to copy the output of any array to the same array.

```
// Input array 
var array = [ 1, 2, 3, 4, 5, 6, 7 ]; 
  
// placing at index position 0 the 
// element between index 4 and 5 
console.log(array.copyWithin(0, 4, 5)); 
```

Output:

`Array [5, 2, 3, 4, 5, 6, 7]`