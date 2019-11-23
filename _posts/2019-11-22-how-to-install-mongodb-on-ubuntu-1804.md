---
title: How to Install MongoDB on Ubuntu 18.04
image: "/assets/default-social-image.png"
categories: mongodb-ubuntu
---

**Introduction**

[MongoDB](https://www.mongodb.com/) (licensed under the Server Side Public License or SSPL) used for common web applications is a free, open source, NoSQL and cross-platform document-oriented database program (which uses JSON-like documents with schema).

**Prerequisites**

By following [this](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-18-04) initial server setup tutorial, for which it also includes sudo non root and a firewall which is required for our 18.04 version and our purposes like managing its service and optionally enable remote access. That’s what you will learn through this tutorial.

**Step 1 — Installing MongoDB**

We can install the necessary packages using `apt`, as Ubuntu’s official package repositories always include an up-to-date version of MongoDB

Update the list of packages so as to have the most recent repository listings version:

`$ sudo apt update`

Now, we install the MongoDB package:

`sudo apt install -y mongodb`

And this installs all the necessary packages that contains the last stable MongoDB version along with the management tools required by the MongoDB server. The DB server starts automatically after installation. Now, let’s check if the server runs and works correctly.

**Step 2 — Checking the Service and Database**

The Installation starts automatically but it’s recommended to verify if the service is started and also if the database is working.

So, let’s check the service’s status:

`$ sudo systemctl status mongodb`

this output is displayed:

```
Output

● mongodb.service - An object/document-oriented database
   Loaded: loaded (/lib/systemd/system/mongodb.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2018-05-26 07:48:04 UTC; 2min 17s ago
     Docs: man:mongod(1)
 Main PID: 2312 (mongod)
    Tasks: 23 (limit: 1153)
   CGroup: /system.slice/mongodb.service
           └─2312 /usr/bin/mongod --unixSocketPrefix=/run/mongodb --config /etc/mongodb.conf
```

The MongoDB server is set up and running, as per `systemd`.

You can connect to the database and execute diagnostic command to verify this:

`$ mongo --eval 'db.runCommand({ connectionStatus: 1 })'`

This will display the current version of database, the port and server address, and also the command status:

```
Output

MongoDB shell version v3.6.3
connecting to: mongodb://127.0.0.1:27017
MongoDB server version: 3.6.3
{
        "authInfo" : {
                "authenticatedUsers" : [ ],
                "authenticatedUserRoles" : [ ]
        },
        "ok" : 1
}
```

The `1` for `ok` here implies that the server is working properly.

Now, we’ll look at managing the server instance.

**Step 3 — Managing the MongoDB Service**

Note that with the installation of MongoDB, you can use standard `systemd` commands along with other services with Ubuntu.

To verify service status of the service:

`$ sudo systemctl status mongodb`

To make the server stop anytime:

`$ sudo systemctl stop mongodb`

To start the stopped server:

`$ sudo systemctl start mongodb`

To restart the server:

`sudo systemctl restart mongodb`

MongoDB is configured by default to start automatically with the server. If you wish to disable this function:

`sudo systemctl disable mongodb`

To enable it again:

`sudo systemctl enable mongodb`

Now, we’ll learn how to adjust the firewall settings for our MongoDB installation.

**Step 4 — Adjusting the Firewall (Optional)**

The MongoDB server will be inaccessible from the internet, assuming that the firewall is enabled on your server.
If you intended to use MongoDB locally with all applications running on the same server, this is a secure and recommended settings for your purposes but if you like to use this server from internet, you have to allow incoming connections:

to use the MongoDB server only locally with applications running on the same server, this is the recommended and secure setting. However, if you would like to be able to connect to your MongoDB server from the internet, you have to allow the incoming connections by `ufw`.

You could use `sudo ufw allow 27017` to allow access to MongoDB from everywhere on its default port `27017`. But it’s access to DB server and its data is restricted if you enable the internet access on a default intallation.
But MongoDB should be accessed only from certain trusted locations (such as hosting an application by another server) in most cases, you have to allow access on default port with IP address of another server to be specified which will be allowed to connect:

`$ sudo ufw allow from your_other_server_ip/32 to any port 27017`

With the following, you will be able to verify the change in firewall settings with `ufw`:

`sudo ufw status`

You should see the allowed traffic to port `27017` in the output:

```
Output
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere
27017                      ALLOW       Anywhere
OpenSSH (v6)               ALLOW       Anywhere (v6)
27017 (v6)                 ALLOW       Anywhere (v6)
```

The IP address of the location allowed will be listed in the output if you allow the MongoDB server to connect to only a specific IP address, instead of the ‘anywhere’.

**UFW Essentials:** [Common Firewall Rules and Commands](https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands) can include more advanced firewall settings to limit access to services. Despite the port being available, MongoDB is currently listening only to the `127.0.0.1` local address. Add the publicly-routable IP address of your server to the `mongod.conf` file to allow remote connections.

Open MongoDB configuration file in  the editor:

`$ sudo nano /etc/mongodb.conf`

Add the IP address of your client to the value of `bindIP`:

```
...
logappend=true

bind_ip = 127.0.0.1,your_server_ip
#port = 27017

...
```

Be sure to place a comma between the IP address you already have and the one you have added.
Save the file and exit the editor. Now, restart the MongoDB:

`$ sudo systemctl restart mongodb`

MongoDB listens to remote connections now, but it can be accessed by anyone. To add an administrator client and further lock things down, follow Part 2 on [How to Install and Secure MongoDB on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-mongodb-on-ubuntu-16-04#part-two-securing-mongodb).

**Conclusion**

[This](https://docs.mongodb.com/v3.2/) MongoDB documentation is a great resource which MongoDB provides on its possibilities. More in-depth tutorials for configuring and using MongoDB can be found in [these](https://www.digitalocean.com/community/search?q=mongodb) DigitalOcean community articles.