Dream Bank System API
Overview

The Dream Bank System API is a MuleSoft System API developed using Mule 4, APIKit, and Anypoint Studio. It provides RESTful APIs to manage bank accounts, including account creation, retrieval, update, deletion, health monitoring, database operations using Snowflake, and automated email notifications.

Features
Account Creation
Get Account Details
Update Account Information
Delete Account
Auto Account Number Generation
Snowflake Database Integration
Email Notifications
API Health Check
Global Error Handling
APIKit Router
REST APIs
Logging
Technology Stack
Technology	Version
Mule Runtime	4.x
Anypoint Studio	7.x
APIKit	Latest
DataWeave	2.0
Snowflake Connector	Mule Connector
SMTP Connector	Mule Email Connector
HTTP Listener	Mule HTTP Connector
Maven	3.x
Project Structure
src
│
├── main
│   ├── mule
│   │   ├── global.xml
│   │   ├── implementation.xml
│   │   ├── database_implementation.xml
│   │   ├── auto_accountNumber_generation.xml
│   │   ├── success_email_integration.xml
│   │   ├── account_already_email_integration.xml
│   │   ├── account_doesnot_exist_email_integration.xml
│   │   └── health_check.xml
│   │
│   └── resources
│       ├── application.yaml
│       ├── log4j2.xml
│       ├── properties
│       └── DataWeave Scripts
│
└── test
    └── resources
API Endpoints
Create Account
POST /accounts

Creates a new customer account.

Get Account Details
GET /accounts

Returns customer account information.

Supports query parameter:

status=ACTIVE
status=INACTIVE
Update Account
PATCH /accounts/{accountNumber}

Updates customer information such as:

Full Name
Address
Mobile Number

After successful update:

Database updated
Success email sent
JSON response returned
Delete Account
DELETE /accounts/{accountNumber}

Deletes customer account.

Workflow:

Verify account
Send account deactivation email
Delete from Snowflake
Return success response
Health Check
GET /health

Example Response

Success

{
   "status":"UP",
   "message":"Dream Bank API is running successfully"
}

Failure

{
   "status":"DOWN",
   "message":"Dream Bank API is not running"
}
Database

The project uses Snowflake Database for storing customer information.

Operations include:

Insert
Select
Update
Delete
Email Notifications

SMTP email integration is configured for:

Account Creation
Account Update
Account Deletion
Account Status Notifications

Emails are sent in HTML format.

Configuration

Application properties include:

HTTP Listener
Snowflake Credentials
SMTP Configuration
Environment Properties

The project uses:

HTTP Listener
APIKit Router
Snowflake Connector
SMTP Connector
Configuration Properties
HTTP Request Configuration
Error Handling

Global APIKit error handling is implemented for:

400 Bad Request
404 Resource Not Found
405 Method Not Allowed
406 Not Acceptable
415 Unsupported Media Type
501 Not Implemented

Custom JSON responses are returned for each error.

Build Project
mvn clean package
Run Project
mvn mule:run

Or run directly from Anypoint Studio.

Testing

Recommended tools:

Postman
API Console
Logging

Application logs are available through:

Anypoint Studio Console
Runtime Logs
CloudHub Logs (if deployed)
Future Enhancements
JWT Authentication
OAuth 2.0
API Manager Policies
Rate Limiting
CloudHub Deployment
CI/CD using GitHub Actions
Monitoring with Anypoint Monitoring
Author

Developer: Narsing Beesetti

Project Name: Dream Bank System API

Version: 1.0.0

This README is suitable for GitHub and professional portfolio documentation, and clearly explains the architecture, features, APIs, technologies, and project organization.
