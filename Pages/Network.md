# Network

## Basic Concepts

### OSI Model

- The Open Systems Interconnection (OSI) model is a conceptual framework used to describe the functions of a networking system.
- It consists of seven layers: Physical, Data Link, Network, Transport, Session, Presentation, and Application.
- Each layer has specific responsibilities and communicates with the layers above and below it.

### How the Web Works

- The web relies on the client-server architecture, where a client (e.g., a web browser) sends requests to a server, and the server responds with the requested resources.
- The communication happens over the HTTP protocol, which is an application-layer protocol.
- Domain Name System (DNS) maps human-readable domain names to IP addresses for server identification.

## Application Layer Protocols

### HTTP/1.x vs HTTP/2 vs HTTP/3

- **HTTP/1.x:** Older version, supports only one outstanding request per TCP connection (addressed by HTTP/1.1 keep-alive).
- **HTTP/2:** Multiplexes multiple requests over a single TCP connection, improving performance and efficiency.
- **HTTP/3:** Built on top of the QUIC protocol, providing additional performance improvements and security benefits.

### Keep-Alive Concept (Pros and Cons)

- **Keep-Alive:** Allows multiple HTTP requests/responses to be sent over a single TCP connection, reducing connection overhead.
- **Pros:** Improved performance, reduced latency, and more efficient resource utilization.
- **Cons:** Potential security risks (e.g., denial of service attacks), increased memory usage, and potential head-of-line blocking issues.
