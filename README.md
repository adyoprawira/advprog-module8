1. What are the key differences between unary, server streaming, and bidirectional streaming RPC?

Unary RPC involves a single request followed by a single response, ideal for standard API-like operations. Server streaming sends one request and receives a stream of responses, suitable for scenarios like fetching logs or reports. Bidirectional streaming allows both client and server to send a stream of messages concurrently, making it ideal for real-time applications like chat or live data feeds.

2. What are potential security considerations in Rust gRPC?

Implementing gRPC in Rust requires attention to secure transport, typically using TLS to encrypt communication. Authentication can be managed with client certificates or token-based systems like JWT. Authorization should be enforced at the service layer to ensure only permitted users access sensitive RPC methods.

3. What are the challenges with bidirectional streaming in Rust gRPC?

Handling bidirectional streams can be complex due to the need for concurrent message processing on both sides. Developers must manage asynchronous tasks carefully and ensure proper error handling, flow control, and shutdown logic. It also increases the risk of race conditions or resource leaks if not implemented correctly.

4. What are the pros and cons of using ReceiverStream for streaming responses?

ReceiverStream makes it easy to convert a tokio::mpsc receiver into a gRPC stream, simplifying implementation. It’s effective for pushing server-side updates to clients using standard async patterns. However, it may introduce latency or backpressure issues if not tuned properly for high-throughput applications.

5. How to structure Rust gRPC code for modularity and reuse?

Separating concerns into distinct modules or crates—such as proto definitions, service logic, and transport layers—improves clarity and maintainability. Using traits for shared behaviors and abstracting over common logic enables code reuse. Keeping proto files in a shared crate also helps coordinate changes across client and server.

6. What more is needed for complex payment logic in MyPaymentService?

Robust payment processing would require validations, transaction deduplication, and audit logging. Integration with external payment gateways and handling retries or failures are crucial for reliability. You’d also need to ensure transactional consistency and possibly implement fraud detection logic.

7. How does gRPC affect distributed system architecture?

gRPC promotes a strongly-typed, service-oriented architecture that enables reliable inter-service communication. It reduces payload size and improves efficiency compared to REST, especially for internal microservices. However, integrating with systems that don’t support gRPC may require additional gateways or adapters.

8. What are the pros and cons of HTTP/2 (gRPC) vs HTTP/1.1/WebSockets (REST)?

HTTP/2, the foundation of gRPC, supports multiplexed streams, reducing latency and improving throughput. It also includes built-in flow control and binary framing, which make it more efficient than HTTP/1.1. However, it’s less human-readable, harder to debug, and requires HTTPS in most environments.

9. How does gRPC’s streaming differ from REST’s request-response?

REST APIs follow a one-request-one-response model, which can be limiting for real-time applications. In contrast, gRPC supports bidirectional and server-side streaming, enabling efficient, low-latency communication. This makes gRPC a better fit for applications that require continuous data flow, like messaging systems or telemetry feeds.

10. What are the implications of gRPC’s schema-based Protobuf vs JSON?

Protocol Buffers enforce a strict schema, offering compact, fast, and type-safe serialization, which is beneficial for performance-critical services. However, schema evolution must be managed carefully to avoid compatibility issues. JSON is more flexible and human-readable but less efficient and more error-prone in typed languages.
