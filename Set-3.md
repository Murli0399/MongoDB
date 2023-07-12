**Problem 26:** Create a **`Rides`** table / collection with the fields defined above.

```
db.createCollection("Rides", {
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["driver_id", "passenger_id", "start_location", "end_location", "distance", "ride_time", "fare"],
      properties: {
        id: {
          bsonType: "objectId"
        },
        driver_id: {
          bsonType: "objectId"
        },
        passenger_id: {
          bsonType: "objectId"
        },
        start_location: {
          bsonType: "string"
        },
        end_location: {
          bsonType: "string"
        },
        distance: {
          bsonType: "number"
        },
        ride_time: {
          bsonType: "number"
        },
        fare: {
          bsonType: "number"
        }
      }
    }
  }
});


```
**Problem 27:** Insert five rows / documents into the **`Rides`** table / collection with data of your choice.


```
db.Rides.insertMany([
  {
    _id: ObjectId(),
    driver_id: ObjectId(),
    passenger_id: ObjectId(),
    start_location: "Location A",
    end_location: "Location B",
    distance: 10.5,
    ride_time: 25.3,
    fare: 15.75
  },
  {
    _id: ObjectId(),
    driver_id: ObjectId(),
    passenger_id: ObjectId(),
    start_location: "Location C",
    end_location: "Location D",
    distance: 8.2,
    ride_time: 20.1,
    fare: 12.50
  },
  {
    _id: ObjectId(),
    driver_id: ObjectId(),
    passenger_id: ObjectId(),
    start_location: "Location E",
    end_location: "Location F",
    distance: 5.7,
    ride_time: 15.8,
    fare: 9.85
  },
  {
    _id: ObjectId(),
    driver_id: ObjectId(),
    passenger_id: ObjectId(),
    start_location: "Location G",
    end_location: "Location H",
    distance: 12.9,
    ride_time: 30.2,
    fare: 18.50
  },
  {
    _id: ObjectId(),
    driver_id: ObjectId(),
    passenger_id: ObjectId(),
    start_location: "Location I",
    end_location: "Location J",
    distance: 7.1,
    ride_time: 18.5,
    fare: 11.25
  }
]);


```
**Problem 28:** Write a query to fetch all rides, ordered by **`fare`** in descending order.


```
db.Rides.find().sort({ fare: -1 });

```
**Problem 29:** Write a query to calculate the total **`distance`** and total **`fare`** for all rides.

```
db.Rides.aggregate([
  { $group: { _id: null, totalDistance: { $sum: "$distance" }, totalFare: { $sum: "$fare" } } }
]);

```
**Problem 30:** Write a query to calculate the average **`ride_time`** of all rides.


```
db.Rides.aggregate([
  { $group: { _id: null, averageRideTime: { $avg: "$ride_time" } } }
]);


```
**Problem 31:** Write a query to fetch all rides whose **`start_location`** or **`end_location`** contains 'Downtown'.


```

db.Rides.find({
  $or: [
    { start_location: /Downtown/ },
    { end_location: /Downtown/ }
  ]
});

```
**Problem 32:** Write a query to count the number of rides for a given **`driver_id`**.

```
db.Rides.countDocuments({ driver_id: ObjectId("64ad967af83ed21d6eb2518e") });

```
**Problem 33:** Write a query to update the **`fare`** of the ride with **`id`** 64ad967af83ed21d6eb2518d.


```

db.Rides.updateOne(
  { _id: ObjectId("64ad967af83ed21d6eb2518d")},
  { $set: { fare: 12.5 } }
);

```
**Problem 34:** Write a query to calculate the total **`fare`** for each **`driver_id`**.


```
db.Rides.aggregate([
  { $group: { _id: "$driver_id", totalFare: { $sum: "$fare" } } }
]);

```
**Problem 35:** Write a query to delete the ride with **`id`** 64ad967af83ed21d6eb2518d.

```

db.Rides.deleteOne({ _id: ObjectId("64ad967af83ed21d6eb2518d") });

```
