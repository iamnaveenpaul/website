---
image: "/assets/default-social-image.png"
title: 'Relational vs. non-relational databases: Which one is right for you?'
categories: Database
---

All right, because we understand you must assess the technical differences in comparison between relational and non-relational databases. However, it is essential for your data model to be whiteboarded before immersion and to define the priority scalability plays for that particular model. Don’t be intimidated anytime to use low-tech devices such as different colored designs with colored pens or pencils, draw it on a page if you need it. It's a clear idea to begin with, and a picture can certainly help you.

You have to ask the right questions in order to make the software template whiteboard as accurate as possible. Not unexpectedly, fuzzy or insufficient questions lead to bad or inadequate information. And that is not our intention, whether you choose the relational or non relation database, when programmatically modeling and solve the problem of someone's real life.

Relational DBMS flatly represents the data and non relational DBMS permits hierarchical representation of the data. Nevertheless, even then, the statement is far too detailed and thin to make any sense. A relational DBMS is essentially a DBMS, which at least conceptually presents data in a form that conforms to the relational model for its clients, users and applications. What this means specifically is not so clearly defined as you would like, and for example, it is not agreed by all whether or not you can nest/hierarchical data. Let's stop and push ahead now, we will have that out of the way.

**Relational databases**

So what exactly is a related database? Relational databases such as MySQL, PostgreSQL and SQLite3 are tables and rows which store and display data. It is based on an algebraic theory branch known as relational algebra. Non-relational databases such as MongoDB represent data in JSON collections. JSON, CSV and TSV file formats are available for import by the Mongo import tool. Technically, Mongo query data targets are represented as BSON (binary JASON).

Structured query language (SQL) is used by relational databases, making them a good choice for applications involving multiple transactions. The structure of a relational database allows you the use of foreign keys (or indexes) to connect information from different tables that are used in the uniqueness of any atomic data piece. Additional tables may refer to the foreign key so that the link between its data and the piece indicated by the foreign key is created. This is useful for applications which are heavy to analyze data.

You'll probably want to stick with a relational database if you want to handle your application with many complicated queries, database transactions and routine data analyses. And it is critical that you perform these transactions efficiently if your software is to rely on multiple server transactions. This is the real point of ACID (the collection of property ensuring accurate database transactions) and of the referential integrity.

**Referential integrity (and minimizing ORM Impedance Mismatch)**

Referential integrity is the concept in which multiple database tables share the relationship based on data stored in the tables. This usually happens when you add, delete and update cascades. Let's discuss an app that helps victims of human trafficking find a safe home and access victim services in real time for an instance of applying referential integrity.

Suppose the city or county X has two tables: a Survivor Shelter Table and a Support Table of the Shelter for Trafficking. There are two columns on the Trafficking Shelter table; Shelter ID (which might be EIN / FEIN) and Shelter Name. The Trafficking Shelter Grant table also includes two colums: Shelter ID (shelter identity) and the amount of funding provided for Shelter ID (Shelter identity). This shelter needs to be removed from Local X because it is no longer available. And as Shelter A is still accessible on the Shelter Funding List, they have to delete it. We can do this correctly and with minimum discomfort, by implementing referential integrity.

Here’s how:

First, define our primary key as the Shelter ID column in the Shelter table. Instead, in the Shelter Funding panel, identify the column for the shelter ID as an internal key leading to the main key (that is the column for the shelter ID in the shelter row). Once we define our relationship between foreign and primary, we have to add limitations.  Particularly one limit is referred to as delete cascading. It ensures that entries for the same shelter will be automatically removed from the Shelter Finance table when a shelter is excluded from the Shelter's table from our list.

Finally, take note of what was the main key and why. Each non-profit Organization with 501(3)c designation is given an EIN in our small example of counter trafficking ngos, equivalent to the social security number of a person. Therefore it makes sense that, in tables where other information is related to the shelter of any individual survivor of slavery in the shelter column, this common id is the primary key, to be implied by international keys.

Please be aware that three rules apply for referential integrity:

* The shelter funding table can not be reported unless the international main points to an actual shelter in the shelter table for that information. This can be viewed as a policy "No Unattended Child" and "No Orphans."
* If a record is deleted in the shelter table, all relevant records must also be deleted in the shelter finance table. Cascade extraction is the best approach to doing it, also known as cascade delete.
* If modifications to the main key for the Shelter table file, the subsequent Shelter funding data must also be updated using something known as a cascade update, and all possible future tables that contain information relevant to Shelter table.

The individual responsible for designing the server scheme is responsible for instilling and preserving referential integrity. If a schema seems like an awkward job to build a server, consider: until 1970 (when the relational database was born), all databases were flat; information are contained in an expansive text file called a tab delimited directory, in which the pipe character “|” separated each entry. It was a complicated, boring, time consuming effort to find relevant information in order to evaluate and examine. With relational databases you can search, sort and analyze specific data pieces without sequential searching via an entire file (or a database), including all data pieces you don't want. In comparison with other data you can usually use other data pieces.

They need not dig through the whole database of information in the previous example of the relational database (Postgresql) to find information about the facility, which either has its funding slowed down and is expected to shut out due to lack of financing/funding. We can check for shelters in a specific area or position by using a simple SQL SELECT * FROM statement without having to pass through all information, including shelters not in that region.

Object Relational Mapping (ORM) refers to the programmatic process of converting information into object oriented programming languages (such as Ruby) between incompatible types of systems. The concept of ORM libraries was briefly discussed in our tutorial on [Getting started with Rails](http://blog.pluralsight.com/tutorial-rails) in the context of a ruby program (especially a Rails app).

**When to non-relate:**

Although relational databases are great, we have to deal with their limits/inabilities. One is ORM Impedence Mismatch, as relational databases were not initially developed with the existing OOP languages in mind. The best way to avoid this issue is to build a referential integrity system for your database schema at its core. So you need to think about setting up your primary and foreign keys, how you use constraints (including update and delete cascade), and how you write your migrations when using a relational database with an OOP (like Ruby).

However, if you deal with a huge number of data, the probability of error (in the form of an ORM Impedance Mismatch issue) can become far too tedious. You might need to suggest using a non-relational database in such a case, which only stores data from different tables (or buckets) with each other without definite and organised mechanisms.

The Mongo repository of MongoDB Ember Angular and Node.js (MEAN) stack developers is a common non relational database since it is primarily written in JavaScript; JSON is a lightweight JavaScript Object Notation. If your data model becomes very complex, or if you find your database schema to be denormalized, it may be best to use non-relational databases like Mongo. Additional reasons for selecting a database not related include:

* The serialized arrays must be stored in JSON objects.
* Store records with different fields or attributes in the same collection.
* The database schema tending to be denormalized or to code for reliability or horizontal scalability issues.
* Problems with the design of your software model effectively predefine the schema.

Suppose we were to create an app and our instance of safe houses was part of a data model that had too many tables and was too difficult to provide context credibility making the referential integrity extremely difficult. Then, they can handle the image of the NGOs and trafficking victims by using Mongo:

Note that the output is nice and easy to read. Mongo is usable by JavaScript, and from the point of view of a MEAN stack programmer, a repository/database not readily available would not make sense. The MongoDB platform is well defined and includes simple, succinct descriptions of how you can create and use a Mongo server/database. MongoDB allows developers to configure the stream of the software completely on the code side as a NoSQL repository. The fact that the entities described in the database are placed on the template that the implementations are not readily utilizable on the front end or vice versa, and is one of the biggest problems MEAN Stack Developers have with relational databases.

However, not only MEAN stack developers decided that the best way to go was through a non-relational database. Additionally, the pioneer in the open source Hackety-Hack campaign, Steve Klabnik-a well-known member of the Ruby/Ruby on Rails team-chose the MongoDB. Of course, in taking this route he had to make compromises. This included difficulties re-factoring Hackety-Hack for Facebook, Instagram, Linkedin and Github profile encryption. Nonetheless, other programmers like Mongo are also credited for its excellent horizontal scalability.

One of the biggest advantages in going with a non-relational database is that your database is not at risk for SQL injection attacks, because non-relational databases don’t use SQL and are, for the most part, schema-less. Another major advantage, at least with Mongo, is that you can theoretically shard it forever (although that does bring up replication issues). Sharding distributes the data across partitions to overcome hardware limitations.

A major advantage of a non-relational database is that your database is not exposed to SQL injection attacks, as non-relational databases don't use SQL and are mainly schema-free. At least with Mongo, another major advantage is that you can share it theoretically forever, although it does raise replication problems. Sharding distributes the data to hardware constraints through partitions.

**Non-relational database disadvantages**

There are no links as there would be in relational databases, for non-relational databases like Mongo. It ensures that you have to make multiple queries or manually enter the information in your software with code, which can become incredibly frustrating and disgusting quite easily.

As Mongo does not automatically treat operations like transactions the way how relational database does, you must manually select to create a transaction, then manually verify it, commit it manually, or roll it back. Even the documentation on the MongoDB site warns that the success and failure of a database operation can not be a complete thing or nothing without taking any potentially time consuming precautions and as documents can be relatively complex and nested. Simply put, some operations are going to succeed while others fail.

All this brings us back to the beginning, to learn how to ask questions precisely to whiteboard the data model/template effectively, of course. This is the key step in determining the best route for your application flow. When you select the programming language that is used for writing your application and using one database over another, you will be able to identify the appropriate questions.