An abstract data type describes the shape and behavior of data stored in some structure, as well as a set of operations that we'd like to perform on that data. It does not detail the implementation of the data structure itself --- an abstract data type might admit many different implementations.

# Stack

A stack is a data structure that stores values and supports the following operations:

- _isEmpty_: determining if the stack is empty
- _push_: adding an item to the stack
- _pop_: removing and returning the most recently added item
- _peek_: looking at the most recently added item to the stack without removing it

The basic idea of a stack is that we only have access to the most recently added item. We call this principle Last In First Out (LIFO). Usually, the side of the stack that has the most recent elements is called the "top" of the stack.

Stacks are ubiquitous in algorithms, and in fact form the basis for almost all recursive or hierarchical structures.

## Implementations

### Singly linked list

One possible implementation of a stack uses a singly [linked list](#linked-list). Since we can add and remove items from the head of the list in constant time, we simply use a linked list as a stack, imagining that the head of the list is the "top" of the stack.

### Array

If we know the size of the stack will be bounded ahead of time, we can also implement a stack using an array and keeping track of the index of our top element. Pushing an element just requires incrementing our top index setting a value in the array, while popping just accesses the array at the top index and decrements the index. In many cases this will be much faster than a linked list since the elements are all stored in one continuous block of memory and we don't need to follow any pointers.

### Dynamic Array

If we don't know the size of the stack ahead of time, we can still use a [dynamic array](#dynamic-array), which supports addition and removal from the end in amortized constant time. As with an array this gives better locality (meaning the values are stored next to each other in memory) than the linked list. However the dynamic array allocation can add more wasted space than the linked list approach when the values are being stored directly in the array, since the dynamic array has to allocate an array with extra capacity.

# Queue

A queue is a structure that stores items where the items can only be retrieved in First In First Out order. What this means is that at any given moment we only have access to the earliest inserted element that's still in the queue. As with the stack, we have four operations:

- _isEmpty_: determines if the list is empty
- _enqueue_: adds an item to the queue
- _dequeue_: removes the item from the queue that has been in the queue the longest and returns it
- _peek_: looks at the item from the queue that has been in the queue the longest without returning it

Queues are usually thought of has having two sides, a "front" and a "back", where elements are inserted at the back, and removed at the front.

## Implementations

### Singly Linked List

As with the stack, we can implement a queue with a singly linked list. But which side of the list is the front of the queue, and which side is the last? To remind ourselves, a singly linked list with a head and a tail pointer supports these operations:

- _Add to beginning_: O(1)
- _Remove from beginning_: O(1)
- _Add to end_: O(1)
- _Remove from end_: O(n)

As we can see, the singly linked list can do everything above in constant time except for removing from the end. Since we need to remove elements from the "front" of the queue, we want to make the beginning of the list represent the front of the queue. This means our enqueue operation appends elements to the end of the list, and our dequeue operation removes elements from the beginning of the list.

### Array

Implementing a queue with an array is a little trickier than implement the stack with an array. The basic approach is to allocate an array with a certain capacity, and then to keep track of the `front` index and keep track of the `rear` index, which both start at 0. New elements are enqueued at the `rear` index and increment it. Elements are dequeued at the `front` index and increment it as well. When the `front` is equal to the `rear`, we know the queue is empty.

Where this gets complicated is what happens when the `rear` index reaches the capacity of the array. As with a dynamic array, we can allocate a new array and copy the existing values into the new array. However, since the actual number of items at this point could be much smaller than the capacity of the array (since the number of items is `rear - front`), we don't necessarily need to allocate a new array with double the capacity, as in a dynamic array. In fact, we don't necessarily need to allocate a new array at all --- we can perform a memory copy from the items (which at this point are all at the end of the array) to the beginning of the current array.

A variant of this is the circular buffer, which we can use in any situation where the size of the queue is bounded. We allocate our array some capacity and when either the `rear` or `front` indices reaches the end of the array, we start them out at `0`. We then just need to perform a check to make sure we never increment `front` to equals `rear`, since the condition `front == rear` represents an empty queue. In this version, we refuse to `enqueue` any more items when the queue is at capacity, and let the user know with either an exception or a return value that the item was rejected.

There are many other array-based strategies that can be used to implement a queue.

# List

A list represents sequential data. It provides some or all of the following operations:

- Constructing an empty list
- Adding elements to the list at the beginning or end
- Inserting elements in the interior of the list
- Getting the element at the beginning or end of the list
- Getting the element at some arbitrary index
- Getting the length of the list, or determining whether it is an empty list

## Dynamic Array

The dynamic array implements the list data type using a simple array. The structure has a _size_, which is the number of elements currently stored in it, and a _capacity_, which is the size of the underlying array. Elements can be added to the end of the list by simply setting the array at the next unused index. When the size grows to equal the capacity, a new larger underlying array is calculated and the elements are copied from the original list to the larger list. By growing the size of the list by some constant factor, the dynamic array is able to add elements to the end in amortized constant time.

Deleting any number elements from the end of the list can be done in constant time by setting the size to a smaller number.

Random access is also constant time since the dynamic array uses an array to store the elements.

However, adding or deleting elements to the beginning or interior of the array is a linear time operation, since it requires shifting the elements.

## Linked List

The linked list implements the list data type by storing elements anywhere in memory along with pointers between those elements. In the _singly linked list_, each element is stored with a pointer to the next element. The linked list structure just stores a pointer to the first element of the list, allowing us to reach any element by following the sequence of pointers.

This allows us to easily add elements to the beginning of the list, by simply allocating a new element in memory and adding a pointer to the previous first element. Then we change the first element pointer to point to our newly inserted element. Similarly we can delete elements from the beginning of the list by changing our first element pointer to point to the next element in the list.

If the linked list keeps a pointer to the last element of the list, then we can also add elements to the end of the list in constant time.

If we have a pointer to any element in the list, we can insert a new element right after that element in constant time, by updating the chain of pointers. We can also delete any element in the list in constant time, provided we have a pointer to the previous element.

There are a number of other variations on the linked list. In the _doubly linked list_, each element maintains a pointer to both the next and previous element. This allows traversing the list in both directions, as well as allowing insertion or deletion at, before, or after an element given a pointer to that element. This comes at the cost of storing an extra pointer per node.

Linked lists have a number of advantages and disadvantages versus arrays or dynamic arrays. Linked lists are ideal when they only need to be accessed sequentially, and they excel when elements need to be inserted or removed frequently. However, they don't allow random access, and if we're not searching the list, an operation like "insert a new element after the nth element" still takes O(n) time since we have to traverse the whole list to get to the nth element.

# Set

# Map
