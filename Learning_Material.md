# Step-by-Step Learning Material

### **Introduction to SQL and MongoDB**

### What is SQL?

Structured Query Language (SQL) is a programming language designed for managing data in relational database management systems (RDBMS), or for stream processing in a relational data stream management system (RDSMS). It is particularly useful in handling structured data, i.e., data incorporating relations among entities and variables.

### Real-life situations using SQL:

1. **Banking Systems**: SQL databases are crucial for banking systems to manage all transactions, customer data, loans, and credits. A single query can affect multiple tables, which makes SQL's ACID (Atomicity, Consistency, Isolation, Durability) properties invaluable in maintaining data integrity.
2. **Healthcare Services**: In healthcare, SQL databases can help manage patient records, doctor's schedules, medical billing information, and more. It aids in complex queries, like retrieving the medical history of patients, counting the number of patients in each department, etc.
3. **Educational Institutes**: Institutions use SQL databases to manage and maintain students' records, courses, results, and other related data. For instance, they can execute a query to find out all the students who scored more than 90% in Math.

### What is MongoDB?

MongoDB is a source-available cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with optional schemas. MongoDB is developed by MongoDB Inc.

### Real-life situations using MongoDB:

1. **Content Management Systems**: MongoDB's flexible, JSON-like documents can easily store and combine any type of data—a natural fit for content management systems. For example, a blogging platform might use MongoDB to store all blog posts, metadata, authors, and comments.
2. **Real-Time Analytics and IoT**: MongoDB is capable of handling a massive amount of unstructured data, which makes it a good fit for real-time analytics and Internet of Things (IoT) applications. MongoDB can ingest, store, and process diverse data coming in at a high velocity and volume from various IoT devices.
3. **Mobile Applications**: MongoDB provides the speed, flexibility, and power required by mobile apps while keeping up with rapidly changing user expectations and trends. For instance, a mobile game might use MongoDB to store player profiles, scores, complex game state data, etc.

### SQL and MongoDB Schema Structure

**SQL Schema:**

In SQL, a schema represents the structure of a database in terms of tables, relationships, and the data types of columns. Here's an example of what an SQL schema might look like:

```
CREATE TABLE Customers (
    ID INT PRIMARY KEY,
    Name VARCHAR(100),
    Email VARCHAR(100),
    Address VARCHAR(255)
);

CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    OrderNumber INT,
    CustomerID INT FOREIGN KEY REFERENCES Customers(ID)
);
```

In this example, there are two tables: **`Customers`** and **`Orders`**. Each table has columns with defined data types. For example, the **`Customers`** table has an **`ID`**, **`Name`**, **`Email`**, and **`Address`**. The **`Orders`** table includes a foreign key reference, **`CustomerID`**, which creates a relationship between the **`Orders`** and **`Customers`** tables.

**MongoDB Schema:**

In MongoDB, there is no predefined schema. Instead, data is stored in flexible, JSON-like documents, meaning fields can vary from document to document and data structure can be changed over time. The equivalent data might look like this in MongoDB:

```
{
    "_id": ObjectId("50a8240b927d5d8193b63c99"),
    "Name": "John Doe",
    "Email": "john@example.com",
    "Address": "123 Main St.",
    "Orders": [
        {
            "OrderID": "1001",
            "OrderNumber": "789"
        },
        {
            "OrderID": "1002",
            "OrderNumber": "790"
        }
    ]
}
```

In this example, a customer and their orders are stored in the same document, making the relationship between these data points explicit without the need for foreign keys or separate tables. The **`_id`** field is automatically added by MongoDB as a unique identifier for the document.

### Core Differences in Syntax

The syntax between SQL and MongoDB is very different due to their different data models:

- **SQL** uses a traditional language-syntax based on algebra and tuple relational calculus. For example, to select a user from a **`Users`** table, you might write: **`SELECT * FROM Users WHERE FirstName = 'John'`**.
- **MongoDB** uses a more object-oriented, JSON-style syntax. To accomplish the same task in MongoDB, you might write: **`db.users.find({FirstName: 'John'})`**.

### Choosing Between SQL and MongoDB

Choosing between SQL and MongoDB depends on the specific requirements of your project:

- **Data Structure**: If you need to store structured data with set relationships, SQL might be your choice. If you need more flexibility to handle diverse data types and structures, MongoDB may be better.
    - **Problem Statement**: You're developing an application for a school to manage its records. The application needs to handle data about students, classes, teachers, and grades. Each of these entities has relationships with others—students are assigned to classes, teachers instruct multiple classes, and each student has a grade in each class.
    - **Solution**: In this situation, SQL would be the best choice because the data is structured and the relationships between entities are important. SQL's table-based structure and powerful JOIN operations would allow for efficient querying and manipulation of this kind of relational data.
    
- **Scalability**: If you expect a lot of traffic and need to scale your database horizontally (adding more machines), MongoDB's built-in sharding support can be beneficial. SQL databases traditionally scale vertically by upgrading the hardware of a single machine, which can be limiting.
    - **Problem Statement**: You're building a social media application that could potentially gain a large number of users in a short period. The application needs to handle a high volume of posts, comments, and likes, and you need to be able to scale your solution quickly to keep up with the load.
    - **Solution**: In this case, MongoDB would be a better choice because it's designed for horizontal scaling. As your user base grows, you can easily add more servers to your MongoDB cluster to distribute the database load and handle increased traffic without any significant changes to your application code.

- **Transactions**: If your application requires complex transactions with multiple operations, SQL is the more established option, offering ACID (Atomicity, Consistency, Isolation, Durability) properties. MongoDB also supports ACID transactions but only from version 4.0 onwards.
    - **Problem Statement**: You're designing a banking application where users can make transactions between accounts. The system needs to ensure that if a user transfers money from one account to another, the transaction is atomic (either fully completed or not at all) to avoid any inconsistencies in account balances.
    - **Solution**: For this scenario, SQL is a better fit because it supports complex transactions with multiple operations. SQL's ACID (Atomicity, Consistency, Isolation, Durability) properties ensure that each transaction is processed reliably and fully, which is critical in a banking application where data consistency is key.

- **Speed**: If you need to perform many read operations quickly, MongoDB may offer better performance due to its in-memory nature, which allows data fetching directly from RAM. SQL can be faster for operations involving complex queries across multiple tables.
    - **Problem Statement**: You're developing a real-time analytics dashboard for an e-commerce website. The dashboard needs to display the number of current users, most viewed products, current sales, etc., all in real time.
    - **Solution**: MongoDB would be an ideal choice in this scenario because it's designed for high-speed read operations. MongoDB stores data in a format similar to JSON, which can be read directly from the database to the web, making it a good fit for real-time analytics applications that require high read speeds and where data structure may vary.

In the end, the choice between SQL and MongoDB largely depends on the specific use case and requirements of your project. It's common for businesses to use a combination of both SQL and NoSQL databases to leverage the strengths of each

### **Key Differences Between SQL and MongoDB**

In the course, we can also elaborate on key differences between SQL and MongoDB, such as:

1. **Data Structure**
    
    **SQL**: SQL databases are table-based, meaning they store data in rows and columns, which is a good fit for applications requiring multi-row transactions like an accounting system or systems that need to maintain a strong relationship between data.
    
    **Example**: Zomato may use an SQL database to handle relationships between its restaurants, meals, customers, and order history. Each of these categories would be a table (e.g., Customers, Restaurants), with relationships between them (e.g., a Customer orders from a Restaurant).
    
    **MongoDB**: MongoDB is a document-based database, which stores data in BSON format, a binary representation of JSON documents. This flexible data model makes it easy to store and combine data of any structure, without losing data integrity.
    
    **Example**: Swiggy may use MongoDB to store detailed information about a food delivery, which may include complex nested data like customer information, order items with different food preferences, payment details, and dynamic data like real-time location updates.
    
2. **Schema**
    
    **SQL**: SQL databases have a predefined schema, which means you have to define tables and columns before you can store data. This provides a level of data consistency across the application.
    
    **Example**: Uber might use an SQL database to maintain a structured record of trips. Each trip has to have a defined set of data such as driver ID, rider ID, start time, end time, and fare, providing a consistent way to analyze the trips.
    
    **MongoDB**: MongoDB is schema-less, allowing you to create documents without having to define the structure of the document first, like the fields or the types of their values. This flexibility can speed up development in projects where structure is less certain.
    
    **Example**: A rapidly evolving application like a new feature in Swiggy might benefit from MongoDB's flexible schema, allowing developers to iterate and change the data model quickly based on new requirements without downtime or costly migrations.
    
3. **Scaling**
    
    **SQL**: SQL databases are scaled vertically by increasing the power of the hardware. While this often leads to increased costs, it also allows for powerful transactions and complex queries to be executed efficiently.
    
    **Example**: Zomato, with a large, consistent structure of restaurant menus and millions of customer reviews, may benefit from the vertical scaling capabilities of SQL, which can handle complex queries over these structured datasets.
    
    **MongoDB**: MongoDB, on the other hand, is designed with horizontal scaling in mind. You can add more servers to your MongoDB cluster to handle the extra load. This approach can be more cost-effective and allows MongoDB to handle large amounts of data and traffic.
    
    **Example**: Uber, dealing with huge data sets from millions of rides each day and needing to distribute this data geographically close to users for low latency, may benefit from MongoDB's horizontal scaling.
    
4. **Query Language**
    
    **SQL**: SQL databases use the SQL language which has a powerful query capability. It has a rich standard with a variety of functions and operators and supports complex queries to retrieve data.
    
    **Example**: A data analyst at Zomato might use SQL's powerful querying capabilities to perform complex analysis, like identifying the average rating of restaurants in a specific region that offer a particular cuisine.
    
    **MongoDB**: MongoDB uses JavaScript as its querying language. For developers familiar with JavaScript, MongoDB queries can feel intuitive. Its queries are represented as JSON-style documents.
    
    **Example**: In Uber, where developers might be iterating fast and dealing with semi-structured and geographically distributed data, they might benefit from MongoDB's intuitive, flexible query language to quickly

## ****Querying in SQL and MongoDB****

We'll consider an e-commerce scenario where we have a **`Products`** collection in MongoDB and a **`Products`** table in SQL. Here are the details:

**MongoDB `Products` Collection Schema:**

```
{
    "_id": ObjectId,
    "name": String,
    "price": Number,
    "category": String,
    "rating": Number,
    "in_stock": Boolean
}
```

**SQL `Products` Table Schema:**

```
CREATE TABLE Products (
    ID INT PRIMARY KEY,
    Name VARCHAR(255),
    Price DECIMAL(10,2),
    Category VARCHAR(100),
    Rating DECIMAL(3,2),
    In_Stock BOOLEAN
);
```

The fields **`ID`** (SQL) / **`_id`** (MongoDB), **`Name`**, **`Price`**, **`Category`**, **`Rating`**, **`In_Stock`** represent the product's unique identifier, name, price, category, average user rating, and availability status respectively.

### **Query Examples**

**1. Fetching all Data:**

Fetches all the documents in the collection or rows in the table.

SQL:

```
SELECT * FROM Products;
```

MongoDB:

```
db.Products.find()
```

**2. Selecting Specific Fields:**

Returns only the **`name`** and **`price`** fields from all documents/rows.

SQL:

```
SELECT Name, Price FROM Products;
```

MongoDB:

```
db.Products.find({}, {name: 1, price: 1})
```

**3. Filtering Data:**

Returns only the products which have a **`rating`** greater than 4.

SQL:

```
SELECT * FROM Products WHERE Rating > 4;
```

MongoDB:

```
db.Products.find({rating: {$gt: 4}})
```

**4. Sorting Data:**

Returns all products sorted by **`price`** in descending order.

SQL:

```
SELECT * FROM Products ORDER BY Price DESC;
```

MongoDB:

```
db.Products.find().sort({price: -1})
```

**5. Counting Documents/Rows:**

Counts the number of products in a specific **`category`**.

SQL:

```
SELECT COUNT(*) FROM Products WHERE Category = 'Electronics';
```

MongoDB:

```
db.Products.count({category: 'Electronics'})
```

**6. Limiting Results:**

Fetches the top 5 most expensive products.

SQL:

```
SELECT * FROM Products ORDER BY Price DESC LIMIT 5;
```

MongoDB:

```
db.Products.find().sort({price: -1}).limit(5)
```

**7. Skipping Documents/Rows:**

Fetches all products except the 5 most expensive ones.

SQL:

```
SELECT * FROM Products ORDER BY Price DESC OFFSET 5;
```

MongoDB:

```
db.Products.find().sort({price: -1}).skip(5)
```

**8. Updating Documents/Rows:**

Increases the **`price`** of all products in the 'Electronics' category by 10.

SQL:

```
UPDATE Products SET Price = Price + 10 WHERE Category = 'Electronics';
```

MongoDB:

```
db.Products.updateMany({category: 'Electronics'}, {$inc: {price: 10}})
```

**9. Deleting Documents/Rows:**

Deletes all products that are not **`in_stock`**.

SQL:

```
DELETE FROM Products WHERE In_Stock = FALSE;
```

MongoDB:

```
db.Products.deleteMany({in_stock: false})
```

**10. Fetching Distinct Values:**

Fetches distinct **`category`** values in the Products table or collection.

SQL:

```
SELECT DISTINCT Category FROM Products;
```

MongoDB:

```
db.Products.distinct('category')
```

**11. Aggregating Data:**

Calculates the average **`price`** of all products in the 'Electronics' category.

SQL:

```
SELECT AVG(Price) FROM Products WHERE Category = 'Electronics';
```

MongoDB:

```
db.Products.aggregate([{$match: {category: 'Electronics'}}, {$group: {_id: null, avgPrice: {$avg: '$price'}}}])
```

**12. Grouping Data:**

Groups products by **`category`** and counts the number of products in each category.

SQL:

```
SELECT Category, COUNT(*) FROM Products GROUP BY Category;
```

MongoDB:

```
javascriptCopy code
db.Products.aggregate([{$group: {_id: '$category', count: {$sum: 1}}}])

```

**13. Filtering with Multiple Conditions:**

Fetches all products in the 'Electronics' category that have a **`rating`** higher than 4.

SQL:

```
SELECT * FROM Products WHERE Category = 'Electronics' AND Rating > 4;
```

MongoDB:

```
javascriptCopy code
db.Products.find({category: 'Electronics', rating: {$gt: 4}})

```

**14. Fetching Data with OR Condition:**

Fetches all products that either have a **`rating`** higher than 4 or are **`in_stock`**.

SQL:

```
SELECT * FROM Products WHERE Rating > 4 OR In_Stock = TRUE;
```

MongoDB:

```
db.Products.find({$or: [{rating: {$gt: 4}}, {in_stock: true}]})
```

**15. Using a LIKE Operator (SQL) / Regex (MongoDB):**

Fetches all products where the **`name`** starts with "Ele".

SQL:

```
SELECT * FROM Products WHERE Name LIKE 'Ele%';
```

MongoDB:

```
javascriptCopy code
db.Products.find({name: {$regex: '^Ele'}})

```

**16. Updating a Single Document/Row:**

Updates the **`price`** of a product with a specific ID.

SQL:

```
UPDATE Products SET Price = 100 WHERE ID = 1;
```

MongoDB:

```
db.Products.updateOne({_id: ObjectId("uniqueID")}, {$set: {price: 100}})
```

**17. Joining Tables (SQL) / Embedding Documents (MongoDB):**

For this example, we'll assume we have an **`Orders`** table or collection where each order has a product ID.

SQL:

```
SELECT Orders.OrderID, Products.Name FROM Orders INNER JOIN Products ON Orders.ProductID = Products.ID;
```

MongoDB (Products document with an embedded **`Orders`** array):

```
db.Products.find({"Orders.OrderID": "uniqueOrderID"}, {name: 1, "Orders.$": 1})
```

**18. Inserting Multiple Rows/Documents:**

Inserts multiple new products.

SQL:

```
INSERT INTO Products (Name, Price, Category, Rating, In_Stock) VALUES ('Product 1', 99.99, 'Electronics', 4.5, TRUE), ('Product 2', 49.99, 'Books', 4.7, FALSE);
```

MongoDB:

```
db.Products.insertMany([{name: 'Product 1', price: 99.99, category: 'Electronics', rating: 4.5, in_stock: true}, {name: 'Product 2', price: 49.99,category: 'Books', rating: 4.7, in_stock: false}])
```

**19. Changing Data Type:**

Changes the data type of the **`Price`** column in SQL or in MongoDB. (Let's assume it's currently a String/Text data type)

SQL:

```
ALTER TABLE Products ALTER COLUMN Price TYPE DECIMAL(10,2) USING (Price::decimal);
```

MongoDB:

MongoDB does not support changing the type of a field directly. We need to iterate over all documents and apply the conversion. Assuming we want to change **`price`** to a number:

```
db.Products.find().forEach(function(doc) { doc.price = Number(doc.price); db.Products.save(doc); })
```

**20. Searching for Null Values:**

Fetches all products where the **`rating`** is not set or is null.

SQL:

```
SELECT * FROM Products WHERE Rating IS NULL;
```

MongoDB:

```
db.Products.find({rating: null})
```

Remember, these examples have been simplified for clarity. Real-world applications might require more complex queries or data handling. Also, both SQL and MongoDB offer additional features and capabilities beyond the ones covered here.
