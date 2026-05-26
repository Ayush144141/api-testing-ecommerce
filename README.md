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

Base URL: `https://fakestoreapi.com/`

| Module | Endpoints Tested |
|--------|-----------------|
| Auth | /auth/login |
| Products | /products, /products/{id}, /products/categories, /products/category/{name} |
| Users | /users, /users/{id} |
| Carts | /carts, /carts?userId={id}, /carts?startdate=&enddate= |

---

## What I Found

| Bug ID | Summary | Severity |
| BUG-001 | Invalid product ID returns 200 instead of 404 | Medium |
| BUG-002 | Invalid category returns 200 with empty [] | Low |
| BUG-003 | POST /products accepts missing required fields | High |
| BUG-004 | DELETE works without any auth token — security bug | Critical |
| BUG-005 | Invalid user ID returns 200 instead of 404 | Medium |
| BUG-006 | Cart accepts negative quantity values | High |

Full bug reports are in the `/bug-reports` folder.

*Built by Ayush Kumar — QA Engineer (Fresher)*  
*Tools: Postman · JIRA · REST API · JSON*
