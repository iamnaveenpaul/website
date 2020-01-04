---
title: How to Install Node.js 10 with node-oracledb and Connect it to Oracle Database
image: "/assets/default-social-image.png"
categories: Node.js
---

The Oracle Linux yum repository offers [dedicated repositories for Node.js](https://yum.oracle.com/oracle-linux-nodejs.html). Such repositories also include a Node.js [node-oracledb](http://oracle.github.io/node-oracledb/) RPM with the Oracle Database driver so you can link the Node.js code to the Oracle Database.

In this post, I explain the steps for installing to Oracle Database, Node.js 10 and Node-oracledb Node.js. I recommend that you use the new [Oracle Linux 7 Vagrant box](https://github.com/oracle/vagrant-boxes/tree/master/OracleLinux/7) if you are in a rush or want to do this in a non-destructive way.

**Configure Yum with Repositories of Node.js and Oracle Instant Client**

Install the oracle-nodejs-release-el7 and oracle-release-el7 RPMs to set up your system to access Node.js and Oracle Instant Client repository on the Oracle Linux yum server. When you install the Oracle Node.js repel RPM, the Node.js 10 repo will be enabled by default.

```
$ sudo yum -y oracle-node-release-el7 oracle-release-el7
```

Then, install Node.js 10 and the compatible node-oracledb, making sure that the EPEL repository is temporarily disabled to prevent installing the wrong Node.js version.

```
$ sudo yum -y install --disablerepo=ol7_developer_EPEL nodejs node-oracledb-node10
```

**Connecting to Oracle Database**

I used the [18c Express Edition (XE) Oracle Database](https://oracle.com/xe) for my analysis. This is where you can download it. Instructions for Quick Start are here.

**About Oracle Instant Client**

Oracle Instant Client relies on the node-oracledb. [Oracle Instant Client 18.3 RPMs were launched in the ol7_oracle_instantclient and ol6_oracle_instantclient repositories on the Oracle Linux yum repository](https://blogs.oracle.com/linux/oracle-instant-client-rpms-now-available-on-oracle-linux-yum-server-yumoraclecom) during OpenWorld 2018, rendering installation a seamless process. If you have allowed the Oracle Instant Client repository appropriate for the introduction of Oracle Linux, it will be configured as a dependency. Node-oracledb is developed for Oracle Server 18.3 as of release 3.0, and integrates with Oracle Database 11.2 and higher. Older Oracle Instant Client updates can be found on [OTN](https://www.oracle.com/technetwork/database/database-technologies/instant-client/overview/index.html).

**Add the instant Oracle Client to the path of the runtime link.**

```
$ sudo sh -c "echo /usr/lib/oracle/18.3/client64/lib > /etc/ld.so.conf.d/oracle-instantclient.conf"
$ sudo ldconfig
```

**Connecting to Oracle Database Quick Node.js Test Program**

I copied this file from the samples in the [Github repo node-oracledb](https://github.com/oracle/node-oracledb). If Node.js will link to the database, that informs us if we run this. Copy this code into the connect.js file.

```
var oracledb = require('oracledb');
var dbConfig = require('./dbconfig.js');

oracledb.getConnection(
{
user : dbConfig.user,
password : dbConfig.password,
connectString : dbConfig.connectString
},
function(err, connection)
{
if (err) {
console.error(err.message);
return;
}
console.log('Connection was successful!');

connection.close(
function(err)
{
if (err) {
console.error(err.message);
return;
}
});
});
```

The following file comes from the same repo of GitHub. Copy and edit the code into a file called dbconfig.js to include the username, password, and connect string of your database.

```
module.exports = {
user : process.env.NODE_ORACLEDB_USER || "<YOUR DATABASE USER HERE>",

password : process.env.NODE_ORACLEDB_PASSWORD || "<YOUR DATABASE PASSWORD HERE>",

connectString : process.env.NODE_ORACLEDB_CONNECTIONSTRING || "<YOUR DATABASE CONNECT STRING HERE>",

externalAuth : process.env.NODE_ORACLEDB_EXTERNALAUTH ? true : false
};
```

**Run connect.js with node**

Make sure the NODE_PATH is set before running connect.js so that the node-oracledb module can be located.

```
$ export NODE_PATH=`npm root -g`
$ node connect.js
Connection was successful!
```