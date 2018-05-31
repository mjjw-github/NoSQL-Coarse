## Exercise 5: mongoimport, Compass, and Aggregation

Retrieve the dataset from: http://media.mongodb.org/zips.json and save to a file named primer-dataset.json.

Import data into the collection.

In the system shell or command prompt, use mongoimport to insert the documents into the restaurants collection in the test database. If the collection already exists in the test database, the operation will drop the restaurants collection first.
```
mongoimport --db test --collection zipcodes --drop --file ~/Downloads/primer-dataset.json --host localhost:27017
```
Open MongoDB Compass and enter the mongod hostname and port

Open the test database.

Follow along the Mongo Tutorial: https://docs.mongodb.com/manual/tutorial/aggregation-zip-code-data-set/
