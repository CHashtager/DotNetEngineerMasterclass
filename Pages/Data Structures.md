# Data Structures

## Time and Space Complexity

- **Time Complexity:** How the runtime scales with input size
- **Space Complexity:** How the memory usage scales with input size

### Time Complexity

- **O(1)**: Constant time, the algorithm's time complexity does not depend on the input size.
- **O(log n)**: Logarithmic time, the algorithm's time complexity grows logarithmically with the input size.
- **O(n)**: Linear time, the algorithm's time complexity grows linearly with the input size.
- **O(n log n)**: Linearithmic time, the algorithm's time complexity grows as the product of linear and logarithmic factors.
- **O(n^2)**: Quadratic time, the algorithm's time complexity grows quadratically with the input size.
- **O(n^3)**: Cubic time, the algorithm's time complexity grows as a cubic function of the input size.
- **O(n^k)**: Polynomial time, the algorithm's time complexity grows as a polynomial function of the input size.
- **O(a^n)**: Exponential time, the algorithm's time complexity grows exponentially with the input size.
- **O(n!)**: Factorial time, the algorithm's time complexity grows as the factorial of the input size.

### Space Complexity

- The amount of memory or space required by an algorithm or data structure as the input size grows.

## Linear Data Structures

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

## Sorting Algorithms

- **Bubble Sort:** Simple but inefficient for large inputs
  - O(n^2) time complexity.
- **Selection Sort:** In-place but inefficient for large inputs
  - O(n^2) time complexity.
- **Insertion Sort:** Efficient for small or mostly sorted inputs
  - O(n^2) time complexity, but efficient for small or mostly sorted inputs.
- **Merge Sort:** Divide-and-conquer, efficient and stable
  - O(n log n) time complexity and O(n) space complexity.
  - Divides the input array into two halves, calls itself for the two halves, and then merges the two sorted halves.
- **Quick Sort:** Divide-and-conquer, efficient but unstable
  - O(n log n) average time complexity, but O(n^2) in the worst case when the pivot is not chosen optimally.
  - It picks an element as pivot and partitions the given array around the picked pivot.

## Search Algorithms

- **Linear Search:** Brute force search, O(n) time complexity
- **Binary Search:** Efficient search for sorted arrays, O(log n) time complexity
  - O(log n) time complexity and O(log n) space complexity for the recursive implementation, or O(1) space complexity for the iterative implementation.

## Tree Data Structures

- **Binary Search Tree:** Sorted data with efficient search, insert and delete operations
  - For any given node, all values in the left subtree are less than the node's value, and all values in the right subtree are greater.
  - Lookup, insertion, and deletion operations have an average time complexity of O(log n) and a worst-case time complexity of O(n) when the tree is skewed.
  - The value of each node is greater than the left subtree and less than the right subtree.
- **Tree Traversals:** Different ways to visit nodes in a tree
  - **Breadth-First:** Level by level
    - Visits all nodes at the same level before moving to the next level.
  - **Depth-First:** Pre-order, In-order, Post-order
    - **Pre-order**: Root -> Left -> Right
    - **Post-order**: Left -> Right -> Root
    - **In-order**: Left -> Root -> Right (ascending order for BST)
- **Balanced Trees:** Self-balancing trees for efficient operations
  - **Self-Balancing Trees**: AVL Tree, Red-Black Tree, and B-Tree are examples of self-balancing trees that maintain a balanced structure to ensure logarithmic time complexity for operations.
  - O(log n) complexity
  - **AVL Tree:** Height-balanced binary search tree
    - The heights of the two child subtrees of any node differ by no more than one.
  - **Red-Black Tree:** Self-balancing binary search tree
    - Ensures balance by coloring nodes red or black
  - **B-Tree:** Self-balancing tree for disk-based data structures
    - Allowing more than two children per node. B-Trees are optimized for systems that read and write large blocks of data, such as databases and filesystems.

## Binary Tree Problems

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

## Tries (Digital, Radix, or Prefix Tree)

Prefix tree, efficient information retrieval operations

- Tries are not binary trees; they are tree-based data structures used for efficient information retrieval operations like prefix search and autocomplete.
- Lookup, insertion, and deletion operations have a time complexity of O(L), where L is the length of the word being processed.
- Pre-order traversal is used to print all words, and post-order traversal is used to delete a word.

## Graphs

There are two primary types of graphs:

- **Directed Graphs (Digraphs):** Where edges have a direction, from one vertex to another.
- **Undirected Graphs:** Where edges are bidirectional.

Collection of vertices and edges

- Graphs are used to represent connected objects, and a tree is a type of graph without cycles.
- **Adjacency Matrix**:
  - Space complexity: O(n^2)
  - Add/Remove Node: O(V^2), where V is the number of vertices
  - Add/Remove Edge: O(1)
  - Find adjacent nodes: O(V)
- **Adjacency List**:
  - Space complexity: O(V+E), where E is the number of edges
  - Add Node: O(1)
  - Remove Node: O(V+E)
  - Add/Remove Edge: O(V)
  - Check if two nodes are connected: O(V)
  - Find adjacent nodes: O(K) or O(V), where K is the number of adjacent nodes
- **Traversal**:
  - **Depth-First**: Uses recursion or iteration with a HashSet to track visited nodes.
  - **Breadth-First**: Uses a queue or iteration.
- **Topological Sort**: Performed using Depth-First traversal and a stack.
  - Is possible only for Directed Acyclic Graphs (DAGs) and is useful in scheduling tasks, ordering of cells in spreadsheets, and determining compilation sequence in programming languages.
- **Cycle Detection**: Algorithms exist to detect cycles in graphs.
  - Directed graphs, this can be done using algorithms like Depth-First Search (DFS) with additional data structures to track ancestors.
  - Undirected graphs, DFS or Union-Find can be used to detect cycles.
  - Cycle detection is crucial in applications such as network analysis, deadlock detection in operating systems, and more.
- **Problems**: Finding the shortest path between two nodes and finding a node's "best friend" (adjacent node with the highest weight) are common graph problems.

## String Manipulation

- **Count Vowels**: Use a loop to iterate over the string and count vowels, resulting in O(n) time complexity.
- **Reverse**: Iterate from the start, iterate from the end, or use a stack, all resulting in O(n) time complexity.
- **Reverse Words in a Sentence**: Use a stack or iterate from the end of words, resulting in O(n) time complexity.
- **Remove Duplicates**: Use a HashSet to track visited characters, resulting in O(n) time complexity.
- **Most Repeated Character**: Use a HashMap or an array of size 256 (ASCII values) to count character frequencies, resulting in O(n) time complexity.
