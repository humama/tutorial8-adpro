# tutorial-8-advprog

## Reflection
1. In unary RPC, the client sends a single request to the server and receives a single response from the server at a time. This data transmission mechanism is most suitable for clients who only fetch certain data once in a while from the same endpoint. One use case for unary RPC is fetching static web page resources like CSS and JavaScript files.
<br><br>
In server-streaming RPC, the server uses a stream to continuously send data to the client. This mechanism is most suitable for clients who need to fetch data of large size or access to real-time data. One use case of server-streaming RPC is the media playback service that online streaming platforms provide.

2. Regarding authentication, we could use token-based authentication like JSON Web Tokens or mutual TLS authentication (mTLS) to verify the identity of the client that sends requests to a server. Regarding authorization, we could use OAuth2 to determine the client's access rights. Regarding data encryption, we could use TLS/SSL to encrypt the communication channel used for data transfer, securing it from malicious attacks like man-in-the-middle attacks

3. There are some potential challenges in implementing bidirectional streaming, like ensuring the order of the received messages are the same as the sent messages, handling concurrency problems like race conditions, and ensuring that the bidirectional stream is secure.

4. Advantages include asynchronous streaming where consuming the stream doesn't block other tasks from executing, backpressure handling in case the publisher emits more data than the consumer could handle, and seamless integration with other libraries such as tonic.
<br><br>
Disadvantages include increased complexity of the codebase, steep learning curve for some developers in understanding the async/await concurrency model, and complex error handling in case the stream produces an error.

5. Adhering to clean code and SOLID principles is a good way to increase code modularity, Rust code included. Splitting the code logic into separate modules, especially when the current code size is large is preferred.

6. The payment service could use a repository to handle the data access of the payment data and possibly a controller/view layer for handling network requests so that the payment service could just handle the business logic, adhering to Single Responsibility Principle.

7. gRPC, implementing HTTP/2, is obviously more efficient than HTTP/1.1. It is also language-agnostic, enabling support for various projects written in different programming language. It also provides streaming service in addition to single request model.

8. HTTP/2 allows multiplexing, where multiple requests and responses is included in a single TCP connection. Other than that, HTTP/2 uses header compression for small requests and responses to reduce overhead.<br>
Disadvantages include complexity of the HTTP/1.1, making it more difficult to implement and debug. Another disadvantage include the inavailable support of HTTP/2 in older browsers and environments.

9. Bidirectional communication in gRPC allows the client and the server to create a single connection that listens to a certain endpoint. This enables the server and the client to send data to each other, since both of them are listening to the same endpoint. Request/response model of REST API, on the other hand, uses 2 connections in total, the first for sending request from the client to the server, the second for sending response from the server to the client. Each connections are destroyed immediately after use, in constrast to bidirectional streaming.

10. Implications include an even more complex communication between clients and servers, since schema setup is mandatory for using gRPC. gRPC, using HTTP/2, could potentially be unsupported in certain browsers and environments, especially the old ones. However, the schema approach help to catch errors early in development process, especially when the structure of the data don't match with the schema.