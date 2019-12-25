---
image: "/assets/default-social-image.png"
title: Map.clear() In JavaScript
categories: JavaScript-functions
---

**What is a map in JavaScript?**

* Map is a JavaScript data structure that enables [key, value] pairs to be stored in which any value can be used either as a key or as a value.
* The keys and values in the collection of maps can be of any type and if a value is added to the collection of maps using a key that already appears in the set, the new value would replace the old value.
* Element iteration in a map object is performed in the insertion order and a "for..." loop returns for each iteration an array of all [key, value] pairs.

**Differences between Objects and Maps in JavaScript**

Each of these data structures are similar in many ways, such as using keys to both store values, allowing those values to be retrieved using keys, deleting keys and checking whether a key holds any value or not. Though, there are quite substantial differences in JavaScript between objects and maps which in many cases make the use of maps a better and preferable option.

The keys for use in maps may be any kind of values such as functions, objects, and so on, while the keys in objects are restricted to symbols and strings.
The size of a map can be easily known using the size property, but it is necessary to manually determine the size while dealing with objects.
A map should be chosen in situations where the condition includes repeated insertion and removal of [key, value] pairs because a map is an iterative data type that can be immediately iterated when iterating an object demands that its keys be retrieved in a specific way.

**Map.clear() Method in JavaScript**

The JavaScript Map.clear() method is used to remove and empty all the elements from a map. It eliminates from the map all the [key, value] attributes. There is no need to provide arguments to the Map.clear() method as parameters, it returns an undefined value.

**Syntax:**

`mapObj.clear()`

**Parameters Used:**

The Map.clear() method requires no parameters.

**Return Value:**

Map.clear() has an undefined type of return.

Examples:

```
Input : var myMap = new Map();
        myMap.set(0, 'thisismyworld');
        console.log(myMap.size);
        myMap.clear();
        console.log(myMap.size);

Output: 1
        0
```

Explanation: a map object "myMap" with a single [key, value] pair was generated in this case, and the Map.clear() method is used to delete the [key, value] pair from "myMap." MyMap.size() is used to test the map object's number of [key, value] pairs.

```
Input : var myMap = new Map();
        myMap.set(0, 'griva');
        myMap.set(1, 'is an online portal');
        myMap.set(2, 'for geeks');
        console.log(myMap.size);
        myMap.clear();
        console.log(myMap.size);
Output : 3
         0
```

Explanation: a map object "myMap" with three [key, value] pairs was generated in this case, and the Map.clear() method is used to delete all [key, value] pairs from "myMap." MyMap.size() is used to test the map object's number of [key, value] pairs.

**Code 1:**

```
<script> 
  
    // creating a map object 
    var myMap = new Map(); 
  
// Adding [key, value] pair to the map 
myMap.set(0, 'geeksforgeeks'); 
  
// displaying the number of  
// [key, value] pairs the map has 
document.write(myMap.size); 
document.write("<br>"); 
  
// removing the [key, value] pairs of 
// the map using Map.clear() method 
myMap.clear(); 
  
// displaying the number of  
// [key, value] pairs the map has 
document.write(myMap.size); 
  
</script> 
```

OUTPUT :

```
1
0
```

**Code 2:**

```
<script> 
    // creating a map object 
    var myMap = new Map(); 
  
// Adding [key, value] pair to the map 
myMap.set(0, 'geeksforgeeks'); 
myMap.set(1, 'is an online portal'); 
myMap.set(2, 'for geeks'); 
  
// displaying the number of  
// [key, value] pairs the map has 
document.write(myMap.size); 
document.write("<br>"); 
  
// removing the [key, value] pairs 
// of the map using Map.clear() method 
myMap.clear(); 
  
// displaying the number of 
// [key, value] pairs the map has 
document.write(myMap.size); 
  
< /script> 
```

OUTPUT :

```
3
0
```

**Applications:**

Map.clear() is used to remove all of a map's [key, value] pairs.

Example:

```
<script> 
  
    // creating a map object 
    var myMap = new Map(); 
  
// Adding [key, value] pair to the map 
myMap.set(0, 'Maps'); 
myMap.set(1, 'in JavaScript'); 
  
// displaying the number of 
// [key, value] pairs the map has 
document.write(myMap.size); 
document.write("<br>"); 
  
// removing the [key, value] pairs of 
// the map using Map.clear() method 
myMap.clear(); 
  
// displaying the number of  
// [key, value] pairs the map has 
document.write(myMap.size); 
  
<script> 
```

OUTPUT :

```
     2
     0
```

**Exceptions :**

If the variable is not Map type then a TypeError will be thrown by the Map.entries() operation. 

**Reference:** [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/clear](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/clear)