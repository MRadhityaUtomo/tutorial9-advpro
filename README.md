# Module 9
## REFLECTION
<br>
1. What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable? <br>
Jawab : 

- Unary is an interaction that sends 1 request and accepts 1 response (1 to 1). Unary is most fitted to be used for simple operations that doesn't need any continuous data transfers, such as user authentications or database rips. An example for this module is the Payment Service function.

- Server Streaming RPC is an interaction where the client sends one request and the server sends back a stream of responses. Server Streaming RPC is most suitable for situations where the server needs to continuously send data or large amounts of data to the client, such as real-time updates or continuous data delivery. An example in this tutorial is a Transaction Service.

- Bi-directional Streaming RPC is an interaction between a client and a server where both can send data streams to each other within the same session. Bi-directional Streaming RPC is most suitable for real-time interactive communication that requires continuous two-way communication. An example in this tutorial is a Chat Service.

<br>
<br>

2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption? <br>
Jawab :<br>
In implementing gRPC services in Rust, ensuring security from authentication to data encryption is crucial. Authentication is the first step to determine who can access the system. Mechanisms such as JWT tokens or mutual authentication with TLS should be implemented to verify identities before allowing access to services. After that, authorization needs to be enforced to determine that users have the right to perform certain actions, such as accessing or modifying resources. Middleware can be used for implementing authorization. In addition to the above two steps, encrypting data through TLS is also important to secure the communication process between the client and server.

<br>
<br>

3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications? <br>
Jawab : 

In handling bidirectional streaming in Rust gRPC, especially for chat applications, various challenges or issues may arise, such as:

- Memory management and asynchronous handling: In Rust, managing ownership and the lifecycle of data needs to be carefully handled to avoid memory leaks or race conditions.

- Security concerns (Encryption and Authentication): Because sensitive data such as private messages are continuously transmitted, ensuring encryption and authentication mechanisms are in place is crucial.

- Concurrency: Ensuring the application can handle a large volume of messages concurrently is not a trivial task and requires careful consideration to avoid bottlenecks or performance issues.

<br>
<br>

4. What are the advantages and disadvantages of using the tokio_stream::wrappers::ReceiverStream for streaming responses in Rust gRPC services? <br>
Jawab : 

Advantages: <br>
- Integration with Tokio: ReceiverStream integrates well with the Tokio ecosystem, providing seamless asynchronous operations.
- Asynchronous data management: The ability to manage data asynchronously allows for improved efficiency and responsiveness in handling bidirectional streaming.

Disadvantages: <br>
- Potential overhead: Introducing asynchronous operations may introduce some overhead, impacting performance.
- Increased complexity: Implementing asynchronous operations can increase the complexity of the codebase, requiring additional effort for development and maintenance.
- Dependency on Tokio: Since ReceiverStream is part of the Tokio ecosystem, its usage necessitates the entire application to run on the Tokio runtime, which can limit flexibility and interoperability with other runtime systems.

<br>
<br>

5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time? <br>
Jawab : 

- Modularity: Separate gRPC service functions and functionalities into different modules or crates. For instance, the definition of the gRPC service (`services.proto`), server implementation (`grpc_server.rs`), and client (`grpc_client.rs`) can be managed in separate modules. This facilitates code management and reuse.

- Trait Usage: Utilize traits to define functionalities that can be shared among components. By defining traits, you can abstract common behavior and allow different components to implement them as needed, promoting code reuse and maintainability.

- External Library Usage: Incorporate external libraries for common tasks to reduce code duplication. Leveraging existing libraries can streamline development efforts and ensure consistency in implementing common functionalities.

<br>
<br>

6. In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic? <br>
Jawab : 

In implementing MyPaymentService for more complex payment processing, additional steps can be helpful:
- Data validation: Validate data to ensure all incoming payment information is valid.

- Secure integration with payment gateways: The system should securely integrate with payment gateways to process transactions.

- Implementation replacement using server streaming: Replace the implementation with server streaming to support processing large volumes of transaction data simultaneously and continuously.

<br>
<br>

7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms? <br>
Jawab : <br>
The use of gRPC as a communication protocol has a significant impact on the architecture and design of distributed systems. By relying on clear definitions in proto files, gRPC simplifies interactions between modules without the need for manual configuration of HTTP methods, as often required in REST approaches. Operating over HTTP/2, gRPC facilitates more efficient and faster communication between services with low overhead and superior streaming capabilities. These features enable systems using gRPC to communicate more effectively and efficiently, enhancing performance and facilitating integration between various system components.

<br>
<br>

8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs? <br>
Jawab : <br>

Advantages:

- Ability to manage multiple requests and responses through a single connection using multiplexing techniques. This effectively reduces latency and improves application performance because, compared to HTTP/1.1, HTTP/2 allows multiple requests or responses to be sent through the same TCP connection simultaneously. <br>

Disadvantages:

- HTTP/2 implementation tends to be more complex and requires SSL/TLS encryption, which can add administrative overhead and costs. On the other hand, WebSocket in HTTP/1.1 allows effective two-way and real-time communication, which in some cases may be simpler to set up compared to HTTP/2 setups.

<br>
<br>

9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness? <br>
Jawab : <br>
The request-response model in REST API differs significantly from bidirectional streaming in gRPC, especially in terms of real-time communication and responsiveness. In REST API, which uses HTTP/1.1, communication is confined to a pattern where the client sends one request and waits for one response from the server. This can be limiting in real-time applications because each interaction requires a separate round trip, which can result in higher latency. In contrast, gRPC uses HTTP/2 which supports multiplexing, allowing simultaneous transmission of multiple requests and responses within the same connection. This significantly reduces latency and improves communication efficiency, making gRPC highly suitable for applications requiring real-time and responsive data exchange between client and server.

<br>
<br>

10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads? <br>
Jawab : <br>
The use of schema-based approach in gRPC with Protocol Buffers differs significantly from the more flexible schema-less approach of JSON in REST API. Protocol Buffers in gRPC provide automatic data validation and optimization, helping to reduce bandwidth and improve data processing speed. This is particularly useful for applications requiring high efficiency and consistent data formats. On the other hand, JSON in REST API offers more flexibility in handling dynamic and changing data, facilitating adaptation to diverse needs without needing to define a schema beforehand. However, this approach can be slower and consume more resources compared to the schema-based approach because JSON needs to be parsed each time data is received or sent.

