
**Problem 1:** Create a **`Customers`** table / collection with the following fields: **`id`** (unique identifier), **`name`**, **`email`**, **`address`**, and **`phone_number`**.
```
db.createCollection("Customers")
```


**Problem 2:** Insert five rows / documents into the **`Customers`** table / collection with data of your choice.

```
db.Customers.insertMany([
    { id: 1, name: 'John Doe', email: 'john@example.com', address: '123 Main St', phone_number: '1234567890' },
    { id: 2, name: 'Jane Smith', email: 'jane@example.com', address: '456 Oak Ave', phone_number: '9876543210' },
    { id: 3, name: 'Alice Johnson', email: 'alice@example.com', address: '789 Elm Rd', phone_number: '4561237890' },
    { id: 4, name: 'Bob Williams', email: 'bob@example.com', address: '321 Pine Ln', phone_number: '7890123456' },
    { id: 5, name: 'Sarah Davis', email: 'sarah@example.com', address: '567 Maple Dr', phone_number: '5432109876' }
]);
```

**Problem 3:** Write a query to fetch all data from the **`Customers`** table / collection.

```
db.Customers.find()

```
**Problem 4:** Write a query to select only the **`name`** and **`email`** fields for all customers.


```
db.Customers.find({}, { name: 1, email: 1 })

```
**Problem 5:** Write a query to fetch the customer with the **`id`** of 3.

```
db.Customers.find({ id: 3 });
```

**Problem 6:** Write a query to fetch all customers whose **`name`** starts with 'A'.

```
db.Customers.find({ name: /^A/ });
```
**Problem 7:** Write a query to fetch all customers, ordered by **`name`** in descending order.

```
db.Customers.find().sort({ name: -1 });
```
**Problem 8:** Write a query to update the **`address`** of the customer with **`id`** 4.

```
db.Customers.updateOne({ id: 4 }, { $set: { address: 'New Address' } });
```
**Problem 9:** Write a query to fetch the top 3 customers when ordered by **`id`** in ascending order.

```
db.Customers.find().sort({ id: 1 }).limit(3);
```
**Problem 10:** Write a query to delete the customer with **`id`** 2.

```
db.Customers.deleteOne({ id: 2 });
```

**Problem 11:** Write a query to count the number of customers.

```
db.Customers.countDocuments();
```
**Problem 12:** Write a query to fetch all customers except the first two when ordered by **`id`** in ascending order.

```
db.Customers.find().sort({ id: 1 }).skip(2);
```

**Problem 13:** Write a query to fetch all customers whose **`id`** is greater than 2 and **`name`** starts with 'B'.


```
db.Customers.find({ id: { $gt: 2 }, name: /^B/ });
```
**Problem 14:** Write a query to fetch all customers whose **`id`** is less than 3 or **`name`** ends with 's'.


```
db.Customers.find({ $or: [{ id: { $lt: 3 } }, { name: /s$/ }] });

```
**Problem 15:** Write a query to fetch all customers where the **`phone_number`** field is not set or is null.

```
db.Customers.find({ $or: [{ phone_number: null }, { phone_number: '' }] });
```