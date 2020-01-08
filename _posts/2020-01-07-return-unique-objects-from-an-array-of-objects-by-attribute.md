---
image: "/assets/default-social-image.png"
title: Return unique objects from an array of objects by attribute.
categories: JavaScript-array
---

The goal here is to extract the unique object by the attribute given an array of objects.

Examples:

Input: 
[ { name: 'Griva', id: 10 },
  { name: 'GrivaForCoding', id: 10 },
  { name: 'Griva', id: 20 },
  { name: 'Griva', id: 10 } ]
Output:
[ { name: 'Griva', id: 10 }, 
  { name: 'GrivaForCoding', id: 10 } ]

**Approach:**

Let's presume the name is an attribute that distinguishes objects and allows an object with a minimum id number if there are several objects for the same name. Use the map to store objects and test whether or not they have seen similar objects.

* Set up an empty map.
* Iterate using the filter method through the array.
* Check whether there is an entry with the same name in the map as the current object.
* -If it's true: i.e. the same name entry exists, check if the id is less than the current object id.
* --If it's true i.e. the current object id is less than the map returned object id, then remove the map entry and insert the current object and return true.
* ---if false: i.e. the present object id is greater than the map-returned object id, and then it returns false.
* --if false: i.e. no map entry with the same name is inserted into the map of the current object.
* Print unique objects.

Example:

```
<script> 
objects = [{ 
    name: 'Griva', 
    id: 10 
}, { 
    name: 'GrivaForCoding', 
    id: 10 
}, { 
    name: 'Griva', 
    id: 20 
}, { 
    name: 'Griva', 
    id: 10 
}]; 
  
let mymap = new Map(); 
  
unique = objects.filter(el => { 
    const val = mymap.get(el.name); 
    if(val) { 
        if(el.id < val) { 
            mymap.delete(el.name); 
            mymap.set(el.name, el.id); 
            return true; 
        } else { 
            return false; 
        } 
    } 
    mymap.set(el.name, el.id); 
    return true; 
}); 
  
console.log(unique); 
</script> 
```

Output:

```
[ { name: 'Griva', id: 10 }, 
  { name: 'GrivaForCoding', id: 10 } ]
Time Complexity: O(n)
Space Complexity: O(n)
```