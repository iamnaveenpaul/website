---
image: "/assets/default-social-image.png"
title: JavaScript Spread Operator
categories: JavaScript-operators
---

Spread operator helps an iterable to expand in positions that anticipate 0+ arguments. It is mostly used in variable array where there are supposed to be more than 1 values. It helps us to get a set of parameters from an array. The Spread operator syntax is the same as the Rest parameter but it operates in the opposite way.

Syntax:

`var variablename1 = [...value]; `

is a spread operator in the above syntax that will target all values in specific variable. When... happens in a call or equivalent function, it is considered a spread operator. In many instances, such as when we want to extend, copy, concat, with math object., Spread operator can be used. Let's look one by one at each of them:

**Concat()**

Javascript's concat() method helps to concatenate two or more strings (String concat()) or is used to merge two or more arrays. This method does not change the existing arrays in the case of arrays, but rather returns a new array.

```
// normal array concat() method 
let arr = [1,2,3]; 
let arr2 = [4,5]; 
  
arr = arr.concat(arr2); 
  
console.log(arr); // [ 1, 2, 3, 4, 5 ] 
```

With the aid of the spread operator, we can achieve the same output, the code would look like this:

```
// spread operator doing the concat job 
let arr = [1,2,3]; 
let arr2 = [4,5]; 
  
arr = [...arr,...arr2]; 
console.log(arr); // [ 1, 2, 3, 4, 5 ] 
```

Note: Although we can achieve the same result, in this particular case it is not recommended to use the spread as a large data set will work slower than the native concat() method.

**Copy(like splice method)**

We can do something like this to transfer the content of the array to another:

```
// copying without the spread operator 
let arr = ['a','b','c']; 
let arr2 = arr; 
  
console.log(arr2); // [ 'a', 'b', 'c' ] 
```

The above code works fine given that we can transfer the contents of one array to another, but it's very different under the hood as it will also impact the old array (the one we copied) as we mutate new array. See the following code:

```
// changed the original array 
let arr = ['a','b','c']; 
let arr2 = arr; 
  
arr2.push('d'); 
  
console.log(arr2); 
console.log(arr); // even affected the original array(arr)  
```

In the above code, we can easily see that the initial array is also altered because we attempted to inject an element inside the array, something we did not intend to do and is not advised. In this case, we can use the spread operator as follows:

```
// spread operator for copying  
let arr = ['a','b','c']; 
let arr2 = [...arr]; 
  
console.log(arr); // [ 'a', 'b', 'c' ] 
  
arr2.push('d'); //inserting an element at the end of arr2 
  
console.log(arr2); // [ 'a', 'b', 'c', 'd' ] 
console.log(arr); // [ 'a', 'b', 'c' ] 
```

We made sure that the initial array is not affected if we adjust the new array by using the spread operator.

**Expand**

We do something like this whenever we want to extend an array into another:

```
// normally used expand method 
let arr = ['a','b']; 
let arr2 = [arr,'c','d']; 
  
console.log(arr2); // [ [ 'a', 'b' ], 'c', 'd' ] 
```

And though we get the content inside the other array, it's just an array inside another array which is obviously not what we expected. We can use the spread operator if we want the content to be within a single array.

```
// expand using spread operator 
  
let arr = ['a','b']; 
let arr2 = [...arr,'c','d']; 
  
console.log(arr2); // [ 'a', 'b', 'c', 'd' ] 
```

**Math**

The Javascript Math object has different properties that we can use to do what we want, such as finding the minimum from a number set, finding the maximum, etc. Consider the situation that from a list of numbers we want to locate the least, we'll compose something like this:

`console.log(Math.min(1,2,3,-1)); //-1  `

Now assume that we have an array instead of a list, this procedure above will not operate and will return NaN

```
// min in an array using Math.min() 
let arr = [1,2,3,-1]; 
console.log(Math.min(arr)); //NaN 
```

When ... arr is used in the call function, an iterable object "expands" into the argument list

We use the spread operator to avoid this NaN output, such as:

```
// with spread  
let arr = [1,2,3,-1]; 
  
console.log(Math.min(...arr)); //-1 
```