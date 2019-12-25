---
image: "/assets/default-social-image.png"
title: Map.entries() In JavaScript
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

**Map.entries() Method in JavaScript**

* The JavaScript Map.entries() method is used to return an iterator object that contains all the pairs of [key, value] of each map element. It returns the [key, value] pairs in the order of their insertion of all the elements of a map.
* The function Map.entries() doesn't involve passing any argument and returns the map's iterator object.

**Applications:**

We use the Map.entries() method whenever we want to get all the [key, value] pairs of each element in a map using an iterator object.

**Syntax:**

`mapObj.entries()`

**Parameters Used:**

It does not include the passage of any parameters.

**Return Value:**

The Map.entries() function returns in the order of its entry of the [key, value] pairs of all the elements of a map.

Example:

```
Input : var myMap = new Map();
        myMap.set(0, 'griva');
        myMap.set(1, 'is an online portal');
        myMap.set(2, 'for geeks');
        var iterator_obj=myMap.entries();
        document.write(iterator_obj.next().value,"<br>");
        document.write(iterator_obj.next().value,"<br>");
        document.write(iterator_obj.next().value,"<br>");


Output : Array [0, "griva"]
         Array [1, "is an online portal"]
         Array [2, "for geeks"]
```

Explanation: a map object "myMap" has been generated with three [key, value] pairs and an iterator object "iterator_obj" has been created using the Map.entries() function to return the [key, value] pairs of all the map elements in the order of their inclusion.

**Code 1:**

```
<script> 
    // creating a map object 
    var myMap = new Map(); 
  
// Adding [key, value] pair to the map 
myMap.set(0, 'griva'); 
myMap.set(1, 'is an online portal'); 
myMap.set(2, 'for geeks'); 
  
// creating an iterator object using Map.entries() method 
var iterator_obj = myMap.entries(); 
  
// displaying the [key, value] pairs of all the elements of the map 
document.write(iterator_obj.next().value,"</br>"); 
document.write(iterator_obj.next().value,"</br>"); 
document.write(iterator_obj.next().value,"</br>"); 
  
</script> 
```

Output :

```
     Array [0, "griva"]
     Array [1, "is an online portal"]
     Array [2, "for geeks"]
```

**Code 2:**

```
<script> 
    // creating a map object 
    var myMap = new Map(); 
  
// Adding [key, value] pair to the map 
myMap.set(0, 'Maps'); 
myMap.set(1, 'in JavaScript'); 
  
// creating an iterator object using Map.entries() method 
var iterator_obj = myMap.entries(); 
  
// displaying the [key, value] pairs of all the elements of the map 
document.write(iterator_obj.next().value,"</br>"); 
document.write(iterator_obj.next().value,"</br>"); 
  
</script> 
```

Output :

```
     Array [0, "Maps"]
     Array [1, "in JavaScript"]
```

**Exceptions :**

* If the variable is not of the type Map then a TypeError will be thrown by the Map.entries() method.
* The Map.entries() process returns undefined for all those instances if the "iterator_obj.next().value" is used more often than the [key, value] pairs of a map.

Reference: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/entries](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/entries)