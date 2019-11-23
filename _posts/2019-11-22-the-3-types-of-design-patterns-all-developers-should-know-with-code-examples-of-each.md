---
title: The 3 Types of Design Patterns All Developers Should Know (with code examples
  of each)
image: "/assets/default-social-image.png"
categories: Naveen_Paul
---

The 3 Types of Design Patterns All Developers Should Know (with code examples of each)

**What is a Design Pattern?**

Design trends are model level approaches that we software engineers frequently encounter for recurring problems. It's not code, always remember what I said, ‘It’s not a code’. It's like an overview of how to deal with these issues and how to model a solution.

Following such patterns is considered good practice, as the solution layout is thoroughly tried and tested, resulting in the final code being more readable. OOP Languages produces and uses design patterns quite often, such as Java, in which most of the examples will be written from here on.

**Types of design patterns**

Currently discovered are some about 26 Patterns, classified into three types:

**1. Creational:** These can either be patterns of class-creation or patterns of object-creation as these patterns are designed for instantiation of class.

**2. Structural:** Most of these pattern’s main goal is to improve the class(es) involved's usefulness without modifying much of their composition. Such patterns are structured for the structure and composition of a class.

**3. Behavioral:** The development of these patterns depends on how one class interacts with others.
We will go through one basic design pattern for each categorized type in this article:

**Type 1: Creational - The Singleton Design Pattern**

The Singleton Design Pattern is a Creational pattern whose goal is to provide only one global point of access to that object and create only one instance of a class. an example of such a Java class is a Calendar, where you can't make the class as an instance. It also gets the object by using its own method of `getInstance()`.

A singleton design pattern used by a class will include,

Singleton Class Diagram

* A personal static variable that contains the class's only instance.
* A private constructor to avoid its instantiation anywhere else.
* A public static method for returning the class’s single instance.

There are various singleton design implementations. Some of them are;

1. Eager Instantiation
2. Lazy Instantiation
3. Thread-safe Instantiation
 
**Eager Beaver ?️**

```
public class EagerSingleton {
	// create an instance of the class.
	private static EagerSingleton instance = new EagerSingleton();

	// private constructor, so it cannot be instantiated outside this class.
	private EagerSingleton() {  }

	// get the only instance of the object created.
	public static EagerSingleton getInstance() {
		return instance;
	}
}
```

This type of instantiation occurs during class loading, as variable instance instantiation occurs outside of any method. If the client application does not use this class at all, this poses a heavy drawback. If this class is not used, the contingency plan is the Lazy Instantiation.

**Lazy Days ?**

There is little change from the above-mentioned implementation. The main differences are that the static variable is initially declared null and is instantiated within the `getInstance()` method if-and only if-the instance variable remains null at the time of the test.

```
public class LazySingleton {
	// initialize the instance as null.
	private static LazySingleton instance = null;

	// private constructor, so it cannot be instantiated outside this class.
	private LazySingleton() {  }

	// check if the instance is null, and if so, create the object.
	public static LazySingleton getInstance() {
		if (instance == null) {
			instance = new LazySingleton();
		}
		return instance;
	}
}
```

It solves one problem, but there is still one. And right up to the millisecond, what if at the same time two different customers enter the Singleton class? Okay, they're going to check if the instance is null at the same time and find it valid, so the two clients are going to create two instances of the class for each query. To fix this, the instantiation of Thread Safe must be implemented.

**(Thread) Safety is Key ?**

In Java for one thread to access a specific resource at one time only, the clustered keyword is used to enforce thread protection on methods or artifacts. For only one user to access the method at a given time, the instantiation of the class is positioned in a synchronized block.

```
public class ThreadSafeSingleton {
	// initialize the instance as null.
	private static ThreadSafeSingleton instance = null;

	// private constructor, so it cannot be instantiated outside this class.
	private ThreadSafeSingleton() {  }

	// check if the instance is null, within a synchronized block. If so, create the object
	public static ThreadSafeSingleton getInstance() {
		synchronized (ThreadSafeSingleton.class) {
			if (instance == null) {
				instance = new ThreadSafeSingleton();
			}
		}
		return instance;
	}
}
```

The synchronized approach overhead is high, decreasing the entire operation's efficiency.

For example, the `synchronized` method is run and the performance drops every time any user accesses the `getInstance()` function if the instance variable has already been instantiated. This only happens to test if the value of the `instance` variable is null. It leaves the process if it finds so.

Double locking is used to reduce this overhead. The test is also used before the `synchronized` method, and the method runs if the value is null alone.

```
// double locking is used to reduce the overhead of the synchronized method
public static ThreadSafeSingleton getInstanceDoubleLocking() {
	if (instance == null) {
		synchronized (ThreadSafeSingleton.class) {
			if (instance == null) {
				instance = new ThreadSafeSingleton();
			}
		}
	}
	return instance;
}
```

Now let’s move onto the next classification.

**Type 2: Structural - The Decorator Design Pattern**

I'll give you a small scenario to explain why and where you should use the Decorator Pattern in a better context.

Say you own a coffee shop and start with just two types of plain coffee, the house blend and dark roast, just like any newbie. There was one class for the different coffee blends in your billing system, which inherits the abstract category of drinks. People are actually beginning to get along with your delicious coffee.

Say you own a coffee shop, and like any newbie, you start out with just two types of plain coffee, the house blend and dark roast. In your billing system, there was one class for the different coffee blends, which inherits the beverage abstract class. People actually start to come by and have your wonderful (albeit bitter?) coffee. Then there's the coffee newbs that want sugar or milk, such a coffee transvestite!!

Initially, both coffees, one including sugar, and the other milk, will be subclassed by your IT man but unfortunately, now you need to have these two add-ons on the menu as well as on the billing system. So, as consumers are always wrong, the dreaded words are said:

"Can I have a milk coffee with sugar, please?”

Your billing system is going to laugh in your face again. Well, go back to the drawing board...

The IT person then adds milk coffee with sugar to each parent's coffee class as another subclass and there’s a smooth sailing trip from here on where people lined up to have their coffee and you're actually making money. But there’s more to it..

A competitor opens up across the street but more than 10 add-ons and not just the usual four types of coffee! Once again, the world is against you.

You may not be able to make an infinite number of subclasses for any and all combinations of all the add-ons, including new coffee blends but you buy all of these and more, to sell better coffee yourself, and just remember that you forgot to upgrade your dratted billing system. Not to mention the size of the final system.

You'll find new IT staff who actually know what they're doing and it's time to actually invest in a proper billing system for which they say:

"Why, if the decorator pattern is used if this is going to be so much easier and smaller."

The aim of the design is to modify the functionality of the objects at runtime. The design pattern of the decorator falls within the structural category, which deals with the actual structure of the class, whether by composition, inheritance, or both. This is one of the many other design patterns that to get the desired result, it uses the abstract classes and composition interfaces.

To bring this all into perspective, let’s give a chance to the Math;

Take 10 add-ons and 4 blends of coffee and if we stick to the subclasses generation of subclasses for each different combination of all the add-ons for one type of coffee;

(10–1)² = 9² = 81 subclasses

We're subtracting 1 out of 10. Look into the coding we will do because you can't combine one add-on with another of the same type, sugar with sugar sounds stupid. And that's just a blend of coffee. Multiply that 81 by 4 and you get 324 different subclasses!

Only 16 classes in this scenario are required with the decorator pattern.

Decorator Design Pattern Class diagram

Class diagram according to coffee shop scenario

We get 4 classes for 4 coffee blends if we map our scenario according to the class diagram above, 10 for each add-on and 1 for the abstract component and 1 for the abstract decorator. It's 16!

The add-ons, which are its subclasses, in turn inherit any new methods to add functionality to the base object when needed and as you can see from above, just as concrete coffee blends are subclasses of the abstract beverage class, the AddOn abstract class also inherits its methods.

Let’s see this pattern in use.

All the different blends of coffee will inherit from, to make the Abstract beverage class first:

```
public abstract class Beverage {
	private String description;
    
	public Beverage(String description) {
		super();
		this.description = description;
	}
    
	public String getDescription() {
		return description;
	}
    
	public abstract double cost();
}
```

For both the concrete coffee blend classes to add:

```
public class HouseBlend extends Beverage {
	public HouseBlend() {
		super(“House blend”);
	}

	@Override
	public double cost() {
		return 250;
	}
}

public class DarkRoast extends Beverage {
	public DarkRoast() {
		super(“Dark roast”);
	}

	@Override
	public double cost() {
		return 300;
	}
}
```

From the Beverage abstract class, the AddOn abstract class also inherits.

```
public abstract class AddOn extends Beverage {
	protected Beverage beverage;

	public AddOn(String description, Beverage bev) {
		super(description);
		this.beverage = bev;
	}

	public abstract String getDescription();
}
```

And now the concrete implementation of this abstract class:

```
public class Sugar extends AddOn {
	public Sugar(Beverage bev) {
		super(“Sugar”, bev);
	}

	@Override
	public String getDescription() {
		return beverage.getDescription() + “ with Mocha”;
	}

	@Override
	public double cost() {
		return beverage.cost() + 50;
	}
}

public class Milk extends AddOn {
	public Milk(Beverage bev) {
		super(“Milk”, bev);
	}

	@Override
	public String getDescription() {
		return beverage.getDescription() + “ with Milk”;
	}

	@Override  public double cost() {
		return beverage.cost() + 100;
	}
}
```

We can pass any of the Beverage subclasses to any AddOn subclass as you can see above, and then get the added cost as well as the updated description. We can pass the AddOn to another AddOn since the AddOn class is essentially a beverage type. This way, we can add any number of add-ons to a specific blend of coffee.

Now let’s test this out by writing some code.

```
public class CoffeeShop {
	public static void main(String[] args) {
		HouseBlend houseblend = new HouseBlend();
		System.out.println(houseblend.getDescription() + “: “ + houseblend.cost());

		Milk milkAddOn = new Milk(houseblend);
		System.out.println(milkAddOn.getDescription() + “: “ + milkAddOn.cost());

		Sugar sugarAddOn = new Sugar(milkAddOn);
		System.out.println(sugarAddOn.getDescription() + “: “ + sugarAddOn.cost());
	}
}
```

The final result is:

It's working! without the need to make endless subclasses for each add-on combination for all coffee blends, we were able to add more than one add-on to the coffee blend and successfully update its final cost and description.

Finally, to the last category.

**Type 3: Behavioral - The Command Design Pattern**

The main focus of the command pattern is to inculcate a higher degree of loose coupling between the parties involved (read: classes), a pattern of behavioral design focuses on how classes and objects communicate with each other.

Let’s see what it means.

A better definition of loose coupling would be the classes that are interconnected, making the least use of each other, as coupling is the way that two (or more) classes interact with each other. The ideal scenario is the loose coupling when these classes interact is that they don't depend heavily on each other.

When requests needed to be sent without knowing consciously what you are asking for or who the receiver is, the need for this pattern arose.

The invocation class is decoupled from the class that actually performs an action in this pattern. The invoker class only has to execute the callable method that runs the required command when the client requests it.

Order a meal at a fancy restaurant, as a basic real-world example. As the flow goes, you'll give your order (command) to the waiter (invoker) who'll hand it over to the chef (receiver) so you can get food. Possibly simple, but to code.


Command Design Pattern Class Diagram

A specific command that implements the command interface, asks the receiver to complete the action, and sends the command to the invoker, this is the flow of operation on the technical side. The person who knows when to give this command is the invoker. The only one who knows what to do with the specific order/command is the chef. When we run the method of invoker execution, it causes the execution method of the command objects to run on the receiver, thus completing the necessary actions.

**What we need to implement is;**

* An interface Command
* A class Order that implements Command interface
* A class Waiter (invoker)
* A class Chef (receiver)

So, the coding goes like this:

**Chef, the receiver**

```
public class Chef {
	public void cookPasta() {
		System.out.println(“Chef is cooking Chicken Alfredo…”);
	}

	public void bakeCake() {
		System.out.println(“Chef is baking Chocolate Fudge Cake…”);
	}
}
```

**Command, the interface**

```
public interface Command {
	public abstract void execute();
}
```

**Order, the concrete command**

```
public class Order implements Command {
	private Chef chef;
	private String food;

	public Order(Chef chef, String food) {
		this.chef = chef;
		this.food = food;
	}

	@Override
	public void execute() {
		if (this.food.equals(“Pasta”)) {
			this.chef.cookPasta();
		} else {
			this.chef.bakeCake();
		}
	}
}
```

**Waiter, the invoker**

```
public class Waiter {
	private Order order;

	public Waiter(Order ord) {
		this.order = ord;
	}

	public void execute() {
		this.order.execute();
	}
}
```

**You, the client**

```
public class Client {
	public static void main(String[] args) {
		Chef chef = new Chef();
        
		Order order = new Order(chef, “Pasta”);
		Waiter waiter = new Waiter(order);
		waiter.execute();

		order = new Order(chef, “Cake”);
		waiter = new Waiter(order);
		waiter.execute();
	}
}
```

The Customer makes an order and sets the Receiver as the Chef. The order is sent to the waiter as you can see this above, who will know when to execute the order i.e. when to order the chef to cook. When the invoker is executed, the order execution method is run on the receiver i.e. the chef is given the command to either cook pasta or bake a cake.

Final Client Output

**Quick recap**

In this post we went through:

* What really is a design pattern,
* The design patterns types and why they are different
* For a type, One common design pattern.

I hope this is going to be helpful in the end.

Find the code repo for the post, [here](https://github.com/samsam-026/Design_Patterns).