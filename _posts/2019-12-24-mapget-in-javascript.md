---
title: Map.get() In JavaScript
image: "/assets/default-social-image.png"
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

**Map.get() Method in JavaScript**

* JavaScript's Map.get() method is used to retrieve a particular element among all the elements present in a map.
* The function Map.get() takes the key of the returned element as an argument and returns the element associated with the passed key as an argument. If the passed key is not present in the map as an argument, then the function Map.get() returns undefined.

**Applications:**

Map.get() function is used to retrieve a specific element of all the elements in a map.

**Syntax:**

`mapObj.get(key)`

**Parameters Used:**

Key: This will be the key of the map element to return.

**Return Value:**

Function Map.get() returns the element associated with the passed key as an argument or undefined if the passed key is not present in the map.

Examples:

```
Input : var myMap = new Map();
        myMap.set(0, 'ThisIsMyWorld');
        document.write(myMap.get(0));

Output: "ThisIsMyWorld"
```

Explanation: a map object "myMap" with a single [key, value] pair was generated in this case, and the Map.get() method is used to retrieve the element associated with the key '0'.

```
Input : var myMap = new Map();
        myMap.set(0, 'griva');
        myMap.set(1, 'is an online portal');
        myMap.set(2, 'for geeks');
        document.write(myMap.get(0),"<br>");
        document.write(myMap.get(2),"<br>");
        document.write(myMap.get(4),"<br>");

Output: "griva"
         "for geeks"
          undefined
```

Explanation: a map object "myMap" with three [key, value] pairs was generated in this case, and the Map.get() method is used to retrieve the elements associated with the keys ‘0’, ‘2’ and ‘4’. Explanation: a map object "myMap" with three [key, value] pairs was generated in this case, and the Map.get() method is used to retrieve the elements associated with the keys ‘0’, ‘2’ and ‘4’. Map.get() returns undefined when the transferred key is '4' because the map does not contain the value '4'.

**Code 1:**

```
<script> 
    // creating a map object 
    var myMap = new Map(); 
  
// Adding [key, value] pair to the map 
myMap.set(0, 'thisismyworld'); 
  
// displaying the element which is associated with 
// the key '0' using Map.get() method 
document.write(myMap.get(0)); 
  
</script> 
```

Output :

`"thisismyworld"`

**Code 2:**

```
<script> 
  
    // creating a map object 
    var myMap = new Map(); 
  
// Adding [key, value] pair to the map 
myMap.set(0, 'griva'); 
myMap.set(1, 'is an online portal'); 
myMap.set(2, 'for geeks'); 
  
// displaying the elements which are associated with the keys '0', '2'  
// and '4' using Map.get() method 
document.write(myMap.get(0),"</br>"); 
document.write(myMap.get(2),"</br>"); 
document.write(myMap.get(4),"</br>"); 
  
</script> 
```

Output :

```
"griva"
"for geeks"
undefined
```

**Exceptions :**

* If the variable is not of the type Map then a TypeError will be thrown by the Map.get() operation.
* If the index stated in the function Map.get() does not belong to the pairs [key, value] of a map, the function Map.get() returns undefined.