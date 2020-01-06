---
image: "/assets/default-social-image.png"
title: JavaScript Sort() method
categories: JavaScript-array
---

The array.sort() is a JavaScript built-in function used to sort the array. An array of any kind can be string, numbers, characters, etc.

**Syntax:**

`array.sort()`

The array here is the set of values to be sorted.

**Parameters:** This acknowledges no parameters.

**Return values:** This doesn't return anything.

Examples:

```
Input:  var arr = ["Manish", "Rishabh", "Nitika", "Harshita"];
Output: Harshita, Manish, Nitika, Rishabh

Input: var arr = [1, 4, 3, 2];
Output: 1, 2, 3, 4
```

Code #1: Sorting an array of strings:

```
<html> 
  
<body> 
    <p>Click on the Sort button to sort the array</p> 
  
    <!-- button for click event --> 
    <!-- onclick event is generated when the button is clicked --> 
    <p id="demo"></p> 
  
    <script> 
  
        <!-- array of names --> 
        var names = [" Manish", " Rishabh", " Nitika", " Harshita"]; 
        document.getElementById("demo").innerHTML = names; 
  
        <!-- sortAlphabet function that sort above array alphabetically --> 
        function sortAlphabet() { 
            names.sort(); 
            document.getElementById("demo").innerHTML = names; 
        } 
    </script> 
  
     <button onclick="sortAlphabet()"> Sort </button> 
</body> 
  
</html> 
```

Code #2: Sorting an array of integers:

```
<html> 
   
<body> 
    <p>Click on the Sort button to sort the array</p> 
   
    <!-- button for click event --> 
    <!-- onclick event is generated when the button is clicked--> 
    <p id="demo"></p> 
  
    <script> 
  
       <!-- array numbers --> 
       var numbers = [7, 1, 6, 9, 2]; 
       document.getElementById("demo").innerHTML = numbers; 
  
    <!-- sortNumber function that sort the array --> 
    function sortNumber() { 
        numbers.sort(); 
        document.getElementById("demo").innerHTML = numbers; 
        } 
    </script> 
  
     <button onclick="sortNumber()"> Sort </button> 
</body> 
   
</html> 
```