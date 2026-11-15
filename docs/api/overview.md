
# API Documentation

## 1. Introduction

The Smart Expense Tracker REST API provides backend services for user authentication and expense management.

The API is developed using Java and Spring Boot. It communicates with the frontend application through HTTP requests and returns data in JSON format where applicable.

This documentation is intended for developers who want to understand, test, or integrate with the application's backend services.

## 2. API Base URL

For local development, the backend API runs on:

`http://localhost:8080`

API endpoints are accessed by appending their paths to this base URL.

For example:

`http://localhost:8080/api/auth/login`

The port may differ depending on the backend configuration.

## 3. Technology

The backend uses the following technologies:

| Technology | Purpose |
|---|---|
| Java | Backend programming language |
| Spring Boot | Application framework |
| Spring Data JPA | Database access |
| Hibernate | Object-relational mapping |
| PostgreSQL | Relational database |
| JSON | Data exchange format |
| JWT | Token generation and authentication |

## 4. API Categories

The available endpoints are grouped into two main categories.

### Authentication APIs

These endpoints support user registration and login.

- Register a new user.
- Authenticate an existing user.
- Generate a JSON Web Token (JWT) after successful login.

### Expense APIs

These endpoints support expense-related operations.

- Retrieve expenses.
- Create an expense.
- Update an expense.
- Delete an expense.
- Retrieve expenses by category.
- Calculate monthly expense totals.
- Retrieve or delete expenses associated with a user ID.

Refer to the [API Endpoint Inventory](endpoint-inventory.md) for the complete endpoint list.

## 5. Authentication

The application uses JSON Web Tokens (JWT) for certain expense API operations.

For endpoints that require authentication, include the token in the HTTP request header:

`Authorization: Bearer <JWT_TOKEN>`

To obtain a token, first send a login request using the authentication API.

**Important:** Authentication is not consistently enforced across all currently implemented expense endpoints. Some endpoints do not verify the requesting user's identity or ownership of the requested data. Review the endpoint inventory and the application's security limitations before using these APIs.

## 6. Request and Response Format

The API uses HTTP methods to perform operations:

| HTTP method | General purpose |
|---|---|
| GET | Retrieve information |
| POST | Submit information or create a resource |
| PUT | Update a resource |
| DELETE | Remove a resource |

JSON is used for request and response data where applicable.

The exact request fields and response formats depend on the individual endpoint.

## 7. Error Handling

The current implementation uses HTTP status codes for some authentication outcomes, including:

| Status code | Meaning in the current authentication implementation |
|---|---|
| 401 | Login password does not match |
| 404 | User account was not found |
| 400 | Registration email already exists |

Other endpoint responses should be verified through local API testing before publishing detailed response examples.

## 8. Security Considerations

The current application is a learning and portfolio project. It should not be treated as production-ready.

The source-code review identified the following limitations:

- Passwords are stored and compared as plain text.
- The JWT signing secret is hard-coded.
- The registration response may expose the password field.
- Several expense endpoints do not enforce authentication and ownership checks.

Use fictional test data and a local development environment when testing. Do not use real passwords, financial information, or production credentials.

## 9. API Reference

For endpoint-level details, see:

- [API Endpoint Inventory](endpoint-inventory.md)

## 10. Related Documentation

- [Product Overview](../product-overview.md)
- [Installation Guide](../getting-started/installation.md)
- [Dashboard User Guide](../user-guide/dashboard.md)
