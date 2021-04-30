# Data structures

# Hash Tables

Hash tables are used to implement a variety of abstract data types, including [maps](adts.md#map) and [sets](adts.md#set). Hash tables describe a way of storing items in an indexed structure by using a hash function to determine the index of any given item.

Hash tables are generally built with an array since they allow efficient access by index. A hash function is used to produce an index for any given item or key-value pair that we'd like to insert into the table. The hash function is mapped to an array index, and then the item or key-value pair is stored in that array location. Since computing the hash function and indexing the array are both constant time operations, adding or accessing values in a hash table is generally a constant time operation, given some key assumptions.

## A good hash function

A hash function accepts values from an input domain and maps those values into an output domain. The main criteria for a good hash function for implementing a hash table is that it distributes data points uniformly into the output domain. In other words, we'd like our hash function to avoid assigning the same output values to different input values whenever possible, which we term a "collision". Since the output domain is usually smaller than the input domain, it's impossible to completely prevent collisions, but a function that distributes input values as evenly as possible is ideal as it minimizes the expected number of collisions.

## Handling collisions

How to handle collisions is the central question of the design of a data structure based on hash tables. There are two main approaches:

- **Separate chaining**: Store the values in a linked list at each array index. When collisions occur, append the new value or key-value pair to the linked list.
- **Open addressing**: Store the values directly in the array, but when a collision occurs, store the value in the "next" available index according to some sequence of indices.

## Separate chaining

In separate chaining, the array stores the head of a linked list that contains the values whose hashes mapped to that index. Initially the array is initialized to null values.

To add a value, we hash the value or its key, and map that to an array index using the modulo function. Then we insert the value or key-value pair to the linked list. This can be done in O(1) since adding a value to a linked list to either the front or the back can be done in constant time.

To lookup a value or key-value pair, we perform the hash and access the array index corresponding to that hash. Then, we need to traverse the linked list at that array index in order to determine whether that value or key is a member of that linked list.

In the best case when collisions are rare, the length of each linked list is small and the operations all run in constant time. In the worst case, when there are many collisions and when the hashes are unevenly distributed the algorithm becomes O(n). The linked lists also grow as the number of elements in the table grow as a proportion of size of the array.

## Open addressing

In open addressing the values are stored directly in the array. When a collision is detected on an insertion, the value is inserted in the next index in some sequence of indices that depends on its value. There are a number of open addressing schemes that have different sequences. The basic methods are:

- Linear probing
- Quadratic probing
- Double hashing

### Linear probing

In linear probing, when we are attempting to insert an element which hashes to index `i` and index `i` is already occupied, we attempt to store the element at index `i + k`, where `k` is some constant. If that index is occupied, we add `k` again, and try and store the element there. We continue jumping like this until we find an unoccupied slot and store the value there.

To lookup in a hash table with linear probing, we need to lookup the index for the hash value, and then repeatedly look up the next index by adding `k` until we find an empty slot.

Finally deletion is somewhat complicated.

### Quadratic probing

### Double hashing
