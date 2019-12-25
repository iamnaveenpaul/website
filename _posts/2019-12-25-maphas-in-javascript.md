---
image: "/assets/default-social-image.png"
title: Map.has() In JavaScript
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

**Map.has() Method in JavaScript**

JavaScript's Map.has() method is used to test whether or not there is an element with a given key in a map. It returns a boolean value signaling an element with a given key in a map's presence or absence.

The function Map.has() takes as an argument the key of the element to be checked and returns a boolean value. If the element occurs in the map, it returns true, otherwise it returns false if there is no element.

**Applications:**

Map.has() method can be used to test whether or not there is an element with a given key in a map.

**Syntax:**

`mapObj.has(key)`

**Parameters Used:**

Key: This is the key of the map element to be looked out for.

**Return Value:**

The function Map.has() returns a boolean value. If the element appears in the map, it returns true, otherwise it returns false if there is no element.

Examples:

```
Input : var myMap = new Map();
        myMap.set(0, 'griva');
        console.log(myMap.has(0));
        
Output: true
```

Explanation: a map object "myMap" with a single [key, value] pair was generated in this case, and the Map.has() method is used to test whether or not an element with the key '0' exists in the map.

```
Input : var myMap = new Map();
        myMap.set(0, 'griva');
        myMap.set(1, 'is an online portal');
        myMap.set(2, 'for geeks');
        console.log(myMap.has(0));
        console.log(myMap.has(3));

Output: true
        false
```

Explanation: a map object "myMap" with three [key, value] pairs was generated in this case, and the Map.has() function is used to test whether or not an element with the key ' 0 ' and ' 3 ' occurs in the map.

**Code 1:**

```
<script> 
    // creating a map object 
    var myMap = new Map(); 
  
// Adding [key, value] pair to the map 
myMap.set(0, 'griva'); 
  
// displaying whether an element with the key '0' exists in the map or not 
// using Map.has() method 
console.log(myMap.has(0)); 
  
< /script> 
```

OUTPUT :

`true`

**Code 2:**

```
<script> 
    // creating a map object 
    var myMap = new Map(); 
  
// Adding [key, value] pair to the map 
myMap.set(0, 'griva'); 
myMap.set(1, 'is an online portal'); 
myMap.set(2, 'for geeks'); 
  
// displaying whether an element with the key '0' and '3' exists in 
// the map or not using Map.has() method 
console.log(myMap.has(0)); 
console.log(myMap.has(3)); 
  
< /script> 
```

OUTPUT :

```
true
false
```

**Reference:** [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/has](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/has)