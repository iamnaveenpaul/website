---
image: "/assets/default-social-image.png"
title: Must use JavaScript Array Functions – Part 3
categories: JavaScript-array
---

We will discuss the following JavaScript array functions in this article

1. prototype.reduce()
2. prototype.concat()
3. prototype.sort()
4. prototype.reverse()

**Array.Prototype.reduce()**

**Description:** When the user has to iterate over a JavaScript array and minimize it to a single value, the function Array.prototype.reduce() is used. For each value in the array, a callback function is called from left to right. The value returned by the callback function is available as an argument for the callback function for the next element. If the initialValue is not provided, the callback function of the reduction is called directly on the 2nd element with the passing of the first element as previousValue. If the array is empty and there is no initial value, a TypeError will be thrown.

**Syntax:**

`arr.reduce(callback[, initialValue])`

**Parameters:**

callback: callback function to be invoked for each array element arr

* **previousValue:** value returned by the call or initial value of the previous function.
* **currentValue:** Value of the currently processing array element.
* **currentIndex:** Index of the currently processing array element.
* **array:** The original reduction array is called.
* **initialValue(optional):** Initial value to be used as a previousValue when first time callback method is invoked.

**Sample Use Cases:**

Finding sum of an array of integers.

```
function reduceFun1(previousValue, currentValue, index, array){ 
    return previousValue + currentValue; 
} 
var result = [1,2,3,4,5].reduce(reduceFun1); 
          
console.log(result); // Output : 15 
```

Given a array of objects containing sales location addresses and finding the total sales in NY

```
var arr=[{name: "customer 1", sales: 500, location: "NY"}, 
         {name: "customer 1", sales: 200, location: "NJ"}, 
          {name: "customer 1", sales: 700, location: "NY"}, 
         {name: "customer 1", sales: 200, location: "ORD"}, 
         {name: "customer 1", sales: 300, location: "NY"}]; 
  
        function reduceFun2(previousValue, currentValue, index, array) { 
              
            if (currentValue.location === "NY") { 
                //console.log(previousValue.sales); 
                previousValue.sales =  previousValue.sales + Number(currentValue.sales); 
            } 
            return previousValue; 
        } 
  
var totalSalesInNY = arr.reduce(reduceFun2); 
  
console.log(totalSalesInNY.sales); // Output: 1500 
```

In the above example, when calling the Array.reduce() on arr, an initial value0 is provided. In this case, the initial integer value must be provided. This is because the previousValue variable must have an integer value and not an entire object for each iteration of the callback function. If we don't pass the initialValue as 0, then the preceding value becomes the whole object for the first iteration and attempts to add an integer value to it, giving junk output.

**2. Array.prototype.concat()**

**Description:** Array.prototype.concat() is used with another array/value to concatenate an array. It does not alter the current array but returns a modified array instead. This considers all new ranges and values as an argument that it fits with the method calling array and returns the corresponding array.

**Syntax:**

`NewArray = Array1.concat(value1[, value2[, ...[, valueN]]])`

**Parameters:**

**valueN :** New array or value to be concatenated to Array1.

**Sample Use Case:**

Concatenate 2 integer arrays:

```
var arr1 = [1,2,3,4]; 
var arr2 = [5,6,7,8]; 
var arr3 = arr1.concat(arr2); 
console.log(arr3); // Output :  [1, 2, 3, 4, 5, 6, 7, 8] 
```

Concatenate 3 integer arrays:

```
var arr1 = [1,2,3,4]; 
var arr2 = [5,6]; 
var arr3 = [7,8]; 
var arr4 = arr1.concat(arr2,arr3); 
console.log(arr4); // Output :  [1, 2, 3, 4, 5, 6, 7, 8] 
```

Concatenate an array with individual integer values:

```
var arr1 = [1,2,3,4]; 
var arr2 = arr1.concat(5,6,7,8); 
console.log(arr2); // Output :  [1, 2, 3, 4, 5, 6, 7, 8] 
```

Concatenate an array with another array and other multiple values:

```
var arr1 = [1,2,3,4]; 
var arr2 = [5,6]; 
var arr3 = arr1.concat(arr2, 7, 8); 
console.log(arr3); // Output :  [1, 2, 3, 4, 5, 6, 7, 8] 
```

**3. Array.prototype.sort()**

**Description:** For sorting an array, Array.prototype.sort() is used. It accepts a compareFunction optional argument that defines the criteria to determine which element of the array is small and which is larger. The FunctionCompare supports two arguments i.e. the values being compared. When value1 is lower then a negative value should be returned to the comparing function. If value2 is lower, a positive value should be returned by compareFunction. In the absence of a comparison function, the default compareFunction transforms the array elements to strings and then compares certain strings in Unicode point order.

**Syntax:**

`arr.sort([compareFunction])`

**Parameters:**

CompareFunction (optional): Sort order function.

**Sample Use Case:**

Sort a simple integer array:

```
var arr = [3, 1, 5, 4, 2].sort(); 
console.log(arr); // Output : [1, 2, 3, 4, 5] 
```

Sort a string array:

```
var arr = ["Orange", "Apple", "Banana"].sort(); 
console.log(arr); // Output : ["Apple", "Banana", "Orange"] 
```

Sort another integer array:

```
var arr = [1, 30, 5].sort(); 
console.log(arr); // Output : [1, 30, 5] 
```

The order of the sorted array resulting here is not correct. This is because it converts all integers into strings as we use the default sortFunction and then compares them based on their Unicode value. Hence the incorrect sort order from 30 < 5 in Unicode.

Sort the integer array using sort function:

```
function sortFun(a,b){ 
    return a - b; 
} 
var arr = [1, 30, 5].sort(sortFun); 
console.log(arr); // Output : [1, 5, 30] 
```

There, the order is right since we did not use the default sortFunction, but rather our own sortFunction, which compares the integer values to evaluate the order.

Sort an object array using sort function:

```
var arr = [{name:"NY",  count: 20}, 
           {name:"NJ",  count: 5}, 
           {name:"JFK", count: 60}, 
           {name:"ORD", count: 1}]; 
function sortFun(obj1, obj2){ 
    return obj1.count - obj2.count; 
} 
arr.sort(sortFun); 
console.log(arr);  // Output [{name:"ORD",  count: 1}, 
                      //         {name:"NJ",  count: 5}, 
                      //         {name:"NY", count: 20}, 
                      //         {name:"JFK", count: 60}] 
```

**4. Array.prototype.reverse()**

**Description:** For reverse a JavaScript array, Array.prototype.reverse() is used. Reverse() modifies the calling array itself and returns a reference to the array that is now reversed.

**Syntax:**

`array.reverse()`

**Parameters:**

No parameters

**Sample Use Case:**

```
var arr = [1,2,3,4,5,6,7,8,9,10]; 
arr.reverse(); 
console.log(arr); //Output : [10, 9, 8, 7, 6, 5, 4, 3, 2, 1] 
```

All code snippets used in this article can be found at
[https://github.com/hjaintech/GeeksForGeeks/blob/master/Array_Functions_3.html](https://github.com/hjaintech/GeeksForGeeks/blob/master/Array_Functions_3.html)

Additionally, you can refer to the following links if you want to dive deeper into the above functions.

* [http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.21](http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.21)
* [http://www.ecma-international.org/ecma-262/5.1/#sec-15.5.4.6](http://www.ecma-international.org/ecma-262/5.1/#sec-15.5.4.6)
* [http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.11](http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.11)
* [http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.8](http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.8)