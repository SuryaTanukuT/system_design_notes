# system_design_notes

1. Client-Server Architecture
Overview:
This is a model where multiple client devices request and receive services from a centralized server. The server hosts resources, services, or data, while the clients interact with the server through well-defined protocols.

Key Points:

Separation of Concerns:

Clients handle presentation and user interactions.

Servers handle data processing, business logic, and storage.

Scalability:

Horizontal scaling (adding more servers) is common.

Use of load balancers to distribute client requests across multiple servers.

Stateless vs. Stateful:

Stateless systems (e.g., HTTP) do not retain client session information between requests.

Stateful systems maintain session state which can complicate scaling.

Best Practices:

Use caching mechanisms (e.g., CDN, in-memory caches) to reduce server load.

Employ fault tolerance and redundancy to handle server failures.

Secure communication channels and validate client requests to prevent unauthorized access.

2. IP Address
Overview:
An IP (Internet Protocol) address is a unique identifier for devices on a network. It enables routing of data packets between hosts.

Key Points:

Types:

IPv4: Uses 32-bit addresses (e.g., 192.168.0.1) and supports about 4.3 billion unique addresses.

IPv6: Uses 128-bit addresses (e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334) to overcome IPv4 exhaustion.

Subnetting:

Divides networks into smaller segments to optimize routing and improve security.

Dynamic vs. Static IPs:

Dynamic IPs are assigned by DHCP servers.

Static IPs are manually assigned and remain constant.

Best Practices:

Plan address allocation to support scalability.

Implement NAT (Network Address Translation) where necessary to conserve public IP addresses.

Use IPv6 adoption strategies as network needs grow.

3. DNS (Domain Name System)
Overview:
DNS translates human-readable domain names (like www.example.com) into IP addresses required for locating computer services and devices.

Key Points:

Hierarchy:

Root Servers: Begin the lookup process.

TLD Servers: Handle top-level domains (.com, .org, etc.).

Authoritative Servers: Store actual domain-to-IP mappings.

Caching:

Reduces lookup times by storing query results locally.

Time-to-Live (TTL) values govern how long records are cached.

Load Balancing:

DNS can distribute traffic among multiple servers using techniques like round-robin.

Best Practices:

Secure your DNS infrastructure to prevent spoofing or cache poisoning.

Monitor DNS performance to reduce latency.

Consider using secondary DNS providers for redundancy.

4. Proxy / Reverse Proxy
Overview:
Both proxy and reverse proxy servers act as intermediaries in network communications, though their roles differ.

Key Points:

Proxy Server (Forward Proxy):

Sits between clients and the internet.

Often used for caching, filtering content, or providing anonymity.

Reverse Proxy:

Sits in front of one or more web servers.

Distributes incoming client requests to the appropriate backend servers.

Common uses include load balancing, SSL termination, and caching.

Differences:

Forward Proxy: Client-aware; hides clients’ identities.

Reverse Proxy: Server-aware; hides backend server details from clients.

Best Practices:

Choose based on your security, performance, and scaling needs.

Ensure proper logging and monitoring.

Configure caching rules and timeouts carefully to enhance performance.

5. Latency
Overview:
Latency is the time delay between the initiation of a request and the receipt of the response. In distributed systems, low latency is crucial for a responsive user experience.

Key Points:

Components of Latency:

Propagation Delay: Time for a signal to travel through the medium.

Transmission Delay: Time to push all the packet’s bits onto the wire.

Processing Delay: Time taken by network devices to process the packet.

Queuing Delay: Time spent waiting in queues.

Measurement:

Typically measured in milliseconds (ms) using tools like ping and traceroute.

Mitigation Techniques:

Use Content Delivery Networks (CDNs) to bring content closer to users.

Optimize network paths and use efficient protocols.

Employ asynchronous processing and caching strategies.

Best Practices:

Continuously monitor and measure latency.

Optimize code and infrastructure to reduce processing delays.

Design systems to handle latency gracefully (e.g., using timeouts and retries).

6. HTTP/HTTPS
Overview:
HTTP (Hypertext Transfer Protocol) is the foundation of data communication for the web. HTTPS is the secure version that uses encryption to protect data.

Key Points:

HTTP:

Operates over a TCP/IP connection.

Utilizes methods like GET, POST, PUT, DELETE, etc.

Is stateless by design.

HTTPS:

Wraps HTTP in SSL/TLS protocols for encryption.

Ensures data integrity and confidentiality between client and server.

Differences & Use Cases:

HTTP is used for public information; HTTPS is critical for sensitive data like financial transactions.

Best Practices:

Always use HTTPS for secure data transfer.

Keep your certificates updated and follow modern TLS protocols.

Leverage HTTP/2 or HTTP/3 where supported to improve performance.

7. APIs (Application Programming Interfaces)
Overview:
APIs are sets of rules that allow software components to communicate with each other. They provide a means for different systems to exchange data and functionality.

Key Points:

Types:

Web APIs: Often use HTTP/HTTPS.

Library/Framework APIs: Provide language-specific functionalities.

Design Considerations:

Versioning: Ensure backward compatibility.

Security: Implement authentication (e.g., API keys, OAuth).

Rate Limiting: Protect against abuse and overloading.

Best Practices:

Keep the interface intuitive and consistent.

Document your API thoroughly.

Ensure scalability by decoupling API layers from business logic.

8. REST API
Overview:
REST (Representational State Transfer) is an architectural style that uses standard HTTP methods to interact with resources.

Key Points:

Principles:

Statelessness: Each request from a client contains all necessary information.

Uniform Interface: Consistent use of HTTP methods and status codes.

Resource-Based: Uses URIs to identify resources (nouns rather than verbs).

Cacheable: Responses should define if they can be cached.

Layered System: Supports separation between client and server through intermediaries.

Design Guidelines:

Use standard HTTP methods: GET, POST, PUT, DELETE.

Structure URIs clearly (e.g., /users, /orders/123).

Use proper status codes (200, 404, 500, etc.).

Best Practices:

Ensure consistency in naming and versioning.

Provide comprehensive documentation and examples.

Use hypermedia (HATEOAS) where applicable to guide client interactions.

9. GraphQL
Overview:
GraphQL is a query language for APIs that allows clients to request exactly the data they need. It’s an alternative to REST and aims to reduce issues like over-fetching or under-fetching.

Key Points:

Core Concepts:

Schema: Defines the types and relationships available.

Queries: Clients specify the structure of the required response.

Mutations: For modifying data on the server.

Subscriptions: Real-time updates.

Advantages Over REST:

Single endpoint for all data.

Precise data retrieval reduces bandwidth usage.

Strongly typed schema leads to better validation and error handling.

Best Practices:

Use proper caching strategies, as GraphQL queries are often more complex.

Implement depth limiting and query complexity analysis to prevent abuse.

Provide clear schema documentation and use tooling like GraphiQL for interactive exploration.

10. Databases
Overview:
Databases are systems designed for storing, retrieving, and managing data. They come in various types and are chosen based on system requirements.

Key Points:

Types of Databases:

Relational Databases (SQL):

Use structured query language.

Emphasize ACID properties (Atomicity, Consistency, Isolation, Durability).

Examples: MySQL, PostgreSQL.

NoSQL Databases:

Schema-less and more flexible.

Types include document stores (MongoDB), key-value stores (Redis), column stores (Cassandra), and graph databases.

Often follow BASE properties (Basically Available, Soft state, Eventually consistent).

Design Considerations:

Normalization vs. Denormalization:

Normalization reduces data redundancy.

Denormalization improves read performance.

Indexing:

Speeds up query performance but may slow down writes.

Scaling:

Vertical scaling (upgrading hardware) vs. horizontal scaling (sharding, replication).

CAP Theorem:

In distributed systems, you must choose trade-offs between Consistency, Availability, and Partition tolerance.

Best Practices:

Choose the right database type based on data structure and access patterns.

Implement proper backup and disaster recovery strategies.

Monitor performance and adjust indexes, queries, and schema as needed.

