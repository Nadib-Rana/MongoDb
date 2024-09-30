 **What, Why, How, and Installing** approach.

### **What is MongoDB?**
MongoDB is a **NoSQL** database that stores data in flexible, **document-based** structures using BSON (Binary JSON). Instead of relying on rigid tables and columns like in relational databases, MongoDB organizes data as **collections** of documents, which allows for more natural representation of data, especially when dealing with complex, nested structures.

- **Documents**: Key-value pairs, similar to JSON objects.
- **Collections**: Groups of documents.
- **Database**: A collection of collections.

Example of a MongoDB document:
```json
{
   "_id": "001",
   "name": "John Doe",
   "email": "john@example.com",
   "age": 30,
   "address": {
     "street": "123 Main St",
     "city": "New York"
   }
}
```

### **Why use MongoDB?**
MongoDB is ideal for applications that need:
1. **Flexible Schema**: You can have documents with varying fields in the same collection.
2. **Scalability**: It supports horizontal scaling through sharding, making it great for handling large datasets.
3. **High Performance**: It performs well with read/write-heavy applications and can handle large amounts of unstructured data.
4. **NoSQL Flexibility**: Ideal for handling non-relational data such as hierarchical or graph data structures.
5. **Rapid Prototyping**: MongoDB is popular for projects where the data structure may evolve quickly, such as agile development environments.

### **How does MongoDB Work?**
MongoDB organizes data into the following hierarchy:

- **Database**: A container for collections.
- **Collection**: A group of MongoDB documents, similar to a table in a relational database.
- **Document**: A record in the database, represented in BSON format (a binary representation of JSON).

Operations in MongoDB are done using **CRUD** (Create, Read, Update, Delete). MongoDB also supports complex queries, indexing, replication for high availability, and sharding for horizontal scalability.

#### Example of Basic Operations:
1. **Insert a document**:
   ```js
   db.users.insertOne({name: "John", age: 25});
   ```

2. **Query data**:
   ```js
   db.users.find({age: {$gt: 20}});
   ```

3. **Update a document**:
   ```js
   db.users.updateOne({name: "John"}, {$set: {age: 26}});
   ```

4. **Delete a document**:
   ```js
   db.users.deleteOne({name: "John"});
   ```

### **Installing MongoDB** 

#### **Step 1: Installing MongoDB on Local Machine**
Follow these steps to install MongoDB locally:

##### **Windows Installation**:
1. Download MongoDB from the [official MongoDB download page](https://www.mongodb.com/try/download/community).
2. Run the installer and follow the instructions.
3. Configure the service (by default, MongoDB will run as a Windows service).
4. Add the MongoDB bin folder to the system’s PATH environment variable for easier command line access.
5. To start MongoDB, open a terminal (cmd/powershell) and run:
   ```bash
   mongod
   ```

##### **Linux Installation**:
1. Import the MongoDB public GPG key:
   ```bash
   wget -qO - https://www.mongodb.org/static/pgp/server-6.0.asc | sudo apt-key add -
   ```

2. Add the MongoDB repository to the package manager:
   ```bash
   echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
   ```

3. Update the package list and install MongoDB:
   ```bash
   sudo apt-get update
   sudo apt-get install -y mongodb-org
   ```

4. Start MongoDB:
   ```bash
   sudo systemctl start mongod
   ```

##### **macOS Installation (Homebrew)**:
1. Install MongoDB using Homebrew:
   ```bash
   brew tap mongodb/brew
   brew install mongodb-community@6.0
   ```

2. Start MongoDB:
   ```bash
   brew services start mongodb/brew/mongodb-community
   ```

#### **Step 2: Verifying the Installation**
1. After installation, to verify that MongoDB is running, you can connect to the MongoDB shell by running:
   ```bash
   mongo
   ```
   This should open the MongoDB shell where you can start interacting with your database.

#### **Step 3: Installing MongoDB Drivers**
To use MongoDB in your application (e.g., Node.js):
1. Install the MongoDB Node.js driver:
   ```bash
   npm install mongodb
   ```

2. Example of connecting to MongoDB from Node.js:
   ```js
   const { MongoClient } = require('mongodb');
   const uri = "your_mongoDB_connection_string";
   const client = new MongoClient(uri);

   async function run() {
     try {
       await client.connect();
       console.log("Connected to MongoDB");
     } finally {
       await client.close();
     }
   }
   run().catch(console.dir);
   ```
