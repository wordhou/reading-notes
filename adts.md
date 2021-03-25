An abstract data type describes the shape and behavior of data stored in some structure, as well as a set of operations that we'd like to perform on that data. It does not detail the implementation of the data structure itself --- an abstract data type might admit many different implementations.

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
