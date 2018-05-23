## Exercise 1: Startup, Connect, and Shutdown MongoDB
**<img src="https://github.com/mjjw-github/NoSQL-Coarse/blob/master/mongo.png"/>**

Let"s make a directory to hold our files and databases and start mongodb

 First open the terminal
```
cd ~/Desktop
mkdir dbs
mongod --dbpath ~/Desktop/dbs --port 27017
```
  

If you get an error "Unable to lock file", increment the port value from the default port 27017 to 27018 or other.

 Note: A better way to do this is to create a database configuration file for each instance. https://docs.mongodb.com/manual/administration/configuration/#run-multiple-database-instances-on-the-same-system

If we don"t use the parameter, then the default path will be used

  

Within another shell connect to MongoDB with the client mongo by opening a second terminal
```
mongo --host localhost --port 27017  
```
Shutdown the database using ctrl+c in mongod or in mongo client using the following commands:
```
use admin
db.shutdownServer()
```
