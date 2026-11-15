
# API Data Models

## 1. Introduction

This document describes the main data structures used by the Smart Expense Tracker API.

The examples are illustrative and describe the documented core fields.

## 2. User

The User model represents a registered application user.

| Field | Data type | Description |
|---|---|---|
| id | Integer | Unique user identifier |
| name | String | User's display name |
| email | String | User's email address |
| password | String | Password supplied during registration |

**Security note:** The current implementation stores passwords as plain text. The password field must never be exposed in a production API response. The model description above reflects the existing implementation, not a recommended design.

## 3. Expense

The Expense model represents an expense record.

| Field | Data type | Description |
|---|---|---|
| id | Integer | Unique expense identifier |
| title | String | Name or description of the expense |
| amount | Double | Expense amount |
| category | String | Expense category |
| date | LocalDate | Date on which the expense occurred |
| user | User relationship | User associated with the expense |

## 4. Expense Request Example

```json
{
  "title": "Groceries",
  "amount": 850.50,
  "category": "Food",
  "date": "2026-11-10"
}
```

## 5. Data Validation Notes

The current API request models should be reviewed for field-level validation.

Do not assume that required fields, positive amounts, email formats, or valid category values are enforced unless the application code implements those validations.

## 6. Related Documentation

- [API Overview](overview.md)
- [Endpoint Inventory](endpoint-inventory.md)
- [Request and Response Examples](request-response-examples.md)
