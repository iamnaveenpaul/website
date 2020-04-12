---
title: How to convert excel to json with Node.js
image: "/assets/exceltojson.jpg"
categories: Node.js
---

How to convert excel to json with Node.js, Excel to json is a regular requiremnt for web applications node.js.

<img class="width-100" alt="How to convert excel to json" src="/assets/exceltojson.jpg"/>

You might sometimes have a necessity in an application to submit information via an Excel file or a task to interpret data from a bunch of Excel files or some analytics may be required to run. Excel files are commonly handled in web applications. This tutorial aims to make it easier for developers to read excel files using NodeJS.

You will be able to upload an excel file on your application to a particular path after this tutorial, read the file and convert it to json data, and then you can certainly do whatever you want with the programmatically sensitive data.

We're going to take care of two excel file formats. It transforms data from `'.xls'` and `'.xlsx'` to json.

**Roadmap**

Here we will do the following things.

1. Setup Node express server and routes
2. Upload file using Multer
3. Read and convert excel to json

Note: The portion below deals with uploading the files also, if not necessary you can skip directly to Read and further import Excel to json.

[DOWNLOAD](https://github.com/rahil471/excel-to-json-in-Node.js)

**Setting Up Express server and Multer for upload**

We've already done a File Upload tutorial, which includes setting up node-express together with multer for upload, where each stage has been explained in detail. Instead of repeating the same thing, we'll pick up pieces of software from there for this guide. For a detailed explanation, please give a look up to the tutorial below.

Navigate through your console to your working directory and perform the following commands.

```
npm init --yes
npm install express --save
npm install multer --save
npm install body-parser --save
mkdir uploads
touch app.js
```

Now I'll pick up the code from the guide for importing the file and adding it to my `app.js`. We're going to remove the unwanted code blocks at the same time.

**app.js**

```
var express = require('express');
    var app = express();
    var bodyParser = require('body-parser');
    var multer = require('multer');
    app.use(bodyParser.json());
    var storage = multer.diskStorage({ //multers disk storage settings
        destination: function (req, file, cb) {
            cb(null, './uploads/')
        },
        filename: function (req, file, cb) {
            var datetimestamp = Date.now();
            cb(null, file.fieldname + '-' + datetimestamp + '.' + file.originalname.split('.')[file.originalname.split('.').length -1])
        }
    });
    var upload = multer({ //multer settings
                    storage: storage
                }).single('file');
    /** API path that will upload the files */
    app.post('/upload', function(req, res) {
        upload(req,res,function(err){
            if(err){
                 res.json({error_code:1,err_desc:err});
                 return;
            }
             res.json({error_code:0,err_desc:null});
        });
    });
    app.get('/',function(req,res){
    res.sendFile(__dirname + "/index.html");
    });
    app.listen('3000', function(){
        console.log('running on 3000...');
    });
```

Just a brief overview of the above script, first we need the different modules, the body-parser will be used to decode the post information. First, we are configuring the storage configuration of the multer, for the location of the storage, the file name should be uploaded and also the type of storage as disk storage. Below are the multer settings and we've included an express `route/path` where we'll be upload the file.

At the root path, we also have a basic `index.html` file. `Index.html` is nothing more than a form in which we can upload our files. Finally, to start a node server, we are listening to port `3000`.

```
index.html
<form id        =  "uploadForm"
    enctype   =  "multipart/form-data"
    action    =  "upload"
    method    =  "post"
>
<input type="file" name="file" />Upload
<input type="submit" value="Upload" name="submit">
</form>
```

Now, if you run your app, you can submit any file to our directory of uploads. But we need to limit our app to allow only Excel files i.e. (.xls,.xlsx).

**Adding filetype filter**

We will change our upload function only by adding Multer's `fileFilter` option to allow excel file.

**app.js**

```
var upload = multer({ //multer settings
                    storage: storage,
                    fileFilter : function(req, file, callback) { //file filter
                        if (['xls', 'xlsx'].indexOf(file.originalname.split('.')[file.originalname.split('.').length-1]) === -1) {
                            return callback(new Error('Wrong extension type'));
                        }
                        callback(null, true);
                    }
                }).single('file');
```

**Read and convert excel to json**

Now that we can upload files to our server and add the validation of the extension. Reading the uploaded file and converting it to json is the next challenge.

To do this, we will use two node modules, [xls-to-json-lc](https://www.npmjs.com/package/xls-to-json-lc) and [xlsx-to-json-lc](https://www.npmjs.com/package/xlsx-to-json-lc), respectively to convert .xls to json and .xlsx to json.

Use the commands below to install them.

```
npm install xlsx-to-json-lc --save
npm install xls-to-json-lc --save
```

**Usage**

```
var exceltojson = require("xls-to-json-lc");
  exceltojson({
    input: "pass the input excel file here (.xls format)"
    output: "if you want output to be stored in a file"
    sheet: "sheetname",  // specific sheetname inside excel file (if you have multiple sheets)
    lowerCaseHeaders:true //to convert all excel headers to lowr case in json
  }, function(err, result) {
    if(err) {
      console.error(err);
    } else {
      console.log(result);
      //result will contain the overted json data
    }
  });
```

**Implementation**

Note, for the two Excel plugins, we have two separate node modules. We will first check the incoming file extension and then use the correct module based on it. Let's continue with it.

Begin by setting up our modules in our `app.js`.

**app.js**

```
var xlstojson = require("xls-to-json-lc");
var xlsxtojson = require("xlsx-to-json-lc");
```

Let’s make changes in path to `/upload`.

**app.js (/uploads path)**

```
/** API path that will upload the files */
    app.post('/upload', function(req, res) {
        var exceltojson; //Initialization
        upload(req,res,function(err){
            if(err){
                 res.json({error_code:1,err_desc:err});
                 return;
            }
            /** Multer gives us file info in req.file object */
            if(!req.file){
                res.json({error_code:1,err_desc:"No file passed"});
                return;
            }
            //start convert process
            /** Check the extension of the incoming file and
             *  use the appropriate module
             */
            if(req.file.originalname.split('.')[req.file.originalname.split('.').length-1] === 'xlsx'){
                exceltojson = xlsxtojson;
            } else {
                exceltojson = xlstojson;
            }
            try {
                exceltojson({
                    input: req.file.path, //the same path where we uploaded our file
                    output: null, //since we don't need output.json
                    lowerCaseHeaders:true
                }, function(err,result){
                    if(err) {
                        return res.json({error_code:1,err_desc:err, data: null});
                    }
                    res.json({error_code:0,err_desc:null, data: result});
                });
            } catch (e){
                res.json({error_code:1,err_desc:"Corupted excel file"});
            }
        });
    });
```

In the results variable (i.e. the second parameter), we will get our transformed data. Now we're ready to run our application and test it.

**app.js**

```
var express = require('express');
    var app = express();
    var bodyParser = require('body-parser');
    var multer = require('multer');
    var xlstojson = require("xls-to-json-lc");
    var xlsxtojson = require("xlsx-to-json-lc");
    app.use(bodyParser.json());
    var storage = multer.diskStorage({ //multers disk storage settings
        destination: function (req, file, cb) {
            cb(null, './uploads/')
        },
        filename: function (req, file, cb) {
            var datetimestamp = Date.now();
            cb(null, file.fieldname + '-' + datetimestamp + '.' + file.originalname.split('.')[file.originalname.split('.').length -1])
        }
    });
    var upload = multer({ //multer settings
                    storage: storage,
                    fileFilter : function(req, file, callback) { //file filter
                        if (['xls', 'xlsx'].indexOf(file.originalname.split('.')[file.originalname.split('.').length-1]) === -1) {
                            return callback(new Error('Wrong extension type'));
                        }
                        callback(null, true);
                    }
                }).single('file');
    /** API path that will upload the files */
    app.post('/upload', function(req, res) {
        var exceltojson;
        upload(req,res,function(err){
            if(err){
                 res.json({error_code:1,err_desc:err});
                 return;
            }
            /** Multer gives us file info in req.file object */
            if(!req.file){
                res.json({error_code:1,err_desc:"No file passed"});
                return;
            }
            /** Check the extension of the incoming file and
             *  use the appropriate module
             */
            if(req.file.originalname.split('.')[req.file.originalname.split('.').length-1] === 'xlsx'){
                exceltojson = xlsxtojson;
            } else {
                exceltojson = xlstojson;
            }
            try {
                exceltojson({
                    input: req.file.path,
                    output: null, //since we don't need output.json
                    lowerCaseHeaders:true
                }, function(err,result){
                    if(err) {
                        return res.json({error_code:1,err_desc:err, data: null});
                    }
                    res.json({error_code:0,err_desc:null, data: result});
                });
            } catch (e){
                res.json({error_code:1,err_desc:"Corupted excel file"});
            }
        })
    });
    app.get('/',function(req,res){
        res.sendFile(__dirname + "/index.html");
    });
    app.listen('3000', function(){
        console.log('running on 3000...');
    });
```

**package.json**

```
{
  "name": "excelupload",
  "version": "1.0.0",
  "description": "",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" &amp;&amp; exit 1"
  },
  "keywords": [],
  "author": "Rahil Shaikh",
  "license": "ISC",
  "dependencies": {
    "body-parser": "1.15.1",
    "express": "4.13.4",
    "multer": "1.1.0",
    "xls-to-json-lc": "0.3.3",
    "xlsx-to-json-lc": "0.2.5"
  }
}
```

**Run the app**

To run the program, simply use the command line interface to navigate into your woking file and run.

`node app.js`

**Demo and Quick setup**

Follow the steps below to run the application quickly

```
1) git clone https://github.com/rahil471/excel-to-json-in-Node.js.git
2) cd excel-to-json-in-Node.js
3) npm install
4) node app.js
5) In your browser http://localhost:3000
6) Upload excel file and see result
```

**Deleting the uploaded file**

You may not want to keep the Excel file uploaded to the server in some cases. Here is a piece of programming to delete the submitted files once they have been transformed.

```
package.json
var fs = require('fs');
try {
    fs.unlinkSync(req.file.path);
} catch(e) {
    //error deleting the file
}
```

Use this code to convert json just below the excel. `req.file.path` corresponds to the file that has been uploaded.

**Conclusion**

Excel to json is a regular web server requirement. This guide describes how simple in Node.js is to accomplish it.

**Suggest**

* [MEAN Stack 2.0 — Learn Angular 2, Node.js, Express and MongoDb](https://codek.tv/v/HJ8Ldgvb)
* [Node.js Tutorial with Visual Studio Code over 4 Hours](https://codek.tv/v/fFgLjwHcYdo)
* [Learn How To Deploy Node.Js App on Google Compute Engine](https://codequs.com/a/SJv5lWPF)
* [Learn and Understand NodeJS](https://codequs.com/a/B15yw5Ou)
* [Learn Nodejs by Building 12 Projects.](https://codequs.com/a/HJwY85__)
* [Learn Node.js from scratch: From Beginner to Advanced](https://codequs.com/p/HkNRG483H/learn-node-js-from-scratch-from-beginner-to-advanced)
* [Learn Node.js - Node.js API Development for Beginners](https://codequs.com/p/BJ8lFPEPE/learn-node-js-node-js-api-development-for-beginners)
* [Node.js MongoDB Tutorial, Building CRUD App with Node.js Express & MongoDB](https://codequs.com/p/HkXRinGHS/node-js-mongodb-tutorial-building-crud-app-with-node-js-express-mongodb)
* [Testing Node.js with Mocha](https://codequs.com/p/S1nupH3F4/testing-node-js-with-mocha)
* [Black Clouds and Silver Linings in NodeJS Security](https://codequs.com/p/Hk6Jp4kDH/black-clouds-and-silver-linings-in-nodejs-security)
* [Zero to Hero with Nodejs](https://codequs.com/p/HyXZ7_Q9G/zero-to-hero-with-nodejs)