# Read: 30 - Hash Tables

## What is a Hashtable?

![](https://www.uniquesoftwaredev.com/wp-content/uploads/2019/05/chaining.png)

The Hashtable is a data structure that stores information, the information in the hash table has two main components: Key and Value.
and it's a way we can implement an associative array and map this key to this value

### How it's work: Write a hash function which look to a certain key and then evaluate that key and it's going to spit out some sort of index number and tell us what a location in the array to store this information

`Hash(key) -> index`
`Hash(Abdelqader) -> 1`
and every time we want to enter this key, it's going to spit out the same index

- Hash: is the result of some algorithm taking an incoming string and converting it into a value that could be used for either security or some other purpose. In the case of a hashtable, it is used to determine the index of the array.
- Buckets - A bucket is what is contained in each index of the array of the hashtable. Each index is a bucket.
- Collisions - A collision is what happens when more than one key gets hashed to the same location of the hashtable.

## Why do we use Hashtable?

- Hold unique values
- Dictionary
- Library

## What Are they

Hashtables are a data structure that utilize key value pairs. This means every Node or Bucket has both a key, and a value.

The basic idea of a hashtable is the ability to store the key into this data structure, and quickly retrieve the value. This is done through what we call a hash. A hash is the ability to encode the key that will eventually map to a specific location in the data structure that we can look at directly to retrieve the value.

Since we are able to hash our key and determine the exact location where our value is stored, we can do a lookup in an O(1) time complexity. This is ideal when quick lookups are required.

If we know the index of the information we want we can access that information in O(1) time. While searching for a piece of data in a collection is O(N) because we have to look through all N things in the collection.

Hash maps take advantage of an array’s O(1) read access. Instead of adding elements to an array from beginning to end, a hash map uses a “hash function” to place each item at a precise index location, based off it’s key.

Basically, the hash function takes a key and returns an integer. We use the integer to determine where the key/value pair should be placed in the array. The hash code is calculated in constant time and writing to an array at one index is O(1) so the hash map has O(1) access.

## **Structure**

![](https://he-s3.s3.amazonaws.com/media/uploads/e880c21.jpg)

### Hashing

A hash code turns a key into an integer, their output is determined only by their input, The same key should always produce the same hash code.

### Creating a Hash

1. Add or multiply all the ASCII values together.
2. Multiply it by a prime number such as 599.
3. Use modulo to get the remainder of the result, when divided by the total size of the array.
4. Insert into the array at that index.

Example:

```
Key = "Cat"
Value = "Josie"

67 + 97 + 116 = 280

280 * 599 = 69648

69648 % 1024 = 16

Key gets placed in index of 16.

```

### Collisions

![](https://he-s3.s3.amazonaws.com/media/uploads/dda3e36.jpg)

A collision occurs when more than one key hashes to the same index in an array. Collisions are solved by changing the initial state of the buckets.
we can initialize a LinkedList in each one! Each index in the array is called a “bucket” because it can store multiple key/value pairs.

### Hash maps do this to store values

- Accept a key
- Calculate the hash of the key
- Use modulus to convert the hash into an array index
- Store the key with the value by appending both to the end of a linked list

### Hash maps do this to read value

- Accept a key
- Calculate the hash of the key
- Use modulus to convert the hash into an array index
- Use the array index to access the short LinkedList representing a bucket
- Search through the bucket looking for a node with a key/value pair that matches the key you were given

### Bucket Sizes

If a hash map has more buckets it will be more sparsely populated, there will be less collisions, but there may be a lot of extra empty space.
It’s possible to compute the “load factor” of a hash table. The load factor tells us something about how full the hash table is.

### Internal Methods

#### Add()

**Adding a new key/value pair to a hashtable:**

- Send the key to the GetHash method.
- Once you determine the index of where it should be placed, go to that index
- Check if something exists at that index already, if it doesn’t, add it with the key/value pair.
- If something does exist, add the new key/value pair to the data structure within that bucket.

#### Find()

- The Find takes in a key
- Gets the Hash
- Goes to the index location specified.
- Once at the index location is found in the array, it is then the responsibility of the algorithm the iterate through the bucket and see if the key exists
- And return the value.

#### Contains()

- The Contains method will accept a key
- Returns a bool on if that key exists inside the hashtable.
  The best way to do this is to have the contains call the GetHash and check the hashtable if the key exists in the table given the index returned.

#### GetHash()

- Accept a key as a string
- Conduct the hash
- Return the index of the array where the key/value should be placed.
