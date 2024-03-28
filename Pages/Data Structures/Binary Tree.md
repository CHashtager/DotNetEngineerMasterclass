# Binary Tree Problems

- Finding the minimum value in a Binary Tree can be solved by traversing the leftmost nodes, resulting in O(log n) time complexity for a balanced tree and O(n) for a skewed tree.
- Validating a Binary Tree as a Binary Search Tree can be solved by performing an in-order traversal and checking if the values are in ascending order, resulting in O(n) time complexity.
- Finding nodes at distance K from the root can be solved using a combination of depth-first and breadth-first traversals, resulting in O(n) time complexity.

## Heaps

Complete binary tree with heap property, used for priority queues and heap sort

- A heap is a complete binary tree that satisfies the heap property (either min-heap or max-heap).
- Insertion and deletion operations have a time complexity of O(log n) or O(h), where h is the height of the heap.
- Heaps are more efficiently implemented using an array than a tree structure.
- **Heap Sort**: O(n log n) time complexity.
- **Priority Queue**: Array implementation has O(n) time complexity for insertion and O(1) for deletion, while heap implementation has O(log n) time complexity for both insertion and deletion.
- **Problems**: Finding the Kth largest item in a list can be solved using a max heap, and implementing a heapify algorithm transforms an array into a heap in-place.
