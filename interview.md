# API Interview Questions and Answers

## 1. What is an API?

An API is a set of rules that allows software systems to communicate with each other. It defines how a client should send a request and how the server should return a response.

> An API is a communication contract between systems, enabling data exchange, business logic calls, and integration.

---

## 2. What are the main types of APIs?

Common types include:
- REST API
- SOAP API
- GraphQL API
- gRPC

> REST is the most widely used in web and mobile applications because it is simple, scalable, and naturally aligned with HTTP.

---

## 3. What is REST?

REST is an architectural style that uses resources, HTTP methods, and stateless communication. It is widely used for APIs in web applications.

Example:
- GET /users
- POST /users
- PUT /users/1
- DELETE /users/1

---

## 4. Difference between GET and POST

- GET is used to fetch data
- POST is used to create new data
- GET is safe and idempotent
- POST is not safe and not idempotent

> GET should be used only for retrieval, while POST creates or submits new records.

---

## 5. Difference between PUT and PATCH

- PUT replaces the entire resource
- PATCH updates only selected fields
- PUT is idempotent
- PATCH may not be idempotent in all cases

> Use PUT when updating the full object, and PATCH when modifying only part of it.

---

## 6. What are HTTP status codes?

HTTP status codes tell the client whether the request succeeded, failed, or needs redirecting.

Categories:
- 1xx: informational
- 2xx: success
- 3xx: redirection
- 4xx: client error
- 5xx: server error

> Status codes are critical because they immediately tell us whether the API worked or whether the client/server is at fault.

---

## 7. What is the difference between 401 and 403?

- 401 Unauthorized = missing/invalid credentials or token
- 403 Forbidden = valid authentication but not allowed to access the resource

> 401 is about authentication; 403 is about authorization.

---

## 8. What is 404 Not Found?

404 occurs when the requested resource is not available at the given path or URL.

> It usually indicates a wrong endpoint, missing resource, or incorrect API route.

---

## 9. What does 201 Created mean?

It means a new resource has been successfully created.

Example:
- POST /users returns 201 after creating a user

---

## 10. What does 204 No Content mean?

The request was successful, but there is no response body to return.

**Typical cases:**
- successful DELETE
- successful PATCH without payload

---

## 11. What is 429 Too Many Requests?

This indicates the client has sent too many requests in a short time and has been rate-limited by the server.

> 429 is important in automation because APIs often enforce throttling to protect resources.

---

## 12. What does 500 Internal Server Error mean?

This is a generic server-side error. It usually means an unexpected issue occurred on the backend.

> 500 means the server failed while processing the request, not that the client sent bad input.

---

## 13. What is the purpose of Postman?

Postman is used to create, inspect, and test HTTP requests and APIs manually and automatically.

It is useful for:
- validating endpoints
- testing authentication
- checking response payloads
- automating collections with scripts

---

## 14. What is Newman?

Newman is the command-line runner for Postman collections. It allows Postman test suites to be executed in CI/CD pipelines.

> Newman connects manual Postman testing with automated regression runs in build environments.

---

## 15. Why is API testing important before UI testing?

API testing verifies backend logic earlier and faster than UI testing. It catches issues in authentication, data validation, and business logic before the UI is even exercised.

> API testing reduces risk and improves reliability by validating the application at the contract layer first.

---

## 16. What is a good API automation test case?

A good API test case should validate:
- correct endpoint
- correct method
- headers and authorization
- request payload
- expected status code
- response body fields
- error scenarios

---

## 17. What is the difference between authentication and authorization?

- Authentication = who you are
- Authorization = what you are allowed to do

Example:
- login with username/password → authentication
- admin can delete user → authorization

---

## 18. How do you handle failed API tests?

Check:
- request URL and method
- headers and token validity
- request body payload
- server response code and message
- issue in backend logic or data validation

> A failed API test usually exposes either a client-side mistake or an application-side issue; the first step is to inspect the exact request and response details.

---

## 19. Common interview-ready summary

- API is a communication interface between systems.
- HTTP methods define action: GET, POST, PUT, PATCH, DELETE.
- Status codes explain the result: 2xx success, 4xx client issue, 5xx server issue.
- API testing validates business logic, security, and integration.
- Postman/Newman are common tools in real QA workflows.

---

## 20. Final interview answer

> API automation is important because it tests the backend logic directly, faster than UI automation, with more reliability and better regression coverage. It validates request structure, authentication, data validation, response codes, and error handling, which are essential for building stable and secure applications.
