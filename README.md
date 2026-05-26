# API Testing – E-Commerce Platform (FakeStore API)

A manual API testing project where I tested the REST APIs of a dummy e-commerce platform using FakeStoreAPI as the backend. Built to practice real QA skills — writing test cases, finding bugs, and documenting everything properly.

**Tools:** Postman · JIRA · REST API · JSON · GitHub

---

## About the Project

FakeStoreAPI is a free REST API that simulates an e-commerce backend with products, users, carts and authentication. I picked this because it has a good mix of endpoints and actually has some real bugs worth reporting.

The project covers:
- 28 test cases across Auth, Products, Users and Carts modules
- GET, POST, PUT, PATCH, DELETE methods
- Status code validation, response schema checks, boundary condition testing
- 6 defects found and logged with proper JIRA-style reports
- Reusable Postman collection with environment variables and pre-request auth script

---

## API Under Test

Base URL: `https://fakestoreapi.com`

| Module | Endpoints Tested |
|--------|-----------------|
| Auth | /auth/login |
| Products | /products, /products/{id}, /products/categories, /products/category/{name} |
| Users | /users, /users/{id} |
| Carts | /carts, /carts?userId={id}, /carts?startdate=&enddate= |

---

## What I Found

| Bug ID | Summary | Severity |
|--------|---------|----------|
| BUG-001 | Invalid product ID returns 200 instead of 404 | Medium |
| BUG-002 | Invalid category returns 200 with empty [] | Low |
| BUG-003 | POST /products accepts missing required fields | High |
| BUG-004 | DELETE works without any auth token — security bug | Critical |
| BUG-005 | Invalid user ID returns 200 instead of 404 | Medium |
| BUG-006 | Cart accepts negative quantity values | High |

Full bug reports are in the `/bug-reports` folder.

---

## Folder Structure

---

## How to Use This Collection

1. Download and install [Postman](https://www.postman.com/downloads/)
2. Clone this repo or download as ZIP
3. In Postman → Import → upload `FakeStore_Collection.json`
4. Import `FakeStore_Environment.json` and select it from environment dropdown
5. Run individual requests or use Collection Runner for the full suite

---

## Test Summary

| Module | Total | Pass | Fail |
|--------|-------|------|------|
| Auth | 5 | 5 | 0 |
| Products | 14 | 9 | 5 |
| Users | 3 | 2 | 1 |
| Carts | 6 | 4 | 2 |
| **Total** | **28** | **20** | **8** |

Pass rate: 71% — with 6 unique defects identified across modules.

---

## Key Learnings

- Not all APIs return proper HTTP status codes — a 200 with null body is not the same as a 404 and that difference matters a lot for frontend error handling
- Boundary condition testing like negative quantities and missing required fields finds more bugs than happy path testing
- Saving the auth token as an environment variable using a pre-request script saved a lot of manual work across requests
- Writing clear bug reports with exact request and response logs makes it much easier for developers to reproduce and fix issues
- Always test auth protected endpoints without a token — missing auth checks are a critical security issue

---

*Built by Ayush Kumar — QA Engineer (Fresher)*  
*Tools: Postman · JIRA · REST API · JSON*
