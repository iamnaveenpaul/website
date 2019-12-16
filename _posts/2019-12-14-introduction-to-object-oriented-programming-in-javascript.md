---
image: "/assets/default-social-image.png"
title: Introduction to Object Oriented Programming in JavaScript
categories: JavaScript-basics
---

**Introduction to Object Oriented Programming in JavaScript**

As JavaScript is extensively used in Web Development, some of the object-oriented method supported by JavaScript will be explored in this section and get the most out of it. Some of JavaScript's famous interview question on OOPSincludes,-"How JavaScript handles object-oriented programming? How different are they from other languages? Can Inheritance be applied in JavaScript, and so on.

There are certain features or techniques that make something an object-oriented language like:

* **Object**
* **Classes**
* **Encapsulation**
* **Inheritance**

Let's dig into each of the specifics and see how JavaScript executes them.

**Object:** An Object is a unique entity that includes properties and methods. For instance, "car" is an entity in real life that has certain characteristics such as color, size, design, horsepower and conducts certain actions such as drive. The characteristics of an object are called as property, and the actions are called methods in object-oriented programming. An Object is a class instance. In JavaScript, objects are almost everywhere, every element whether it is a function, arrays, and string, is an object.

Note: A javascript method is a property of an object that has a function as its value.

In JavaScript, object can be created in two ways:

Using an **Object Literal**

```
//Defining object 
let person = { 
    first_name:'Mukul', 
    last_name: 'Latiyan', 
  
    //method 
    getFunction : function(){ 
        return (`The name of the person is  
          ${person.first_name} ${person.last_name}`) 
    }, 
    //object within object 
    phone_number : { 
        mobile:'12345', 
        landline:'6789'
    } 
} 
console.log(person.getFunction());  
console.log(person.phone_number.landline); 
```

Using an **Object Constructor**

```
//using a constructor 
function person(first_name,last_name){ 
   this.first_name = first_name; 
   this.last_name = last_name; 
} 
//creating new instances of person object 
let person1 = new person('Mukul','Latiyan'); 
let person2 = new person('Rahul','Avasthi'); 
  
console.log(person1.first_name); 
console.log(`${person2.first_name} ${person2.last_name}`); 
```

Using the method **Object.create()** creates a new object using an existing object as the prototype of the newly created object.

```
// Object.create() example a 
// simple object with some properties 
const coder = { 
    isStudying : false, 
    printIntroduction : function(){ 
        console.log(`My name is ${this.name}. Am I  
          studying?: ${this.isStudying}.`) 
    } 
} 
// Object.create() method 
const me = Object.create(coder); 
  
// "name" is a property set on "me", but not on "coder" 
me.name = 'Mukul';  
  
// Inherited properties can be overwritten 
me.isStudying = 'True';  
  
me.printIntroduction();  
```

**Classes:** Classes are an object's model. A class can have a lot of objects, because class is a template, while objects are class instances or concrete implementation.

Before we go ahead, note that unlike other Object Oriented Languages, we will realize that there are no classes of JavaScript but we only have Object. To be more specific, JavaScript is a prototype object-oriented language, implying that it does not have classes, rather it uses constructor function to describe behaviors and then use the template to reuse it.

Note: Even the ECMA2015 classes are prototypes.

JavaScript classes, introduced in ECMAScript 2015, are primarily syntactical sugar over JavaScript’s existing prototype-based inheritance. The class syntax is not introducing a new object-oriented inheritance model to JavaScript. JavaScript classes provide a much simpler and clearer syntax to create objects and deal with inheritance.
–Mozilla Developer Network

Example:

Let's use ES6 classes then we'll look at the conventional way of defining and simulating objects as classes.

```
// Defining class using es6 
class Vehicle { 
  constructor(name, maker, engine) { 
    this.name = name; 
    this.maker =  maker; 
    this.engine = engine; 
  } 
  getDetails(){ 
      return (`The name of the bike is ${this.name}.`) 
  } 
} 
// Making object with the help of the constructor 
let bike1 = new Vehicle('Hayabusa', 'Suzuki', '1340cc'); 
let bike2 = new Vehicle('Ninja', 'Kawasaki', '998cc'); 
  
console.log(bike1.name);    // Hayabusa 
console.log(bike2.maker);   // Kawasaki 
console.log(bike1.getDetails()); 
```

Traditional Way.

```
// Defining class in a Traditional Way. 
function Vehicle(name,maker,engine){ 
    this.name = name, 
    this.maker = maker, 
    this.engine = engine 
}; 
  
Vehicle.prototype.getDetails = function(){ 
    console.log('The name of the bike is '+ this.name); 
} 
  
let bike1 = new Vehicle('Hayabusa','Suzuki','1340cc'); 
let bike2 = new Vehicle('Ninja','Kawasaki','998cc'); 
  
console.log(bike1.name); 
console.log(bike2.maker); 
console.log(bike1.getDetails()); 
```

As seen in the previous illustration, the defining and reuse of an object in ES6 is much simpler. Therefore, in all our examples, we would use ES6.

**Encapsulation:** Encapsulation is defined as the method of covering properties and function within a single unit.

Example:

```
//encapsulation example 
class person{ 
    constructor(name,id){ 
        this.name = name; 
        this.id = id; 
    } 
    add_Address(add){ 
        this.add = add; 
    } 
    getDetails(){ 
        console.log(`Name is ${this.name},Address is: ${this.add}`); 
    } 
} 
  
let person1 = new person('Mukul',21); 
person1.add_Address('Delhi'); 
person1.getDetails(); 
```

We simply create a person object using the constructor in the above example and initialize it property and use it functions we are not bothered by the details of the implementation. We work with an interface of objects without taking into account the details of implementation.

Encapsulation sometimes refers to data hiding or data abstraction, which means the essential features representing hide its background detail. Most OOP languages provide access modifiers to restrict a variable's scope, but they are not such access modifiers in JavaScript, but they are some way of limiting the variable's scope within the Class/Object.

Example:

```
// Abstraction example 
function person(fname,lname){ 
    let firstname = fname; 
    let lastname = lname; 
  
    let getDetails_noaccess = function(){ 
        return (`First name is: ${firstname} Last  
            name is: ${lastname}`); 
    } 
  
    this.getDetails_access = function(){ 
        return (`First name is: ${firstname}, Last  
            name is: ${lastname}`); 
    } 
} 
let person1 = new person('Mukul','Latiyan'); 
console.log(person1.firstname); 
console.log(person1.getDetails_noaccess); 
console.log(person1.getDetails_access()); 
```

In the instance above, we try to access any property(person1.firstname) and functions(person1.getDetails_noaccess), but it returns undefined while it is a process that we can access from the person object(person1.getDetails_access()) by changing the way we describe a function that we can limit its scope.

**Inheritance:** It is a term in which another object utilizes certain properties and methods of an object. Unlike most OOP languages in which classes inherit classes, JavaScript Object inherits object, i.e. certain attributes (property and methods) of one object can be inherited by other objects.

Example:

```
//Inhertiance example 
class person{ 
    constructor(name){ 
        this.name = name; 
    } 
    //method to return the string 
    toString(){ 
        return (`Name of person: ${this.name}`); 
    } 
} 
class student extends person{ 
    constructor(name,id){ 
        //super keyword to for calling above class constructor 
        super(name); 
        this.id = id; 
    } 
    toString(){ 
        return (`${super.toString()},Student ID: ${this.id}`); 
    } 
} 
let student1 = new student('Mukul',22); 
console.log(student1.toString()); 
```

In the above case, we identify a Person Object with certain property and method and then inherit the Person Object in the Student Object and use all the property and method of the person Object as well as specifying certain properties and methods for the Student.

Note: The object of the student and the person must have the same method, i.e. toString(), which is considered the overriding process. Method Overriding allows the method to have the same naming and method signature as a parent class in a child's class.

Super keyword is used in the above code to refer to the instance variable of the immediate parent class.

We introduced object-oriented functionalities in JavaScript, a whole book explains this in good detail,- "Stoyan Stefanov's object-oriented JavaScript"