# Sorting Algorithms

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
