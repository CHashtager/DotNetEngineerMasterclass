# Network

## Network Architecture

- Handling network-related operations in C#.

### URIs

- **`System.Uri` Class:** Represents a Uniform Resource Identifier (URI) and provides methods for parsing and constructing URIs. It's widely used across .NET networking libraries to specify the addresses of network resources.

### WebClient

- **`WebClient` Class:** A higher-level abstraction for sending HTTP requests and receiving responses. It's easy to use for downloading or uploading data but is considered outdated and has been superseded by **`HttpClient`**.

### HttpClient

- **`HttpClient` Class:** Provides a modern, flexible, and reusable way to send HTTP requests and receive responses. It's designed to be instantiated once and reused throughout the life of an application, supporting asynchronous operations and HTTP/2 features.

### HttpListener

- **`HttpListener` Class:** A simple, programmatically controlled HTTP server that listens for HTTP requests and processes them. Useful for creating HTTP servers without relying on IIS or other external server software.

### TCP and UDP

- **TCP (Transmission Control Protocol):** Provides a reliable, connection-oriented way to send and receive data over the network. In C#, **`TcpClient`** and **`TcpListener`** classes are used for client-server TCP communications.
- **UDP (User Datagram Protocol):** Offers a connectionless protocol for scenarios where speed is preferred over reliability. **`UdpClient`** is used for sending and receiving datagrams over UDP.
