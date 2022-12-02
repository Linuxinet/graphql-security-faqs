### Poorly configured CORS headers

Poorly configured CORS headers are a type of security vulnerability that can occur in GraphQL servers. CORS (Cross-Origin Resource Sharing) headers are used to control access to resources on a server from different origins. When these headers are not properly configured, it can potentially allow attackers to access resources on the server that they are not authorized to access.

Here is an example of a potential poorly configured CORS header in a GraphQL server:

```
Access-Control-Allow-Origin: *
```

In this example, the Access-Control-Allow-Origin header is set to *, which allows access to the server's resources from any origin. This can potentially allow attackers to access resources on the server that they are not authorized to access.

Here are some additional examples of potential poorly configured CORS headers in a GraphQL server:

1. An attacker sends a request to the server with a spoofed origin. If the server's CORS headers are not properly configured, it could potentially allow the attacker to access resources on the server that they are not authorized to access. For example:

```graphql
GET /graphql HTTP/1.1
Host: example.com
Origin: malicious-website.com

query {
  user(userId: "malicious-user-id") {
    name
    email
    password
  }
}
```

In this example, the attacker is sending a request to the server with a spoofed `Origin` header. If the server's CORS headers are not properly configured, it could potentially allow the attacker to access resources on the server that they are not authorized to access.

2. An attacker sends a request to the server with a null origin. If the server's CORS headers are not properly configured, it could potentially allow the attacker to access resources on the server that they are not authorized to access. For example:

```graphql
GET /graphql HTTP/1.1
Host: example.com
Origin: null

query {
  user(userId: "malicious-user-id") {
    name
    email
    password
  }
}
```
In this example, the attacker is sending a request to the server with a null origin. If the server's CORS headers are not properly configured, it could potentially allow the attacker to access resources on the server that they are not authorized to access.

Another example of a poorly configured CORS header in a GraphQL server might involve setting the Access-Control-Allow-Origin header to a specific origin, but not properly validating the origin of requests to the server. This could potentially allow attackers to access resources on the server by spoofing the origin of their requests.

To prevent these types of vulnerabilities, it is important to properly configure the server's CORS headers. This can include setting the Access-Control-Allow-Origin header to a specific origin, and properly validating the origin of requests to the server to ensure that they are coming from a trusted source. It is also important to regularly test and monitor the server's CORS headers to ensure that they are functioning correctly and preventing unauthorized access to resources on the server.
