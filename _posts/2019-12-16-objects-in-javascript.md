---
title: Objects in Javascript
image: "/assets/default-social-image.png"
categories: JavaScript-basics
---

**Objects in Javascript**

Objects is the most important data type in JavaScript and forms the building blocks of modern JavaScript. These objects are rather distinct from the primitive data types (number, string, boolean, null, undefined, and symbol) of JavaScript in the waythat while all these primitive data types store a single value (depending on their types).

* Objects are more complicated and any mixture of these basic data types and reference data types can be found in each object.
* An object is a type of reference data. A reference or a pointer to that value is provided to variables allocated to a reference value. The reference or pointer leads to where the object is located in memory. In addition, the variables do not store the value.
* Roughly speaking, JavaScript objects can be described in the form of "key: value" pairs as an unordered set of related data primitive or reference types. These keys can be variables or functions and in the context of an object, respectively, are called properties and methods.

Figure brackets {...} can be used to build an object with an appropriate list of properties. A property is a pair of "key: value" where a key is a string (also known as a "property name") that can be anything.

Let's look at an instance of a JavaScript Object to explain this quite complex definition:

```
let school = {
    name : "Vivekananda School",
    location : "Delhi",
    established : "1971"
}
```

All **"keys"**, **"Vivekananda School"**, **"Delhi"** and **"1971"** are values of these keys respectively in the above illustration **"name"**, **"location"**, **"established"**.

Each of these keys is referred to as the object's **property**. An object in JavaScript may also have a member function, in which case it will be referred to as the object's **method**.

Example:

```
// javascript code demonstrating a simple object 
let school = { 
    name: 'Vivekananda School', 
    location : 'Delhi', 
    established : '1971', 
    displayInfo : function(){ 
        console.log(`${school.name} was established  
              in ${school.established} at ${school.location}`); 
    } 
} 
school.displayInfo();  
```

In the instance above, **"displayinfo"** is a mechanism used by the school object to interact with the information of the object, contained in its property.

**Properties of JavaScript Object**

The names of the property can be strings or numbers. If the property names are numbers, the "bracket notation" must be used as follows:

```
let school = { 
    name: 'Vivekananda School', 
    location : 'Delhi', 
    established : '1971', 
    20 : 1000, 
    displayInfo : function(){ 
        console.log(`The value of the key 20 is ${school['20']}`); 
    } 
} 
school.displayInfo();  
```

We'll explain more on the bracket notation later.

Property names can also be strings of separate words in more than one space. So in that case, it is important to include these property names inside quotes:

```
let school = {
    "school name" : "Vivekananda School",
}
```

They also need to be accessed using the bracket notation, including property names that are numbers. Like if we want access from "Vivekananda School" to the "Vivekananda", we can do:

```
// bracket notation  
let school = { 
    name: 'Vivekananda School', 
    displayInfo : function(){ 
        console.log(`${school.name.split(' ')[0]}`); 
    } 
} 
school.displayInfo(); // Vivekananda 
```

We used the bracket notation in the above code as well as the split method given by javascript that you will read about in the strings section.

**Inherited Properties**

An object's inherited properties are those properties that were inherited from the prototype of the object, as compared to being determined for the object as a whole, known as the Own property of the object. We can use the hasOwnProperty method to check if a property is an Own property object

**Property Attributes**

In JavaScript, data properties have four attributes.

* **value:** The value of the property.
* **writable:** The value of property can be changed if writable is true
* **enumerable:** By enumerating "for - in," the property can be iterated over, if the value of enumerable is true. Therefore, it is said that the property is not enumerable.
* **configurable:** Attempts to remove the property alter the property as an access-or property, or adjust its attributes (other than [[Value]], or switch [[Writable]] to false) may fail, if configurable is false.

```
// hasOwnProperty code in js 
const object1 = new Object(); 
object1.property1 = 42; 
  
console.log(object1.hasOwnProperty('property1')); // true 
```

**Creating Objects**

There's many ways to create objects, or syntaxes. One of which we have already used, recognized as the Object literal syntax. In contrast to the object literal syntax, JavaScript structures can also be generated using the constructors, the Object Constructor or the pattern of the prototype.

**1# Using the Object literal syntax:** the literal syntax of the object uses the {...} notation to initialize an object explicitly to its methods/properties.

Let's look at an instance of object formation using this method:

```
var obj = {
    member1 : value1,
    member2 : value2,
};
```

Such members can be anything: strings, numbers, functions, arrays or even other objects. An object like this is considered a object literal. This is distinct from other ways for object creation requiring the use of constructors and classes or prototypes listed below.

**#2. Object Constructor:** Using the Object constructor is another way to create structures in JavaScript. For the given value, the object constructor constructs an object wrapper. Used along with the "new" keyword, it helps us to initialize new objects.

Example :

```
const school = new Object(); 
school.name = 'Vivekanada school'; 
school.location = 'Delhi'; 
school.established = 1971; 
  
school.displayInfo = function(){ 
    console.log(`${school.name} was established  
          in ${school.established} at ${school.location}`); 
} 
  
school.displayInfo(); 
```

For programs requiring the creation of multiple objects of the same, the two methods mentioned above are not well appropriate, as it would involve repetitively writing the above lines of code for each such object. In order to address this problem, we can use two other methods of creating objects in JavaScript that significantly reduce this burden, as described below:

**#3 Constructors:** As in most other OOP languages, JavaScript constructors provide a template for object creation. In other terms, it specifies a collection of properties and methods common to all initialized objects using the constructor.

Example :

```
function Vehicle(name, maker) { 
   this.name = name; 
   this.maker = maker; 
} 
  
let car1 = new Vehicle('Fiesta', 'Ford'); 
let car2 = new Vehicle('Santa Fe', 'Hyundai') 
  
console.log(car1.name);    // Output: Fiesta 
console.log(car2.name);    // Output: Santa Fe 
```

Note the use of the "new" keyword prior to the Vehicle function. Before any function turns it into a constructor, use the "new" keyword in this way. What is done by the "new vehicle()" is:

* This creates a new object and assigns the object's constructor property to schools (it is important to note that such a property is an unique default property which can not be enumerated by defining a "constructor: someFunction" property manually).
* It then sets the object to operate with the prototype object of the `Vehicle` function (each function in JavaScript gets a prototype object that is originally only an empty entity but can be changed. The object acquires all property from the prototype object of its constructor once instantiated).
* Then calls Vehicle() in the case of the new object, which implies that it applies to the new object that was generated in the first stage when the "this" keyword is located in the constructor(vehicle)).
* The newly created object is returned to car1 and car2 (in the illustration above) once this is done.

There may be specific methods called `constructor()` inside classes.

```
class people { 
    constructor() 
    { 
        this.name = "Adam"; 
    } 
} 
  
let person1 = new people(); 
  
// Output : Adam     
console.log(person1.name); 
```

In a class with the title of constructor(), using more than one function results in an error.

**#4 Prototypes:** The use of prototypes is another way to create objects. Every JavaScript function has a default object prototype property (default empty). It is possible to attach methods or properties to this property. A comprehensive prototype definition is beyond the reach of this concept description.

You can, however, become acquainted with the simple syntax used as follows:

```
let obj = Object.create(prototype_object, propertiesObject)
          // the second propertiesObject argument is optional
```

An instance to use the form of Object.create() is:

```
let footballers = { 
    position: "Striker"
} 
   
let footballer1 = Object.create(footballers); 
   
    // Output : Striker     
console.log(footballer1.position);  
```

In the illustration above, footballers were used as a prototype to construct the "footballer1" object.

All objects generated in this way are inherited from their prototype objects by its all properties and methods. Prototypes may have prototypes, and those may have prototypes, etc. This is termed as JavaScript prototype chaining. The chain finishes with the `Object.prototype`, the standard fallback prototype for all objects. Through definition, Javascript objects inherit Object.prototype properties and methods, but these can quickly be bypassed.

It is also interesting to note that Object.prototype. For instance, strings and arrays do not always have their own default implementations–string.prototype and Array.prototype respectively.

**Accessing Object Members**

It is possible to access object members(properties or methods) using the following:

#1. dot notation:
`(objectName.memberName)`

```
let school = { 
    name : "Vivekanada", 
    location : "Delhi", 
    established : 1971, 
    20 : 1000, 
    displayinfo : function() { 
        console.log(`${school.name} was established  
          in ${school.established} at ${school.location}`); 
    } 
  
} 
  
console.log(school.name); 
  
console.log(school.established); 
```

#2. Bracket Notation :
`objectName["memberName"]`

```
let school = { 
    name : "Vivekanada School", 
    location : "Delhi", 
    established : 1995, 
    20 : 1000, 
    displayinfo : function() { 
        document.write(`${school.name} was established  
          in ${school.established} at ${school.location}`); 
    } 
} 
  
// Output : Vivekanada School 
console.log(school['name']);  
  
// Output: 1000 
console.log(school['20']);  
```

The bracket keyword works with any combination of strings, including but not limited to multi-word strings, unlike the dot notation.

Example:

```
somePerson.first name // invalid
    somePerson["first name"] // valid
```

As addition to the dot notation, the bracket notation may also include names arising from any variable expressions whose values are determined at runtime.

For instance :

`let key = "first name" somePerson[key] = "Name Surname"`

In the use of the dot notation, similar operations are not practical.

**Iterating over all keys of an object**

We can use the for...in construct to iterate over all current enumerable keys of an object. It should be remembered that this allows us to view only such properties of an object that are enumerable (remember that enumerable is one of the four characteristics of data property).

For instance, Object.prototype inherited properties are not enumerable. Nevertheless, it is also possible to access enumerable properties inherited from somewhere using the for...in construction.

Example:

```
let person = { 
    gender : "male"
} 
  
var person1 = Object.create(person); 
person1.name = "Adam"; 
person1.age = 45; 
person1.nationality = "Australian"; 
  
for (let key in person1) { 
// Output : name, age, nationality  
// and gender 
    console.log(key);  
} 
```

**Deleting Properties**

We can use the delete operator to delete an object property.

Example:

```
let obj1 = { 
    propfirst : "Name"
}  
  
// Output : Name 
console.log(obj1.propfirst);  
delete obj1.propfirst 
  
// Output : undefined 
console.log(obj1.propfirst);  
```

It is important to remember that in this way we can not delete inherited properties or non-configurable properties.

Example :

```
let obj1 = { 
    propfirst : "Name"
}  
// Output : Name 
console.log(obj1.propfirst)  
  let obj2 = Object.create(obj1); 
  
 // Output : Name 
  console.log(obj2.propfirst); 
    
  // Output : true. 
  console.log(delete obj2.propfirst);  
  
    // Surprisingly Note that this will return true 
    // regardless of whether the deletion was successful 
  
    // Output : Name     
    console.log(obj2.propfirst);  
```

**Creating objects in JavaScript (3 Different Ways)**

When it comes to language, JavaScript has always been a dynamic object-oriented scripting one. In this section, we will see the various ways in which entities can be instantiated in JavaScript.

Before we continue, it is worth bearing in mind that JavaScript is a language without a class and that the functions are used to represent a class.

**Using functions as class:**

One of JavaScript's easiest way to instantiate an object, we describe a classic JavaScript feature and use new keyword to construct a function object. Using "this" keyword, the function properties and methods are generated.

```
<script> 
    // Function acting as a Class. 
    function copyClass(name, age) { 
        this.name = name; 
        this.age = age; 
        this.printInfo = function() { 
            console.log(this.name); 
            console.log(this.age); 
        } 
    } 
  
// Creating the object of copyClass 
// and initializing the parameters. 
var obj = new copyClass("Vineet", 20); 
  
// Calling the method of copyClass. 
obj.printInfo(); 
</script> 
```

Output:

```
Vineet
20
```

**Explanation:**

There are two major components in a class of OOPs, other parameters and few functions of members. In this process, we declare a class-like function, there are two parameters, name and age (`this` keyword is used to differentiate the class name and age to the name and age of the arguments being provided) and a `printInfo` method that prints the value of these parameters. Then we simply create a copyClass object obj of it, initialize it and call it the method.

**Using object literals:**

To describe objects, literals are smaller and simpler methods. We instantiate an object with the object literal exactly the same as the previous one.

```
<script> 
    // Creating Object. 
    var obj = { 
        name : "", 
        age : "", 
        printInfo : function() { 
            console.log(this.name); 
            console.log(this.age); 
        } 
    } 
  
// Initializing the parameters. 
obj.name = "Vineet"; 
obj.age = 19; 
  
// Using method of the object. 
obj.printInfo(); 
</script> 
```

Output:

```
Vineet
20
```

**Explanation:**

This approach works in the same way as the former one, but rather than creating the parameters (name and age) and the method (printInfo) within a function, we bundle them into the object itself, initialize the object and just use the methods.

**Singleton using a function:**

The third way is a mixture of the other two we've already seen. We could use a function to describe an object with a singleton.

```
<script> 
    // Creating singleton object. 
    var obj = new function() { 
        this.name = ""; 
        this.age = ""; 
        this.printInfo = function() { 
            console.log(this.name); 
            console.log(this.age); 
        }; 
    } 
  
// Initializing object. 
obj.name = "Vineet"; 
obj.age = 20; 
  
// Calling method of the object. 
obj.printInfo(); 
</script> 
```

Output:

```
Vineet
20
```

**Explanation:**

This to be a mix of the two existing methods, we stack the methods and parameters within a function but do not declare a separate function (like copyClass in Method 1). Rather, we simply use the structure of the function to declare an object.