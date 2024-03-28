# Graphs

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
