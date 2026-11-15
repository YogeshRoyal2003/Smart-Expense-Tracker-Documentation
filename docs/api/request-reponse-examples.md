
# API Request and Response Examples

## 1. Introduction

This document provides example requests and responses for the Smart Expense Tracker REST API.

The examples are based on local API testing performed using Postman.


> **Example data notice:** All names, IDs, dates, amounts, and credentials in this document are fictional. The examples illustrate the API's documented structure and are not captured production responses.

## 2. Retrieve Expenses

**Method:** GET

**Endpoint:** `/api/expenses`

**Authorization:** Bearer JWT required.

### Example request

```http
GET /api/expenses HTTP/1.1
Host: localhost:8080
Authorization: Bearer <REDACTED_JWT_TOKEN>
Accept: application/json
```

### Example response

```json
[
  {
    "id": 101,
    "title": "Groceries",
    "amount": 850.50,
    "category": "Food",
    "date": "2026-11-10"
  },
  {
    "id": 102,
    "title": "Bus ticket",
    "amount": 45.00,
    "category": "Travel",
    "date": "2026-11-10"
  }
]
```

## 3. Create an Expense

**Method:** POST

**Endpoint:** `/api/expenses`

**Authorization:** Bearer JWT required.

### Example request

```http
POST /api/expenses HTTP/1.1
Host: localhost:8080
Authorization: Bearer <REDACTED_JWT_TOKEN>
Content-Type: application/json
Accept: application/json
```

### Request body

```json
{
  "title": "Groceries",
  "amount": 850.50,
  "category": "Food",
  "date": "2026-11-10"
}
```

### Example response

```json
{
  "id": 103,
  "title": "Groceries",
  "amount": 850.50,
  "category": "Food",
  "date": "2026-11-10"
}
```

*The response examples above show the core expense fields. The actual serialized Java entity may contain additional fields.*


## 2. User Registration

**Method:** POST

**Endpoint:** `/api/auth/register`

### Request

```json
{
  "name": "Alex",
  "email": "alex.documentation@example.com",
  "password": "REDACTED"
}
```

### Response

Insert the actual successful response captured from Postman.

Do not publish real passwords or sensitive user information.

## 3. User Login

**Method:** POST

**Endpoint:** `/api/auth/login`

### Request

```json
{
  "email": "alex.documentation@example.com",
  "password": "REDACTED"
}
```

### Successful response

The current controller returns a JWT token as a plain response value.

Use a redacted placeholder in published documentation:

```text
REDACTED_JWT_TOKEN
```

## 4. Retrieve Expenses

**Method:** GET

**Endpoint:** `/api/expenses`

### Request header

```http
Authorization: Bearer REDACTED_JWT_TOKEN
```

### Successful response

Insert the actual JSON response captured from Postman.

## 5. Create an Expense

**Method:** POST

**Endpoint:** `/api/expenses`

### Request header

```http
Authorization: Bearer REDACTED_JWT_TOKEN
Content-Type: application/json
```

### Request body

```json
{
  "title": "Groceries",
  "amount": 850.50,
  "category": "Food",
  "date": "2026-11-10"
}
```

### Successful response

Insert the actual saved expense response captured from Postman.

## 6. Error Responses

Document the actual error response body and HTTP status code for each tested failure scenario.

| Scenario | Expected behaviour identified in source |
|---|---|
| Duplicate registration email | HTTP 400 |
| Login with incorrect password | HTTP 401 |
| Login with unknown email | HTTP 404 |
| Invalid or expired JWT | Verify actual response |

## 7. Testing Notes

- All examples should use fictional test data.
- JWT tokens must be redacted.
- Passwords must never be published.
- Response examples must match the actual application output.
- Record the HTTP status code and content type for each tested response.
