---
image: "/assets/default-social-image.png"
title: How to restore a specific database from backup using mongorestore command
categories: Mongo
---

I used the mongodump command to build a copy of all my servers. Now I want a particular server to be restored using the command mongorestore.

I use this command as to how this is possible: —db choice, otherwise mongodb does not recover a particular database.

To recover a single database, as part of the `mongorestore` command line, you must provide the route to the dump folder.

For example:

```
# Backup the training database
mongodump --db training 
# Restore the training database to a new database called training2
mongorestore --db training2 dump/training
```

The `mongodump` alternative `--db` determines the root database to be dumped.
The `mongorestore` alternative `--db` determines the target database to be restored.

To restore mongo database, use the following command:

`mongorestore -d dbname dbpath`

`$ mongorestore --drop -d <database-name> <dir-of-backup-files>`

`--drop` If you are replacing an existing db, drop is required.
`-d <database-name>` The name required to create/replace database.
`<dir-of-backup-files>` This is necessary for some reason, even if it is the present directory.

Reference: https://coderwall.com/p/3hx06a/restore-a-mongodb-database-mongorestore

**Restoring using mongorestore**

After making sure that `mongod` and `mongo` are running, go to the dump's parent directory in a new terminal. And use the command `mongorestore dump`. Where `dump` is the folder name in which the database dump is present.