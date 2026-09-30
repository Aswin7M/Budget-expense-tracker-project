# Expense Tracker

## Overview

Expense Tracker is a web-based personal finance management application built using PHP and MySQL.

The application allows users to set a monthly budget, record and manage expenses, categorize spending, monitor total expenditure, and generate expense reports.

It also provides visual spending analysis through a category-based pie chart and supports exporting expense information in CSV and PDF formats.

---

## Features

The application provides the following features:

* User login authentication
* Monthly budget configuration
* Expense entry and management
* Expense categorization
* Total spending calculation
* Monthly expense summary
* Budget progress tracking
* Budget exceeded alert
* Category-wise spending visualization
* Pie chart for expense breakdown
* CSV expense export
* PDF expense report generation
* Category-wise PDF report generation
* Expense deletion
* Dark mode
* Responsive expense table

---

## Problem Statement

Managing personal expenses manually can make it difficult to understand spending patterns and maintain a monthly budget.

This project provides a simple web-based solution for recording expenses and monitoring spending against a predefined monthly budget.

The system calculates total expenditure, groups expenses by category and month, and provides downloadable reports for easier financial tracking.

---

## Objectives

The main objectives of the project are:

1. Develop a simple personal expense management system.
2. Allow users to set and monitor a monthly budget.
3. Store expense information using a MySQL database.
4. Categorize expenses for better spending analysis.
5. Calculate total expenditure automatically.
6. Provide monthly spending summaries.
7. Display category-wise spending visually.
8. Generate downloadable expense reports.
9. Provide a simple authentication mechanism.
10. Provide a user-friendly interface for managing personal expenses.

---

## Application Workflow

The overall application workflow is:

```text
User
 |
 v
Login
 |
 v
Expense Tracker Dashboard
 |
 +----------------------+
 |                      |
 v                      v
Set Monthly Budget    Add Expense
 |                      |
 |                      v
 |                MySQL Database
 |                      |
 +----------+-----------+
            |
            v
     Expense Calculation
            |
      +-----+-----+
      |           |
      v           v
Monthly Summary  Category Analysis
      |           |
      |           v
      |       Pie Chart
      |
      v
Budget Monitoring
      |
      +-------------------+
      |                   |
      v                   v
Within Budget       Budget Exceeded
                          |
                          v
                       Alert
```

---

## Technology Stack

### Frontend

* HTML
* CSS
* JavaScript

### Backend

* PHP

### Database

* MySQL

### Development Environment

* XAMPP
* Apache
* MySQL
* PHP

### External Libraries

* Chart.js
* jsPDF

---

## Database

The application uses a MySQL database named:

```text
budget_tracker
```

The primary expense table is:

```text
expenses
```

The application stores expense information including:

| Field      | Description               |
| ---------- | ------------------------- |
| `id`       | Unique expense identifier |
| `title`    | Expense title             |
| `amount`   | Expense amount            |
| `category` | Expense category          |
| `date`     | Date of expense           |

---

## Expense Categories

The application supports the following categories:

* Food
* Rent
* Travel
* Shopping
* Utilities
* Entertainment
* Other

Categories are used to generate the spending breakdown and category-wise reports.

---

## Budget Management

Users can set a monthly budget directly from the dashboard.

The application calculates:

```text
Total Spent = SUM(All Expense Amounts)
```

The budget progress is calculated as:

```text
Budget Progress = (Total Spent / Budget Limit) × 100
```

The progress indicator changes according to the spending level:

```text
Below 50%       -> Normal
50% - 79%       -> Warning
80% and above   -> Critical
```

If total spending exceeds the configured budget, the application displays a budget exceeded alert.

---

## Expense Management

Users can add an expense using:

* Expense title
* Amount
* Category
* Date

The information is submitted to the PHP backend and stored in the MySQL database.

The application displays stored expenses in a table sorted by date.

Users can also delete individual expenses.

---

## Monthly Expense Summary

The application groups expenses by month and calculates the total spending for each month.

Example:

```text
Month       Total Spent
------------------------
2026-01     $500.00
2026-02     $720.50
2026-03     $610.00
```

This allows users to understand their spending patterns over time.

---

## Spending Breakdown

The application generates a category-wise spending breakdown using Chart.js.

The chart displays the total amount spent for each category.

```text
Expenses
   |
   v
Group by Category
   |
   v
Calculate Category Totals
   |
   v
Chart.js
   |
   v
Pie Chart
```

This provides a visual representation of where the user's money is being spent.

---

## Report Generation

The application supports multiple report formats.

### CSV Export

Users can export the complete expense list as a CSV file.

The generated file contains:

```text
Title
Amount
Category
Date
```

The exported file is named:

```text
expenses.csv
```

### PDF Expense Report

The application can generate a PDF containing the expense table.

The generated report is saved as:

```text
expense_report.pdf
```

### Category-Wise PDF Report

A separate PDF report can group expenses by category.

The generated file is:

```text
Category_Wise_Expense_Report.pdf
```

---

## Authentication

The project contains a basic PHP session-based login system.

The login flow is:

```text
Username + Password
        |
        v
Credential Validation
        |
   +----+----+
   |         |
   v         v
Valid      Invalid
   |         |
   v         v
Dashboard   Error
```

The authenticated session is maintained using PHP sessions.

> Note: The current implementation uses hard-coded credentials for demonstration purposes. Production applications should use a database-backed authentication system with securely hashed passwords.

---

## Dark Mode

The dashboard includes a dark mode toggle implemented using JavaScript and CSS.

The mode dynamically applies a `dark-mode` CSS class to the page.

The dark mode changes the appearance of:

* Page background
* Text
* Input fields
* Buttons
* Selection fields
* Expense tables

---

## Project Structure

The current project is organized as follows:

```text
ExpenseTracker-main/
│
└── budget_tracker/
    │
    ├── index.php
    ├── login.php
    ├── logout.php
    ├── add.php
    ├── delete.php
    ├── db.php
    │
    └── images/
        └── budgetimg.png
```

### File Description

| File            | Purpose                        |
| --------------- | ------------------------------ |
| `index.php`     | Main expense tracker dashboard |
| `login.php`     | User authentication            |
| `logout.php`    | Ends the user session          |
| `add.php`       | Adds expenses to the database  |
| `delete.php`    | Deletes an expense             |
| `db.php`        | MySQL database connection      |
| `budgetimg.png` | Dashboard background image     |

---

## Installation

### Requirements

Install the following software:

* XAMPP
* Apache
* MySQL
* PHP
* Web browser

---

## Setup

### Step 1: Install XAMPP

Install XAMPP and start:

```text
Apache
MySQL
```

from the XAMPP Control Panel.

---

### Step 2: Copy the Project

Copy the project folder into the XAMPP web directory:

```text
C:\xampp\htdocs\
```

The resulting structure should look like:

```text
C:\xampp\htdocs\
│
└── ExpenseTracker-main\
    └── budget_tracker\
```

---

### Step 3: Create the Database

Open:

```text
http://localhost/phpmyadmin
```

Create a database named:

```text
budget_tracker
```

Create the `expenses` table with the required fields:

```sql
CREATE TABLE expenses (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    amount DECIMAL(10,2) NOT NULL,
    category VARCHAR(100) NOT NULL,
    date DATE NOT NULL
);
```

---

### Step 4: Configure Database Connection

The database connection is defined in:

```text
budget_tracker/db.php
```

The default configuration is:

```php
$host = "localhost";
$user = "root";
$password = "";
$database = "budget_tracker";
```

These settings correspond to the default XAMPP MySQL configuration.

Update them if your MySQL configuration is different.

---

### Step 5: Run the Application

Open the following URL in your browser:

```text
http://localhost/ExpenseTracker-main/budget_tracker/login.php
```

After successful authentication, the application redirects to the expense tracker dashboard.

---

## Usage

### Login

Enter the configured username and password on the login page.

### Set Budget

Enter the desired monthly budget and select:

```text
Set Budget
```

### Add Expense

Enter:

```text
Expense Title
Amount
Category
Date
```

and select:

```text
Add Expense
```

### View Expenses

All stored expenses are displayed in the main expense table.

### Delete Expense

Select the delete option associated with an expense.

### Analyze Spending

Use the spending breakdown chart and monthly summary to analyze expenses.

### Export Reports

Use the available export options to generate:

```text
CSV
PDF
Category-Wise PDF
```

---

## Security Considerations

The current project is intended primarily for learning and demonstration purposes.

For production deployment, the following improvements should be implemented:

* Password hashing using `password_hash()`
* Secure login sessions
* Authentication middleware for protected pages
* Prepared statements for all database operations
* Input validation
* CSRF protection
* Authorization checks before deleting records
* Secure session configuration
* Environment variables for database credentials
* HTTPS
* Secure database configuration

In particular, database operations such as deleting records should use prepared statements instead of directly inserting URL parameters into SQL queries.

---

## Current Limitations

The current implementation has several limitations:

* Budget information is stored in the PHP session rather than the database.
* The login credentials are hard-coded.
* There is no multi-user account system.
* Expense deletion is performed through a URL parameter.
* The application does not currently provide an expense editing feature.
* There is no persistent monthly budget history.
* The interface is primarily designed for local XAMPP deployment.
* Production-level authentication and authorization are not implemented.

---

## Future Enhancements

Potential improvements include:

### User Accounts

Implement a database-backed user registration and authentication system.

### Password Security

Replace hard-coded credentials with securely hashed passwords.

### Expense Editing

Allow users to update existing expense records.

### Persistent Budgets

Store monthly budgets in the database rather than PHP sessions.

### Advanced Dashboard

Add additional financial metrics such as:

* Average monthly spending
* Highest expense
* Lowest expense
* Category percentages
* Remaining budget
* Monthly savings

### Advanced Charts

Add:

* Monthly spending line charts
* Category bar charts
* Budget versus spending charts
* Yearly spending trends

### Search and Filtering

Allow users to filter expenses by:

* Date
* Category
* Amount
* Title

### Database Backup

Provide an option to export or back up the expense database.

### Responsive Design

Improve the interface for mobile and tablet devices.

---

## Learning Outcomes

This project demonstrates practical experience with:

* PHP backend development
* MySQL database integration
* CRUD operations
* Session management
* HTML and CSS
* JavaScript
* Chart.js
* PDF generation
* CSV generation
* Form handling
* SQL queries
* Basic authentication
* Financial data visualization

---

## License

Add an appropriate open-source license before publicly distributing the project.

For example:

```text
MIT License
```

The selected license should reflect the intended use and distribution of the project.

---

## Author

**Aswin M**

B.Tech Computer Science and Engineering

Areas of Interest:

* Software Development
* Cybersecurity
* Artificial Intelligence
* Machine Learning
* Web Development
* Data Analytics

---

## Acknowledgements

This project uses open-source technologies and libraries including:

* PHP
* MySQL
* HTML
* CSS
* JavaScript
* Chart.js
* jsPDF
* XAMPP

These technologies were used for application development, database management, data visualization, and report generation.
