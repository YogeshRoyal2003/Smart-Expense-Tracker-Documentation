
# Installation Guide

## Introduction

This guide explains how to set up and run Smart Expense Tracker in a local development environment.

The application consists of a React frontend, a Java Spring Boot backend and a PostgreSQL database.

Follow the instructions in sequence to prepare the development environment, configure the application and verify the installation.

## Prerequisites

Install the following software before proceeding.

| Software | Requirement | Purpose |
|---|---|---|
| Java Development Kit | JDK 21 | Runs the Spring Boot backend |
| Apache Maven | Version compatible with the project | Builds and runs the backend |
| Node.js | Version compatible with the project dependencies | Runs the React frontend |
| npm | Installed with Node.js | Installs frontend dependencies |
| PostgreSQL | Supported PostgreSQL installation | Stores application data |
| Git | Current stable version | Clones the project repository |
| Visual Studio Code or IntelliJ IDEA | Optional | Source code editing |

**Note:** Confirm the exact Maven, Node.js and PostgreSQL versions used during your successful local setup before publishing this guide as a verified compatibility list.

## Step 1: Clone the Repository

Clone the Smart Expense Tracker repository to your local machine.

Open a terminal and execute:

```bash
git clone https://github.com/YogeshRoyal2003/Smart-Expense-Tracker.git
```

Navigate to the cloned project directory:

```bash
cd Smart-Expense-Tracker
```

The project contains separate directories for the backend and frontend.

```text
Smart-Expense-Tracker/
├── Backend/
├── frontend/
└── README.md
```

## Step 2: Configure the PostgreSQL Database

Ensure that PostgreSQL is installed and running.

Create a database for the application using your PostgreSQL client.

For example:

```sql
CREATE DATABASE smart_expense_tracker;
```

Record the database connection details. These will be used when configuring the backend.

The database URL generally follows this format:

```text
jdbc:postgresql://localhost:5432/smart_expense_tracker
```

Replace the database name, host and port if your local configuration is different.

## Step 3: Configure the Backend

Navigate to the backend directory:

```bash
cd Backend
```

The backend uses environment variables for database configuration.

Configure the following variables in your local environment:

| Variable | Description |
|---|---|
| DATABASE_URL | PostgreSQL JDBC connection URL |
| DATABASE_USERNAME | PostgreSQL database username |
| DATABASE_PASSWORD | PostgreSQL database password |
| PORT | Backend server port; defaults to 8080 |

Example PowerShell configuration:

```powershell
$env:DATABASE_URL="jdbc:postgresql://localhost:5432/smart_expense_tracker"
$env:DATABASE_USERNAME="your_database_username"
$env:DATABASE_PASSWORD="your_database_password"
$env:PORT="8080"
```

Replace the example username and password with your local database credentials.

Do not commit passwords, JWT secrets or other sensitive configuration values to Git.

## Step 4: Build and Run the Backend

From the Backend directory, execute:

```bash
mvn clean install
```

After the build completes, start the Spring Boot application:

```bash
mvn spring-boot:run
```

The backend is configured to use port 8080 by default, unless another port is supplied through the PORT environment variable.

Check the terminal output for the Spring Boot startup messages.

## Step 5: Configure the Frontend

Open a separate terminal.

Navigate to the frontend directory:

```bash
cd frontend
```

Install the required dependencies:

```bash
npm install
```

Inspect the frontend API configuration in:

```text
src/services/api.js
```

Ensure that the frontend is configured to communicate with your locally running backend when performing a local development setup.

The backend API uses the `/api` path. Confirm the correct local API base URL before starting the frontend.

## Step 6: Start the Frontend

Check the `scripts` section in `frontend/package.json` to identify the configured development command.

If the project defines the usual React start script, execute:

```bash
npm start
```

Otherwise, use the command specified by the project.

Wait for the frontend development server to start and open the local address displayed in the terminal.

## Step 7: Verify the Installation

Perform the following checks:

1. Confirm that the frontend application loads in the browser.
2. Open the registration page.
3. Register a test account using non-sensitive test data.
4. Log in with the registered account.
5. Add an expense with a title, amount, category and date.
6. Confirm that the expense appears in the dashboard.
7. Refresh the dashboard and check whether the expense remains available.
8. Verify that the total spending and category chart reflect the recorded expense.
9. Test the Excel export functionality.

If these operations work as expected, the local application setup has passed the basic functional verification.

## Troubleshooting

| Issue | Possible cause | Suggested action |
|---|---|---|
| Backend fails to start | Incorrect Java version | Verify that JDK 21 is configured |
| Database connection fails | Incorrect connection details | Verify the JDBC URL, username and password |
| Frontend dependencies fail to install | Dependency or Node.js compatibility issue | Check Node.js version and package configuration |
| Frontend cannot communicate with backend | Incorrect API base URL or CORS configuration | Verify the frontend API configuration and backend CORS settings |
| Login or registration fails | Backend or database error | Check the backend logs and database connection |

## Related Documentation

- [Product Overview](../product-overview.md)
- [Dashboard User Guide](../user-guide/dashboard.md)
- [API Overview](../api/overview.md)
- [Troubleshooting](../troubleshooting/common-issues.md)
