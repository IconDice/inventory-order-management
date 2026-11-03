# Project Requirements

## 1. Introduction

The Inventory & Order Management System is a backend application designed to manage products, inventory, customers, orders, and payments for an e-commerce business.

The system provides centralized management of business operations and ensures consistency between product availability, customer orders, and inventory records.

## 2. Problem Statement

Traditional inventory management often relies on spreadsheets or disconnected systems.

This creates several problems:

- Incorrect stock information.
- Duplicate or inconsistent orders.
- Difficulty tracking customer purchases.
- Manual inventory updates.
- Lack of centralized reporting.
- Inconsistent order and payment records.

Our application aims to solve these problems through a centralized RESTful backend system.

## 3. Project Objectives

1. Develop centralized product management.
2. Maintain accurate inventory records.
3. Implement secure user authentication.
4. Provide reliable order processing.
5. Maintain consistent payment information.
6. Prevent inventory inconsistencies.
7. Generate basic business reports.

## 4. Functional Requirements

### FR-01: Product Management

- Administrators can create products.
- Administrators can update product details.
- Administrators can delete products.
- Users can retrieve product information.
- Users can search and filter products.

### FR-02: Category Management

- Administrators can create categories.
- Administrators can update categories.
- Administrators can delete eligible categories.
- Products can be associated with categories.

### FR-03: User Management

- Customers can register.
- Customers can log in.
- Customers can update their profiles.
- Users have assigned roles.

### FR-04: Authentication and Authorization

- Users must authenticate before accessing protected resources.
- Passwords must be securely hashed.
- JWT will be used for authentication.
- Administrators and customers will have different permissions.

### FR-05: Inventory Management

- Administrators can update stock quantities.
- The system maintains available stock.
- Customers can check product availability.
- The system identifies low-stock products.
- Negative inventory quantities are not permitted.

### FR-06: Order Management

- Customers can place orders.
- An order can contain multiple products.
- The system validates product availability.
- Customers can view their order history.
- Customers can cancel eligible orders.
- Administrators can view and manage orders.

### FR-07: Payment Management

- The system records payment attempts.
- Payment status is maintained.
- Failed payments are recorded.
- Successful payments are associated with orders.

### FR-08: Reporting

- Administrators can view sales reports.
- Administrators can view inventory reports.
- Administrators can identify low-stock products.

## 5. Non-Functional Requirements

### NFR-01: Security

User credentials and sensitive information must be protected.

### NFR-02: Performance

API endpoints should respond efficiently under expected application load.

### NFR-03: Reliability

The system must prevent inconsistent inventory and order records.

### NFR-04: Maintainability

The application must follow layered architecture and separation of concerns.

### NFR-05: Scalability

The system should support future expansion of business functionality.

### NFR-06: Data Integrity

Database relationships and business constraints must be maintained.

### NFR-07: Testability

Core business logic must be covered by unit and integration tests.

## 6. System Constraints

- The backend will be developed using Java and Spring Boot.
- MySQL will be used as the relational database.
- The application will expose REST APIs.
- Maven will manage project dependencies.
- Git will maintain version history.

## 7. Future Enhancements

- Redis caching.
- Email notifications.
- Multi-warehouse inventory.
- Payment gateway integration.
- Docker containerization.
- Audit logging.
- Advanced sales analytics.
- Automated inventory notifications.