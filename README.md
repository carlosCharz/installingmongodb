Installing MongoDB on a MAC
================

A simple guide to install MongoDB on a MAC. Based on [MongoDB Tutorial | Installing MongoDB On A MAC - Part 1](https://www.youtube.com/watch?v=-GE2DpwfbW0)

##### 1. Download mongoDB
[MongoDB Download Web Page](https://www.mongodb.org/downloads)

##### 2. Extract the files from the downloaded archive
Easy way: Double-click the downloaded archive

OR
```
tar -zxvf mongodb-osx-x86_64-n.n.n.tgz
```

##### 3. Copy the extracted archive to the target directory
Easy way: Rename the folder (mongodb) and move to the user directory (/Users/charz/)

OR
```
mv /Users/charz/Downloads/mongodb-osx-x86_64-n.n.n /Users/charz/mongodb
```

##### 4. Create the data folder
Easy way: Create the folder structure: data/db under your user directory (/Users/charz)

OR
```
mkdir /Users/charz/data
mkdir /Users/charz/data/db
```

##### 5. Put the binaries in the path
```
cd $HOME (just to make sure you are in the user directory folder - /Users/charz)
echo “export PATH=$PATH:/Users/charz/mongodb/bin” >.bash_profile
```
To make sure it was created correctly:
```
ls -la (the .bash_profile file should appear)
cat .bash_profile (the mongodb/bin folder should appear)
```
Exit the terminal app and reopen it

##### 6. Create a mongod.conf file
My mongod.conf file
```
# mongod.conf

# for documentation of all options, see:
#   http://docs.mongodb.org/manual/reference/configuration-options/

# where to write logging data.
systemLog:
  destination: file
  logAppend: true
  path: /Users/charz/mongodb/mongod.log

# Where and how to store data.
storage:
  dbPath: /Users/charz/data/db
  journal:
    enabled: true
#  engine:
#  mmapv1:
#  wiredTiger:
```

Copy my sample from the lines above or from [MongoDB Github](https://github.com/mongodb/mongo/blob/master/rpm/mongod.conf)
```
Open TextEdit
Format - Make Plain Text
Change “logpath=” and “dbpath=”
Save to /Users/charz/mongodb/mongod.conf (to your mongodb folder installation)
```

##### 7. Start mongoDB
```
mongod -f /Users/charz/mongodb/mongod.conf (it should not give you any error)
```
"mongod" to open the mongodb server

##### 8. Test mongoDB
Open a new terminal app
```
mongo
use mydb
db.test.save({a:1})
db.test.find() (the object just created should appear)
```
"mongo" to open the mongodb client

* New contributions and/or corrections are very WELCOME!
