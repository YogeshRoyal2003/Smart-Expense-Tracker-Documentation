
# API Testing Report

## 1. Purpose

This report records the results of local API testing performed for the Smart Expense Tracker backend using Postman.

## 2. Testing Environment

| Item | Configuration |
|---|---|
| API application | Smart Expense Tracker |
| Testing tool | Postman |
| Environment | Local development |
| Base URL | http://localhost:8080 |
| Data format | JSON |

## 3. Test Results

| Test case | Method | Endpoint | Result |
|---|---|---|---|
| User registration | POST | `/api/auth/register` | Passed |
| User login | POST | `/api/auth/login` | Passed |
| Retrieve expenses | GET | `/api/expenses` | Passed |
| Create expense | POST | `/api/expenses` | Passed |
| Retrieve by category | GET | `/api/expenses/category/{category}` | Pending |
| Retrieve monthly total | GET | `/api/expenses/monthly` | Pending |
| Update expense | PUT | `/api/expenses/{id}` | Pending |
| Delete expense | DELETE | `/api/expenses/{id}` | Pending |
| Delete all expenses | DELETE | `/api/expenses/all` | Pending |
| Retrieve by user ID | GET | `/api/expenses/user/{userId}` | Pending |
| Delete by user ID | DELETE | `/api/expenses/user/{userId}` | Pending |

## 4. Testing Observations

- Registration and login were verified using Postman.
- Expense retrieval returned the expected expense list.
- Expense creation returned the expected saved record.
- Remaining endpoint results must be recorded after individual verification.

## 5. Known Limitations

- Authentication is not consistently enforced across all expense endpoints.
- User ownership checks are missing from some operations.
- Password handling requires security improvements.
- The JWT signing secret should be externalised and managed securely.

## 6. Conclusion

The initial authentication and expense retrieval and creation operations were successfully tested in the local development environment.

Additional testing is required before considering the API documentation complete.
