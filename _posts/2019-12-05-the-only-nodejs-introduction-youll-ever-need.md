---
title: The only NodeJs introduction you’ll ever need.
image: "/assets/default-social-image.png"
categories: Node.js
---

When you write front end code, you can easily write web applications with NodeJs as both rely heavily on JavaScript.

It is quite crucial to understand that Node is not a perfect solution, for every project it isn't always the best solution. Anyone can establish a server in Node, but creating web applications which scale takes a broader grasp of the language.

I've had a great time with Node lately and I believe I've managed to learn enough to associate, get guidance and learn more, in particular, to improve my skills.

lets get ahead to it.

**Before Node.js.**

Web apps are developed in a client/server paradigm where the user requested the database services as well as the server replied with the information. Only when the user requested, the server responded and it would close the connection after each response.

This pattern is effective as it takes time and resources (memory, CPU etc) for every request to the server. So, after serving the requested asset, it is wiser to close a connection so that the server could also respond to other requests.

But how do servers such as these react simultaneously to millions of requests? If you were to bring that up, you agree that it would not be good to postpone requests to databases until all other requests have been addressed.

Consider entering Facebook and you've been told to wait 5 minutes for thousands of individuals for completion of request before you. There must be a way to run thousands of requests or at least hundreds at once. Great news!! As because of `Threads`, there's not an issue.

Threads are a way of running multiple operations simultaneously in machines. So each request would open a new thread, each thread had everything it needed to finish that same script.

If it sounds weird? Let us use an analogy.

Assume a restaurant that serves food with just one person. When food demand increases, situations could go way off the mark wildly. Customers would then have to struggle for the fulfillment of all existing orders first. Will hiring additional people to serve food better become a way to solve this issue? It could serve more clients at once.

Every thread here is a new employee. And browsers, well, people who are hungry. Now I am sure you might've got the point now.

But there's a drawback to this process. It'll get to a stage where a great deal of requests are being made and launching new threads would consume a lot of memory and system resources. Just as it is in our example, this would cost more money as well as space to employ the more people to serve food.

But it's also a good thing that the server will respond to the browser quickly now, the connection will be then closed and all resources (memory etc) will be retrieved.

One advantage of this scheme would be that it specialises in intensive CPU applications. It requires a lot of logic and more time to quantify CPU-intensive operations. Since each each application is addressed by a new thread, the main thread requires serious effort, making the system quicker and capable of performing essential computations.

It is quite effective since the main thread is executed by each operation. Perhaps things could get better?

**Here comes NodeJs.**

Consider that we have this multi-threaded database (running Ruby on rails) which reads and sends a document stored on the server to the user demanding it via his browser. It is important to consider that Ruby is not going to read the document explicitly for us. Ruby will inform the `file system` to read the file and return the content. The file system is a software used on a device to store and retrieve data.

The implication is, until the file system is finished, Ruby's still staying there doing nothing. And now the data is stored by Ruby and the information is sent to the client via browser.

This is where NodeJs starts coming across. Node uses the idle time to manage certain requests while the file system is processing the script. It'll be smart enough to tell Node to come and take the resource and give it to the client when the file system is finished. This is possible due to the `event loop` of the Node.

The node consists primarily of JavaScript and the loop of the event.

Basically, the event loop is a program which waits for events and deploys them when they occur. Another crucial fact that you may know is that JavaScript is a single threaded, so is a node.

Remember the example of our restaurant? Node, no matter the crowd, it would have only one person to serve food.

NodeJs takes all requests and then delegates much of the work to other system workers, unlike other languages which requires a new thread or process for each single request. There is something called a library called `Libuv` that effectively handles this work with the help of the kernel of the OS. When the background workers start doing their job, they emit events registered on that event to NodeJs callbacks.

That brings us to `callbacks`. These are simply structures which are transferred as arguments into other functions and are called if certain conditions happen.

So what developers of NodeJs practically do is compose handlers of events that are called if certain events occur.

NodeJs is much faster than processes of multiple threading systems. Even with just single thread.

That's because programs do not usually consist solely of numerical, arithmetic and logical computations that take a lot of time. In reality, they always write something to the file system a lot of times, perform network requests or access peripherals like the console or an external device. Node thrives in such situations. It immediately transfers the job to someone else when it encounters them and handles many incoming requests

Whether you are observing this exclusively, you might have also hypothesized that NodeJs does not excel in CPU-consuming operations. The main thread (only thread) is overloaded by intensive CPU operations. It is best to prevent these activities when using single threaded structures so that the main thread can do other tasks.

Understanding that everything in JavaScript operates parallel with the exception of your script, is essential. Even when other workers perform their jobs simultaneously, the program performs one thing at a time.

Let’s us another analogy again if in case you didn’t quite grasp it.

Consider a king with thousands of other servants, the king is composing a list of things he needs the servant to do (a lengthy list), a servant is taking it and delegating tasks to all the other servants. He takes his result to the king when someone is finished. While the servants were working, the king is always busy making other lists, so he collects his result and gives him another job.

The implication here is that even though there are a lot of things running parallel, the king does one thing at a time. The king is your script in this anology, and the servants are background staff for NodeJs. With the exception of your code, everything happens in parallel.

Let’s proceed!

**Writing web apps with NodeJs.**

Node-based web apps involve writing event handlers that are named if certain node events happen. Let's look at an example.

#1. Use your terminal or command prompt to create a new directory, cd into that folder.
#2. Write `npm init,` press enter until a `package.json` file is successfully created in the folder root.
#3. Create a `server.js` file, copy and paste the script written below in the root folder.

```
//server.js
const http = require('http'),
      server = http.createServer();

server.on('request',(request,response)=>{
   response.writeHead(200,{'Content-Type':'text/plain'});
   response.write('Hello world');
   response.end();
});

server.listen(3000,()=>{
  console.log('Node server created at port 3000');
});
```

#4. Type `node server.js` in the command prompt and press enter. You will see something like this.

```
node server.js
//Node server started at port 3000
```

Open the browser and enter [localhost:3000](http://localhost:3000/). You should see a message: `Hello world`.

We required the `http` module on the first line. As an interface to handle http processes the module provides, we call the `createServer()` method that generates a server.

Next, we bind the server object to an event handler for `requests`. The on method takes a second callback argument The callback takes as arguments for two objects The `request` and `response` objects that have incoming request and outgoing response information.

We may let Node do some work for us as well.

```
//server.js
const http = require('http'),
server = http.createServer((request,response)=>{
    response.writeHead(200,{'Content-Type':'text/plain'});
    response.write('Hello world');
    response.end();
});
server.listen(3000,()=>{
   console.log('Node server created at port 3000');
});
```

Here we simply perform a callback pass to `createServer()` and Node adds for us the `request` event handler. At this level, we are concerned only with the `request` and `response` object

We use the `response.writeHead()` to attach some headers to the response of the server (status code and type of content), web page is being written by `response.write()`. Then we use the `response.end()` to terminate the server response.

Eventually, we're informing the server to listen to a port (3000). So when we are developing web application on our local computers, we can at least see a prototype of our web app. (localhost:3000). As a second argument, the listening method takes a callback. The server is started immediately with this callback.

**Getting used to callbacks in Node.**

Node is an evented environment with a single thread, which means that everything responds to events. Callbacks are functions which are passed as arguments to other functions and are called when an event occurs.

Our example can be futher coded as.

```
//server.js
const http = require('http'),
      
makeServer = function (request,response){
   response.writeHead(200,{'Content-Type':'text/plain'});
   response.write('Hello world');
   response.end();
},
      
server = http.createServer(makeServer);

server.listen(3000,()=>{
  console.log('Node server created at port 3000');
});
```

`makeServer` is a callback here, as functions are JavaScript entities of first order, they can be moved into variables and then to other functions.

If you're not familiar on using JavaScript, you may need some time to get used to programming which is evented.

You might get into trouble with callback hell if you begin to do some serious JavaScript writing. At which your script becomes difficult to follow because there are several deeply nested functions. You may want to consider more sophisticated and more effective ways to replace callbacks when this occurs. Look at promises, [Eric Elliott](https://medium.com/u/c359511de780?source=post_page-----d969a47ef219----------------------) wrote a [JavaScript interviews guide: What is a promise](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261). It's a nice starting point to get ahead.

**Routing in NodeJs.**

A server holds loads of files, showing the network what they're searching for when browsers ask it. The server responds by providing them with the files they request. `Routing` is the thing that this happens.

In NodeJs, we have to define our routes manually which isn't a big deal, here's a simple thing to do.

```
//server.js
const http = require('http'),
      url = require('url'),
 
makeServer = function (request,response){
   let path = url.parse(request.url).pathname;
   console.log(path);
   if(path === '/'){
      response.writeHead(200,{'Content-Type':'text/plain'});
      response.write('Hello world');
   }
   else if(path === '/about'){
     response.writeHead(200,{'Content-Type':'text/plain'});
     response.write('About page');
   }
   else if(path === '/blog'){
     response.writeHead(200,{'Content-Type':'text/plain'});
     response.write('Blog page');
   }
   else{
     response.writeHead(404,{'Content-Type':'text/plain'});
     response.write('Error page');
   }
   response.end();
 },
server = http.createServer(makeServer);
server.listen(3000,()=>{
 console.log('Node server created at port 3000');
});
```

Paste this script into your server.js file, navigate and run it to your browser and go to localhost:3000 and localhost:3000/about, with node server.js. Try to do it with a localhost like:3000/somethingelse. Is that to our error page?.

Although this may fulfill our instant need to initiate a server, but with every web page on the server, it would be crazy to do it. No one actually does this, but it's just to provide an idea of how things work.

We required another module if you asserted; `url`, which offers us a simple way of working with urls.

The `.parse()` method takes an url as a request, splitting it into `protocol`, `host` `path`, and `querystring` etc. It's okay if you don't get this part.

When we do url.parse(request.url.pathname), it gives us the pathname or url that is largely what we use for requests for routing. Nonetheless, it can get better and easier.

**Routing with Express.**

You must have heard of Express if you've done any underground research. It is a platform for NodeJs to easily create web apps and APIs. Since you want to write apps for NodeJs, Express will also be required. It makes all this simpler, which you will see. 

Navigate to your root folder in your terminal or command line, write `npm to install express—save`. This will install the express package. We need it to be make it available in our program.

`const express = require('express');`

That's as easy as it will become.

Now, let's build some basic express routes.

```
//server.js
const express = require('express'),
      server = express();

server.set('port', process.env.PORT || 3000);

//Basic routes
server.get('/', (request,response)=>{
   response.send('Home page');
});

server.get('/about',(request,response)=>{
   response.send('About page');
});

//Express error handling middleware
server.use((request,response)=>{
   response.type('text/plain');
   response.status(505);
   response.send('Error page');
});

//Binding to a port
server.listen(3000, ()=>{
  console.log('Express server started at port 3000');
});
```

Does that look clean? I hope you may already have tuned. We called it a function after importing the express module. It starts our journey on the server

Now we will be trying to set the `server.set()` for port and `process.env.PORT` takes the environment port on which the app runs, and we default it to 3000 if it is not available.

When you followed the above script, a pattern follows the routing in Express.

`server.VERB('route',callback);`

VERB is one of the GET, POST etc, pathname is a string which gets appended to the domain. And the callback is any function that we want to fire once the requests come in.

Another thing we do is.

`server.use(callback);`

In express, any time you see a `.use()` process, it's called a `middleware`. Its functionality helps us for some heavy http lifting. The middleware is an error handling in the program above.

Eventually, we perform our usual `server.listen()`, right?

For NodeJs apps, this is what routing feels like. We proceed further into the node databases

**Databases in NodeJs applications.**

Several people prefer the idea of doing everything using JavaScript. There are some servers that can blend in well. Like CouchDb, MongoDb and other databases. Such databases are systems that are NoSQL.

In a key/value model, a NoSQL server is organized as such. It is document-based so information in a tabular form is not kept.

Now we are going to look at mongoDB, a NoSQL database that is document based. If you've used MySQL, SQL server, etc databases, The notion of these relational databases such as tables, rows and columns should be familiar to you. It's not that much of a player other than MongoDB.

Here is an article from the official website of Mongo comparing Mongo and MySQL: [MongoDB and MySQL Compared](https://www.mongodb.com/compare/mongodb-mysql?source=post_page-----d969a47ef219----------------------)

To make things more structured, you're supposed to be using the Mongoose which mostly enforces a schema, basic type checks and validate our documents before exporting them to Mongo. Among Mongo and Node, it serves as a middleman.

To begin with Mongo, go over to the official website of Mongo, download it, navigate to the community server, and select your operating system and spec.

This is a long post, make sure to check the official [mongoDB setup](https://docs.mongodb.com/manual/installation/) guide to get going and keep things short and distinct.

[Chris Sevilleja](https://medium.com/u/3197a2cc5a44?source=post_page-----d969a47ef219----------------------) even wrote for [Easily Develop Node.js and MongoDB Apps with Mongoose](http://easily%20develop%20node.js%20and%20mongodb%20apps%20with%20mongoose/) and I believe it should begin with Mongoose as a general guide.

**Building RESTful APIs with Node and Express.**

APIs are a way to transmit data to each other for web based applications. Have you ever used a website in which you use your Facebook account to log in or sign off. Facebook provides a part of its features for other applications to utilise. That's the glance of an API.

A RESTful API is something that has no idea of the state of each other for the server or client. Various clients enter the same REST endpoints by using a REST api, execute the same behavior, and collect the same answers without consideration to each other's condition.

An end point of an API is a particular function returning information in an API.

Sending data in JSON or XML format involves creating a RESTful API. Let's try in NodeJs to make one. When an user requests via Ajax, we must create one that returns dummy json information. It's not a sophisticated API, but it's going to help us understand how things work in Node. Now,

1. Create a `node-api` named folder
2. Go to the command line into folder, by `npm init` which builds a file containing all our dependencies.
3. To setup express, do `npm install --save express`.
4. In the root directory, create `server.js`, `index.html`, and `users.js` files.
5. Write the following code in the respective files.

```
//users.js
module.exports.users = [
 {
  name: 'Mark',
  age : 19,
  occupation: 'Lawyer',
  married : true,
  children : ['John','Edson','ruby']
 },
  
 {
  name: 'Richard',
  age : 27,
  occupation: 'Pilot',
  married : false,
  children : ['Abel']
 },
  
 {
  name: 'Levine',
  age : 34,
  occupation: 'Singer',
  married : false,
  children : ['John','Promise']
 },
  
 {
  name: 'Endurance',
  age : 45,
  occupation: 'Business man',
  married : true,
  children : ['Mary']
 },
]
```

These are the data that we want to share with other applications. We export it so that it can be conveniently used by any application. That is the premise. We store the array of `users` in the object called `modules.exports`.

```
//server.js
const express = require('express'),
      server = express(),
      users = require('./users');

//setting the port.
server.set('port', process.env.PORT || 3000);

//Adding routes
server.get('/',(request,response)=>{
 response.sendFile(__dirname + '/index.html');
});

server.get('/users',(request,response)=>{
 response.json(users);
});

//Binding to localhost://3000
server.listen(3000,()=>{
 console.log('Express server started at port 3000');
});
```

Here we `require('express)` and use `express()` to create our server. If you look carefully, you will see that we need something else as well. That's our `users.js`, do you recall the data stored we would be sharing? We need it to work our software.

Express has some approaches to help us send some content to the browser. The `response.sendFile()` scans for the file and submits it to the browser. We use a `__dirname` here to get the root folder from where our server runs, then add `+ 'index.js'` to make sure we target the correct file.

The `response.json()` transfers information from `json` to requesting websites. We move it on to an argument, array of users that is what we actually share. The remaining, I think, would look familiar to you.

```
//index.html

<!DOCTYPE html>
<html>
<head>
 <meta charset="utf-8">
 <title>Home page</title>
</head>
<body>
 <button>Get data</button>
<script src="https://code.jquery.com/jquery-3.2.1.min.js" integrity="sha256-hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4=" crossorigin="anonymous"></script>
 
  <script type="text/javascript">
  
    const btn = document.querySelector('button');
    btn.addEventListener('click',getData);
    function getData(e){
        $.ajax({
        url : '/users',
        method : 'GET',
        success : function(data){
           console.log(data);
        },
      
        error: function(err){
          console.log('Failed');
        }
   });
  } 
 </script>
</body>
</html>
```

Tap `node server.js` right in the root directory. Now, open your browser. Go to http://localhost:3000/, click the key and access the console of your browser

`btn.addEventListent('click',getData');` where getData makes an ajax request to 'GET' it. It contains a function of `$.ajax({properties})` that sets parameters such as `url`, `success` and `error`, etc.

You're not just going to be reading JSON files in real world applications. You want information to be generated, interpreted, modified and removed. These are allowed by Express by htttp verbs, as POST, GET, PUT and Delete respectively.

Chris Sevilleja wrote: Build a RESTful API with Express 4 to learn more into building APIs for Express.

**Networking with NodeJs sockets.**

A computer network is a computer connection in which data can be shared and received. We need the `net` module to do networking in NodeJs.

`const net = require('net');`

There must be two endpoints in the Transmission Control Protocol (TCP); one endpoint(computer) connects to a numbered port while the other connects to the network.

Take another analogy if you didn’t get that.

Picture your mobile phone. You are assigned a number when you purchase a sim and you bound to that figure. They connect to your phone anytime your buddies want to call you. You are one endpoint and another endpoint is your caller.

You must have understood now.

We will create a program to cement this knowledge that watches a file and informs connected clients when the file changes. Let's dive into it right now.

#1. Create a `node-network` named folder.

#2. Create `filewatcher.js` , `subject.txt` , and `client.js` files and Put the following in `filewatcher.js`

```
//filewatcher.js

const net = require('net'),
   fs = require('fs'),
   filename = process.argv[2],
      
server = net.createServer((connection)=>{
 console.log('Subscriber connected');
 connection.write(`watching ${filename} for changes`);
  
let watcher = fs.watch(filename,(err,data)=>{
  connection.write(`${filename} has changed`);
 });
  
connection.on('close',()=>{
  console.log('Subscriber disconnected');
  watcher.close();
 });
  
});
server.listen(3000,()=>console.log('listening for subscribers'));
```

#3. We should subsequently provide a file to watch. Place this in subject.txt and save it.

`Hello world, I'm gonna change`

#4. Lets create our client next, Save this to client.js .

```
const net = require('net');
let client = net.connect({port:3000});
client.on('data',(data)=>{
 console.log(data.toString());
});
```

#5. We're going to need two terminals. We run the `filename.js` with the file name in the first one to watch it like that.

```
//the subject.txt will get stored in our filename variable
node filewatcher.js subject.txt
//listening for subscribers
```

We run client.js on another terminal.

```
node client.js
//watching subject.txt for file changes.
```

Proceed to change and save any changes you do to `subject.txt`. Look at the terminal `client.js` and watch the additional line.

`//subject.txt has changed.`

One of a network's main features is that many clients will connect concurrently. Begin another command line, switch to `client.js`, execute `node client.js`, modify and save the subject.txt file again.

**What are we doing?**

If you didn’t understand, let’s go over it.

Basically, our filewatcher.js does three things

1. `net.createServer()` creates a server for multiple clients to send messages.
2. `console.log()` and `connection.write()` communicates to the network that connection is done by the client and informs the client that a document is being looked at.
3. `filewatcher.js` when eventually the client disconnects, the file watches the watcher variable and closes it.

```
//filewatcher.js

const net = require('net'),
   fs = require('fs'),
   filename = process.argv[2],
      
server = net.createServer((connection)=>{
 console.log('Subscriber connected');
 connection.write(`watching ${filename} for changes`);
  
let watcher = fs.watch(filename,(err,data)=>{
  connection.write(`${filename} has changed`);
 });
  
connection.on('close',()=>{
  console.log('Subscriber disconnected');
  watcher.close();
 });
  
});
server.listen(3000,()=>console.log('listening for subscribers'));
```

We need two modules, fs and net to relatively read and write files and link to the network. When you keep a close eye on the process.argv[2], the mechanism is a global variable which contains vital information about running NodeJs code Argv[] is an array of arguments. When we mention argv[2], the third argument used to run the code of NodeJs is referred to it. We would enter the file name in the command line as the third argument argv[2]. Did you remember this?

`node filewatcher.js subject.txt`

We do have something very closely associated; when a client connects to the port, the `net.createServer()` fires and acknowledges a callback. The callback just requires one parameter that is the entity which interacts with the clients connecting.

The function `connection.write()` sends data to any client that connects to the 3000 port. In this scenario, the object of our `connection`. and we're telling the user that a file is being watched.

The `watcher` has a feature which sends information that it has modified the document being watched for the `client`. And by leaving the operation, when the `client` exits the connection, the on `close` event fires and the event handler sends signal to the server and closes the `watcher`.

```
//client.js
const net = require('net'),
      client = net.connect({port:3000});
client.on('data',(data)=>{
  console.log(data.toString());
});
```

`client.js` is quite simple, we need the `net` module and link it to port 3000. So we listen to the event of the data and log it into the console.

You will realize that every time a `connection.write()` is created by our `filewatcher.js`, our client receives a `data` event.

This is just a glimpse of how networks operate. Primarily, when certain events occur, one endpoint transmits messages and each connected client receives them as a `data` event.

If you'd like to look further into node networking, here's a post from the official documentation of NodeJs; [The net module](https://nodejs.org/api/net.html). You may also want to read: [Building a Tcp service using Node](https://blog.yld.io/2016/02/23/building-a-tcp-service-using-node-js/#.Wmcc6qinG00).

Now that was quite some exercise.!!

If you want to create NodeJs scalable web apps, you need to learn more than just writing servers and express routing. I suggest few books:

* [NodeJs the right way.](https://www.amazon.com/Node-js-Right-Way-Server-Side-JavaScript/dp/1937785734)
* [Web Development With Node and Express.](https://www.amazon.com/Web-Development-Node-Express-Leveraging/dp/1491949309)