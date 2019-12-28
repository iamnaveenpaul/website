---
image: "/assets/default-social-image.png"
title: JavaScript Array.findIndex() Method
categories: JavaScript-array
---

It returns the first element index in a specified array that satisfies the testing purpose provided. If not -1 is returned.

Once it detects an element that satisfies the testing function, it does not perform the mechanism.
The original array is not changed.

**Syntax:**

`array.findIndex(function(currentValue, index, arr), thisValue)`

**Parameters:**

* **function:** A function to run in the array for each element
* **currentValue:** The existing element's value.
* **index:** The current element's array index
* **array:** It belongs to the object array with the current element
* **thisValue:** A value to be passed as its "this" value to the function to be used.

If this parameter is empty, it will pass the value "undefined" as its value for "this"

**Return value:**

If any of the elements in the array pass the test, it returns the array element index otherwise it returns -1.

**JavaScript Version:**

ECMAScript 6

**Browser Support:**

The version of the related feature browser is included in the 2nd column int values.

```
FEATURE	BASIC SUPPORT
Chrome	45
Edge	Yes
Firefox	25
Internet Explorer	No
Opera	32
Safari	8
Android webview	Yes
Chrome for Android	Yes
Edge mobile	Yes
Firefox for Android	4
Opera Android	Yes
iOS Safari	8
```

Example 1:

```
function isOdd(element, index, array) {
  return (element%2 == 1);
}

print([4, 6, 8, 12].findIndex(isOdd)); 
```

Output:

`-1`

The findIndex() function finds all the indices containing odd numbers in this scenario. So, since there are no odd numbers, it returns -1.

Example 2:

```
function isOdd(element, index, array) {
  return (element%2 == 1);
}

print([4, 6, 7, 12].findIndex(isOdd)); 
```

Output:

`2`

The findIndex() function finds all the indices containing odd numbers in this case. So, because 7 is an odd number, it returns its index 2.

Program:

Here in JavaScript, the Array.findIndex() function returns the index of the first element in the array that satisfies the test function given. If not, -1 is returned.

```
// input array contain some elements whose index 
// need to find which satisfy the provided  
// testing function (element > 25). 
var array = [ 10, 20, 30, 110, 60 ]; 
  
// calling function for testing. 
function finding_index(element)  
{ return element > 25; } 
  
// Printing the index of element which is satisfies 
// the provided testing function (element > 25) 
console.log(array.findIndex(finding_index)); 
```

Output:

`> 2`

Application:

This Array.findIndex() function can be used to find a prime number (or return -1 if there is no prime number) index of an element in the array.

```
// function isPrime is used to find which 
// number is prime or not prime. 
function isPrime(n) { 
  if (n === 1) { 
    return false; 
  } else if (n === 2) { 
    return true; 
  } else { 
    for (var x = 2; x < n; x++) { 
      if (n % x === 0) { 
        return false; 
      } 
    } 
    return true; 
  } 
} 
  
// Printing -1 because prime number is not found. 
console.log([ 4, 6, 8, 12 ].findIndex(isPrime)); 
  
// Printing 2 the index of prime number (7) found. 
console.log([ 4, 6, 7, 12 ].findIndex(isPrime)); 
```

Output:

```
> -1
> 2
```