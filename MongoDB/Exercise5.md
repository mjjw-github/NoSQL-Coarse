## Exercise 5: Compass

Retrieve the dataset from: https://raw.githubusercontent.com/mongodb/docs-assets/primer-dataset/primer-dataset.json and save to a file named primer-dataset.json.

Import data into the collection.

In the system shell or command prompt, use mongoimport to insert the documents into the restaurants collection in the test database. If the collection already exists in the test database, the operation will drop the restaurants collection first.
```
mongoimport --db test --collection restaurants --drop --file ~/Downloads/primer-dataset.json --host localhost:270xx
```
Open MongoDB Compass and enter the mongod hostname and port

Open the test database
