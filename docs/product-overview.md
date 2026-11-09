
# Product Overview

## Introduction

Smart Expense Tracker is a web application that helps users record and review their personal expenses. Users can add expense details, view their spending information, search their expense records and export expense data for further analysis.

This documentation describes the application's current functionality, user workflows, technical architecture and known limitations.

## Intended Users

The application is intended for individuals who want to:

- Record their day-to-day expenses.
- Organize expenses using categories.
- Review their spending history.
- Understand spending distribution across categories.
- Export expense records for offline analysis.

## Key Features

### User Registration and Login

Users can register an account and log in using their email address and password.

### Expense Management

Users can add expenses by providing:

- Expense title
- Amount
- Category
- Date

The dashboard displays the available expense records and provides options to delete an individual expense or clear the expense list.

### Expense Search

Users can search their expense records using the expense title.

### Spending Summary

The dashboard displays the total spending calculated from the available expense records.

### Category-wise Visualization

A pie chart displays the distribution of expenses across categories.

### Excel Export

Users can export their expense records to an Excel file for offline review.

## Application Architecture

The application consists of two primary components.

### Frontend

The frontend is built using React. It provides the user interface for registration, login and expense management.

### Backend

The backend is built using Java and Spring Boot. It exposes REST API endpoints and uses Spring Data JPA for database operations.

### Database

The application is configured to use PostgreSQL for persistent storage.

## Technology Stack

| Component | Technology |
|---|---|
| Frontend | React |
| Backend | Java, Spring Boot |
| Data access | Spring Data JPA, Hibernate |
| Database | PostgreSQL |
| Authentication | JSON Web Tokens (JWT) |
| API communication | REST, Axios |
| Charts | Chart.js |
| Export | Excel file export |

## Current Scope and Limitations

The following points are important when interpreting the current implementation:

- Expense editing is not currently available through the dashboard interface.
- Some backend endpoints are not exposed through the current dashboard workflows.
- Authentication and authorization controls require further security review.
- The application should not be considered production-ready until the identified security issues are addressed.

## Related Documentation

- [Getting Started](getting-started/installation.md)
- [Dashboard User Guide](user-guide/dashboard.md)
- [API Overview](api/overview.md)
- [Troubleshooting](troubleshooting/common-issues.md)
