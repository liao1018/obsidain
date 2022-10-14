#cs #database #mongoDb

[官方文件](https://www.mongodb.com/docs/mongodb-shell

## Switch Databases
`use <database>`

## Create a New Database and Collection
```mongodb
use myNewDatabase
db.myCollection.insertOne( { x: 1 } );
```

If a collection doesn't exitst, MongoDB creates the collection when you first store data for that collection.