---
image: "/assets/default-social-image.png"
title: Must use JavaScript Array Functions – Part 2
categories: JavaScript-array
---

We discussed two array functions, namely Array.Prototype.Every() and Array.prototype.some(), in Must use Javascript Array Functions–Part 1. It is important to note that the array elements were accessed by both of these functions but did not modify/change the array itself. Today we will look at two array methods that modify the array and return the modified array.

**Array.Prototype.filter()**

**Description:** Array.prototype.filter() is used to obtain a new array that only contains those array elements that pass the callback function test. It accepts as an argument a callback function. This callback function will return a true or a false answer. The newly returned array will be added to the elements for which the callback function returned true.

**Syntax:**

`arr.filter(callback[, thisArg])`

**Parameters:**

* **callback :** Function to be called for each array element arr
* **-currentValue:** The value of the elements currently being processed
* **-index(optional):** Index of the currentValue element in the 0-point array
* **-array(optional):** The complete array that is called by Array.prototype.filter()
* **thisArg:** Context to be passed as this for use during the execution of the callback function. When context is passed, it will be used as this for any callback function invocation, else the default would be undefined.

**Sample use Cases:**

1. Scenario where all null values have to be removed from an array by the user.
2. Scenario where the user is required to filter the array based on the value of a particular object property in the array.

Example:

1. Function to filter out students with scores of more than 80%.

Naive Method using loop

```
<script> 
    function fnFilterStudents_loop(aStudent){ 
        var tempArr = []; 
        for(var i = 0 ; i< aStudent.length; i ++){ 
            if(aStudent[i].fPercentage > 80.0){ tempArr.push(aStudent[i]);} 
            } 
        return tempArr; 
    } 
    aStudent = [ 
        {sStudentId : "001" , fPercentage : 91.2}, 
        {sStudentId : "002" , fPercentage : 78.7}, 
        {sStudentId : "003" , fPercentage : 62.9}, 
        {sStudentId : "004" , fPercentage : 81.4}]; 
          
    console.log(fnFilterStudents_loop(aStudent)); 
</script> 
```

Output:

```
[{sStudentId : "001" , fPercentage : 91.2},
{sStudentId : "004" , fPercentage : 81.4}];
```

**Using Array.prototype.filter()**

```
<script> 
    function fnFilterStudents_filter(aStudent){ 
        return aStudent.filter(function(oStudent){ 
            return oStudent.fPercentage > 80.0 ? true : false; 
              
        }); 
    } 
    aStudent = [ 
        {sStudentId : "001" , fPercentage : 91.2}, 
        {sStudentId : "002" , fPercentage : 78.7}, 
        {sStudentId : "003" , fPercentage : 62.9}, 
        {sStudentId : "004" , fPercentage : 81.4}]; 
          
    console.log(fnFilterStudents_filter(aStudent)); 
</script> 
```

Output:

```
[{sStudentId : "001" , fPercentage : 91.2},
{sStudentId : "004" , fPercentage : 81.4}];
```

2. Function for removing undefined elements from an array

```
<script> 
    function removeUndefined(myArray){ 
        return myArray.filter(function(element, index, array){ 
            return element; 
        }); 
    } 
      
    var arr = [1,undefined,3,undefined,5]; 
      
    console.log(arr); 
      
    console.log( removeUndefined(arr)); 
</script> 
```

Output:

```
[1,undefined,3,undefined,5];
[1,3,5];
```

We return element directly in the callback function of the above case. So if the element has value, it will be treated as true, and if it is undefined, it will automatically be treated as false.

**Array.Prototype.map()**

**Description:** Array.prototype.map() is used according to the callback function to modify each element of the array. Array.prototype.map() in the order of each element in the array calls the callback function once. The point to note is that callback function is invoked on element indexes that have assigned value including undefined.

**Syntax:**

`arr.map(callback[, thisArg])`

**Parameters:**

* **callback :** Function to be called for each array element arr
* **-currentValue:** The value of the elements currently being processed
* **-index(optional):** Index of the currentValue element in the 0-point array
* **-array(optional):** The complete array that is called by Array.prototype.map()
* **thisArg:** Context to be passed as this for use during the execution of the callback function. When context is passed, it will be used as this for any callback function invocation, else the default would be undefined.

**Sample use Cases:**

1. Scenario in which the user has to reduce each amount by a particular tax value in an array
2. Scenario where the user in an existing array of objects has to create a new property of each object.

Example:

1. Function to add to each object in the array, the property bIsDistinction.

**Using Loop**

```
<script> 
    function fnAddDistinction_loop(aStudent){ 
        for(var i = 0 ; i< aStudent.length; i ++){ 
            aStudent[i].bIsDistinction = (aStudent[i].fPercentage >= 75.0) ? true : false; 
            } 
        return aStudent; 
    } 
    aStudent = [ 
        {sStudentId : "001" , fPercentage : 91.2}, 
        {sStudentId : "002" , fPercentage : 78.7}, 
        {sStudentId : "003" , fPercentage : 62.9}, 
        {sStudentId : "004" , fPercentage : 81.4}]; 
           
    console.log(fnAddDistinction_loop(aStudent)); 
</script> 
```

Output:

```
[{sStudentId : "001" , fPercentage : 91.2 , bIsDistiction : true},
 {sStudentId : "002" , fPercentage : 78.7 , bIsDistiction : false},
 {sStudentId : "003" , fPercentage : 62.9 , bIsDistiction : false},
 {sStudentId : "004" , fPercentage : 81.4 , bIsDistiction : true}];
```

**Using Array.prototype.map()**

```
<script> 
    function fnAddDistinction_map(aStudent){ 
        return aStudent.map(function(student, index, array){ 
            aStudent.bIsDistinction = (aStudent.fPercentage >= 75.0) ? true : false; 
            return aStudent; 
        }); 
    } 
    aStudent = [ 
        {sStudentId : "001" , fPercentage : 91.2}, 
        {sStudentId : "002" , fPercentage : 78.7}, 
        {sStudentId : "003" , fPercentage : 62.9}, 
        {sStudentId : "004" , fPercentage : 81.4}]; 
           
    console.log(fnAddDistinction_map(aStudent)); 
</script> 
```

Output:

```
[{sStudentId : "001" , fPercentage : 91.2 , bIsDistiction : true},
 {sStudentId : "002" , fPercentage : 78.7 , bIsDistiction : false},
 {sStudentId : "003" , fPercentage : 62.9 , bIsDistiction : false},
 {sStudentId : "004" , fPercentage : 81.4 , bIsDistiction : true}];
```

2. Scenario that uses Array.prototype.Map() with standard functions for JavaScript.

For example, using Math.sqrt to calculate each element's square root in an array or to parse floating string values.

```
[1,4,9].map(Math.sqrt); // Output : [1,2,3] 
["1.232","9.345","3.2345"].map(parseFloat) // Output : [1.232, 9.345, 3.2345] 
```

One has to be careful when using standard functions for Array.prototype.map(), because something like this can happen.

```
["1","2","3"].map(parse.Int); 
//Output : [1, NaN, NaN] 
```

How did NaN returned for the code snippet above? It occurred because the function parseInt takes two arguments, the first being the object to be parsed to Integer and the second being the radix that serves as the base for conversion. If we use it for Array.prototype.map(), although the element is the first argument, the second argument is the index of the array element currently being handled. The index being 0 is passed to parseInt as a radix for the first iteration, which defaults to 10 and thus you see the first element successfully parsed. It gets messed up afterwards. Below is the fix for the above.

```
["1","2","3"].map(function(val{return parseInt(val,10)}); 
// output : [1, 2, 3] 
```

All code snippets used in this article can be found under: [https://github.com/hjaintech/GeeksForGeeks/blob/master/Array_Functions_2.html](https://github.com/hjaintech/GeeksForGeeks/blob/master/Array_Functions_2.html)

As shown in the examples above, for loops can be used to implement both Array.prototype.filter() and Array.prototype.map(). But we're trying to work on very specific use cases in the above scenarios. Keep a variable counter, then check the length of the array and then spike the counter variable. Keeping these things in mind is not just a concern, but it also makes code prone to bugs. For instance, developers will unintentionally misspell "array.length" as "array.lenght." The best way to avoid code glitches is to reduce the number of tasks you keep track of manually, as a rule of thumb. And that's exactly what these array functions do.

Browser support is really good for these functions, but as these array functions were introduced in ECMAScript 5 they are still not supported in IE8 or below. If you also need to use it for older browsers, you can use either es5-shim or any library like Underscore or Lodash that has an equivalent utility function can come to your rescue.

You can also refer to the following official links if you want to dive deeper into the above functions.
1. [http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.20](http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.20)
2. [http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.19](http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.19)