---
image: "/assets/default-social-image.png"
categories: JavaScript-interview
title: |-
  10 Interview Questions
  Every JavaScript Developer Should Know
---

Management has to trust programmers at most companies to give professional interviews to determine applicant skills. You would ultimately need to meet if you do well as. This is how it is.

**It Starts With People**

There are few points in “[How to Build a High Velocity Development Team](https://medium.com/javascript-scene/how-to-build-a-high-velocity-development-team-4b2360d34021)”, that are worth repeating:

“Nothing forecasts better business results than an excellent team. You need to invest here first if you're going to beat the odds.”

Focus on the 3 P's as Marcus Lemonis says: "People, Process, Product"

You should have very good, senior-level applicants for your early hires. Individuals who can recruit and advise other developers and support mid-level and intermediate developers you're going to want to employ down the road eventually.

Read “[Why Hiring is So Hard in Tech](https://medium.com/javascript-scene/why-hiring-is-so-hard-in-tech-c462c3230017)” for a thorough overview of employee assessment of the general do's and don'ts.

A pair programming exercise is the best way to assess a candidate. Let go of the nominee. Watch and listen more than you are thinking about. Pulling messages from the Twitter API and showing them on a timeline could be a good project.

That said, no workout is going to tell you everything you need to say. An interview can also be a really useful tool, but don't waste time and inquire about spelling or word nuances. you need to see the big picture. The big decisions that can have a big impact on the plan as a whole, talk about design and paradigms.

Google can conveniently use syntax and functionality. It's much harder for Google to pick up on expertise of software engineering knowledge or common JavaScript paradigms and idioms developers.

JavaScript is unique, and in almost every broad application it plays a critical role. What is JavaScript, that makes it significantly different from other languages?

Here are a few questions that will help you to explore what is really important:

**1. Could you name two essential programming paradigms for developers of JavaScript apps?**

JavaScript is a multi-paradigm language that supports OOP (Object-Oriented Programming) and functional programming as well as imperative/procedural programming. JavaScript supports design heritage OOP.

**Good to hear:**

* Heritage models (also: prototypes, OLOO).
* Functional programming (including closures, functions of first class, lambdas).

**Red flags:**

* No hint of what a paradigm is, no description of prototype oo or functional programming.

**Learn More:**

* [The Two Pillars of JavaScript Part 1](https://medium.com/javascript-scene/the-two-pillars-of-javascript-ee6f3281e7f3) — Prototypal OO.
* [The Two Pillars of JavaScript Part 2](https://medium.com/javascript-scene/the-two-pillars-of-javascript-pt-2-functional-programming-a63aa53a41a4) — Functional Programming.

**2. What is functional programming?**

Functional programming produces programs through the composition of mathematical functions and prevents shared status and mutable information. As one of the first languages to support functional programming, Lisp specified in 1958, was heavily inspired by the calculus of lambda. Lisp and many languages of the Lisp family are still widely used today.

Functional programming, one of JavaScript's two pillars is an important concept in JavaScript. JavaScript has been applied to several common usable utilities in ES5.

**Good to hear:**

* Pure functions / function purity.
* Avoid side-effects.
* Simple composition of functions.
* Types of functional languages: Lisp, ML, Haskell, Erlang, Clojure, Elm, F Sharp, OCaml, etc.
* Mention of FP supporting features: first-class features, higher-order functions, functions as arguments/values.

**Red flags:**

* No mention of pure functions / side effects avoidance.
* Definitions of functional programming languages could not be presented.
* The JavaScript features that allow FP can not be defined.

**Learn More:**

* [The Two Pillars of JavaScript Part 2](https://medium.com/javascript-scene/the-two-pillars-of-javascript-pt-2-functional-programming-a63aa53a41a4).
* [The Dao of Immutability](https://medium.com/javascript-scene/the-dao-of-immutability-9f91a70c88cd).
* [Composing Software](https://medium.com/javascript-scene/composing-software-an-introduction-27b72500d6ea).
* [The Haskell School of Music](http://haskell.cs.yale.edu/wp-content/uploads/2015/03/HSoM.pdf).

**3. What is the difference between class inheritance and prototypal inheritance?**

**Class Inheritance:** instances inherit classes (such as a blueprint, a class description) and create sub class relationships: hierarchical class taxonomies. Instances are typically instantiated with the `new` keyword via constructor functions. The `class` keyword from ES6 may or may not be used by class inheritance.

**Prototypical inheritance:** instances derive from other objects directly. Instances are typically instantiated via factory or `Object.create()` functions. Instances can be made up of many different artifacts, allowing fast selective inheritance.

Through JavaScript, inheritance of models is simpler and more versatile than inheritance of classes.

**Good to hear:**

**Classes:** establish close couplings or hierarchies/taxonomies.
**Models:** references to concatenative inheritance, delegation of models, functional inheritance, structure of objects.

**Red Flags:**

* No Preference choice for prototypical inheritance & composition over class inheritance.

**Learn More:**

* [The Two Pillars of JavaScript Part 1](https://medium.com/javascript-scene/the-two-pillars-of-javascript-ee6f3281e7f3) — Prototypal OO.
* [Common Misconceptions About Inheritance in JavaScript](https://medium.com/javascript-scene/common-misconceptions-about-inheritance-in-javascript-d5d9bab29b0a).

**4. What are the advantages and disadvantages of object-oriented programming and functional programming?**

**OOP Pros:** The basic concept of artifacts can be easily understood and the meaning of method calls can be easily interpreted. OOP prefers to use an imperative style rather than a declarative style that reads for the machine to follow as a simple set of instructions.

**OOP Cons:** OOP is usually mutual state based. Usually, entities and actions are handled together on the same subject, which can be arbitrarily accessed by any number of non-deterministic functions, which can lead to undesirable behaviors such as race conditions.

**FP Pros:** programmers prevent any common state or side effects using the functional model, removing errors caused by multiple functions vying for the same resources. Through features such as point-free style flexibility (aka tacit programming), functions appear to be drastically simplified and easily recomposed compared to OOP for more commonly reusable software.

FP also tends to favor declarative and denotational types, which do not prescribe step-by-step process instructions, but rather focus on ‘what’ to do, allowing the underlying functions to take care of ‘how’. This leaves immense flexibility for refactoring and improving efficiency, even allowing you to substitute whole algorithms with more efficient ones with very little change of code, for example, memorize or use lazy evaluation instead of eager evaluation.

Computing that uses pure functions is also easy to scale through several processors or dispersed clusters of computing without fear of threading conflicts of energy, race conditions, etc.

**FP Cons:** Using FP features such as point-free style and broad compositions will potentially reduce readability, as the resultant software is often more abstractly defined, simpler, and less concise.

OO and imperative programming are familiar to more people than functional programming, so even specific idioms of functional programming can be frustrating for new members of the team.

FP has a much steeper learning curve than OOP as OOP's widespread popularity has rendered OOP's language and learning materials more conversational, while FP's terminology appears to be much more scholarly and structured. FP definitions are often published on the use of lambda calculus, algebras and category theory idioms and descriptions, all of which includes a basic knowledge base to be learned in those fields.

**Good to hear:**

* Mentions of shared-state challenges, different entities vying for the same services, etc.
* Understanding of the potential of FP to improve most systems dramatically.
* Awareness of the learning curve variations.
* Articulation of side effects and how they impact the effectiveness of the system.
* Awareness that there may be a steep learning curve for a highly functional codebase.
* Awareness that codebas were strongly OOP
* Awareness that immutability gives rise to an exceedingly open and maleable history of system existence, making it possible to quickly add features such as endless undo / redo, rewind / replay, time-travel debugging, etc. In either model, immutability can be accomplished, but a flood of state-of - the-art distributed artifacts complicates OOP implementation.

**Red flags:**

* Incapable of mentioning drawbacks in one type or another — Someone familiar with either design should have encountered some of the weaknesses.

**Learn More:**

* [The Two Pillars of JavaScript Part 1](https://medium.com/javascript-scene/the-two-pillars-of-javascript-ee6f3281e7f3) — Prototypal OO.
* [The Two Pillars of JavaScript Part 2](https://medium.com/javascript-scene/the-two-pillars-of-javascript-pt-2-functional-programming-a63aa53a41a4) — Functional Programming.

**5. When is classical heritage a suitable choice?**

Nothing, or almost never, is the solution. Definitely not reach one point. Hierarchies in multi-level classes are an anti-pattern. For years, I've been launching this question and the only solutions I've ever gotten collapse into one of the several common misconceptions. The obstacle is met with silence more often.

“If a feature is sometimes useful
and sometimes dangerous
and if there is a better option
then always use the better option.”
~ Douglas Crockford

**Good to hear:**

* Rarely, hardly ever, or never.
* Sometimes a single tier is OK from a base-class system such as `React.Component`.
* "Favor composition of artifacts over inheritance of class."

**Learn More:**

* [The Two Pillars of JavaScript Part 1](https://medium.com/javascript-scene/the-two-pillars-of-javascript-ee6f3281e7f3) — Prototypal OO.
* [JS Objects](http://davidwalsh.name/javascript-objects) — Inherited a Mess.

**6. When is prototypical inheritance a suitable choice?**

There is more than one prototypal inheritance type:

* **Delegation** (i.e., the prototype chain).
* **Concatenative** (i.e. mixins, `Object.assign()`).
* **Functional** (Not to be confused with functional programming. A feature used to create a private state/encapsulation closure).
* That form of prototypical inheritance has its own collection of use-cases, but all of them are equally useful in their capacity to allow arrangement that generates has-a or uses-a or can-do relationships as opposed to is-a relationship generated with class inheritance.

**Good to hear:**

* For cases where there is no obvious solution to modules or functional programming.
* When assembling objects from multiple sources is important.
* You need inheritance each time.

**Red flags:**

* No experience of when to use prototypes.
* No mixins or `Object.assign()` knowledge.

**Learn More:**

* “[Programming JavaScript Applications](http://chimera.labs.oreilly.com/books/1234000000262/ch03.html#chcsrdou100015eilvj6l9inj)”: Prototypes section.

**7. What ia the meaning of “favor object composition over class inheritance”?**

This is a quotation from “Design Patterns: [Elements of Reusable Object-Oriented Software](http://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612)”. Through combining smaller units of features into new objects instead of inheriting from classes and establishing entity taxonomies, this ensures that code reuse should be done.

In other terms, use can-do, has-a, or uses-a relationships rather than is-a relationships.

**Good to hear:**

* Avoid class hierarchies.
* Avoid fragile base class problem.
* Avoid tight coupling.
* Avoid rigid taxonomy (forced is-a arrangement that is ultimately wrong in cases of new use).
* Avoid the gorilla banana problem (“what you expected was a banana, what you got was a gorilla holding the banana, and the whole jungle”).
* Increase flexibility of code.

**Red Flags:**

* Fail to mention any of the above problems.
* Unable to express the disparity or the benefits of structure between composition and class inheritance.

**Learn More:**

Introducing the Stamp Specification
Move Over, `class`: [Composable Factory Functions Are Here](https://medium.com/p/77f8911c2fee?source=post_page-----6fa6bdf5ad95----------------------)

**8. What are two-way binding of data and one-way flow of data, and how they are different?**

Binding information in two ways implies that UI fields are connected to dynamically template data so that the design data shifts with it when a UI field changes and vice versa.

Information stream one way means the model is the only source of truth. Changes in UI cause notifications communicating the purpose of the client to the template (or "store" in React). Only the template has access to adjust the state of the system. The result is that in one line information still travels, making it easier to grasp.

Data flows in one direction is deterministic, whereas linking in two way will create side effects that are more difficult to follow and grasp.

**Good to hear:**

React is the latest classic instance of one-way data stream, so it's a good signal to consider React. Cycle.js is another common one-directional data flow implementation.

Angular is a common two-way binding method.

**Red flags:**

Without knowing what one says either. The discrepancy can not be explained.

**Learn more:**

**9. What are the pros and cons of architectures that are monolithic vs microservice?**

A monolithic architecture means that your app is written as one cohesive unit of code whose components are designed to work together, sharing the same memory space and resources.

A microservice design ensures that your software comprises of many tiny, autonomous programs capable of running in their own memory space and spreading through possibly several different devices independently of each other.

**Monolithic Pros:** The major advantage is that most applications usually have a large number of cross-cutting issues, such as monitoring, frequency restricting, and security features such as audit trails and DOS defense.

It's quick to hook up modules to those cross-cutting issues when everything runs through the same device.

Speed advantages may also occur, as access to shared memory is quicker than interaction between processes (IPC).

**Monolithic cons:** software services continue to get closely linked and embroidered as the framework develops, making it difficult to separate resources for reasons such as autonomous scaling or preservation of code.

Furthermore, monolithic systems are much more difficult to understand, as there may be interactions, side effects, and complexities that are not apparent when you glance at a particular service or controller or device.

**Microservice pros:** Usually, microservice systems are better organized, as each microservice has a very specific job and is not associated with other element jobs. Decoupled resources are also simpler to recompose and reconfigure to suit the needs of various applications (such as supporting all web clients and public APIs).

These may also have performance benefits based on how they are arranged, as it is possible to separate and scale hot resources independently of the rest of the app.

**Microservice cons:** As you're building a new microservice architecture, you're likely to find tons of cross-cutting issues you didn't anticipate at the time of layout. A monolithic device might set up collaborative magic aids or middleware without much effort to deal with such cross-cutting issues.

You will either have to incur the overhead for different modules for each cross-cutting problem in a microservice design, or encapsulate cross-cutting issues in another service layer through which all traffic is redirected.

Finally, still monolithic designs prefer to channel traffic through an external service layer to cross-cutting considerations, but with them, the expense of that function can be postponed until the project is much more advanced.

Microservices are often run on their own virtual machines or servers, allowing the VM wrangling job to proliferate. For container fleet management software, these functions are often automated.

**Good to hear:**

* Notwithstanding the higher initial expense vs. monolithic devices, optimistic attitudes towards microservices. Conscious that in the long run microservices tend to perform better and scale well.
* Practical of microservices and monolithic systems. Structure the system so that functions at the code level are independent of each other, but are easy to combine in the beginning as a monolithic device. The overhead costs for microservice can be deferred before charging of the product becomes more realistic.

**Red flags:**

* Unconscious of the variations between systems of monolithic and microservice.
* The added cost for microservices is ignorant or inefficient.
* Unconscious of the increased overhead loss induced by IPC and microservices network interaction.
* So pessimistic about microservices disadvantages. Incapable of articulating ways to decouple monolithic applications so that when the time comes they are easy to split into microservices.
* Underestimates the value from microservices that are individually scalable.

**10. What is asynchronous programming, and why is it important in JavaScript?**

Synchronous programming means that code is performed sequentially from top to bottom, including conditionals and function calls, ignoring long-running functions such as queries from the network and I/O disk.

Asynchronous programming indicates the engine is running in an action loop. The application will be initiated when a blocking procedure is requested, and the program will continue to run without blocking the response. When the answer is complete, an interrupt is released, resulting in the execution of an activity handler where the control flow begins. In this way, most parallel operations can be done by a single program thread.

Through default, user interfaces are asynchronous and spend most of their time waiting for user input to split the process loop and activate event handlers.

By definition, the node is asynchronous, ensuring the database operates much the same way, waiting for a network query in a chain, then allowing further incoming applications while the first application is being treated.

In JavaScript, this is important because it is a very natural fit for user interface programming, and very useful for database performance.

**Good to hear:**

* A knowledge of what blocking entails and the consequences of results.
* A comprehension of the handling of events and why it is essential for UI software.

**Red flags:**

* Unfamiliar to the asynchronous or synchronous words.
* Implications of success or the interaction between asynchronous software and UI application can not be expressed.

**Conclusion**

Stick with subjects of the highest level. If they can answer these questions, it typically means that they will have ample programming experience in a few weeks to pick up language glitches & syntax, even if they don't have much JavaScript knowledge.

Do not disqualify candidates based on easy-to-learn stuff (including classicCS-101 algorithms or any kind of puzzle issue).

What you really need to ask is, "Does this applicant know how to put together an application?"

For the spoken Interview, that's it.

I put a much stronger emphasis on programming issues in actual interviews and watching code for candidates. Within "[Master the JavaScript Interview](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36)" episode, these subjects are covered in depth.