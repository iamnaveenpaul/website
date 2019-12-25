---
image: "/assets/default-social-image.png"
title: Map.delete() In JavaScript
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

**Map.delete() Method in JavaScript**

The JavaScript Map.delete() method is used to remove the specified element from all the elements present in the map.

The function Map.delete() takes the key to be deleted from the map, deleting the element associated with that key and returning true. If the key is not available, it's going to return false.

**Applications:**

Map.delete() is used to delete one of the elements present in the map corresponding with the key.

**Syntax:**

`my_map.delete(key)`

**Parameters Used:**

Key: This key element is to be removed from the map.

**Return value:**

The Map.delete() method returns true, otherwise it returns false if the key is present whose associated element is to be removed and passed as an argument.

Examples:

```
Input :  my_map.set(1, 'first');
         my_map.set(2, 'second');
         my_map.set(3,'third');
         my_map.set(4,'fourth');

         document.write(my_map.delete(3));

Output : true
```

Explanation: In the map element associated with it, the key '3' is removed and returned true

```
Input :  my_map.set(1, 'first');
         my_map.set(2, 'second');
         my_map.set(3,'third');
         my_map.set(4,'fourth');
   
         document.write(my_map.delete(5));

Output : false
```

Explanation: There is no key '5' in the map which returns false.

**Code 1:**

```
<script> 
// creating a map object 
var my_map = new Map(); 
  
// Adding [key, value] pair to the map 
my_map.set(1, 'first'); 
my_map.set(2, 'second'); 
my_map.set(3,'third'); 
my_map.set(4,'fourth'); 
  
// will display true as key '3' 
// is present and its associated   
// element is removed as well 
document.write(my_map.delete(3),"</br>","</br>"); 
  
  
// elements left in the map after deletion 
document.write("key-value pair of the map", 
                " after deletion-","</br>"); 
  
my_map.forEach(function (item, key, mapObj)  
{  
    document.write(key.toString(),":", 
                   " ",item.toString() + "<br />");  
});  
  
</script> 
```

Output:

```
true

key-value pair of the map after deletion-
1: first
2: second
4: fourth
```

**Code 2:**

```
<script> 
// creating a map object 
var my_map = new Map(); 
  
// Adding [key, value] pair to the map 
my_map.set(1, 'first'); 
my_map.set(2, 'second'); 
my_map.set(3,'third'); 
my_map.set(4,'fourth'); 
  
// will display false as key '5' 
// is not present and its associated   
// element is removed as well 
document.write(my_map.delete(5), 
               "</br>","</br>"); 
  
// elements left in the map after deletion 
document.write("key-value pair of the map", 
               " after deletion-","</br>"); 
  
my_map.forEach(function (item, key, mapObj) {  
    document.write(key.toString(),":"," ", 
                   item.toString() + "<br />");  
});  
  
</script> 
```

Output:

```
false

key-value pair of the map after deletion-
1: first
2: second
3: third
4: fourth
```

**Error and Exception:**

If the key passed to the method as an argument is not present in the map, it will return false. It essentially does not throw any exception or create some error.

**Difference in working of Map.clear(),Map.erase() and this function**

Map.clear() removes the map's key value pairs and decreases the map's size to zero. Although Map.erase() removes the stated mapped value that passes the key as an argument or iterator or in range for pair removal.