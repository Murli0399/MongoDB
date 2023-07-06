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

3. Problem: Write a query to fetch all data from the Customers table / collection.

4. Problem: Write a query to select only the name and email fields for all customers.

5. Problem: Write a query to fetch the customer with the id of 3.

6. Problem: Write a query to fetch all customers whose name starts with 'A'.

7. Problem: Write a query to fetch all customers, ordered by name in descending order.

8. Problem: Write a query to update the address of the customer with id 4.

9. Problem: Write a query to fetch the top 3 customers when ordered by id in ascending order.

10. Problem: Write a query to delete the customer with id 2.

11. Problem: Write a query to count the number of customers.

12. Problem: Write a query to fetch all customers except the first two when ordered by id in ascending order.

13. Problem: Write a query to fetch all customers whose id is greater than 2 and name starts with 'B'.

14. Problem: Write a query to fetch all customers whose id is less than 3 or name ends with 's'.

15. Problem: Write a query to fetch all customers where the phone_number field is not set or is null.
