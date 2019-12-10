---
title: classical inheritance vs prototypal inheritance in javascript
image: "/assets/default-social-image.png"
categories: JavaScript
---

I have googled so many links and can't get good idea about the difference between classical inheritance and prototypal inheritance?

I have learned some things from these but I'm still confused about the concepts.

* [Benefits of prototypal inheritance over classical?](https://stackoverflow.com/questions/2800964/benefits-of-prototypal-inheritance-over-classical)
* [http://aaditmshah.github.io/why-prototypal-inheritance-matters/](http://aaditmshah.github.io/why-prototypal-inheritance-matters/)

**Classical inheritance**

```
// Shape - superclass
function Shape() {
  this.x = 0;
  this.y = 0;
}

//superclass method
Shape.prototype.move = function(x, y) {
    this.x += x;
    this.y += y;
    console.info("Shape moved.");
};

// Rectangle - subclass
function Rectangle() {
  Shape.call(this); //call super constructor.
}

//subclass extends superclass
Rectangle.prototype = Object.create(Shape.prototype);
```

Does classical inheritance use prototypal inheritance inside?

[http://aaditmshah.github.io/why-prototypal-inheritance-matters/](http://aaditmshah.github.io/why-prototypal-inheritance-matters/)

From above link, I learned **we can't add new methods at run time in classical inheritance**. Is this correct? But you can check the above code **I can add "move" method and any methods at run time through prototype**. So this is prototype based classical inheritance? If so what is actual classical inheritance and prototype inheritance? I am confused about that.

**Prototypal inheritance.**

```
function Circle(radius) {
    this.radius = radius;
}
Circle.prototype.area = function () {
    var radius = this.radius;
    return Math.PI * radius * radius;
};
Circle.prototype.circumference: function () {
    return 2 * Math.PI * this.radius;
};
var circle = new Circle(5);
var circle2 = new Circle(10);
```

Is this similar to classical inheritance? I'm totally confused about what is prototypal inheritance? What is classical inheritance? Why is classical inheritance bad?

Can you give me a simple example for better understanding these in a simple manner.

#1. Both the code samples you demonstrated in your question make use of prototypal inheritance. In fact any object-oriented code you write in JavaScript is a paradigm of prototypal inheritance. JavaScript simply doesn't have classical inheritance. This should clear things up a bit:

```

                                   Inheritance
                                        |
                         +-----------------------------+
                         |                             |
                         v                             v
                    Prototypal                     Classical
                         |
         +------------------------------+
         |                              |
         v                              v
Prototypal Pattern             Constructor Pattern

```

As you can see prototypal inheritance and classical inheritance are two different paradigms of inheritance. Some languages like Self, Lua and JavaScript support prototypal inheritance. However most languages like C++, Java and C# support classical inheritance.

**A Quick Overview of Object-Oriented Programming**

Both prototypal inheritance and classical inheritance are object-oriented programming paradigms (i.e. they deal with objects). Objects are simply abstractions which encapsulate the properties of a real world entity (i.e. they represent real word things in the program). This is known as abstraction.

**Abstraction:** The representation of real world things in computer programs.

Theoretically an abstraction is defined as "a general concept formed by extracting common features from specific examples". However for the sake of this explanation we're going to use the aforementioned definition instead.

Now some objects have a lot of things in common. For example a mud bike and a Harley Davidson have a lot in common.

A mud bike and a Harley Davidson are both bikes. Hence a bike is a generalization of both a mud bike and a Harley Davidson.

```

                   Bike
                     |
    +---------------------------------+
    |                                 |
    v                                 v
Mud Bike                       Harley Davidson

```

In the above example the bike, the mud bike and the Harley Davidson are all abstractions. However the bike is a more general abstraction of the mud bike and the Harley Davidson (i.e. both the mud bike and the Harley Davidson are specific types of bikes).

**Generalization:** An abstraction of a more specific abstraction.

In object-oriented programming we create objects (which are abstractions of real world entities) and we use either classes or prototypes to create generalizations of these objects. Generalizations are created via inheritance. A bike is a generalization of a mud bike. Hence mud bikes inherit from bikes.

**Classical Object-Oriented Programming**

In classical object-oriented programming we have two types of abstractions: classes and objects. An object, as mentioned before, is an abstraction of a real world entity. A class on the other hand is an abstraction of an object or another class (i.e. it's a generalization). For example, consider:

```

+----------------------+----------------+---------------------------------------+
| Level of Abstraction | Name of Entity |                Comments               |
+----------------------+----------------+---------------------------------------+
| 0                    | John Doe       | Real World Entity.                    |
| 1                    | johnDoe        | Variable holding object.              |
| 2                    | Man            | Class of object johnDoe.              |
| 3                    | Human          | Superclass of class Man.              |
+----------------------+----------------+---------------------------------------+

```

As you can see in classical object-oriented programming languages objects are only abstractions (i.e. all objects have an abstraction level of 1) and classes are only generalizations (i.e. all classes have an abstraction level greater than 1).

Objects in classical object-oriented programming languages can only be created by instantiating classes:

```
class Human {
    // ...
}

class Man extends Human {
    // ...
}

Man johnDoe = new Man();
```

In summation in classical object-oriented programming languages objects are abstractions of real world entities and classes are generalizations (i.e. abstractions of either objects or other classes).

Hence as the level of abstraction increases entities become more general and as the level of abstraction decreases entities become more specific. In this sense the level of abstraction is analogous to a scale ranging from more specific entities to more general entities.

**Prototypal Object-Oriented Programming**

Prototypal object-oriented programming languages are much simpler than classical object-oriented programming languages because in prototypal object-oriented programming we only have one type of abstraction (i.e. objects). For example, consider:

```
+----------------------+----------------+---------------------------------------+
| Level of Abstraction | Name of Entity |                Comments               |
+----------------------+----------------+---------------------------------------+
| 0                    | John Doe       | Real World Entity.                    |
| 1                    | johnDoe        | Variable holding object.              |
| 2                    | man            | Prototype of object johnDoe.          |
| 3                    | human          | Prototype of object man.              |
+----------------------+----------------+---------------------------------------+
```

As you can see in prototypal object-oriented programming languages objects are abstractions of either real world entities (in which case they are simply called objects) or other objects (in which case they are called prototypes of those objects that they abstract). Hence a prototype is a generalization.

Objects in prototypal object-oriented programming languages may be created either ex-nihilo (i.e. out of nothing) or from another object (which becomes the prototype of the newly created object):

```
var human = {};
var man = Object.create(human);
var johnDoe = Object.create(man);
```

In my humble opinion prototypal object-oriented programming languages are more powerful than classical object-oriented programming languages because:

1. There is only one type of abstraction.
2. Generalizations are simply objects.

By now you must have realized the difference between classical inheritance and prototypal inheritance. Classical inheritance is limited to classes inheriting from other classes. However prototypal inheritance includes not only prototypes inheriting from other prototypes but also objects inheriting from prototypes.

**Prototype-Class Isomorphism**

You must have noticed that prototypes and classes are very similar. That's true. They are. In fact they are so similar that you can actually use prototypes to model classes:

```
function CLASS(base, body) {
    if (arguments.length < 2) body = base, base = Object.prototype;
    var prototype = Object.create(base, {new: {value: create}});
    return body.call(prototype, base), prototype;

    function create() {
        var self = Object.create(prototype);
        return prototype.hasOwnProperty("constructor") &&
            prototype.constructor.apply(self, arguments), self;
    }
}
```

Using the above `CLASS` function you can create prototypes that look like classes:

```
var Human = CLASS(function () {
    var milliseconds = 1
      , seconds      = 1000 * milliseconds
      , minutes      = 60 * seconds
      , hours        = 60 * minutes
      , days         = 24 * hours
      , years        = 365.2425 * days;

    this.constructor = function (name, sex, dob) {
        this.name = name;
        this.sex = sex;
        this.dob = dob;
    };

    this.age = function () {
        return Math.floor((new Date - this.dob) / years);
    };
});

var Man = CLASS(Human, function (Human) {
    this.constructor = function (name, dob) {
        Human.constructor.call(this, name, "male", dob);
        if (this.age() < 18) throw new Error(name + " is a boy, not a man!");
    };
});

var johnDoe = Man.new("John Doe", new Date(1970, 0, 1));
```

The reverse is not true however (i.e. you can't use classes to model prototypes). This is because prototypes are objects but classes are not objects. They are an entirely different type of abstraction.

**Conclusion**

In summation we learned that an abstraction is a "a general concept formed by extracting common features from specific examples" and that generalization is "an abstraction of a more specific abstraction". We also learned about the differences between prototypal and classical inheritance and how both of them are two faces of the same coin.

On a parting note I would like to remark that there are two patterns of prototypal inheritance: the prototypal pattern and the constructor pattern. The prototypal pattern is the canonical pattern of prototypal inheritance whereas the constructor pattern is used to make prototypal inheritance look more like classical inheritance. Personally I prefer the prototypal pattern.

P.S. I'm the guy who wrote the blog post "[Why Prototypal Inheritance Matters](http://aaditmshah.github.io/why-prototypal-inheritance-matters/)" and answered the question "[Benefits of prototypal inheritance over classical?](https://stackoverflow.com/questions/2800964/benefits-of-prototypal-inheritance-over-classical)". My answer is the accepted answer.

#2. Before jumping into inheritance, we will take a look at two primary models to create instances (objects) in javascript:

**Classical model:** Object is created from a blueprint (class)

```
class Person {
  fn() {...}
} // or constructor function say, function Person() {}

// create instance
let person = new Person();
```

**Prototypal model:** Object is created directly from another object.

```
// base object
let Person = { fn(){...} }

// instance
let person = Object.create(Person);
```

In either case, Inheritance* is achieved by linking objects using prototype object.

(*base class methods are accessible via. derived class through the prototype object and not required to be explicitly present in derived class.)

Here is a good explanation to understand better ([http://www.objectplayground.com/](http://www.objectplayground.com/))