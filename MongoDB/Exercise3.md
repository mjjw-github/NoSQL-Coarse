## **Exercise 3: Create/Read/Update a Database Collection**

See what databases exists.
```
show dbs
```
Which databases are we connected to?
```
db
```
Switch database and show collections.
```
use local
show collections
```
What documents are within the collections.  Using db. means current database then collection "startup_log" then the method .find() to get data from that collection in a .pretty() format.
```
db.startup_log.find().pretty()
```
How many documents are in the collection?
```
db.startup_log.count()
```
A database is created automatically upon the first creation of a document when it"s added to a collection "myfirstcollection" for this new database.
```
db.myfirstcollection.insert({name:"marklogic"})
show dbs
show collections
db.mydb.myfirstcollection.find().pretty()
```
To interact with a database, we use the pattern: db.{collectionname}.:method}
```
db.myfirstcollection.[tab][tab]
```
```
db.myfirstcollection.find()
```
Deleting records from this collection is accomplished with this method remove.
```
db.myfirstollection.remove({})
show collections
```
Notice how the collection myfirstcollection still exists; so to remove a collection use the drop method.
```
db.myfirstollection.drop()
```
```
show myfirstollection
```
Has the db been deleted?
```
show dbs
```
To delete a database full of collections, first create two collections.
```
db.myfirstollection.insert({name:"marklogic"})
db.mysecondcollection.insert({type:"multi-model"})
show collections
```
Deleting the database requires that we make sure we are connected to the database we want to drop.
```
db
db.dropDatabase()
show dbs
```
**Update Operations**

Insert a single document.
```
use crud
db.myfirstcollection.insert({  
   name:"mongodb",
   type:"document store",
   sql:"no",
   initialrelease:2009,
   license:"open source",
   apis:["Actionscript","C","C#","C++","Clojure","ColdFusion","D","Dart","Delphi","Erlang","Go","Groovy","Haskell","Java", "JavaScript","Lisp","Lua","Matlab","Perl","PHP",   "PowerShell","Prolog","Python","R","Ruby","Scala","Smalltalk"],
   rankings:[{rank:1,year:2013,medianscore:139.597},
      {rank:1,year:2014,medianscore:212.375},
      {rank:1,year:2015,medianscore:276.144},      
      {rank:1,year:2016,medianscore:317.357},
      {rank:1,year:2017,medianscore:331.337}],
   consistency:{  
      eventual:"yes",
      immediate:"can be decided upon write"
   },
   inmemorycapable:"yes",
   partitioning:"sharding"
})
```
```
db.myfirstcollection.find().pretty()
```
Notice a primary key bson type is added in the form "_id": objectid("").  This objectid is unique across all databases;
however, you can specify the pk.
```
db.myfirstcollection.insert({  
   _id:1,
   name:"cassandra",
   type:"wide column store",
   sql:"SQL-like DML and DDL statements (CQL)",
   initialrelease:2008,
   license:"open source",
   apis:"thrift",
   rankings:[{rank:2,year:2013,medianscore:57.36},
      {rank:2,year:2014,medianscore:87.623},
      {rank:2,year:2015,medianscore:114.794},      
      {rank:2,year:2016,medianscore:132.615},
      {rank:2,year:2017,medianscore:129.839}],
   consistency:{  
      eventual:"yes",
      immediate:"can be decided upon write"
   },
   inmemorycapable:"no",
   partitioning:"sharding"
})
```
```
db.myfirstcollection.find().pretty() 
```
Let's try a multiple insert by inserting an array of documents into the myfirstcollection collection. 
```
array =[{
	_id:1, 
	name:"cassandra", 
	type:"wide column store", 
	sql:"SQL-like DML and DDL statements (CQL)", "initial.release":2008, license:"open source", apis:["thrift"], rankings:[{rank:2,year:2013,medianscore:57.36}, {rank:2,year:2014,medianscore:87.623}, {rank:2,year:2015,medianscore:114.794}, {rank:2,year:2016,medianscore:132.615}, {rank:2,year:2017,medianscore:129.839}], consistency:{ eventual:"yes", immediate:"can be decided upon write" }, "inmemory.capable":"no", partitioning:"sharding" },  
   {  
   _id:3,
   name:"redis",
   type:"key-value store",
   sql:0,
   initialrelease:"unknown",
   license:"open source",
   apis:["C","C#","C++","Clojure","Crystal","D","Dart","Elixir","Erlang","Fancy","Go","Haskell","Haxe","Java","JavaScript (Node.js)","Lisp","Lua","MatLab","Objective-C","OCaml","Pascal","Perl","PHP","Prolog","Pure Data","Python","R","Rebol","Ruby","Rust","Scala","Scheme","Smalltalk","Swift","Tcl","Visual Basic",],
   rankings:[{rank:3,year:2013,medianscore:38.875},
      {rank:3,year:2014,medianscore:70.185},
      {rank:3,year:2015,medianscore:99.642},      
      {rank:3,year:2016,medianscore:110.525},
      {rank:3,year:2017,medianscore:119.239}],
   consistency:{  
      eventual:"yes",
      immediate:"can be decided upon write"
   },
   inmemorycapable:"yes",
   partitioning:"sharding"
   },
   {  
   _id:4,
   name:"elasticsearch",
   type:"search engine",
   sql:"no",
   initialrelease:2010,
   license:"open source",
   apis:["Java", "RESTful"],
   rankings:[{rank:7,year:2013,medianscore:12.259},
      {rank:5,year:2014,medianscore:31.733},
      {rank:4,year:2015,medianscore:62.802},      
      {rank:4,year:2016,medianscore:90.242},
      {rank:4,year:2017,medianscore:112.975}
   ],
   consistency:{  
      eventual:"yes"
   },
   inmemorycapable:"memcached and redis",
   partitioning:"sharding"
},
{  
   _id:5,
   name:"hbase",
   type:"wide-column store",
   sql:"no",
   initialrelease:2008,
   license:"open source",
   apis:["Java", "RESTful", "Thrift"],
   rankings:[{rank:6,year:2013,medianscore:28.01},
      {rank:4,year:2014,medianscore:43.172},
      {rank:5,year:2015,medianscore:53.917},      
      {rank:5,year:2016,medianscore:55.996},
      {rank:5,year:2017,medianscore:60.388}
   ],
   consistency:{  
      immediate:"yes"
   },
   inmemorycapable:"no",
   partitioning:"sharding"
}
]
```  
```
db.myfirstcollection.insert(array)
```
Notice the error occurred in the on _id: 1 and the insert stopped after that error. To enable mongodb to continue on just add {ordered: false}.
```
db.myfirstcollection.insert(array, {ordered: false})
db.myfirstcollection.find().pretty()
```
Now it finished inserting the rest except where there were duplicates.
Let's save the results from the find method cursor into a variable named cursor.
```
cursor = db.myfirstcollection.find();null;
```
Null prevents the shell from using the returned cursor and the results are saved in variable cursor.
Let's count the documents in the cursor.
```
cursor.count()
```
```
cursor.hasNext()
```
True means there are still documents to retrieve from the cursor; hence, false means there are no more documents to return.
Let"s get the 1st document from the cursor.
```
cursor.next()
```
We can loop through documents to print all docs from the cursor.
```
while(cursor.hasNext()){
   printjson(cursor.next())
};
```
Alternatively, we can use the forEach() method which accepts javascript functions as a single argument to pass a current document.
```
cursor = db.numbers.find(); null;
```
```
cursor.forEach(function(doc) {printjson(doc);})
```
To understand the cursor better, create a new collection with more than 101 documents (e.g., 105).
```
for (i=0; i<105; i++) {db.numbers.insert({_id:i, number: i})}
```
```
db.numbers.count()
```
Now let's call the find method again to store the results in the cursor variable.
```
cursor = db.numbers.find(); null;
```
How many cursors are open right now?
```
db.serverStatus().metrics.cursor
cursor.hasNext()
db.serverStatus().metrics.cursor
```

## *Find basic operations*

| Find  |  Operation|
|--|--|
| {field: {$eq:<value>}} | equal |
|{field: {$ne:<value>}} |not equal
|{field: {$gt:<value>}} | >
|{field: {$gte:<value>}} | >=
|{field: {$lt:<value>}} |  <
|{field: {$lte:<value>}} | <=
|{field: {$in:<array}} | in
|{field: {$nin:<array>}} | not in

Find all documents whose initial release is less than 2010.
```
db.myfirstcollection.find({initialrelease: {$lt: 2010}}).pretty()
db.myfirstcollection.find({initialrelease: {$eq: 2008}}).pretty()
db.myfirstcollection.find({initialrelease: 2009}).pretty()
db.myfirstcollection.find({initialrelease: {$lt: 2011, $gt: 2008}}).pretty()
```
We can even use lt and gt for strings.
```
db.myfirstcollection.find({name: {$gt: "l", $lt: "n"}}).pretty()
db.myfirstcollection.find({name: {$gt: "d", $lt: "maa"}}).pretty()
```
$in operator passing an array
```
db.myfirstcollection.find({apis: {$in: ["Java","Python"]}}).pretty()
```
```
db.myfirstcollection.find({apis: {$nin: ["Java","Thrift"]}}).pretty()
```
Boolean and Logical Operations with find()

## Top Level Operators
| Syntax: | Operation: |
|--|--|
|  { $and: [ { <expression1> }, { <expression2> } , ... , { <expressionN> } ] } | ALL
|{ $or: [ { <expression1> }, { <expression2> } , ... , { <expressionN> } ] } | AT LEAST ONE TRUE
|{ $nor: [ { <expression1> }, { <expression2> } , ... , { <expressionN> } ] } | NONE

## Specific Field Operator

{field: {$not: {conditional}}
  
Let' find the initial release with multiple expressions.

```
db.myfirstcollection.find({  
   $and:[  
      {  
         $or:[  
            {  
               initialrelease:2008
            },
            {  
               initialrelease:2010
            }
         ]
      },
      {  
         $or:[  
            {  
               type:"wide column store"
            },
            {  
               type:"key-value store"
            }
         ]
      }
   ]
}).pretty()
```
Use find() to retrieve documents that match certain fields or type

{field: { $exists: <boolean> }}  Matches documents that contain a field
{field: { $type: <BSON Type> }}
Let's find all the documents that do not contain the field "eventual"
```
db.myfirstcollection.find( {eventual: {$exists: false}}).pretty()
```
Find all the documents who"s category does not that have a string which is a BSON Type Number 2 or alias "string" (refer to BSON Types slide for enumerated types numbers)
```
db.myfirstcollection.find( {sql: {$not: {$type: "string"}}}).pretty()
```
```
db.myfirstcollection.find( {sql: {$not: {$type: 2}}}).pretty()
```
You can do this for types "array" etc.
```
db.myfirstcollection.find( {apis: {$type: "array"}}).pretty()
db.myfirstcollection.find( {apis: {$type: "string"}}).pretty()
```
Find embedded documents (e.g., consistency:)
```
db.myfirstcollection.find( {consistency:{ eventual:"yes", immediate:"can be decided upon write"}}).pretty()
db.myfirstcollection.find( {consistency:{ eventual:"yes"}}).pretty()
```
$where operator uses a JavaScript expression or function as it's parameter that can be executed for all documents. However, this a slow operation that cannot leverage indexes, so avoid it if you can.
```
db.myfirstcollection.find( {$where: "this.initialrelease > 2008"}).pretty() //string containing javascript expression "this.initialrelease > 2008"
```
## Array find() operators

{ <field>: { $all: [ <value1> , <value2> ... ] } }
```
db.collection.find( { apis: { $size: 2 } } );
```
This returns all documents in collection where field is an array with 2 elements.

The $elemMatch operator matches documents that contain an array field with at least one element that matches all the specified query criteria.

{ <field>: { $elemMatch: { <query1>, <query2>, ... } } }

If you specify only a single <query> condition in the $elemMatch expression, you do not need to use $elemMatch.

The $all operator selects the documents where the value of a field is an array that contains all the specified elements.
```
db.myfirstcollection.find({"apis": {$all: ["Java","Go","C"]}}).pretty()
db.myfirstcollection.find({"apis": {$size: 2}}).pretty()
```
$size is exact so if your looking for gt or lt use"
```
db.myfirstcollection.find({$where: "this.apis instanceof Array && this.apis.length < 3"}).pretty()
db.myfirstcollection.find({initialrelease: {$gt:2008}}).pretty()
```
What if you only want certain fields to limit the return of data.  This can be done with projections.  Similiar to select in sql.

find(criteria, projection) and findOne(criteria, projection) methods accepts 2 arguments criteria and projection.  So when you omit the projection it will return all the documents. The projection argument can accept values of boolean true/1 to include the field or false/0 to exclude a field from the find() method, but you can also use an expression of projection operators.

Let"s return every field except partitioning
```
 db.myfirstcollection.find({"name":"mongodb"},{"partitioning":0}).pretty()
```

We can include/exclude fields from embedded documents as well
```
db.myfirstcollection.find({name: "mongodb"},{"consistency.eventual": true}).pretty()
db.myfirstcollection.find({name: "cassandra"},{"consistency.eventual": false}).pretty()
```
Let"s look at the projection operators: $, $elemMatch, $meta, $slice

$ is always used in tandem with a condition and the operator syntax {"<array>.$":1}
$ limits elements in the return array to 1
```
db.myfirstcollection.find({"apis": {$in: ["C#"]}},{"apis.$": 3}).pretty()
```
This will not work without a condition on the array (e.g., $in)
We can use the elemMatch as a projections operator
```
db.myfirstcollection.find({"apis": {$in: ["C#"]}},{"apis.$elemMatch": 1}).pretty()
```
$slice returns many elements
```
db.myfirstcollection.find({name: "mongodb"}, {"apis": true})
```
Get the first 2 elements using {$slice: limit} on an array
```
db.myfirstcollection.find({name: "mongodb"}, {"apis": {$slice: 2}}).pretty()
```
Let"s use the skip and limit on {$slice: [skip,limit]}
```
db.myfirstcollection.find({name: "mongodb"}, {apis: {$slice: [3,2]}}).pretty()
```
Limit and Skip results
```
db.myfirstcollection.find().limit(2).skip(1).pretty()
```
**The sort() Method**

To sort documents in MongoDB, you need to use sort() method. The method accepts a document containing a list of fields along with their sorting order. To specify sorting order 1 and -1 are used. 1 is used for ascending order while -1 is used for descending order.

Sort on a field with different types: Numbers and Strings
```
db.myfirstcollection.find({},{initialrelease: true}).sort({category: 1})
db.myfirstcollection.find({},{initialrelease: true}).sort({category:-1})
```
Note: Different types are sorted differently. see https://docs.mongodb.com/manual/reference/bson-type-comparison-order/

Modifying documents with update(criteria, update, {upsert: bool, multi: bool, writeConcern: <document>})

Replacing a whole document (i.e., all fields except primary key)
Say we need to change "type" to document.
```
db.myfirstcollection.update({name:"mongodb" }, {type: "document"})
db.myfirstcollection.find({name:"mongodb"}).pretty()
```
Notice it replaced everything except the primary key _id

To update a selected field
```
db.myfirstcollection.update({_id: 4},{$set: {sql: 1, type: "search"}})
db.myfirstcollection.find({_id: 4}).pretty()
```
Remove fields
```
db.myfirstcollection.update({_id: 4},{$unset: {sql: "", type: ""}})
db.myfirstcollection.find({_id: 4}).pretty()
```
Update & Remove fields
```
db.myfirstcollection.update({_id: 4},{$set: {name: "elk", type: "search engine"},$unset: {initialrelease:""}})
db.myfirstcollection.find({_id: 4}).pretty()
```
Update an embedded document
```
db.myfirstcollection.update({_id: 3},{$set: {consistency:{ eventual:"yup", immediate:"decide on write"}})
db.myfirstcollection.find({_id: 3}).pretty()
```
Arithmethic modifications $inc, $mul
Let's increment the initialrelease by 2
```
db.myfirstcollection.update({_id: 4},{$inc: {initialrelease: 2}})
db.myfirstcollection.find({_id: 4}).pretty()
db.myfirstcollection.update({_id: 4},{$inc: {initialrelease: -2}})
db.myfirstcollection.find({_id: 4}).pretty()
db.myfirstcollection.update({_id: 4},{$mul: {initialrelease: 2}})
db.myfirstcollection.find({_id: 4}).pretty()
db.myfirstcollection.update({_id: 4},{$mul: {initialrelease: 0.5}})
db.myfirstcollection.find({_id: 4}).pretty()
```
Add ($addToSet, $push) or remove elements of an array
$addToSet 1st checks if the element is in the array, but $push doesn"t
```
db.myfirstcollection.update({_id: 4},{$addToSet: {name: "elk"}})
db.myfirstcollection.find({_id: 4}).pretty()
db.myfirstcollection.update({_id: 4},{$addToSet: {apis: {$each: ["Java8", "Java9"]}}})
db.myfirstcollection.find({_id: 4}).pretty()
```
You can pass an upsert boolean argument to the update method if upsert returns true.
```
db.myfirstcollection.find({name: "mongodb"})
db.myfirstcollection.update({name: "mongodb"}, {$set: {initialrelease: 2020}})
```
As you can see no documents were modified
```
db.myfirstcollection.update({name: "mongodb"}, {$set: {initialrelease: 2009}}, {upsert: true})
db.myfirstcollection.find({name: "mongodb"}).pretty()
db.myfirstcollection.update({name: "mongodb"}, {$set: {initialrelease: 2009}}, {upsert: true})
```
It's already in the collection
Update multiple documents using the second argument of the update method multi: true
By default only one document can be updated so make sure you use the multi: true argument
```
db.myfirstcollection.update({initialrelease: {$gte: 2008}}, {$inc: {initialrelease: 10}}, {multi: true})
db.myfirstcollection.find()
```

```
db.myfirstcollection.find({initialrelease: {$gt: 2010}}).pretty()
```
Notice initial releases are now increment by 10.

Let's delete some documents using the remove() method.
```
show collections
```
Let's use the numbers collection we created earlier to demonstrate the remove method. If you dropped it, just recreate it using
```
for (i = 0; i < 105; i++) {
    db.numbers.insert({
        _id: i,
        number: i
    })
}
```
Let"s remove all documents with id < 7.
```
db.numbers.remove({_id: {$lt: 7}})
```
Notice the default is to remove multiple documents unlike update() method
You can use the {justOne: true} argument within remove() to remove one (i.e., 1st one that matches the criteria).
Note:  remove({}) deletes all documents one-by-one. while drop deletes all documents, indexes, and validation rules.
