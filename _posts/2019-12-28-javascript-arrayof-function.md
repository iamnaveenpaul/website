---
image: "/assets/default-social-image.png"
title: JavaScript Array.of() function
categories: JavaScript-array
---

The array.of() method is a JavaScript built-in function that creates a new array instance of variables present as the function's argument.

**Syntax:**

`Array.of(element0, element1, ....)`

**Parameters:**

There are parameters of element0, element1, .... Which are basically the elements for which the array is produced.

**Return Value:**

It just returns a new instance of the Array.

Examples:

```
Input: Array.of(10, 20, 30)
Output: > Array [10, 20, 30]
```

**Explaination:**

Numbers are converted to an array representing the same argument shown in the output in the input arguments of the array.of() function.

```
Input: Array.of("Ram","Geeta")
Output: > Array ["Ram", "Geeta"]
```

**Explaination:**

Here in the array.of() method input arguments string is converted into an array representing the same argument shown in the output.

```
//  Here the Array.of() method creates a new Array instance with  
// a variable number of arguments, regardless of 
// number or type of the arguments. 
console.log(Array.of(0, 0, 0)); 
console.log(Array.of(11, 21, 33)); 
console.log(Array.of("Ram","Geeta")); 
console.log(Array.of('geeksforgeeks')); 
console.log(Array.of(2,3,4,'Sheeta')); 
```

Output:

```
> Array [0, 0, 0]
> Array [11, 21, 33]
> Array ["Ram", "Geeta"]
> Array ["geeksforgeeks"]
> Array [2, 3, 4, "Sheeta"]
```

**Application:**

We use the Array.of() function in JavaScript whenever we need to get elements of any array every time.

`console.log(Array.of(['Ram', 'Rahim', 'Geeta', 'Sheeta'])); `

Output:

`> Array [Array ["Ram", "Rahim", "Geeta", "Sheeta"]]`