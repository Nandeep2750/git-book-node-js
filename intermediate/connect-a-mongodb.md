# Connect a MongoDB

To create a database in MongoDB:

* Start by creating a MongoClient object
* Specify a connection URL with the correct IP address and the name of the database you want to create

<figure><img src="../.gitbook/assets/Connect a MongoDB.png" alt=""><figcaption><p>Connect a MongoDB</p></figcaption></figure>

Connect using mongoose...

```javascript
const mongoose = require('mongoose');

/* ---------- connect Databse ---------- */
mongoose.connect(process.env.MONGO_DB_CONNECTION_STRING,
    {
        useNewUrlParser: true,
        useUnifiedTopology: true
    }, () => {
        console.info("Mongo db connected!");
    }
);
```
