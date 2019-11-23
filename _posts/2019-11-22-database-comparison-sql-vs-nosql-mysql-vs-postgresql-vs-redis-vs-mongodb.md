---
title: Database Comparison - SQL vs. NoSQL (MySQL vs PostgreSQL vs Redis vs MongoDB)
image: "/assets/default-social-image.png"
categories: database-comparison
---

I've recently carried out a number of database operations that took hours or days to complete that forced me to look for a new, better alternative to my current database engine. To help myself out, based on the performance of the database, I sought to find a comparison, but couldn't find anything suitable. That's when I decided to make a small comparison of my own.

**Databases**

I used four databases for my analysis:

* MySQL
* PostgreSQL
* Redis
* MongoDB

The main difference between the SQL and NoSQL here is that the former, also called as RDBMS (Relational Databases)  have a relational structure and vertically scalable (meaning the work is done by one final machine), NoSQL does not use a relationship and it is horizontally scalable, means that multiple smaller machines will work for you.

Because of the build differences, Comparing NoSQL and SQL databases is difficult. A user by the name ‘Euphoric’ on StackExchange, made a good comment on this:

The thing you are missing about NoSQL is that NoSQl cannot be compared to SQL in any way. NoSQL is name of all persistence technologies that are not SQL. Document DBs, Key-Value DBs, Event DBs are all NoSQL. They are all different in almost all aspects, be it structure of saved data, querying, performance and available tools.

I’m going to test only select, update, insert and remove operations for this comparison which can be applied to both SQL and NoSQL.

Google trends displays a high interest rate for MySQL in searches, but does that means it has the highest performance?

**MySQL** is a full-featured, open source, relational database management system written in C and C++ which works with most OS engines out there, and I used 5.7 version for our comparison, which is hopefully supported till october 2023. MySQL is sponsored by the company MYSQL AB.

**PostgreSQL** is also an open-source, relational database management system which provides support for advanced data types and optimization. It is not controlled by a single company but is developed through community effort of diverse group of many companies and individual contributors.

**Redis** (Remote Directory Server) is an open source, in-memory key-value data structure store, Redis supports different kinds of abstract data structures, such as strings, lists, maps, sets, sorted sets, HyperLogLogs, bitmaps, streams, and spatial indexes which can be used as a database, cache or message broker and in GitHub, Pinterest and Snapchat, it is used as a NoSQL database. Its performance and data structure atomic manipulation solves problems which often can be spotted with the relational databases.

**MongoDB** is a general purpose free, open source, document-based, distributed database, NoSQL and cross-platform document-oriented database program (which uses JSON-like documents with schema). Document (record) values can be looked up by their field’s key, which makes MongoDB extremely versatile. Its fields and value follow the columns of a table and the individual records match the rows which makes it distinct compared to SQL servers such as MySQL or PostgreSQL.

**Tools**

For comparison, I collected some databases and needed to use a language with good drivers for them. I didn't have to search, because Python, which I use already provides a lot of good drivers for these databases.

The drivers that I used for the specified database are:

* MySQL -> MySQL Connector
* Postgres -> psycopg2
* Redis -> redis-py
* MongoDB -> PyMongo

I created Docker-compose, which handled the databases as services to manage all the databases in a single application, which helped me a great deal to avoid installing every database locally.

Take an example that I used to generate sample data:

```
version: '3'
services:
 postgres:
   container_name: postgres_container
   image: postgres
   environment:
     POSTGRES_USER: ${POSTGRES_USER:-postgres}
     POSTGRES_PASSWORD: ${POSTGRES_PASSWORD:-postgres}
     PGDATA: /data/postgres
   volumes:
     - postgres:/data/postgres
   ports:
     - "5432:5432"
   restart: unless-stopped
 mysql:
   image: mysql:5.7
   privileged: true
   command: "--skip-grant-tables"
   volumes:
     - my-datavolume:/var/lib/mysql
   environment:
     MYSQL_ROOT_USER: mysql
     MYSQL_ROOT_PASSWORD: mysql
     MYSQL_DATABASE: mysql
     MYSQL_USER: mysql
     MYSQL_PASSWORD: mysql
   ports:
     - '3306:3306'
 mongodb:
     image: mongo:latest
     container_name: mongodb
     ports:
         - "27017:27017"
 redis:
   container_name: redis
   image: redis
   ports:
     - "6379:6379"
   volumes:
     - ../data/redis:/data
   restart: always

 web:
   build: .
   depends_on:
     - postgres
     - mysql
     - redis
     - mongodb
volumes:
   postgres:
   My-datavolume:
```

I have created a database dispatcher that executes a specified operation for each database, in order for each operation to create a similar execution.

Here, the insert operation part can be seen:

```
class DataDispatcher:
   databases = {
       'mysql': MySQLDatabase(),
       'postgres': PSQLDatabase(),
       'redis': RedisDatabase(),
       'mongo': MongoDatabase()
   }

   def get_insert_data(self):
       insert_data = {}
       for name, database in self.databases.items():
           print(Insert for: {name})
           insert_data[name] = database.generate_insert_data()
       return insert_data
```

**Operations**

We will be looking at create, read, update, and delete and I used all CRUD operations for the comparison.

In the create category, We can see that Mongo and Redis are at the top and MySQL seems promising at about 400-500 ops but as usual but after around 600, we notice that the performance is decreased, along with Postgres.

The select operation has Mongo and Redis independent on operations where time is constant, but SQL is worst here. Time grows rapidly for performing in MySQL and Postgres.

Time consumption for update is highest in Postgres where it takes 10 seconds for 5000 records. For comparison, MySQL and Redis and Mongo is under 1 second while increase in time is almost similar for both databases.
 
The delete operation for Redis is very promising, time is independent or stable for removal of many records in memory for all but the almost instant removal in Redis seems good. This is slightly different for mongo where the time is dependent on records to some extent. We have seen the biggest differences in results here.

**Conclusion**

This conclusion is in the sense that measured single use case of the database and time for a specific operation type. When I performed operations to find records with a specified value it was logical that Redis should win, as it is just key/value storage to provide the best performance.

NoSQL creates optimization for the deformalized case and relies on demoralization. And there won’t be a need to perform any join operations because take as an example for a blog post, everything connected with single text, comments or likes will be stored in a single document.

Also here, we should remember that SQL can perform many more operations but we can see that single CRUD operations are much faster in NoSQL databases in comparison. But besides this, the overall speed of the database depends on the actual application you are creating.