1. Problem: Create a Customers table / collection with the following fields: id (unique identifier), name, email, address, and phone_number.
```
db.Customers.insertOne({
  "_id": 1,
  "name": "John Doe",
  "email": "johndoe@example.com",
  "address": "123 Main St",
  "phone_number": "555-1234"
})

```
2. Problem: Insert five rows / documents into the Customers table / collection with data of your choice.
```
db.Customers.insertMany([
  {
    "name": "Alice",
    "email": "alice@example.com",
    "address": "456 Elm St",
    "phone_number": "555-5678"
  },
  {
    "name": "Bob",
    "email": "bob@example.com",
    "address": "789 Oak St",
    "phone_number": "555-9012"
  },
  {
    "name": "Charlie",
    "email": "charlie@example.com",
    "address": "123 Maple Ave",
    "phone_number": "555-3456"
  },
  {
    "name": "Diana",
    "email": "diana@example.com",
    "address": "987 Pine St",
    "phone_number": "555-7890"
  },
  {
    "name": "Eve",
    "email": "eve@example.com",
    "address": "654 Cedar Ln",
    "phone_number": "555-1234"
  }
])

```
3. Problem: Write a query to fetch all data from the Customers table / collection.
```
db.Customers.find({})
```
4. Problem: Write a query to select only the name and email fields for all customers.
```
db.Customers.find({}, { name: 1, email: 1 })
```
5. Problem: Write a query to fetch the customer with the id of 3.
```
db.Customers.findOne({ _id: "64a6b0f3f604ab1e13e029b5" })
```
6. Problem: Write a query to fetch all customers whose name starts with 'A'.
```
db.Customers.find({ name: { $regex: '^A', $options: 'i' } })
```
7. Problem: Write a query to fetch all customers, ordered by name in descending order.
```
db.Customers.find().sort({ name: -1 })
```
8. Problem: Write a query to update the address of the customer with id 4.
```
db.Customers.updateOne({ _id: 4 }, { $set: { address: "New Address" } })
```
9. Problem: Write a query to fetch the top 3 customers when ordered by id in ascending order.
```
db.Customers.find().sort({ _id: 1 }).limit(3)
```
10. Problem: Write a query to delete the customer with id 2.
```
db.Customers.deleteOne({ _id: 2 })
```
11. Problem: Write a query to count the number of customers.
```
db.Customers.countDocuments()
```
12. Problem: Write a query to fetch all customers except the first two when ordered by id in ascending order.
```
db.Customers.find().sort({ _id: 1 }).skip(2)
```
13. Problem: Write a query to fetch all customers whose id is greater than 2 and name starts with 'B'.
```
db.Customers.find({ _id: { $gt: 2 }, name: { $regex: '^B', $options: 'i' } })
```
14. Problem: Write a query to fetch all customers whose id is less than 3 or name ends with 's'.
```
db.Customers.find({ $or: [ { _id: { $lt: 3 } }, { name: { $regex: 's$', $options: 'i' } } ] })
```
15. Problem: Write a query to fetch all customers where the phone_number field is not set or is null.
```
db.Customers.find({ $or: [ { phone_number: { $exists: false } }, { phone_number: null } ] })
```
