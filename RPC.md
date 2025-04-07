# RPC, JSON-RPC
JSON-RPC is a remote procedure call (RPC) protocol encoded in JSON (Javascript Object Notation). It allows for communication between a client and a server over a network. JSON-RPC enables a client to invoke methods on a server and receive responses, similar to traditional RPC but using JSON for data formatting.

AS a user, you interact with the blockchain for two purposes - 
 - To send a `transaction`.
 - To fetch some details from the blockchain (balances, etc).

In both of these, the way to interact with the blockchain is using JSON-RPC.
JSON-RPC Spec - (click me!!!)[https://www.jsonrpc.org/specification]

``There are other ways to do RPC's like GRPC, TRPC``

## Understanding RPC
RPC is a client-server model where the client makes a request to exectue specific procedure or function on the server. The server processes the request, performs the requested operation, and sends the result back to the client. This process is transparent to the client, making it appear as if the procedure is being executed locally.

#### Why use RPC?
1. **Language and Platform independence**: RPC allows applications written in different programming languages and running on different platforms to communicate seamlessly. This promotes code reusability and interoperability across diverse systems.
2. **Abstraction of Communication Details**: RPC abstracts away the complexities of network communication, such as socket programming, serialization, and deserialization of data. Developers can focus on the application logic rather than low-level communication details.
3. **Distributed Computing**: RPC enables the distribution of computational tasks across multiple systems, allowing for better resource utilization, load balancing, and scalability.
4. **Code Modularity**: RPC promotes code modularity by separating the client and server components. This separation of converns makes the codebase more maintainable and easier to evolve.