# 04. API Testing Tools

## 1. Why tools matter

API testing tools help QA engineers and developers:
- send HTTP requests
- validate request and response data
- automate regression checks
- inspect headers, cookies, tokens, and payloads
- manage collections and environments

---

## 2. Postman

### What is it?
Postman is one of the most popular API testing and API design tools used by developers and QA teams.

### Features
- create requests manually
- collections and folders
- environment variables
- pre-request scripts
- tests scripts
- monitors and automation
- API mocking and documentation

### Best use
- exploratory testing
- debugging APIs
- building API test suites
- validating request/response contracts

### Example
```js
pm.test("Status code is 200", function () {
  pm.response.to.have.status(200);
});
```

### Interview point
> Postman is widely used because it makes API testing faster, collaborative, and easy to automate with collections and scripts.

---

## 3. Newman

### What is it?
Newman is the command-line runner for Postman collections.

### Features
- run Postman collections from CLI
- integrate with Jenkins, GitHub Actions, Azure DevOps
- JSON or HTML reporting
- suitable for CI/CD execution

### Example command
```bash
newman run collection.json -e environment.json --reporters cli,json
```

### Best use
- running Postman suites in CI pipelines
- regression automation
- scheduled tests in build pipelines

### Interview point
> Newman bridges the gap between manual Postman testing and automated pipeline execution.

---

## 4. Yaak

### What is it?
Yaak is a lightweight API client designed for quick API exploration and testing.

### Features
- simple interface
- fast request execution
- collection management
- environment variables and request reuse

### Best use
- quick testing
- local API debugging
- exploratory validation before automation

---

## 5. curl

### What is it?
curl is a command-line tool for transferring data with URLs.

### Example
```bash
curl -X GET "https://api.example.com/users" \
  -H "Authorization: Bearer token123" \
  -H "Accept: application/json"
```

### Best use
- quick checks from terminal
- scripts and CI tasks
- debugging HTTP requests and headers

### Interview point
> curl is the fundamental command-line tool behind many API checks and automation scripts.

---

## 6. Insomnia

### What is it?
Insomnia is a desktop API client for API development and testing.

### Features
- request building
- environment variables
- plugin ecosystem
- documentation and mock server support

### Best use
- quick testing
- local integration validation
- REST design and debugging

---

## 7. Bruno

### What is it?
Bruno is a modern API client focused on local-first testing and portable collections.

### Features
- simple request workspace
- environment support
- collections saved as files
- good for teams that want version-controlled API tests

### Best use
- lightweight API validation
- versioned request docs
- collaborative API testing

---

## 8. SoapUI

### What is it?
SoapUI is used for web service and API testing, especially for SOAP, REST, and service virtualization.

### Best use
- enterprise web service testing
- SOAP-based integrations
- complex service validation

### Interview point
> SoapUI is still relevant in enterprise testing, particularly for SOAP and heavy integration environments.

---

## 9. JMeter

### What is it?
Apache JMeter is mainly used for performance and load testing, but it also supports API-level request testing.

### Best use
- performance benchmarking
- API load/performance validation
- concurrency checks

---

## 10. Other API testing options

- RestAssured: Java-based API testing library
- Karate: BDD-style API automation
- HTTPie: friendly command-line API client
- Paw: Mac API client
- Hoppscotch: browser-based API client
- Katalon Studio: broader test automation platform with API support

---

## 11. Tool selection guidance

Choose the tool based on need:

- Postman = manual + semi-automation
- Newman = CI/CD execution of Postman collections
- curl = quick terminal checks
- SoapUI = SOAP and enterprise service testing
- JMeter = performance testing
- RestAssured/Karate = code-based API automation for test frameworks

---

## 12. Interview perspective

### Q: Which tool is most commonly used for API testing?
> Postman is one of the most widely used API testing tools for manual validation and collection-based automation.

### Q: Why use Newman?
> Newman lets teams run Postman collections in CI/CD pipelines, enabling automated regression tests.

### Q: What is the benefit of using command-line tools like curl?
> They are lightweight, scriptable, and useful for debugging HTTP requests in shell or CI environments.

### Q: Which tools are useful for code-based API automation?
> RestAssured, Karate, and custom JavaScript/Python automation frameworks are commonly used when API tests are integrated with release pipelines.

---

## 13. Key takeaways

- Tools help simplify API request creation, validation, automation, and reporting.
- Postman and Newman are highly relevant for real-world QA automation.
- curl remains an essential command-line debugging tool.
- Choosing the right tool depends on whether the goal is manual testing, CI automation, or performance testing.
