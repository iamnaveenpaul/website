---
image: "/assets/default-social-image.png"
title: JavaScript array.entries() Method
categories: JavaScript-array
---

The array.entries() is a JavaScript built-in function that is used to get a new array that includes the key and value pairs for each array index.

**Syntax:**

`array.entries();`

**Return value:**

It returns an index array and values of the specified array that will function with array.entries().

**Browser Support:**

The 2nd column here includes int values which are the corresponding browser version.

```
FEATURE	BASIC SUPPORT
Chrome	38
Edge	Yes
Firefox	28
Internet Explorer	No
Opera	25
Safari	8
Android webview	Yes
Chrome for Android	Yes
Edge mobile	Yes
Firefox for Android	28
Opera Android	Yes
iOS Safari	8
```

Examples:

Here is the function array.entries() in javaScript used in any specified array to locate key and value pairs for each index.

```
var array = [\'griva\', \'gfg\', \'Jhon\']; 
var iterator = array.entries(); 
  
// expected output: Array [0, \"griva\"] 
console.log(iterator.next().value); 
  
// expected output: Array [1, \"gfg\"] 
console.log(iterator.next().value); 
  
// expected output: Array [2, \"Jhon\"] 
console.log(iterator.next().value); 
```

Output:

```
> Array [0, \"griva\"]
> Array [1, \"gfg\"]
> Array [2, \"Jhon\"]
```

**Application:**

Whenever in any array we use array.entries() method to get key and value pairs for each index

```
var array = [\'griva\', \'gfg\', \'Jhon\']; 
var iterator = array.entries(); 
  
// printing key and value pair from the given 
// array using for loop. 
for (let e of iterator) { 
  console.log(e); 
} 
```

Output:

```
> Array [0, \"griva\"]
> Array [1, \"gfg\"]
> Array [2, \"Jhon\"]
```