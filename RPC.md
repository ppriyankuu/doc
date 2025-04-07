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

#### Drawbacks of HTTP for Backend Communication
While HTTP is a widely used protocol for communication between web applications and servers, it has some limitation when it comes to backend-to-backend communication:
1. **Lack of Type Safety**: HTTP requests and responses are typically transmitted as plain text or JSON, which lacks type safety. This can lead to runtime errors and make it harder to ensure data integrity.
2. **Overhead**: HTTP has additional overhead due to headers, parsing, and serialization/deserialization of data, which can impact performance, especially in high-throughput scenarios.
3. **Language Dependency**: HTTP libraries and their usage can vary across programming languages, making it harder to maintain consistent communication patterns across different backend systems.
4. **Limited Funcionality**: HTTP is primarily designed for request-response communication, which may not be suitable for more complex scenarios like bi-directional streaming or long-lived connections.

RPC addresses these limitations by providing a more efficient, language-agnostic, and type-safe communication mechanism for backend systems.

To illustrate RPC in actions, let's consider making a HTTP request:
```javascript
const https = require('https');

const options = {
  hostname: 'sum-server.100xdevs.com',
  port: 443,
  path: '/todos',
  method: 'GET'
};

const req = https.request(options, (res) => {
  console.log(`Status Code: ${res.statusCode}`);

  res.on('data', (chunk) => {
    console.log(`Body: ${chunk}`);
  });

  res.on('end', () => {
    console.log('No more data in response.');
  });
});

req.on('error', (e) => {
  console.error(`problem with request: ${e.message}`);
});

req.end();
```

This code sends an HTTP GET request to the specified URL and logs the response status code and body to the console. While this approach works, it requires handling low-level details like creating the request options, managing the response data, and handling error explicitly.

With RPC, the communication between the client and server would be abstracted away, allowing developers to focus on the application logic rather than underlying communication details.