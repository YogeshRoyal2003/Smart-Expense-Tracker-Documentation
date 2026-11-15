
# API Error Reference

## 1. Introduction

This document describes error conditions identified in the Smart Expense Tracker API.

It provides developers with information about authentication failures, invalid requests, and troubleshooting considerations.

The HTTP status codes below are based on the current controller implementation where specified. Other responses must be verified through local API testing.

## 2. Authentication Errors

### 2.1 Duplicate email during registration

**Endpoint:** `POST /api/auth/register`

**HTTP status:** `400 Bad Request`

**Cause:**

The supplied email address is already registered.

**Recommended action:**

Use a different email address or sign in using the existing account.

### 2.2 Incorrect password

**Endpoint:** `POST /api/auth/login`

**HTTP status:** `401 Unauthorized`

**Cause:**

The supplied password does not match the stored password.

**Recommended action:**

Check the supplied credentials and try again.

### 2.3 User account not found

**Endpoint:** `POST /api/auth/login`

**HTTP status:** `404 Not Found`

**Cause:**

No account was found for the supplied email address.

**Recommended action:**

Check the email address or register a new account.

## 3. Expense API Troubleshooting

### 3.1 Missing authorization token

**Affected endpoint:** `GET /api/expenses`

**Cause:**

The request does not include the required Authorization header.

**Recommended action:**

Include a valid JWT in the request header:

`Authorization: Bearer <JWT_TOKEN>`

The exact HTTP response for a missing token must be verified against the running application.

### 3.2 Invalid or expired token

**Affected endpoint:** `GET /api/expenses`

**Cause:**

The supplied token may be malformed, invalid, or expired.

**Recommended action:**

Sign in again and use a newly generated token.

The actual HTTP status and response body must be verified through testing.

## 4. General Troubleshooting

| Symptom | Possible cause | Recommended investigation |
|---|---|---|
| Cannot connect to API | Backend is not running | Check the Spring Boot application |
| Connection refused | Incorrect port or server address | Verify the configured server port |
| Database connection failure | Database configuration issue | Check database URL and credentials |
| Unexpected response | Request format or backend behaviour | Inspect the Postman request and response |
| Expense list is empty | No matching expense records | Verify the test account and database records |

## 5. Security Considerations

The current implementation has known security limitations:

- Passwords are stored and compared as plain text.
- The JWT signing secret is hard-coded.
- Some expense endpoints do not enforce authentication.
- Some operations do not verify expense ownership.

Do not expose real credentials, JWT tokens, or personal financial data in error reports or documentation examples.

## 6. Related Documentation

- [API Overview](overview.md)
- [API Endpoint Inventory](endpoint-inventory.md)
- [Interactive API Reference](reference.md)
- [Request and Response Examples](request-response-examples.md)
- [API Testing Report](testing-report.md)
