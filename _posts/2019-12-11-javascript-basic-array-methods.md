---
image: "/assets/default-social-image.png"
title: JavaScript Basic Array Methods
categories: JavaScript-arrays
---

In JavaScript, it is advised to go thru the Arrays. Now we would examine the role of the following function of array:

**#1. Array.push() :**

Adding Element to an Array at the end. Because array is a mutable entity in JavaScript, we may easily add or remove elements from the array. And as we alter the elements from the list, it changes dynamically.

**Syntax :**

Array.push(item1, item2 …)

Parameters: Items to be added to an array.

Description: At the end of an array, this process is used to add elements.

```
// Adding elements at the end of an array 
// Declaring and initializing arrays 
var number_arr = [ 10, 20, 30, 40, 50 ]; 
var string_arr = [ "piyush", "gourav", "smruti", "ritu" ]; 
  
// push() 
// number_arr contains [10, 20, 30, 40, 50, 60] 
number_arr.push(60); 
  
// We can pass multiple parameters to the push() 
// number_arr contains 
// [10, 20, 30, 40, 50, 60, 70, 80, 90] 
number_arr.push(70, 80, 90); 
  
// string_arr contains 
// ["piyush", "gourav", "smruti", "ritu", "sumit", "amit"]; 
string_arr.push("sumit", "amit"); 
  
// Printing both the array after performing push operation 
console.log("After push op " + number_arr); 
console.log("After push op " + string_arr); 
```

**#2. Array.unshift() :**

To add elements on the front of an array

**Syntax :**

Array.unshift(item1, item2 …)

Parameters: Items to be added to the array

Description: This approach is used at the beginning of an array to add elements to it.

```
// Adding element at the beginning of an array 
// Declaring and initializing arrays 
var number_arr = [ 20, 30, 40 ]; 
var string_arr = [ "amit", "sumit" ]; 
  
// unshift() 
// number_arr contains 
// [10, 20, 20, 30, 40] 
number_arr.unshift(10, 20); 
  
// string_arr contains 
// ["sunil", "anil", "amit", "sumit"] 
string_arr.unshift("sunil", "anil"); 
  
// Printing both the array after performing unshift operation 
console.log("After unshift op " + number_arr); 
console.log("After unshift op " + string_arr); 
```

**#3. Array.pop() :**

Remove elements from the end of an array

**Syntax:**

Array.pop()

Parameters: It has no parameter to take.

Description: It is used at the end of an array to remove array elements.

```
// Removing elements from the end of an array 
// Declaring and initializing arrays 
var number_arr = [ 20, 30, 40, 50 ]; 
var string_arr = [ "amit", "sumit", "anil" ]; 
  
// pop() 
// number_arr contains 
// [ 20, 30, 40 ] 
number_arr.pop(); 
  
// string_arr contains 
// ["amit", "sumit"] 
string_arr.pop(); 
  
// Printing both the array after performing pop operation 
console.log("After pop op " + number_arr); 
console.log("After popo op " + string_arr); 
```

**#4. Array.shift() :**

Removing of elements at the start of an array

**Syntax :**

Array.shift()

Parameter : It has no parameter to take.

Description : Removing elements at the beginning of an array.

```
// Removing element from the beginning of an array 
// Declaring and initializing arrays 
var number_arr = [ 20, 30, 40, 50, 60 ]; 
var string_arr = [ "amit", "sumit", "anil", "prateek" ]; 
  
// shift() 
// number_arr contains 
//  [30, 40, 50, 60]; 
number_arr.shift(); 
  
// string_arr contains 
// ["sumit", "anil", "prateek"] 
string_arr.shift(); 
  
// Printing both the array after performing shifts operation 
console.log("After shift op " + number_arr); 
console.log("After shift op " + string_arr); 
```

**#5. Array.splice() :**

Insertion and Removal within an array

**Syntax:**

Array.splice (start, deleteCount, item 1, item 2….) 

Parameters:  

Start : Location where an operation can be carried out

deleteCount: Number of elements to be removed

Pass 0 If there is no element to be removed

Item1, item2 …..- an optional parameter . 

The elements to be inserted from the start of the location

Description: Splice is a very useful method because from the specific location it can remove and add elements.

```
// Removing an adding element at a particular location 
// in an array 
// Declaring and initializing arrays 
var number_arr = [ 20, 30, 40, 50, 60 ]; 
var string_arr = [ "amit", "sumit", "anil", "prateek" ]; 
  
// splice() 
// deletes 3 elements starting from 1 
// number array contains [20, 60] 
number_arr.splice(1, 3); 
  
// doesn't delete but inserts 3, 4, 5 
// at starting location 1 
number_arr.splice(1, 0, 3, 4, 5); 
  
// deletes two elements starting from index 1 
// and add three elements. 
// It contains  ["amit", "xyz", "geek 1", "geek 2", "prateek"]; 
string_arr.splice(1, 2, "xyz", "geek 1", "geek 2"); 
  
// Printing both the array after performing splice operation 
console.log("After splice op " + number_arr); 
console.log("After splice op " + string_arr); 
```

JavaScript provides multiple array features, see the references given below:

[Functions Part 1](https://www.geeksforgeeks.org/must-use-javascript-array-functions-part-1/)
[Functions Part 2](https://www.geeksforgeeks.org/must-use-javascript-array-functions-part-2/)
[Functions Part 3](https://www.geeksforgeeks.org/must-use-javascript-array-functions-part-3/)

Note: You may check all the above definitions by entering them in the HTML script tag or directly into the console of the browser.

**Recommended Posts:**

[JavaScript | Array Iteration Methods](https://www.geeksforgeeks.org/javascript-array-iteration-methods/)
[Understanding basic JavaScript codes.](https://www.geeksforgeeks.org/understanding-basic-javascript-codes/)
[JavaScript | Get Date Methods](https://www.geeksforgeeks.org/javascript-get-date-methods/)
[JavaScript | Object Methods](https://www.geeksforgeeks.org/javascript-object-methods/)
[JavaScript | Set Date Methods](https://www.geeksforgeeks.org/javascript-set-date-methods/)
[JavaScript methods to increment/decrement alphabetical letters](https://www.geeksforgeeks.org/javascript-methods-to-increment-decrement-alphabetical-letters/)
[How to compare two JavaScript array objects using jQuery/JavaScript ?](https://www.geeksforgeeks.org/how-to-compare-two-javascript-array-objects-using-jquery-javascript/)
[How to get the elements of one array which are not present in another array using JavaScript?](https://www.geeksforgeeks.org/how-to-get-the-elements-of-one-array-which-are-not-present-in-another-array-using-javascript/)
[How to check whether an array is subset of another array using JavaScript ?](https://www.geeksforgeeks.org/how-to-check-whether-an-array-is-subset-of-another-array-using-javascript/)
[What’s the difference between “Array()” and “[]” while declaring a JavaScript array?](https://www.geeksforgeeks.org/whats-the-difference-between-array-and-while-declaring-a-javascript-array/)
[JavaScript | Array pop()](https://www.geeksforgeeks.org/javascript-array-prototype-pop/)
[RMS Value Of Array in JavaScript](https://www.geeksforgeeks.org/rms-value-of-array-in-javascript/)
[JavaScript | Array unshift()](https://www.geeksforgeeks.org/javascript-array-prototype-unshift-function/)
[JavaScript | Array concat()](https://www.geeksforgeeks.org/javascript-array-prototype-concat-function/)
[JavaScript | Array copyWithin()](https://www.geeksforgeeks.org/javascript-array-copywithin/)