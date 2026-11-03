# Business Rules

## 1. User Management Rules

### BR-01: Unique Email
Every user must have a unique email address.

### BR-02: Password Security
Passwords must be stored using secure password hashing.

### BR-03: Role Permissions
Only administrators can perform administrative operations.

### BR-04: Customer Data Isolation
Customers can access only their own orders and personal information.

---

## 2. Product Management Rules

### BR-05: Product Price
A product must have a price greater than zero.

### BR-06: Product Name
A product must have a valid, non-empty name.

### BR-07: Category Association
Every active product must belong to a valid category.

### BR-08: Product Deletion
A product that has historical order records should not be physically deleted. It should be deactivated or archived.

---

## 3. Inventory Management Rules

### BR-09: Non-Negative Stock
Inventory quantity must never become negative.

### BR-10: Stock Deduction
Stock must be deducted when an order is successfully created.

### BR-11: Stock Validation
The system must verify available stock before accepting an order.

### BR-12: Low Stock
A product is considered low-stock when its quantity reaches or falls below its configured reorder level.

### BR-13: Stock Restoration
When an eligible order is cancelled, its deducted stock must be restored.

### BR-14: Concurrent Purchases
The system must prevent multiple customers from purchasing stock that is no longer available.

---

## 4. Order Management Rules

### BR-15: Minimum Order Items
An order must contain at least one product.

### BR-16: Server-Side Total
The backend must calculate the order total. Frontend-submitted totals must never be trusted.

### BR-17: Historical Price
The purchase price of each product must be stored in the order item.

### BR-18: Order Ownership
Customers can view and cancel only their own eligible orders.

### BR-19: Order Status
An order must follow valid status transitions.

Initial statuses:

- PENDING_PAYMENT
- CONFIRMED
- CANCELLED
- PAYMENT_FAILED

### BR-20: Order Cancellation
An order can only be cancelled when its current status permits cancellation.

---

## 5. Payment Management Rules

### BR-21: Payment Tracking
Every payment attempt must have a recorded status.

### BR-22: Payment Success
An order can only be marked confirmed after successful payment.

### BR-23: Payment Failure
Failed payments must not be recorded as successful transactions.

### BR-24: Duplicate Payment Protection
Repeated payment requests must not result in duplicate successful charges.

---

## 6. Transaction Management Rules

### BR-25: Atomic Order Creation
Order creation and stock deduction must be handled within a database transaction.

### BR-26: Rollback
If order creation or stock deduction fails, the database changes must be rolled back.

### BR-27: Data Consistency
Order totals, order items, inventory and payment records must remain consistent.

---

## 7. General Business Constraints

- All monetary calculations must use decimal precision.
- Inventory quantities must be whole numbers for our initial product model.
- Important business operations must be logged.
- Invalid operations must return meaningful API errors.
- Database constraints must reinforce critical business rules.