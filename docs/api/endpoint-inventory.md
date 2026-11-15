
# API Endpoint Inventory

## 1. Introduction

This document lists the REST API endpoints currently implemented in the Smart Expense Tracker backend.

The API is built using Java and Spring Boot. It provides endpoints for user registration, authentication, and expense management.

**Base URL (local development):**

`http://localhost:8080`

All endpoint paths listed below are relative to this base URL.

## 2. Authentication APIs

| Method | Endpoint | Description | Request body |
|---|---|---|---|
| POST | `/api/auth/register` | Registers a new user | User details |
| POST | `/api/auth/login` | Authenticates a user and returns a JWT | Login credentials |

### 2.1 Register a user

**Endpoint:** `POST /api/auth/register`

**Request body:**

```json
{
  "name": "Alex",
  "email": "alex@example.com",
  "password": "example-password"
}
```

**Behaviour:**
- Checks whether the email address already exists.
- Returns a bad-request response if the email is already registered.
- Otherwise, saves the user and returns the saved user object.

**Documentation and security note:** The current implementation accepts and stores the password as plain text. The returned user object may also contain the password. Do not use real credentials when testing this endpoint.

### 2.2 Login

**Endpoint:** `POST /api/auth/login`

**Request body:**

```json
{
  "email": "alex@example.com",
  "password": "example-password"
}
```

**Behaviour:**
- Looks up the user by email.
- Returns `404` if the user is not found.
- Returns `401` if the password does not match.
- Returns a JWT token if authentication succeeds.

The current implementation returns the token as a plain response value.

## 3. Expense APIs

| Method | Endpoint | Description | Authorization header in controller |
|---|---|---|---|
| GET | `/api/expenses` | Retrieves expenses for the authenticated user | Required |
| POST | `/api/expenses` | Creates an expense for the authenticated user | Required |
| DELETE | `/api/expenses/all` | Deletes all expenses for the authenticated user | Required |
| DELETE | `/api/expenses/{id}` | Deletes an expense by ID | Not checked |
| PUT | `/api/expenses/{id}` | Updates an expense by ID | Not checked |
| GET | `/api/expenses/category/{category}` | Retrieves expenses by category | Not checked |
| GET | `/api/expenses/monthly?year={year}&month={month}` | Retrieves the monthly expense total | Not checked |
| GET | `/api/expenses/user/{userId}` | Retrieves expenses for a user ID | Not checked |
| DELETE | `/api/expenses/user/{userId}` | Deletes expenses for a user ID | Not checked |

### 3.1 Retrieve expenses

**Endpoint:** `GET /api/expenses`

**Request header:**

`Authorization: Bearer <JWT_TOKEN>`

**Behaviour:**
- Extracts the email address from the JWT.
- Finds the corresponding user.
- Returns the expenses associated with that user.

### 3.2 Create an expense

**Endpoint:** `POST /api/expenses`

**Request header:**

`Authorization: Bearer <JWT_TOKEN>`

**Request body:**

```json
{
  "title": "Groceries",
  "amount": 850.50,
  "category": "Food",
  "date": "2026-11-10"
}
```

**Behaviour:**
- Extracts the user's email from the JWT.
- Finds the corresponding user.
- Associates the new expense with that user.
- Saves and returns the expense.

### 3.3 Delete all expenses

**Endpoint:** `DELETE /api/expenses/all`

**Request header:**

`Authorization: Bearer <JWT_TOKEN>`

**Behaviour:**
- Identifies the user from the JWT.
- Deletes all expenses associated with that user.

### 3.4 Delete an expense by ID

**Endpoint:** `DELETE /api/expenses/{id}`

**Path parameter:**
- `id`: ID of the expense to delete.

**Behaviour:** Deletes the expense with the supplied ID.

### 3.5 Update an expense

**Endpoint:** `PUT /api/expenses/{id}`

**Path parameter:**
- `id`: ID of the expense to update.

**Request body:** Expense fields.

**Behaviour:** Passes the supplied ID and expense object to the expense service for updating.

### 3.6 Retrieve expenses by category

**Endpoint:** `GET /api/expenses/category/{category}`

**Path parameter:**
- `category`: Expense category to retrieve.

**Behaviour:** Returns expenses matching the supplied category.

### 3.7 Retrieve monthly expense total

**Endpoint:** `GET /api/expenses/monthly`

**Query parameters:**
- `year`: Year to retrieve.
- `month`: Month number to retrieve.

**Example:**

`GET /api/expenses/monthly?year=2026&month=11`

**Behaviour:** Returns the calculated expense total for the supplied year and month.

### 3.8 Retrieve expenses by user ID

**Endpoint:** `GET /api/expenses/user/{userId}`

**Path parameter:**
- `userId`: ID of the user.

**Behaviour:** Returns expenses associated with the supplied user ID.

### 3.9 Delete expenses by user ID

**Endpoint:** `DELETE /api/expenses/user/{userId}`

**Path parameter:**
- `userId`: ID of the user.

**Behaviour:** Deletes expenses associated with the supplied user ID.

## 4. Important implementation limitations

The following observations were identified during source-code review:

1. Passwords are currently stored and compared as plain text.
2. The registration endpoint returns the saved user entity, which includes the password field.
3. Several expense endpoints do not perform authentication or verify that the requested expense belongs to the requesting user.
4. The JWT secret is hard-coded in the current implementation.
5. Some backend endpoints are not exposed through the current frontend dashboard.

These limitations must be addressed before the API is considered suitable for production use.


## API Testing Status

The following endpoints have been tested locally using Postman.

| Endpoint | Method | Test result |
|---|---|---|
| `/api/auth/register` | POST | Passed |
| `/api/auth/login` | POST | Passed |
| `/api/expenses` | GET | Passed |
| `/api/expenses` | POST | Passed |
| `/api/expenses/category/{category}` | GET | Pending |
| `/api/expenses/monthly` | GET | Pending |
| `/api/expenses/{id}` | PUT | Pending |
| `/api/expenses/{id}` | DELETE | Pending |
| `/api/expenses/all` | DELETE | Pending |
| `/api/expenses/user/{userId}` | GET | Pending |
| `/api/expenses/user/{userId}` | DELETE | Pending |

*Testing status reflects local verification and should be updated as additional endpoints are tested.*


## 5. Related documentation

- [API Overview](overview.md)
- [Product Overview](../product-overview.md)
- [Dashboard User Guide](../user-guide/dashboard.md)
- [Installation Guide](../getting-started/installation.md)
