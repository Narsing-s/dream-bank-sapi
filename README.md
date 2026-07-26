# 🏦 Dream Bank System API

## Overview

Dream Bank System API is a MuleSoft System API developed using Mule 4 and APIKit. It provides REST APIs for managing customer bank accounts, including account creation, retrieval, update, deletion, health monitoring, and email notifications. Customer information is stored in Snowflake Database, and email notifications are sent using the SMTP connector.

---

# Project Architecture

```
Client
   │
   ▼
HTTP Listener
   │
APIKit Router
   │
Implementation Flow
   │
─────────────────────────────────────────────
│                 │                │
▼                 ▼                ▼
Snowflake DB   Email Service   Health Check
│
▼
JSON Response
```

---

# Project Structure

```
src
│
├── main
│   ├── mule
│   │   ├── global.xml
│   │   ├── implementation.xml
│   │   ├── database_implementation.xml
│   │   ├── auto_accountNumber_generation.xml
│   │   ├── account_already_email_integration.xml
│   │   ├── account_doesnot_exist_email_integration.xml
│   │   ├── success_email_integration.xml
│   │   └── health_check.xml
│   │
│   └── resources
│       ├── application.yaml
│       ├── log4j2.xml
│       ├── RAML
│       ├── Properties
│       └── DataWeave Scripts
│
└── test
    └── resources
```

---

# Modules Description

## global.xml

Contains all reusable configurations.

- HTTP Listener Configuration
- APIKit Configuration
- Snowflake Database Configuration
- SMTP Email Configuration
- HTTP Request Configuration
- Global Error Handling

---

## implementation.xml

Main business logic.

Responsible for:

- API Request Processing
- Data Validation
- Calling Database Flows
- Calling Email Flows
- Returning API Response

---

## database_implementation.xml

Handles all database operations.

Functions

- Insert Customer
- Retrieve Customer
- Update Customer
- Delete Customer

---

## auto_accountNumber_generation.xml

Generates a unique account number automatically during account creation.

---

## success_email_integration.xml

Sends account creation success email to the customer.

---

## account_already_email_integration.xml

Sends notification when the customer account already exists.

---

## account_doesnot_exist_email_integration.xml

Sends notification when the requested account is not found.

---

## health_check.xml

Checks whether the application is running successfully.

Example Response

```json
{
    "status":"UP",
    "message":"Dream Bank API is Running"
}
```

---

# REST APIs

## Create Account

```
POST /accounts
```

Creates a new customer account.

---

## Get Account Details

```
GET /accounts
```

Retrieve customer information.

Query Parameter

```
status=ACTIVE
status=INACTIVE
```

---

## Update Account

```
PATCH /accounts/{accountNumber}
```

Updates customer information.

Example

- Full Name
- Address
- Mobile Number

---

## Delete Account

```
DELETE /accounts/{accountNumber}
```

Deletes customer account after verification.

---

## Health Check

```
GET /health
```

Success

```json
{
    "status":"UP",
    "message":"API is Running"
}
```

Failure

```json
{
    "status":"DOWN",
    "message":"API is Not Running"
}
```

---

# Technologies Used

- MuleSoft 4.x
- APIKit
- DataWeave 2.0
- HTTP Connector
- Snowflake Connector
- SMTP Connector
- Maven
- Java 17
- Anypoint Studio

---

# Database

Database Used

- Snowflake

Operations

- Insert
- Select
- Update
- Delete

---

# Email Notifications

Emails are automatically sent for

- Account Creation
- Account Update
- Account Deletion
- Account Validation

Email Format

- HTML Email Template

---

# Error Handling

The application returns appropriate HTTP status codes.

| Status Code | Description |
|-------------|-------------|
| 200 | Success |
| 400 | Bad Request |
| 404 | Resource Not Found |
| 405 | Method Not Allowed |
| 406 | Not Acceptable |
| 415 | Unsupported Media Type |
| 500 | Internal Server Error |
| 501 | Not Implemented |

---

# Build Project

```bash
mvn clean package
```

---

# Run Project

```bash
mvn mule:run
```

Or

Run directly from **Anypoint Studio**.

---

# Testing

Use

- Postman
- API Console
- MUnit

---

# Logging

Application logs are available in

- Anypoint Studio Console
- Runtime Logs
- CloudHub Logs

---

# Future Enhancements

- OAuth 2.0 Authentication
- JWT Security
- Rate Limiting
- CI/CD Pipeline
- CloudHub Deployment
- API Monitoring
- Anypoint API Manager Policies

---

# Author

**Developer:** Narsing Beesetti

**Project:** Dream Bank System API

**Version:** 1.0.0
