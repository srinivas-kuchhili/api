# 02. HTTP Methods

## 1. Importance of HTTP methods

HTTP methods tell the server what action to perform on a resource. In API testing and automation, these methods are the core of RESTful design.

---

## 2. Common HTTP methods

| Method | Meaning | Typical Use | Safe | Idempotent |
| ------ | ------- | ------------ | ---- | ---------- |
| GET | Read data | Fetch user or product details | Yes | Yes |
| POST | Create new resource | Create user, order, or record | No | No |
| PUT | Replace entire resource | Full update of a record | No | Yes |
| PATCH | Partial update | Update one field | No | No |
| DELETE | Remove resource | Delete user/order | No | Yes |
| HEAD | Get headers only | Check metadata | Yes | Yes |
| OPTIONS | Discover allowed methods | CORS / preflight | Yes | Yes |

---

## 3. GET

Use case:
- fetch data from API
- read single item or list
- filter and pagination query

Example:

```http
GET /api/products/12
```

Characteristics:
- does not modify server state
- safe and idempotent
- usually returns 200 OK

---

## 4. POST

Use case:
- create new records
- submit form data
- register user

Example:

```http
POST /api/users
Content-Type: application/json

{
  "name": "Alice",
  "email": "alice@example.com"
}
```

Characteristics:
- creates new resource
- not safe
- not idempotent
- usually returns 201 Created

---

## 5. PUT

Use case:
- full replacement of an object

Example:

```http
PUT /api/users/5
Content-Type: application/json

{
  "id": 5,
  "name": "Alice Updated",
  "email": "alice.new@example.com"
}
```

Characteristics:
- replaces resource completely
- idempotent: repeating the same request should not change result further

---

## 6. PATCH

Use case:
- partial modification of data

Example:

```http
PATCH /api/users/5
Content-Type: application/json

{
  "email": "new@example.com"
}
```

Characteristics:
- updates only specific fields
- common for partial updates
- usually returns 200 OK or 204 No Content

---

## 7. DELETE

Use case:
- remove a resource

Example:

```http
DELETE /api/users/5
```

Characteristics:
- removes record or resource
- idempotent: repeated delete requests should not keep changing state
- often returns 200 OK or 204 No Content

---

## 8. HEAD

Use case:
- get response headers without body
- check if resource exists
- verify caching metadata

Example:

```http
HEAD /api/users/5
```

---

## 9. OPTIONS

Use case:
- check which methods are allowed on an endpoint
- useful in CORS and API discovery

Example:

```http
OPTIONS /api/users
```

Typical response includes headers like:
- Allow: GET, POST, PUT, DELETE
- Access-Control-Allow-Origin

---

## 10. Safe vs Idempotent

### Safe methods
Methods that do not modify server state.
- GET
- HEAD
- OPTIONS

### Idempotent methods
Methods that can be repeated without additional side effects.
- GET
- PUT
- DELETE
- HEAD
- OPTIONS

### Not idempotent
- POST
- PATCH

This distinction is important in interviews and API design.

---

## 11. Interview-focused comparison

### Q: What is the difference between PUT and PATCH?
> PUT replaces the whole resource, whereas PATCH updates only specific fields.

### Q: Why is GET safe?
> Because it only reads data and does not change server state.

### Q: Why is POST not idempotent?
> Sending the same POST request multiple times may create duplicate resources.

### Q: When should you use DELETE?
> When the goal is to remove a resource or disable an item permanently.

---

## 12. Real-world API design examples

- GET /orders → list all orders
- POST /orders → create an order
- GET /orders/10 → fetch one order
- PATCH /orders/10 → update shipping address
- DELETE /orders/10 → cancel order

---

## 13. Key takeaways

- HTTP methods define the action to be performed.
- GET reads, POST creates, PUT updates full entity, PATCH updates partial record.
- Understanding safe and idempotent methods is critical for API design and automated tests.
- Wrong method usage often leads to broken or inconsistent behavior.
