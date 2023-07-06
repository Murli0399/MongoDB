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

