---
title: Express JS & NodeJS RESTful API tutorial
image: "/assets/default-social-image.png"
categories: Express  JS Tutorial
---

In this tutorial we will see how to 

1. Install NodeJS, ExpressJs and Mongodb
2. Create a REST API endpoints in Express Js
3. Write Insert queries in Mongodb using Mongoose
4. Write update queries in Mongodb using Mongoose
5. Write find queries in Mongodb using Mongoose
6. Write delete or remove queries in Mongodb using Mongoose

The software installation is for Ubuntu OS but the rest of the app tutorial will work on windows setup as well. 

# Install the latest version of NodeJS and NPM
```
sudo apt-get update
sudo apt-get install nodejs
sudo apt-get install npm
```

# Install the latest version of Mongodb
```
sudo apt update
sudo apt install -y mongodb
```

The Installation starts automatically but it’s recommended to verify if the service is started and also if the database is working.
```
sudo systemctl status mongodb
```

The output should be like below

Output

```
● mongodb.service - An object/document-oriented database
   Loaded: loaded (/lib/systemd/system/mongodb.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2018-05-26 07:48:04 UTC; 2min 17s ago
     Docs: man:mongod(1)
 Main PID: 2312 (mongod)
    Tasks: 23 (limit: 1153)
   CGroup: /system.slice/mongodb.service
           └─2312 /usr/bin/mongod --unixSocketPrefix=/run/mongodb --config /etc/mongodb.conf
```


Now that our setup is done, lets start by installing express js using npm to kickstart our app development.

# Installing Express Js
Create a directory to hold your application, and make that your working directory. And then use the npm init command to create a package.json file for your application. Afte that install Express in the crudapp directory and save it in the dependencies list.

```
$ mkdir crudapp
$ cd crudapp
$ npm init
entry point: (index.js)
$ npm install express --save
```

Next open the index.js file in your favorite IDE or text editor and paste the following code in it.

```
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => res.send('Hello World!'))

app.listen(port, () => console.log(`Example app listening at http://localhost:${port}`))
```

And then go to your terminal and start the Nodejs server by running
```
$ node index.js
```

If you go to http://localhost:3000/, you should see **Hello World** in the broswer.

# Installing Mongoose
Mongoose is a MongoDB object modeling tool designed to work in an asynchronous environment. Mongoose supports both promises and callbacks.

```
$ npm install mongoose
```

After installation update our index.js with the below code. This will import mongoose into our app
```
const mongoose = require('mongoose');
```

Let's create a mongoose schema to store our data and also lets connect to Mongodb.

```
const express = require('express')
const app = express()
const port = 3000;
const mongoose = require('mongoose');

const Schema = mongoose.Schema;
const ObjectId = Schema.ObjectId;
 
const ourNewCollection = new Schema({
  title: String,
  body: String,
  date: Date
});

mongoose.connect('mongodb://localhost/my_database', {
  useNewUrlParser: true,
  useUnifiedTopology: true
});

app.get('/', (req, res) => res.send('Hello World!'));

app.listen(port, () => console.log(`Example app listening at http://localhost:${port}`))
```


Next we will create 4 different APIs as promised.

# POST request:
```
app.post('/save/data', function (req, res) {
	ourNewCollection.collection.insert([req.body],function(err,result){
		res.send(result)
	})
});
```

# GET request:
```
app.get('/fetch/all/data', function (req, res) {
	ourNewCollection.find({},function(err,result){
		res.send(result)
	})
});
```

# DELETE request:
```
app.delete('/delete/data', function (req, res) {
	ourNewCollection.delete({title:req.query.title},function(err,result){
		res.send(result)
	})
});
```

# UPDATE request:
```
app.post('/update/title', function (req, res) {
	ourNewCollection.update({title:req.query.title},{$set:{title:req.query.newtitle}},function(err,result){
		res.send(result)
	})
});
```

The final index.js should look like below.
```
const express = require('express')
const app = express()
const port = 3000;
const mongoose = require('mongoose');

const Schema = mongoose.Schema;
const ObjectId = Schema.ObjectId;
 
const ourNewCollection = new Schema({
  title: String,
  body: String,
  date: Date
});

mongoose.connect('mongodb://localhost/my_database', {
  useNewUrlParser: true,
  useUnifiedTopology: true
});

app.get('/', (req, res) => res.send('Hello World!'));

app.listen(port, () => console.log(`Example app listening at http://localhost:${port}`))

app.post('/save/data', function (req, res) {
	ourNewCollection.collection.insert([req.body],function(err,result){
		res.send(result)
	})
});

app.post('/update/title', function (req, res) {
	ourNewCollection.update({title:req.query.title},{$set:{title:req.query.newtitle}},function(err,result){
		res.send(result)
	})
});

app.get('/fetch/all/data', function (req, res) {
	ourNewCollection.find({},function(err,result){
		res.send(result)
	})
});

app.delete('/delete/data', function (req, res) {
	ourNewCollection.delete({title:req.query.title},function(err,result){
		res.send(result)
	})
});

```