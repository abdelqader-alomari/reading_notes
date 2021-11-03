# Read: 29 - Room

# Room

![Library](https://developer.android.com/images/training/data-storage/room_architecture.png)

- The Room persistence library provides an abstraction layer over SQLite to allow fluent database access while harnessing the full power of SQLite.

### Room provides the following benefits:

- Compile-time verification of SQL queries.
- Convenience annotations that minimize repetitive and error-prone boilerplate code.
- Streamlined database migration paths.
- To use Room in your app, add the following dependencies to your app's build.gradle file:

```
dependencies {
def room_version = "2.3.0"

implementation "androidx.room:room-runtime:$room_version"
annotationProcessor "androidx.room:room-compiler:$room_version"

// optional - RxJava2 support for Room
implementation "androidx.room:room-rxjava2:$room_version"

// optional - RxJava3 support for Room
implementation "androidx.room:room-rxjava3:$room_version"

// optional - Guava support for Room, including Optional and ListenableFuture
implementation "androidx.room:room-guava:$room_version"

// optional - Test helpers
testImplementation "androidx.room:room-testing:$room_version"

// optional - Paging 3 Integration
implementation "androidx.room:room-paging:2.4.0-alpha04"
}
```

- It's highly recommend that you use Room instead of using the SQLite APIs directly because Room provides the following benefits:

  - Compile-time verification of SQL queries.
  - Convenience annotations that minimize repetitive and error-prone boilerplate code.
  - Streamlined database migration paths.

## Room Components are mainly

- The database class that holds the database and serves as the main access point for the underlying connection to your app's persisted data.
- Data entities that represent tables in your app's database.
- Data access objects (DAOs) that provide methods that your app can use to query, update, insert, and delete data in the database.
- Data access object (DAO) => to provide methods interacting with data.

## Entities in room

- You define each Room entity as a class that is annotated with @Entity. A Room entity includes fields for each column in the corresponding table in the database, including one or more columns that comprise the primary key.

- Each Entity should have a unique primary key.

- Because SQLite is a relational database, you can specify relationships between entities. Even though most object-relational mapping libraries allow entity objects to reference each other,Room explicitly forbids this.

- Relationship between entities: One to one, one to many & many to many relationships

## DAO

![](https://www.journaldev.com/wp-content/uploads/2018/04/android-room-structure-docs.png)

- Is either an interface or an abstract class. For basic use cases, you should usually use an interface. In either case, you must always annotate your DAOs with @Dao. DAOs don't have properties, but they do define one or more methods for interacting with the data in your app's database. => ( @Insert, @Delete, @Update, @Query).

### Insert

```
 @Insert(onConflict = OnConflictStrategy.REPLACE)
   public void insertUsers(User... users);

   @Insert
   public void insertBothUsers(User user1, User user2);
```

### Update

```
   @Update
   public void updateUsers(User... users);
```

### Delete

```
 @Delete
    public void deleteUsers(User... users);
```

- If your app's logic requires direct access to the return rows, you can write your DAO methods to return a Cursor object

![](https://gorillalogic.com/wp-content/uploads/2019/12/RoomDB_Transparent.png)

## References

- [Overview: Saving data with Room](https://developer.android.com/training/data-storage/room)
- [Defining entities in Room](https://developer.android.com/training/data-storage/room/defining-data)
- [Related entities in Room](https://developer.android.com/training/data-storage/room/relationships)
- [Accessing data with Room](https://developer.android.com/training/data-storage/room/accessing-data#java)
