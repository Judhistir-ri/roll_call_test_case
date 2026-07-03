# Roll Call API Automation Test Suite

## Overview

This project contains the API automation test suite for the **Roll Call** backend application.

The automation framework is built using **Jest** and **Supertest** to validate the functionality of Roll Call APIs. It covers both **positive** and **negative** test scenarios to ensure the APIs work as expected.

---

# Technology Stack

- Node.js
- Jest
- Supertest
- dotenv

---

# Project Structure

```text
api-tests/
│
├── tests/
│   ├── roll_call_old.test.js
│   ├── roll_call_v2.test.js
│
├── helpers/
│   └── testState.js
│
├── .env
├── package.json
└── README.md
```

---

# Prerequisites

Before running the automation tests, make sure the following are installed:

- Node.js (v18 or above)
- npm

---

# Installation

Clone the repository.

```bash
git clone <repository-url>
```

Navigate to the project directory.

```bash
cd api-tests
```

Install the required dependencies.

```bash
npm install
```

---

# Environment Configuration

Create a `.env` file in the project root directory.

Example:

```env
BASE_URL=https://your-api-url

ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD=admin123
```

Update the values according to your environment.

---

# Test User Configuration

Update the test user information in:

```text
helpers/testState.js
```

Example:

```javascript
module.exports = {
    token: "",
    userId: "c4241735465b27084abc"
};
```

---

# Running the Automation Tests

Run all API automation tests using:

```bash
npm test
```

or

```bash
npm run test
```

The test suite executes sequentially using the following script:

```json
"scripts": {
    "test": "jest --runInBand"
}
```

---

# Test Suites

## Roll Call Old Version

**File:**

```text
roll_call_old.test.js
```

**Modules Covered**

- Authentication
- User Management
- Emergency Information (V1)
- Alert Timing
- Check-In
- Language
- Subscription APIs

---

## Roll Call Version 2

**File:**

```text
roll_call_v2.test.js
```

**Modules Covered**

- Authentication
- User Management
- Emergency Contacts
- Alert Timing
- Check-In
- Language
- FCM Token
- Subscription APIs

---

# APIs Covered

| Module | APIs |
|---------|------|
| Authentication | Login |
| User | Create User, Get User, Update Name |
| Emergency Contact | Create, Update, Delete |
| Alert Timing | Update Alert Timing |
| Check-In | User Check-In |
| Language | Update Language |
| FCM Token | Update Device Token |
| Subscription | Subscription Details |
| Subscription History | Fetch Subscription History |

---

# Test Scenarios

## Positive Test Cases

- Login with valid credentials
- Create user successfully
- Get user details
- Update user name
- Create emergency contact
- Update emergency contact
- Delete emergency contact
- Update alert timing
- User check-in
- Update language
- Update FCM token
- Fetch subscription details
- Fetch subscription history

---

## Negative Test Cases

- Invalid login credentials
- Missing authorization token
- Invalid authorization token
- Empty request body
- Missing required fields
- Invalid email format
- Duplicate email
- Duplicate mobile number
- Invalid user ID
- Invalid emergency ID
- Invalid alert timing
- Invalid language code

---

# Expected Results

Execute the following command:

```bash
npm test
```

A successful execution should produce output similar to the following:

```text
PASS tests/roll_call_old.test.js
PASS tests/roll_call_v2.test.js

Test Suites: 2 passed, 2 total
Tests:       159 passed, 159 total
Snapshots:   0 total
Time:        104.511 s

Ran all test suites.
```

---

# Success Criteria

The automation execution is considered successful when:

- All test suites pass successfully.
- All test cases pass.
- Expected HTTP status codes are returned.
- API response validation passes.
- Authentication is successful where required.
- Validation and error handling behave as expected.
- No Jest assertion failures occur.

---

# Common Issues

## Invalid Credentials

Verify the following values in the `.env` file:

- ADMIN_EMAIL
- ADMIN_PASSWORD

---

## Unauthorized (401)

Possible reasons:

- Missing Authorization header
- Invalid Bearer Token
- Expired Token

---

## User Not Found

Verify that the configured `userId` in `helpers/testState.js` exists in the target environment.

---

## API Not Reachable

Verify the `BASE_URL` in the `.env` file and ensure the backend service is running.

---

## Test Failures

If any test fails:

- Verify the API is running.
- Verify the environment variables.
- Verify the test user exists.
- Check if the API behavior has changed.
- Review the error message displayed by Jest.

---

# Notes

- Run the automation against the **Development** or **QA** environment only.
- Do not execute the test suite against the Production environment.
- Ensure the `.env` file contains valid credentials before running the tests.
- Keep the test user data updated whenever required.
- Execute tests using `jest --runInBand` to ensure sequential execution and avoid test data conflicts.

---

# Conclusion

The Roll Call API Automation Test Suite verifies the core functionality of the application by executing comprehensive positive and negative test scenarios. Running the test suite before deployment helps ensure API stability, validates expected behavior, and improves overall software quality.