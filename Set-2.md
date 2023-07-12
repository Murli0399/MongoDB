**Problem 16:** Create a **`Restaurants`** table / collection with the fields defined above.


```
db.createCollection("Restaurants")

```
**Problem 17:** Insert five rows / documents into the **`Restaurants`** table / collection with data of your choice.

```
db.Restaurants.insertMany([
    {
        id:1,
        name: "Pizza Hut",
        cuisine_type: "Italian",
        location: "New York",
        average_rating: 4.5,
        delivery_available: true
    },
    {
        id:2,
        name: "McDonalds",
        cuisine_type: "Fast Food",
        location: "Los Angeles",
        average_rating: 3.5,
        delivery_available: true
    },
    {
        id:3,
        name: "Chipotle",
        cuisine_type: "Mexican",
        location: "San Francisco",
        average_rating: 4.0,
        delivery_available: true
    },
    {
        id:4,
        name: "Subway",
        cuisine_type: "Sandwiches",
        location: "Chicago",
        average_rating: 3.0,
        delivery_available: true
    },
    {
        id:5,
        name: "Taco Bell",
        cuisine_type: "Mexican",
        location: "Miami",
        average_rating: 3.5,
        delivery_available: true
    }
]);


```
**Problem 18:** Write a query to fetch all restaurants, ordered by **`average_rating`** in descending order.


```
db.Restaurants.find().sort({ average_rating: -1 });
```
**Problem 19:** Write a query to fetch all restaurants that offer **`delivery_available`** and have an **`average_rating`** of more than 4.


```
db.Restaurants.find({
    delivery_available: true,
    average_rating: { $gt: 4 }
});
```
**Problem 20:** Write a query to fetch all restaurants where the **`cuisine_type`** field is not set or is null.

```
db.Restaurants.find({
    cuisine_type: { $exists: false }
});
```
**Problem 21:** Write a query to count the number of restaurants that have **`delivery_available`**.


```
db.Restaurants.count({
    delivery_available: true
});

```
**Problem 22:** Write a query to fetch all restaurants whose **`location`** contains 'New York'.


```
db.Restaurants.find({
    location: { $regex: /New York/i }
});
```
**Problem 23:** Write a query to calculate the average **`average_rating`** of all restaurants.


```
db.Restaurants.aggregate([
  { $group: { _id: null, average_rating: { $avg: "$average_rating" } } }
]);

```
**Problem 24:** Write a query to fetch the top 5 restaurants when ordered by **`average_rating`** in descending order.


```
db.Restaurants.find().sort({ average_rating: -1 }).limit(5);

```
**Problem 25:** Write a query to delete the restaurant with **`id`** 3.

```
db.Restaurants.deleteOne({ _id: 3 });
```
