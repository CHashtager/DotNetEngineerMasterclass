# Linear Data Structures

- **Array:** Contiguous block of memory, constant time access
  - **Lookup**: Accessing an element in an array by its index is a constant time operation, O(1).
  - **Insertion**: Inserting an element at the end of an array is a constant time operation, O(1), but if the array needs to grow, it requires allocating a new larger array and copying the elements, resulting in O(n) time complexity.
  - **Deletion**: Removing an element from the end of an array is a constant time operation, O(1), but if elements need to be shifted, it requires O(n) time complexity.
- **Linked List:** Chain of nodes, efficient insertions/deletions
  - **Lookup**: Finding an element in a linked list by its value or index requires traversing the list, resulting in O(n) time complexity.
  - **Insertion**: Inserting an element at the beginning of a linked list is a constant time operation, O(1). Inserting at the end or in the middle requires traversing the list, resulting in O(n) time complexity, unless you maintain a tail pointer for inserting at the end, which is O(1).
  - **Deletion**: Removing an element from the beginning of a linked list is a constant time operation, O(1). Removing from the end or in the middle requires traversing the list, resulting in O(n) time complexity, unless you maintain a tail pointer for removing from the end, which is O(1).
  - **Problems**: Finding the Kth node from the end can be solved using two pointers with a distance of `K-1` between them, resulting in O(n) time complexity.
- **Stack:** Last-In-First-Out (LIFO) data structure
  - All operations on a stack, such as push, pop, and peek, have a constant time complexity, O(1).
  - **Problem**: Checking if an expression is balanced (e.g., parentheses, brackets) can be solved using a stack.
- **Queue:** First-In-First-Out (FIFO) data structure
  - All operations on a queue, such as enqueue and dequeue, have a constant time complexity, O(1).
  - **Implementations**: A queue can be implemented using a circular array with two pointers for enqueue and dequeue, or using two stacks, one for enqueue and one for dequeue.
  - **Problems**: Reversing the items in a queue can be solved by using an auxiliary stack, resulting in O(n) time complexity.
  - **Priority Queue**: A priority queue can be implemented using an array or a heap, with different time complexities for insertion and deletion operations.
- **Hash Table:** Key-value storage with constant time access on average
  - Hash functions are deterministic, meaning they will always produce the same output for a given input.
  - Hash tables use an array to store items internally.
  - All operations (insertion, lookup, deletion) have an average time complexity of O(1), except when iterating over the values, which has a time complexity of O(n).
  - **Collision Handling**: Collisions (when two keys map to the same index) can be handled using techniques like chaining or open addressing (linear probing, quadratic probing, double hashing).
  - **Problems**: Finding the first non-repeated character, removing duplicate items in an array, or finding the first repeated character can be solved using a set, resulting in O(n) time complexity.
- **Collision:** Handled via separate chaining or open addressing
