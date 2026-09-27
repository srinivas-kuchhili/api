# 05. API Automation

## 1. What is API automation?

API automation is the practice of testing backend services automatically by sending HTTP requests and validating responses without involving the UI.

This is important because APIs are where the actual business logic, validations, authentication, and data processing happen.

Example goals:
- validate login API
- test create/update/delete operations
- verify error handling
- confirm token-based security
- validate response schema and contract

---

## 2. Why automate APIs?

Benefits:
- faster than UI testing for backend logic
- more stable and deterministic
- easier to run in CI/CD
- helps catch regressions early
- reduces dependency on browser rendering

### Interview answer
> API automation is critical because it validates the core business functionality faster and more reliably than UI automation, especially for login, validation, and CRUD flows.

---

## 3. API testing vs UI testing

| Area | API Testing | UI Testing |
| ---- | ----------- | --------- |
| Focus | Business logic and backend contract | User interaction and appearance |
| Speed | Faster | Slower |
| Stability | More stable | More brittle |
| Debugging | Easier to isolate | Harder due to DOM complexity |
| Coverage | Business rules and integrations | End-to-end user flows |

---

## 4. Key parts of an API test

A good API test usually validates:

1. request method and endpoint
2. headers and authentication
3. payload correctness
4. status code
5. response body structure
6. response time / performance
7. error messages and validation rules

Example:

```js
const response = await request.post('/api/users', {
  data: {
    name: 'John',
    email: 'john@example.com'
  },
  headers: {
    Authorization: 'Bearer token123'
  }
});

expect(response.status()).toBe(201);
expect(await response.json()).toHaveProperty('id');
```

---

## 5. Best practices for API automation

### 1. Keep tests independent
Each test should not depend on another test state unless intentionally designed to do so.

### 2. Validate status codes
Always verify the correct HTTP response code.

### 3. Validate response payload
Check required fields, data type, and structure.

### 4. Use environment variables
Keep base URLs, tokens, and endpoints configurable.

### 5. Handle authentication properly
Test valid and invalid token scenarios.

### 6. Test negative scenarios
- invalid input
- unauthorized access
- missing fields
- duplicate data
- expired token

### 7. Use data-driven testing
Reuse same tests with multiple valid and invalid data sets.

### 8. Add schema validation
Check JSON response structure and required keys.

---

## 6. Common API test scenarios

### Login flow
- valid credentials → 200/201
- invalid password → 401/400
- missing token → 401

### CRUD operations
- create item → 201
- fetch item → 200
- update item → 200/204
- delete item → 200/204

### Validation flow
- missing required field → 400/422
- invalid email → 400/422
- duplicate entity → 409

### Authorization flow
- admin access → 200
- normal user access → 403

---

## 7. API test design patterns

### Smoke test
Small set of high-priority end-to-end API tests to verify critical functionality.

### Regression test
Large suite to ensure changes do not break existing API behavior.

### Contract test
Ensures producer and consumer agree on request/response structure.

### Integration test
Verifies interactions between multiple services or components.

---

## 8. Tools for API automation

Popular options:
- Postman + Newman
- RestAssured (Java)
- Karate
- Playwright request API
- Cypress API testing support
- Python requests
- Node.js supertest / axios

### Interview point
> For QA automation, Postman/Newman are common for team workflows, while JavaScript or Java-based frameworks are common when API tests are part of automated pipelines and code repositories.

---

## 9. Common automation architecture

A typical API automation framework includes:
- base URL configuration
- request builder/helper methods
- authentication manager
- environment data
- assertion library
- reporting and logs
- reusable test data

Typical folder structure:

```text
api-tests/
  src/
    requests/
    assertions/
    utils/
    data/
  test/
    login.spec.js
    users.spec.js
  reports/
```

---

## 10. Assertions in API tests

Typical checks:

```js
expect(response.status()).toBe(200);
expect(response.headers()['content-type']).toContain('application/json');
expect(body).toHaveProperty('success', true);
expect(body.data).toHaveLength(3);
```

Common things to assert:
- status code
- response time
- JSON structure
- field values
- validation message
- pagination metadata

---

## 11. Handling dynamic values

APIs often return dynamic values like:
- IDs
- timestamps
- tokens
- session IDs

In automation, store and reuse these using:
- environment variables
- test data files
- response extraction

Example:

```js
const body = await response.json();
const userId = body.id;
```

Then pass it in subsequent requests.

---

## 12. Error handling and retries

Real API automation should account for:
- 401 expired token
- 429 rate limit
- 500 transient server error
- network timeouts

Good automation includes:
- proper retry strategy when allowed
- clear logs
- useful error messages

---

## 13. CI/CD integration

API tests should run in pipelines with:
- build validation
- nightly regression suites
- deployment smoke checks
- environment-specific runs

Example CI use cases:
- run login and health checks after merge
- execute regression suite before deployment
- block deploy if API contract breaks

---

## 14. Interview questions

### Q: Why is API automation important?
> Because it validates business logic at the backend level and catches issues faster than UI automation.

### Q: What is the most important validation in an API test?
> The status code and response structure, along with correctness of the business result.

### Q: What should you check in a failed API test?
> Request details, response code, server message, body fields, headers, and authentication context.

### Q: Why do we use environment variables?
> To support testing across dev, QA, and production without hardcoding sensitive or environment-specific values.

---

## 15. Key takeaways

- API automation is the foundation of backend validation.
- It runs faster and is more stable than UI tests.
- It verifies business logic, security, validation, and integration behavior.
- Good API automation validates both success and failure scenarios.
- In real projects, API tests are usually part of CI/CD and regression suites.
