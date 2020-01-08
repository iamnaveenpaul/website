---
image: "/assets/default-social-image.png"
title: Must use JavaScript Array Functions – Part 1
categories: JavaScript-array
---

We will discuss the following two JavaScript array functions in this article

* Array.prototype.every()
* Array.prototype.some()

Both of these functions are commonly used in industry and make the Javascript code easy to understand, tidy and modularized.

**Array.prototype.every()**

**Description:** The function Array.every() is used when validating each element in a given array. Array.every() accepts as an argument a callback function that is called for each element of the array. The callback function must return a true or a false. If all array elements satisfy the validation function and therefore callback function returns true to all array elements, then Array.every() returns true otherwise, it returns false as soon as it detects the first element that fails to satisfy the validator function.

**Syntax :**

`arr.every(callback[,thisArg])`

**Parameters :**

* **callback :** Function to be called for each array element arr
* **-currentValue:** The value of the elements currently being processed
* **-index(optional):** Index of the currentValue element in the 0-point array
* **-array(optional):** The complete array that is called by Array.every
* **thisArg (optional):** Context to be passed as this for use during the execution of the callback function. When context is passed, it will be used as this for any callback function invocation, else the default would be undefined.

**Sample Use Case:**

1. To check that each integer array element is less than 100
2. To check whether each element in the array has a particular type of data, such as string.

Examples

1. Write a function, given an array, to check whether or not all elements in that array are less than 100.

So, as shown below, the naive approach is to use the for loop.

```
function fnIsLEssThan100_loop(arr){ 
  for(var i = 0 ; i < arr.length; i ++){ 
      if(arr[i] >= 100){ 
          return false; 
      } 
  } 
  return true; 
} 
function fnIsLEssThan100_loop([30,60,90]); 
function fnIsLEssThan100_loop([30,60,90,120]); 
```

Output:

```
true
false
```

Although the above specification is simple for any inexperienced programmer to grasp, there are some redundant tests to be taken care of by the programmer. For example, the short circuit mechanism, i.e. the programmer, must explicitly ensure that the loop should break and return false as soon as the loop encounters the first element that fails the condition. Also, others will not be able to understand what this for loop is doing until and unless that programmer dives deep into the code logic. But with the use of Array.every(), with much clearer, intuitive and less code, the same behavior can be achieved.

```
function fnIsLesThan100_Every(arr){ 
   return arr.every(function(element){ 
            return(element < 100): 
           }); 
} 
  
fnIsLesThan100_Every([30,60,90]) 
fnIsLesThan100_Every([30,60,90,120]) 
```

Output:

```
true
false
```

2. Write a function to check if all elements in that array are of a defined type of data, provided an array.

Again, the naive approach is to use the for loop.

```
function fnCheckDatatype_loop(arr. sDatatype){ 
    for(var i = 0 ; i < arr.length; i ++){ 
      if(typeof(arr[i]) !== sDatatype){ 
          return false; 
} 
  
 fnCheckDatatype_loop(["Geeks","for","Geeks"],"string") 
 fnCheckDatatype_loop(["Geeks",4,"Geeks"],"string") 
```

Output

```
true
false
```

The code snippet above has the same loopholes as the example above. In the code snippet below, these loopholes are taken care of again using arr. Every(). Another point to note is that we send two arguments to the array.every() method in the code snippet below. The first is the callback function (in our case anonymous function) and the second is the sDatype function. Because in every call of callback function we need an external variable, we pass it as 'this' variable as a second argument.

```
function fnCheckDatatype_Every(arr, sDatatype){ 
   return arr.every(function(element){ 
            return typeof(element) === sDatatype; 
           },sDatatype); 
} 
  
fnCheckDatatype_loop(["Geeks","for","Geeks"],"string") 
 fnCheckDatatype_loop(["Geeks",4,"Geeks"],"string") 
```

Output

```
true
false
```

**Array.prototype.some()**

**Description:** The Array.some() function of the JavaScript array is in a manner opposite to Array.every(). The function Array.some() is used when it is necessary to check whether at least one element of a specified array passes the callback function test. Array.some() recognizes a callback method as an argument for returning either a true or a false value.

**Syntax :**

`Array.some(callback[,thisArg])`

**Parameters :**

* **callback :** Function to be called for each array element arr
* **-currentValue:** The value of the elements currently being processed
* **-index(optional):** Index of the currentValue element in the 0-point array
* **-array(optional):** The complete array that is called by Array.some()
* **thisArg (optional):** Context to be passed as this for use during the execution of the callback function. When context is passed, it will be used as this for any callback function invocation, else the default would be undefined.

**Sample Use Case:**

1. To check that each integer array element is less than 100
2. To check if there are any even elements in the array.

Examples

1. Write a function, given an array, to check whether or not all elements in that array are less than 100.

Naive Approach

```
function fnIsGreaterThan100_loop(arr){ 
    for(var i = 0 ; i < arr.length; i ++){ 
      if(arr[i] > 100){ 
          return true; 
      } 
   } 
   return false; 
} 
  
fnIsGreaterThan100_loop([30,60,90,120]); 
fnIsGreaterThan100_loop([30,60,90]); 
```

Output

```
true
false
```

**Using Array.some()**

```
function fnIsGreaterThan100_some(arr){ 
     return arr.some(function(element){ 
            return(element . 100): 
     }); 
} 
  
fnIsGreaterThan100_some([30,60,90,120]); 
fnIsGreaterThan100_some([30,60,90]); 
```

Output

```
true
false
```

Write a function, given an array, to check if the array contains an even number.

Naive approach

```
function fnIsEven_loop(arr){ 
    for(var i = 0 ; i < arr.length; i ++){ 
      if(arr[i] % 2 === 0){ 
          return true; 
      } 
    } 
    return false; 
} 
  
fnIsEven_loop([1,3,5]); 
fnIsEven_loop([1,3,5,6]); 
```

Output

```
false
true
```

**Using Array.some()**

```
function fnIsEven_some(arr){ 
       return arr.some(function(element){ 
            return(element %2 === 0): 
       }); 
} 
  
fnIsEven_some([1,3,5]); 
fnIsEven_some([1,3,5,6]); 
```

Output

```
false
true
```

One of the common mistakes programmers make when using array functions such as Array.every() and Array.some() is forgetting to return the value in the callback function. Keep it in mind that if you don't return any value from the callback function, it returns null, which is interpreted as false.

It is also important to know that ECMAScript 5 introduced these array functions. In IE9 or higher, these functions are supported. If you also need to use it for older browsers, a library such as underscore.js can come to your rescue with an equivalent implementation of these functions.

Additionally, if you wish to dive deeper into the above functions, you can refer to following official links

1. [http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.16](http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.16)
2. [http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.17](http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.17)