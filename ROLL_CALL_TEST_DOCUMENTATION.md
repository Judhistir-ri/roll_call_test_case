# Roll Call API Test Execution Guide

## Purpose

This document explains how to execute the Roll Call API automation tests and verify the expected results.

---

## Prerequisites

Before running the tests, ensure the following are installed:

- Node.js
- npm

Also ensure that:

- The Roll Call backend API is running.
- The `.env` file contains valid configuration values.

Example:

```env
BASE_URL=https://your-api-url

ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD=admin123
```

---

## Install Dependencies

Open the project folder and install the required packages.

```bash
npm install
```

---

## Run the Test Suite

Execute the following command:

```bash
npm test
```

or

```bash
npm run test
```

The test suite is configured to execute sequentially using Jest.

---

## Test Coverage

The automation suite covers the following modules:

- Authentication
- User Management
- Emergency Contact APIs
- Alert Timing
- Check-In
- Language APIs
- FCM Token APIs
- Subscription APIs

The suite includes both positive and negative test scenarios.

---

## Expected Result

If all tests execute successfully, the terminal output will be similar to:

```text
PASS tests/roll_call_old.test.js
PASS tests/roll_call_v2.test.js

Test Suites: 2 passed, 2 total
Tests:       159 passed, 159 total
Snapshots:   0 total
Time:        104.511 s

Ran all test suites.
```

This indicates that:

- All test suites executed successfully.
- All test cases passed.
- No assertion failures occurred.

---

## Troubleshooting

### Unauthorized (401)

- Verify the admin credentials in the `.env` file.
- Ensure the authorization token is valid.

### API Connection Failed

- Verify the `BASE_URL`.
- Ensure the backend service is running.

### Test Failures

If any test fails:

- Verify the backend API is available.
- Check the environment configuration.
- Verify the test user exists.
- Review the Jest error message to identify the failed assertion.

---

## Notes

- Run the tests against the Development or QA environment.
- Do not execute the automation against the Production environment.
- Ensure the `.env` file contains valid credentials before running the tests.
- Execute the test suite using `npm test` before submitting code changes.