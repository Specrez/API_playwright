# Playwright API Testing

A REST API automation project built using **Playwright with JavaScript**. The project demonstrates automated testing of API endpoints using Playwright's built-in API request capabilities.

The test suite validates the main HTTP methods — **GET, POST, PUT, and DELETE** — against the ReqRes API and verifies HTTP response status codes and response data.

---

## 🛠️ Tech Stack

* **JavaScript**
* **Playwright**
* **Node.js**
* **NPM**
* **REST API**
* **ReqRes API**

---

## 📌 Project Overview

This project focuses on API-level automation rather than UI testing. Playwright's `request` fixture is used to send HTTP requests directly to the API endpoints.

The automation validates:

* API response status codes
* Response body content
* Successful resource retrieval
* Resource creation
* Resource update
* Resource deletion

The project contains automated tests for the following HTTP methods:

```text
GET
POST
PUT
DELETE
```

---

## 🧪 API Test Coverage

### 1. GET Request

The GET test sends a request to:

```text
GET /api/users/2
```

The test verifies:

* HTTP status code is `200`
* Response contains the expected user information
* Response body contains `"janet"`

The response is also converted to JSON and logged to the console for inspection.

---

### 2. POST Request

The POST test sends a request to:

```text
POST /api/users
```

with the following request body:

```json
{
  "name": "oshadha",
  "job": "engineer"
}
```

The test verifies:

* HTTP status code is `201`
* Response contains the submitted user name
* Response body contains `"oshadha"`

The returned JSON response is also logged to the console.

---

### 3. PUT Request

The PUT test sends a request to:

```text
PUT /api/users/2
```

with:

```json
{
  "name": "oshadha",
  "job": "engineer"
}
```

The test verifies:

* HTTP status code is `200`
* Updated user information is returned
* Response contains `"oshadha"`

The response JSON is logged for verification.

---

### 4. DELETE Request

The DELETE test sends a request to:

```text
DELETE /api/users/2
```

The test verifies that the API returns:

```text
204 No Content
```

This confirms that the delete request was processed successfully.

---

## 🔍 How the Automation Works

The tests use Playwright's built-in `request` fixture:

```javascript
test("API GET Request", async ({ request }) => {
```

The `request` object allows HTTP requests to be sent directly to the API without opening a browser.

For example:

```javascript
const response = await request.get(
  "https://reqres.in/api/users/2"
);
```

The response status is then validated using Playwright's `expect` assertion:

```javascript
expect(response.status()).toBe(200);
```

The response body can also be retrieved and validated:

```javascript
const text = await response.text();

expect(text).toContain("janet");
```

For POST and PUT requests, request data is provided using:

```javascript
data: {
  name: "oshadha",
  job: "engineer"
}
```

The returned response can then be converted into JSON:

```javascript
console.log(await response.json());
```

---

## 📊 Validation Performed

| HTTP Method | Endpoint       | Expected Status | Main Validation     |
| ----------- | -------------- | --------------: | ------------------- |
| GET         | `/api/users/2` |             200 | User data           |
| POST        | `/api/users`   |             201 | Created user data   |
| PUT         | `/api/users/2` |             200 | Updated user data   |
| DELETE      | `/api/users/2` |             204 | Successful deletion |

---

## ▶️ Running the Tests

Install project dependencies:

```bash
npm install
```

Install Playwright:

```bash
npm install -D @playwright/test
```

Run all API tests:

```bash
npx playwright test
```

Run the tests with a specific project:

```bash
npx playwright test --project chromium
```

Run in headed mode if required:

```bash
npx playwright test --project chromium --headed
```

Open the HTML test report:

```bash
npx playwright show-report
```

If port `9323` is already in use:

```bash
npx playwright show-report --port 9324
```

---

## 🎯 Skills Demonstrated

This project demonstrates practical experience with:

* REST API testing
* API automation
* Playwright API testing
* HTTP methods
* GET, POST, PUT, and DELETE requests
* Request payloads
* HTTP status-code validation
* Response-body validation
* JSON response handling
* Assertions
* Automated test execution
* HTML test reporting

---

## 📈 Test Result

The project contains **4 automated API test cases**, covering the four main HTTP methods:

```text
GET     → 200 OK
POST    → 201 Created
PUT     → 200 OK
DELETE  → 204 No Content
```

The tests validate both **HTTP response status codes and response content**, providing basic end-to-end API validation.
