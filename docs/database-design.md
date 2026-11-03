# Database Design

## 1. Database

MySQL

## 2. Database Entities

The application initially consists of the following entities:

1. User
2. Role
3. UserRole
4. Address
5. Category
6. Product
7. Inventory
8. Order
9. OrderItem
10. Payment

## 3. Entity Relationships

| Parent Entity | Child Entity | Relationship |
|---|---|---|
| User | UserRole | One-to-many |
| Role | UserRole | One-to-many |
| User | Address | One-to-many |
| User | Order | One-to-many |
| Category | Product | One-to-many |
| Product | Inventory | One-to-one |
| Order | OrderItem | One-to-many |
| Product | OrderItem | One-to-many |
| Order | Payment | One-to-many |

## 4. Primary Keys and Foreign Keys

- Every main entity has a primary key.
- UserRole uses a composite primary key consisting of user_id and role_id.
- Products reference categories through category_id.
- Inventory references products through product_id.
- Orders reference users through user_id.
- OrderItems reference orders and products.
- Payments reference orders.
- Addresses reference users.

## 5. Important Database Constraints

- User email must be unique.
- Product price must be greater than zero.
- Inventory quantity cannot be negative.
- Inventory product_id must be unique.
- OrderItem quantity must be greater than zero.
- Order total must be calculated by the backend.
- Historical product prices must be preserved in OrderItem.
- Foreign key relationships must maintain referential integrity.

## 6. Design Decisions

### Separate Product and Inventory
Product information and stock management have separate responsibilities.

### Order and OrderItem
An order can contain multiple products. Each item maintains its own quantity and purchase price.

### Separate Payment Records
An order can have multiple payment attempts.

### Historical Shipping Information
Shipping details are stored with the order so that changes to a customer's saved address do not affect historical orders.

### Monetary Precision
DECIMAL is used for monetary values to avoid floating-point rounding errors.

### Transaction Management
Order creation and stock deduction must be performed atomically.

## 7. Future Database Improvements

- Add inventory movement history.
- Introduce multi-warehouse support.
- Add order status history.
- Add audit timestamps and user tracking.
- Implement Flyway database migrations.