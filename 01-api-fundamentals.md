# 01. API Fundamentals

## 1. What is an API?

An API (Application Programming Interface) is a set of rules and contracts that allows one software system to communicate with another.

In simple terms, an API defines:
- how a client requests data
- how the server responds
- what methods and formats are allowed
- how authentication and errors are handled

Example:
- Browser calls a backend API to get product details
- Mobile app calls an API to log in a user
- Payment gateway sends success/failure response

### Real-world analogy
Think of an API as a waiter in a restaurant:
- You give an order (request)
- The waiter carries it to the kitchen (server)
- The kitchen prepares the order and sends back the result (response)

---

## 2. What does an API request look like?

A typical HTTP request contains:

- Method: GET, POST, PUT, PATCH, DELETE, etc.
- URL: endpoint or resource path
- Headers: content type, authorization, cookies, custom metadata
- Body: JSON/XML payload for POST/PUT/PATCH
- Query parameters: filters, pagination, sorting

Example request:

```http
GET /api/users/101 HTTP/1.1
Host: example.com
Authorization: Bearer token123
Accept: application/json
```

Example response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": 101,
  "name": "John",
  "email": "john@example.com"
}
```

---

## 3. Why are APIs important?

APIs enable:
- frontend and backend communication
- integration between systems
- microservices communication
- third-party service integration
- automation and testing of business flows

Without APIs, applications would be tightly coupled and hard to scale.

---

## 4. Types of APIs

### REST API
Most common type in web applications.

Features:
- uses HTTP methods
- resources are identified by URLs
- usually JSON payloads
- stateless communication

Example:
- GET /users
- POST /users
- GET /users/1

### SOAP API
A protocol-based API with XML structure.

Uses:
- enterprise systems
- banking and legacy integrations
- strict contracts

### GraphQL API
Allows clients to request only specific fields.

Example:
- fetch only name and email instead of full user record

### gRPC
High-performance API framework for service-to-service communication.

Used in:
- microservices
- internal system calls
- high-throughput applications

---

## 5. REST vs SOAP vs GraphQL

| Type | Style | Data Format | Common Use |
| ---- | ----- | ----------- | ----------- |
| REST | Resource-based | JSON/XML | Web and mobile apps |
| SOAP | Protocol-based | XML | Enterprise, legacy systems |
| GraphQL | Query-based | JSON | Flexible front-end data fetching |
| gRPC | RPC | Protobuf | Internal microservices |

---

## 6. API Architecture basics

An API works as follows:

1. Client sends a request to server
2. Server validates the request
3. Server processes logic/business rules
4. Server returns response and status code
5. Client parses and acts on it

Key concepts:
- endpoint: URL that identifies the resource
- resource: user, product, order, etc.
- payload: request/response body
- authentication: token, API key, OAuth
- authorization: permissions for allowed actions

---

## 7. Common API examples

### User login API
```http
POST /api/login
Content-Type: application/json

{
  "username": "admin",
  "password": "pass123"
}
```

### Get user details
```http
GET /api/users/5
```

### Create order
```http
POST /api/orders
Content-Type: application/json

{
  "productId": 88,
  "quantity": 2
}
```

---

## 8. Interview points

### Q: What is an API?
> An API is a contract or interface that allows different software systems to communicate with each other in a controlled and standardized way.

### Q: Why is API testing important?
> API testing verifies backend business logic, data validation, authentication, response structure, and error handling before UI testing.

### Q: Why is REST widely used?
> REST is simple, scalable, stateless, and works naturally with HTTP methods and JSON payloads.

### Q: What is the difference between API and Web Service?
> All web services are APIs, but not all APIs are web services. Web services usually use protocols like HTTP/SOAP, while APIs can be broader in design and implementation.

---

## 9. Key takeaways

- API is the interface for system-to-system communication.
- REST is the most widely used design style in modern apps.
- The request includes method, URL, headers, and payload.
- The response includes status code, headers, and body.
- API testing is critical because it validates core business logic before UI automation.

---

## 10. Quick revision summary

- API = communication contract between systems
- REST = resource-oriented API style
- Request = method + URL + headers + body
- Response = status + headers + body
- API testing = validation of functionality, security, and data integrity
