Java provides us with a rich set of data structures and interfaces in the standard Collections library.

# List interface

More to say here.

# ArrayList

`ArrayList`s give us an array-like interface, with `O(1)` random access, but also with the ability to add and remove elements from the end in amortized constant time. Behind the scenes `ArrayList` is backed by a plain Java array with a size value and a capacity. This is a classic implementation of the [dynamic array](https://en.wikipedia.org/wiki/Dynamic_array) data structure. The size indicates the current number of elements stored in the ArrayList, while the capacity is the size of the underlying array. Elements are pushed onto the end of the ArrayList by simple assignment until the size reaches the capacity. When that happens a new larger array is allocated in memory. This larger array is allocated with a capacity equal to some factor multiplied by the previous capacity. (I believe it's 1.8 for Java's ArrayList implementation.)

# Map interface

A [map](https://en.wikipedia.org/wiki/Associative_array) is an abstract data type that consists of key-value pairs, where each key is paired with at most one value. At a minimum the map will support the following operations: looking up a value at a key, setting a value to a new key, removing a key-value pair, and modifying an existing value at a key.

# HashMap

Depending on implementation, a hash map will generally support the map operations in constant time or near constant time.
