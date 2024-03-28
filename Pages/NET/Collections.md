# Collections

- Various collections and their use in C#.

## **BitArray**

- **Namespace**: **`System.Collections`**
- **Description**: Represents an array of boolean values (true or false) that are represented as bits (1 or 0). It is a compact way to store bit flags in a single value.
- **Use Cases**: Useful for handling sets of binary flags efficiently, performing bitwise operations, and when you need to manipulate large amounts of bits while minimizing memory usage.

## **HashSet`<T>`**

- **Namespace**: **`System.Collections.Generic`**
- **Description**: Represents a set of unique values. It is implemented as a hash table, providing fast operations for insertion, deletion, and searches.
- **Use Cases**: Ideal for ensuring no duplicates are stored, performing set operations like union, intersection, and determining whether a particular item is present in a collection quickly.

## **SortedSet`<T>`**

- **Namespace**: **`System.Collections.Generic`**
- **Description**: Similar to **`HashSet<T>`**, but automatically sorts the elements as they are inserted. It uses a binary search tree under the hood.
- **Use Cases**: Useful when you need to maintain a sorted collection of unique items. It allows for efficient searches, insertions, and deletions while maintaining order.

## **Dictionaries**

    Dictionaries are collections that store key-value pairs. They are optimized for fast retrieval of values based on keys.

## Dictionary<TKey, TValue>

- **Namespace**: **`System.Collections.Generic`**
- **Description**: A collection of key-value pairs that are organized based on the hash code of the key. It allows for fast lookups.
- **Use Cases**: Ideal for scenarios where you need to quickly access data using a unique key, such as caching, lookups, and settings/preferences storage.

## SortedDictionary<TKey, TValue>

- **Namespace**: **`System.Collections.Generic`**
- **Description**: Similar to **`Dictionary<TKey, TValue>`** but maintains the keys in sorted order. It is implemented using a binary search tree.
- **Use Cases**: Useful when you need the functionality of a dictionary but also need to maintain the keys in a sorted order for iteration purposes.

## **EqualityComparer`<T>`**

- **Namespace**: **`System.Collections.Generic`**
- **Description**: An abstract class that allows for the creation of equality comparison operations for types. The default implementation uses **`Object.Equals`** and **`Object.GetHashCode`** methods, but it can be overridden.
- **Use Cases**: Customizing how collections that rely on equality checks (like **`HashSet<T>`** and **`Dictionary<TKey, TValue>`**) determine whether items are equal. This is particularly useful for implementing case-insensitive checks or comparing complex objects based on certain fields/properties.
