---
image: "/assets/default-social-image.png"
title: JavaScript Array.from() method
categories: JavaScript-array
---

**Introduction:**

The function Array.from() is a built-in function in JavaScript that creates from a given array a new array instance. In the case of a string, each string alphabet is translated to an element of the new array instance and in the case of integer values, the elements of the specified array are taken from the new array instance.

**Syntax 1 :**

```
**Array.from(A)**
**A:**
A can be an array to convert to an array or string where each string alphabet is to be transformed to a new array instance element.
```

**Syntax 2 :**

```
**Array.from(mapFn,thisArg)**
**Parameters:**
**mapFn (Optional):** Map function to call each of the array elements.
**thisArg (Optional):** Use value as this when running mapFn.
```

**Return value:** returns a new instance of the Array whose elements are identical to the specified array. Each string alphabet is converted to an element of the new array instance in the case of string.

**Browser Support:**

```
FEATURE	BASIC SUPPORT
Chrome	45
Edge	Yes
Firefox	32
Internet Explorer	No
Opera	Yes
Safari	9
Chrome for Android	Yes
Edge mobile	Yes
Firefox for Android	32
Opera Android	Yes
iOS Safari	Yes
```

Examples:

```
Input : griva
Output : Array ["g", "r", "i", "v", "a"]
```

```
Input : 10, 20, 30
Output :  Array [10, 20, 30]
```

There as we see that output creates a new array whose content is the same as input in the case of integer, but in the case of string, and string alphabet is transformed to a new array instance element.

```
console.log(Array.from("griva")); 
console.log(Array.from([10, 20, 30])); 
```

Output:

```
> Array ["g", "r", "i", "v", "a"]
> Array [10, 20, 30]
```

**Errors and Exceptions:**

When we take complex number as the parameter, it returns error because the parameter can only be taken as array and string.

```
// When the complex number is used as the function parameter, it will return an error. 
console.log(Array.from(1+2i)); 
```

Output:

`Error: Invalid or unexpected token`

**Application:**

We can use the Array.from() method in javaScript whenever we need to do any opearation with the array elements that time.

```
// Here input array is [1,2,3] and output become bouble of each elements. 
console.log(Array.from([1, 2, 3], x => x + x)); 
```

Output:

`> Array [2, 4, 6]`