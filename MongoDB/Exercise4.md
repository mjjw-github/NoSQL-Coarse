## Exercise 4: Indexes

Recall that indexes are the same in RDBMSs as they are special data structures containing some portion of the data and are smaller than the whole data so it can reside in RAM. Indexes can also be used to sort data.  If no indexes were used, then MongoDB would do a full collection scan (very slow).  Again, indexes are special data structures that contain some portion of the collection that point to the location of the document on disk and are much smaller than the whole collection plus typically reside in RAM.  Try to use at least one index when you query.  Also, only create indexes if use them a lot.

List Indexes
```
db.myfirstcollection.getIndexes()
```
This returns one document, one index.
"v" is version and all created indexes.
The field that is indexed is "_id:"

Create an index using the createIndex(keys, options) method
```
db.myfirstcollection.createIndex({name: 1})  // 1 indicates sort ascending
```
Now we have 2 indexes
```
db.myfirstcollection.getIndexes()
```
You can create a collection and index simultaneously.
```
db.myfirstindexedcollection.createIndex({name: 1})
show collections
db.myfirstindexedcollection.getIndexes()
```
  
Delete indexes using the dropIndex() method.
Let's drop the name index usimg the index name
```
db.myfirstindexedcollection.dropIndex("name_1")
db.myfirstindexedcollection.getIndexes()
```
If you want to drop ALL indexes except the default _id, use the dropIndexes() method.

Single field indexes
```
use secondindexedcollection
```
```
for (i = 0; i < 20; i++) {
    for (j = 0; j < 20; j++) {
        for (k = 0; k < 20; k++) {
            db.secondindexedcollection.insert({
                _id: i * 100 + j * 20 + k,
                a: i,
                b: j,
                c: k
            });
        }
    }
}
```
```
db.secondindexedcollection.count()
db.secondindexedcollection.createIndex({a: 1})
```
Using indexes in queries
```
db.secondindexedcollection.find({_id: 3}).explain()
```
https://docs.mongodb.com/manual/reference/explain-results/
