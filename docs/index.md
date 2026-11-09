
# Smart Expense Tracker

**A personal expense management application**

Smart Expense Tracker is a web-based application developed to help users record, organize and review their daily expenses. It provides an expense dashboard with category-wise spending visualization, expense search and Excel export functionality.

This documentation portal provides product information, user instructions, installation procedures, API references and troubleshooting guidance for the application.

---

## About the Project

Smart Expense Tracker consists of a React frontend, a Java Spring Boot backend and a PostgreSQL database.

The application communicates with the backend through REST APIs. JSON Web Tokens (JWT) are used in the authentication implementation.

The documentation describes the current implementation and identifies areas that require further validation or improvement.

## What You Can Do

| Feature | Description |
|---|---|
| User registration | Create a user account. |
| User login | Log in using registered credentials. |
| Add expenses | Record an expense with its title, amount, category and date. |
| Search expenses | Find expenses using their title. |
| Spending summary | View the total spending displayed on the dashboard. |
| Category visualization | Review expense distribution using a pie chart. |
| Excel export | Export expense records for offline analysis. |
| Delete expenses | Delete individual expenses or clear the expense list. |

## Documentation

Use the following sections to explore the application.

### Product Information

Understand the purpose, features and technical architecture of the application.

[Read the Product Overview](product-overview.md)

### Getting Started

Learn about the prerequisites, environment configuration and steps required to run the application locally.

[Installation Guide](getting-started/installation.md)

### User Guide

Learn how to navigate the dashboard, add expenses, search records and export expense data.

[Dashboard User Guide](user-guide/dashboard.md)

### API Documentation

Explore the backend REST API, available endpoints, request parameters and response structures.

[API Overview](api/overview.md)

### Troubleshooting

Find guidance for common installation, configuration and application issues.

[Troubleshooting Guide](troubleshooting/common-issues.md)

## Technology Stack

| Layer | Technology |
|---|---|
| Frontend | React |
| Backend | Java, Spring Boot |
| Database | PostgreSQL |
| ORM and Data Access | Hibernate, Spring Data JPA |
| Authentication | JWT |
| API Communication | REST, Axios |
| Visualization | Chart.js |
| Documentation | MkDocs, Material for MkDocs |

## Documentation Scope

This documentation is maintained alongside the application source code.

It covers:

- Product functionality and architecture.
- Local installation and configuration.
- User-facing workflows.
- Backend API reference.
- Troubleshooting and known limitations.
- Documentation maintenance and release updates.

## Documentation Status

This is a portfolio documentation project. The pages are being developed and reviewed against the available source code.

Application runtime behavior, database-backed workflows and security improvements require separate validation before the documentation can be considered production-ready.

---

**Project Repository:** [Smart Expense Tracker on GitHub](https://github.com/YogeshRoyal2003/Smart-Expense-Tracker)
