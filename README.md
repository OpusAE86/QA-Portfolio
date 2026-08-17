# QA Portfolio

Welcome to my QA Engineering portfolio.

This repository contains practical examples of my work in software testing, including manual testing, API testing, test documentation, bug reporting, and test automation.

---

## About Me

I am developing my skills as a QA Engineer with a focus on manual and API testing.

I practice testing real API scenarios and document test results, defects, expected behavior, and actual behavior.

---

## QA Skills

- Manual Testing
- Functional Testing
- API Testing
- REST API
- Positive and Negative Testing
- Regression Testing
- Smoke Testing
- Test Case Design
- Bug Reporting
- Boundary Value Analysis
- Equivalence Partitioning
- JSON Validation
- HTTP Status Codes
- Data Type Validation
- Basic API Test Automation

---

## Tools

- Postman
- Git
- GitHub
- Visual Studio Code
- JavaScript
- REST API

---

## Projects

### API Testing — ReqRes

Practical REST API testing project using Postman.

The project includes:

- API test cases
- Positive and negative scenarios
- Bug reports
- Automated Postman tests
- JSON response validation
- HTTP status code validation
- Data type validation
- Email format validation
- ISO 8601 date validation
- Git/GitHub version control

**Project:** [API Testing](./API-Testing/)

**Postman Collection:** [ReqRes API Tests](./API-Testing/Postman/)

**Test Cases:** [Test Cases](./API-Testing/Test-Cases/)

**Bug Reports:** [Bug Reports](./API-Testing/Bug-Reports/)

---

## API Testing Results

### GET `/api/users?page=2`

7 automated checks:

- Status Code = 200
- Page = 2
- per_page = 6
- Number of users matches per_page
- Required fields exist
- Correct data types
- Email format

**Result: 7/7 PASS**

### POST `/api/users`

Automated checks include:

- Status Code = 201
- Name validation
- Job validation
- ID presence
- ID data type
- createdAt presence
- ISO 8601 date format
- createdAt data type

**Result: 7 checks — 6 PASS / 1 FAIL**

The failed test detected an API response data type issue:

```text
Expected: id → number
Actual:   id → string
```

Defects Found
API ID Data Type

Endpoint: POST /api/users

The API returns the created user's id as a string instead of a number.

Expected:
{
"id": 271
}
Actual:
{
"id": "271"
}
Severity: High

Priority: High
DELETE Resource Validation

The DELETE request returned:

204 No Content

However, a subsequent GET request returned:

200 OK

and the deleted user was still available.

This indicates that the deletion was not reflected when the resource was requested again.
QA-Portfolio
│
├── API-Testing
│ ├── README.md
│ ├── Test-Cases
│ ├── Bug-Reports
│ └── Postman
│ └── ReqRes API Tests.postman_collection.json
│
└── README.md
Currently Learning
Advanced API Testing
Postman Test Automation
JavaScript for QA Automation
Test Design Techniques
SQL
Software Testing Processes
Git and GitHub
Goal

My goal is to develop strong practical QA skills and build experience in manual testing, API testing, and test automation.
