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
