# Stream

## Stream Architecture

- Managing streams of data in C#.

### Backing Stores

- **`FileStream`**, **`NetworkStream`**, **`MemoryStream`**, and **`PipeStream`** are examples of stream implementations for different data sources.

### Decorators

- Decorator streams like **`BufferedStream`**, **`GZipStream`**, and **`CryptoStream`** add additional functionality (buffering, compression, encryption) to underlying streams.

### Adapters

- **`StreamReader`** and **`StreamWriter`** adapt streams for reading and writing text, converting bytes to characters and vice versa.

### Thread Safety

- Streams are generally not thread-safe, meaning simultaneous reads or writes from multiple threads require synchronization.

### **`File`** and **`Directory`** Classes vs **`FileInfo`** and **`DirectoryInfo`**

- **`File`** and **`Directory`** provide static methods for file and directory operations, while **`FileInfo`** and **`DirectoryInfo`** offer instance methods.

### Memory-Mapped Files

- Memory-mapped files allow for efficient file access by mapping them into memory, useful for working with large files or for inter-process communication.
