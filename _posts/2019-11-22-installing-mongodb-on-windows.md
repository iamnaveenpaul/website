---
title: Installing MongoDB on Windows
image: "/assets/default-social-image.png"
categories: Mongodb-Windows
---

**What’s MongoDB?**

MongoDB (licensed under the Server Side Public License or SSPL) used for common web applications is a free, open source, NoSQL and cross-platform document-oriented database program (which uses JSON-like documents with schema). Document values can be looked up by their field’s key, which makes MongoDB extremely versatile.

MongoDB fields follow the columns of a table and the individual records match the rows which makes it distinct compared to SQL servers such as MySQL or PostgreSQL. In this brief tutorial, we will look on how to Install MongoDB on Windows.

**Prerequisites**

You should be familiar with the Windows command prompt.

**Installing and Running MongoDB on a Windows Machine**

Download the installer file from the [downloads section](https://www.mongodb.org/downloads#production).

* Double click the downloaded .msi file in the Windows Explorer and install Mongo by following the prompts. By default, Mongo is most probably in the `C:\mongodb` directory, unless you specify manually. However, it’s actually based on the settings of your machine, for example, `C:\Program Files\MongoDB\Server\3.2`. Also, you will find MongoDB in the add/remove programs section. 
* Create the directory for storing MongoDB files. Run `md \data\db` from the command prompt which would be the default location but using the --dbpath parameter other locations can also be specified using the `--dbpath` parameter. For more information, refer the [Mongo docs](https://docs.mongodb.org/v3.0/tutorial/install-mongodb-on-windows/#set-up-the-mongodb-environment).
* run `C:\mongodb\bin\mongod.exe` in the Command Prompt or `C:\path\to\mongodb\bin\mongod.exe` to start the mongodb daemon.
* While the MongoDB daemon is running, run `C:\mongodb\bin\mongo.exe` from a different Command prompt window to connect to MongoDB using the Mongo shell.