# REST API Design

## 1. API Overview

The application exposes RESTful APIs for managing products, categories, users, inventory, orders and payments.

Base URL:

`/api/v1`

Data format: JSON

Authentication: JWT Bearer Token

## 2. Authentication APIs

| Method | Endpoint | Access |
|---|---|---|
| POST | /api/v1/auth/register | Public |
| POST | /api/v1/auth/login | Public |
| GET | /api/v1/auth/me | Authenticated |

## 3. Product APIs

| Method | Endpoint | Access |
|---|---|---|
| GET | /api/v1/products | Public |
| GET | /api/v1/products/{id} | Public |
| POST | /api/v1/admin/products | Admin |
| PUT | /api/v1/admin/products/{id} | Admin |
| DELETE | /api/v1/admin/products/{id} | Admin |

## 4. Category APIs

| Method | Endpoint | Access |
|---|---|---|
| GET | /api/v1/categories | Public |
| GET | /api/v1/categories/{id} | Public |
| POST | /api/v1/admin/categories | Admin |
| PUT | /api/v1/admin/categories/{id} | Admin |
| DELETE | /api/v1/admin/categories/{id} | Admin |

## 5. Inventory APIs

| Method | Endpoint | Access |
|---|---|---|
| GET | /api/v1/inventory/{productId} | Public |
| GET | /api/v1/admin/inventory | Admin |
| PATCH | /api/v1/admin/inventory/{productId} | Admin |
| GET | /api/v1/admin/inventory/low-stock | Admin |

## 6. Order APIs

| Method | Endpoint | Access |
|---|---|---|
| POST | /api/v1/orders | Customer |
| GET | /api/v1/orders/my-orders | Customer |
| GET | /api/v1/orders/{id} | Order owner or Admin |
| PATCH | /api/v1/orders/{id}/cancel | Order owner |
| GET | /api/v1/admin/orders | Admin |
| PATCH | /api/v1/admin/orders/{id}/status | Admin |

## 7. Payment APIs

| Method | Endpoint | Access |
|---|---|---|
| POST | /api/v1/orders/{id}/payments | Order owner |
| GET | /api/v1/orders/{id}/payments | Order owner or Admin |
| GET | /api/v1/payments/{id} | Payment owner or Admin |

## 8. Reporting APIs

| Method | Endpoint | Access |
|---|---|---|
| GET | /api/v1/admin/reports/sales | Admin |
| GET | /api/v1/admin/reports/inventory | Admin |

## 9. HTTP Methods

- GET: Retrieve resources.
- POST: Create resources or initiate operations.
- PUT: Replace an existing resource.
- PATCH: Partially update a resource.
- DELETE: Delete or deactivate eligible resources.

## 10. HTTP Status Codes

| Code | Meaning |
|---|---|
| 200 | OK |
| 201 | Created |
| 204 | No Content |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 409 | Conflict |
| 500 | Internal Server Error |

## 11. Request and Response Standards

- All request and response bodies use JSON.
- Monetary values are calculated by the backend.
- Passwords are never returned in API responses.
- Product and order identifiers are returned in responses.
- Sensitive operations require authentication and authorization.
- Validation failures return meaningful error messages.

## 12. Error Response Structure

The application uses a consistent error response containing:

- timestamp
- status
- error
- message
- path

## 13. API Design Improvements

Future improvements include:

- Pagination and sorting.
- Filtering and searching.
- API versioning.
- Idempotency keys.
- Centralized exception handling.
- OpenAPI / Swagger documentation.
- Request validation.
- Rate limiting.