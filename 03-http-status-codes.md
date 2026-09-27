# 03. HTTP Status Codes (1XX to 5XX)

## 1. Why status codes matter

HTTP status codes tell the client whether the request succeeded, failed, or requires additional action. In automation, status codes are one of the first things to validate after every API call.

---

## 2. Status code categories

| Category | Range | Meaning |
| -------- | ----- | ------- |
| Informational | 1xx | Request received, continuing |
| Success | 2xx | Request succeeded |
| Redirection | 3xx | Further action needed |
| Client Error | 4xx | Client sent invalid or unauthorized request |
| Server Error | 5xx | Server failed to process request |

---

## 3. 1XX — Informational

These mean the request was received and is being processed.

| Code | Meaning | Typical Use |
| ---- | ------- | ----------- |
| 100 Continue | Server has received initial headers | Client sends large request body |
| 101 Switching Protocols | Server switches protocol | WebSocket upgrade |
| 102 Processing | Request is being processed | Server-side long-running task |
| 103 Early Hints | Preliminary response before final answer | Resource hints |

### Interview point
> 1xx responses indicate that the server is still working on the request and not yet done.

---

## 4. 2XX — Success

These mean the request was successful.

| Code | Meaning | Typical Use |
| ---- | ------- | ----------- |
| 200 OK | Standard success | GET success |
| 201 Created | Resource created | POST success |
| 202 Accepted | Request accepted for processing | Async jobs |
| 203 Non-Authoritative Information | Response from intermediary | Proxies |
| 204 No Content | Success without body | DELETE or PATCH |
| 205 Reset Content | Ask client to reset view | Form reset |
| 206 Partial Content | Partial data returned | Range requests |
| 207 Multi-Status | Multiple statuses | WebDAV |
| 208 Already Reported | Resource already reported | WebDAV |
| 226 IM Used | Server used a delta encoding | Advanced content negotiation |

### Common ones to remember
- 200 → success
- 201 → created
- 204 → no content

---

## 5. 3XX — Redirection

These mean the client must take another step.

| Code | Meaning | Typical Use |
| ---- | ------- | ----------- |
| 300 Multiple Choices | Multiple resources available | Content negotiation |
| 301 Moved Permanently | Resource permanently moved | Old URL redirect |
| 302 Found | Temporary redirect | Common redirect |
| 303 See Other | Redirect to a different resource | POST to GET follow-up |
| 304 Not Modified | Cached resource still valid | Browser caching |
| 307 Temporary Redirect | Temporary redirect without changing method | Retain HTTP method |
| 308 Permanent Redirect | Permanent redirect without changing method | Stable redirect |

### Interview point
> Redirection codes tell the client to fetch a different resource or reissue the request to a new URL.

---

## 6. 4XX — Client Errors

These indicate the request from the client is invalid or not allowed.

| Code | Meaning | Typical Use |
| ---- | ------- | ----------- |
| 400 Bad Request | Invalid request syntax or payload | Malformed JSON |
| 401 Unauthorized | Authentication required | Missing or invalid token |
| 402 Payment Required | Reserved for future use | Rare in practice |
| 403 Forbidden | Authenticated but not allowed | Missing permission |
| 404 Not Found | Resource does not exist | Wrong URL |
| 405 Method Not Allowed | HTTP method not supported | GET used on POST endpoint |
| 406 Not Acceptable | Server cannot produce requested format | Wrong Accept header |
| 407 Proxy Authentication Required | Proxy auth needed | Corporate proxy |
| 408 Request Timeout | Client took too long | Slow request |
| 409 Conflict | Resource conflict | Duplicate data |
| 410 Gone | Resource removed permanently | Deprecated endpoint |
| 411 Length Required | Missing Content-Length | Request without body length |
| 412 Precondition Failed | Condition not met | If-Match failure |
| 413 Payload Too Large | Request body too large | Oversized upload |
| 414 URI Too Long | URL too long | Long query string |
| 415 Unsupported Media Type | Wrong content type | Wrong payload format |
| 416 Range Not Satisfiable | Invalid range header | Partial content issue |
| 417 Expectation Failed | Server cannot meet Expect header | Rare |
| 418 I’m a teapot | April Fool’s joke | Legacy humorous status |
| 421 Misdirected Request | Request directed to wrong server | Proxy misuse |
| 422 Unprocessable Entity | Valid syntax but semantic error | Validation failure |
| 423 Locked | Resource locked | Concurrent access |
| 424 Failed Dependency | Dependency failed | Multi-step request |
| 425 Too Early | Server refuses early processing | Retry / race condition |
| 426 Upgrade Required | Must use a different protocol | Protocol negotiation |
| 428 Precondition Required | Request requires condition header | API locking / optimistic concurrency |
| 429 Too Many Requests | Rate limit exceeded | API throttle |
| 431 Request Header Fields Too Large | Headers too large | Excessive headers |
| 451 Unavailable For Legal Reasons | Blocked for legal reasons | Content restrictions |

### Most common client errors
- 400: bad request
- 401: unauthorized
- 403: forbidden
- 404: not found
- 405: method not allowed
- 409: conflict
- 422: validation issue
- 429: too many requests

---

## 7. 5XX — Server Errors

These indicate that the server failed to complete the request.

| Code | Meaning | Typical Use |
| ---- | ------- | ----------- |
| 500 Internal Server Error | Generic server failure | Unexpected bug |
| 501 Not Implemented | Server does not support function | Missing feature |
| 502 Bad Gateway | Invalid response from upstream | Reverse proxy issue |
| 503 Service Unavailable | Server unavailable | Maintenance or overload |
| 504 Gateway Timeout | Upstream timed out | Slow downstream system |
| 505 HTTP Version Not Supported | Unsupported HTTP version | Old client |
| 506 Variant Also Negotiates | Content negotiation issue | Rare |
| 507 Insufficient Storage | Server has no storage | WebDAV issue |
| 508 Loop Detected | Infinite loop in processing | Server recursion |
| 510 Not Extended | Server requires extension | Protocol extension required |
| 511 Network Authentication Required | Client must authenticate to network | Captive portal |

### Common server errors
- 500: generic server failure
- 502: bad gateway
- 503: service unavailable
- 504: gateway timeout

---

## 8. Status code selection in automation

When validating API responses, automation typically checks:
- expected status code matches actual status code
- message body is correct
- response time is acceptable
- headers are appropriate
- error payload is informative

Example assertion:

```js
expect(response.status).toBe(200);
expect(response.body).toHaveProperty('id');
```

---

## 9. Interview Q&A

### Q: What is the most important status code for successful API response?
> 200 OK for general success, 201 Created for resource creation, and 204 No Content for successful deletion or no-payload cases.

### Q: What is the difference between 401 and 403?
> 401 means the request is unauthenticated or lacks valid credentials. 403 means the user is authenticated but not allowed to access the resource.

### Q: Why do we care about 429?
> 429 indicates rate limiting. It is important for API health, resilience, and retry strategy.

### Q: When do you expect a 500 error?
> A 500 usually means a server-side bug or an unhandled exception.

---

## 10. Quick revision cheat sheet

- 1xx = processing
- 2xx = success
- 3xx = redirect
- 4xx = client problem
- 5xx = server problem

Highest-value codes to know:
- 200, 201, 204
- 301, 302, 307, 308
- 400, 401, 403, 404, 405, 409, 422, 429
- 500, 502, 503, 504

---

## 11. Key takeaways

HTTP status codes are the language of API communication. For QA and automation engineers, understanding them is essential because they indicate whether the backend is healthy, whether the request is valid, and whether the client should retry or revise the request.
