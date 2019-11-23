---
image: "/assets/default-social-image.png"
categories: Redis
title: 'Redis: What and Why?'
---

As users for our product started to grow rapidly at my work, since a few days ago. My seniors suddenly began to worry about the cost of AWS, meaning large database requests, long response times, large audience interaction and obviously large costs. As far as I knew saving data could be done via database only and it was really hard for me to grasp the whole situation because of my very little IT industry experience to know how to save the database requests?

I was wrong and we finally decided to do something known as caching after an hour of debate on how we can potentially save in the server the number of requests.

**So what is Caching and Cache?**

Cache is a hardware or software component that stores data to allow future requests for that data to be served more quickly; data stored in a cache that result from earlier computations or copies of data stored elsewhere. If the requested information can be located in a cache, a cache hit occurs while a cache miss occurs if it is not possible. Cache hits are served by reading cache data faster than recomputing a result or reading from a slower data store; therefore, the quicker the process performs the more requests that can be served from the cache.

Caching is the process of storing some data in Cache.

For our purposes of this Caching, we decided to go with Redis.

**What is Redis?**

Redis (Remote Directory Server) is an open source, in-memory key-value data structure store, Redis supports different kinds of abstract data structures, such as strings, lists, maps, sets, sorted sets, Hashes, HyperLogLogs, bitmaps, streams, and spatial indexes which can be used as a database, cache or message broker and in GitHub, Pinterest and Snapchat, it is used as a NoSQL database. Its performance and data structure atomic manipulation solves problems which often can be spotted with the relational databases.

**Why use Redis?**

* It is very fast! It was written in C afterall. On top of that, it is open source and secure and is of NoSQL Database which is incredibly awesome.
* So called Pun for Nerds and by Nerds of Databases.
* Redis is supported in most languages (Open Source Software Parks). Languages such as JavaScript, Java, Go, C, C++, C #, Python, Objective-C, PHP and nearly every popular language is supported, Hence it is developer friendly.
* To save the cloud server calls and potentially save some money out there, you can choose to cache the Redis like that, of course.
* Tech giants such as GitHub, Weibo, Pinterest, Snapchat, Craigslist, Digg, StackOverflow, Flickr are currently using it.

**Sample Redis Commands**

Although Redis comes with written documentation, I'm presenting few here to give the audience an idea. For the example, I use Redis-CLI. Redis-CLI runs at port 6379 by default.

Although Redis comes with written documentation, but in order to give idea to the audience, I am presenting few over here where I am using Redis-CLI for the demonstration. By Default, Redis-CLI runs on port 6379.

**SET (Setting a Key)**

```
127.0.0.1:6379> SET foo "Hello World"
OK // setting a key
```

**GET (Getting a Key)**

```
127.0.0.1:6379> GET foo
"Hello World" // getting a key
```

DEL (Deleting a Key)

```
127.0.0.1:6379> GET foo
"Hello World" // getting a key
127.0.0.1:6379> DEL foo
(integer) 1 // key just got deleted
127.0.0.1:6379> GET foo
(nil) // since key is deleted therefore, result is nil.
```

**SETEX (Setting a key with an expiry)**

```
127.0.0.1:6379> SETEX foo 40 "I said, Hello World!"
OK // key has been set with 40 seconds as expiration
```

**TTL (Total Time left for a key that has a timeout)**

```
127.0.0.1:6379> TTL foo
(integer) 36 // 36 seconds left to timeout
```

**PERSIST (Removing the timeout from key)**

```
127.0.0.1:6379> PERSIST foo
(integer) 1 // turning the key from volatile to persistent (key won't expire)
```

**RENAME (Renaming the current existing key)**

```
127.0.0.1:6379> RENAME foo bar
OK // renaming the key 'foo' as bar
```

**FLUSHALL (Flushing everything so far saved)**

```
127.0.0.1:6379> flushall
OK // just got flushed
```

Redis is extremely powerful and I also use it on a daily basis for faster data transfer between the applications. In short, Redis is cool!
So that brings us to the end of just an introductory part of what Redis can do.