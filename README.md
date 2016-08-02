# How to install MongoDB on Windows 10

- Download the MongoDB Community Server **.msi** installer [here](http://www.mongodb.org/downloads)
- Install it to `C:/mongodb`
- Create a file inside `C:/mongodb` called `mongod.cfg` with the following content:
```
systemLog:
    destination: file
    path: c:\mongodb\data\log\mongod.log
storage:
    dbPath: c:\mongodb\data\db
```
- Open the `cmd` as administrator and run:
`"C:\mongodb\bin\mongod.exe" --config "C:\mongodb\mongod.cfg" --install`
- Start the MongoDB service with `net start MongoDB`
- *Optional*: Add "**C:\mongodb\bin**" to the system path

## Test the installation with [Node.js](https://nodejs.org/)
- Install the official MongoDB driver for Node.js with `npm install mongodb`
- Create a new **.js** file (I'll name mine `testing_mongo_with_node.js`
- Write to the file:
```javascript
var mongodb = require('mongodb');
var MongoClient = mongodb.MongoClient;
var url = 'mongodb://localhost:27017/database_test';

MongoClient.connect(url, function (err, db) {
  if (err) {
    console.log('The connection failed. Error:', err);
  } else {
    console.log('The connection to ' + url + ' succeed.');
  }
  db.close();
});
```
- Run the script with `node testing_mongo_with_node.js`

If everything is OK you should read **The connection to mongodb://localhost:27017/database_test succeed.**

:pig:

Sources:
- [*Install MongoDB Community Edition on Windows*](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/)
- [*Node.js Tutorial: Using MongoDB*](http://blog.modulus.io/mongodb-tutorial)
