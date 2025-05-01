# Core Business Entity Relationships

### Employee Management

- **EMPLOYEE (1) — HAS → (M) SHIFTS** Each employee can have multiple shifts, but each shift belongs to exactly one employee.

### Customer and Orders

- **CUSTOMER (1) — PLACES → (M) ORDERS** One customer can place multiple orders, but each order is placed by exactly one customer.
- **CUSTOMER (1) — MAKES → (M) RESERVATION** One customer can make multiple reservations, but each reservation is made by one customer.

### Menu and Ingredients

- **MENU ITEMS (M) — CONTAINS → (N) INGREDIENTS** Many-to-many relationship where menu items contain multiple ingredients, and ingredients can be used in multiple menu items.
- **MENU ITEMS (M) — INCLUDED IN → (N) ORDERS** One menu item can be included in multiple orders (through order items).

### Inventory Management

- **INGREDIENTS (1) — HAS → (1) STOCK** One-to-one relationship where each ingredient has exactly one stock entry.
- **INGREDIENTS (M) — INCLUDED IN → (N) RESTOCK REQUEST**: One restock request can include multiple ingredients, and one ingredient can appear in multiple restock requests over time.
- **INGREDIENTS (M) — SUPPLIED BY → (N) SUPPLIER**: Many-to-many relationship where one ingredient can be sourced from multiple suppliers, and one supplier can provide multiple ingredients.
- **RESTOCK REQUEST (1)  — SENT TO → SUPPLIER (1)**  One supplier can receive multiple restock requests.

### Order Processing

- **ORDERS (1) — HAS → (0,1) DELIVERY DETAILS** An order can have at most one delivery detail (only for delivery orders).
- **ORDERS (1) — PROCESSED IN → (1) TRANSACTIONS** Each order has exactly one transaction record.
- **DISCOUNTS (M) — APPLIED TO → (N) ORDERS** Many-to-many relationship where multiple discounts can be applied to multiple orders.

### Delivery Management

- **DELIVERY SERVICE (1) — HANDLES → (M) DELIVERY** One delivery service can handle multiple deliveries.

### Payment Processing

- **TRANSACTIONS (1) — Processes → (M) PAYMENTS** One transaction can have multiple payment methods (e.g., split payments).

### Reservation System

- **TABLES (1) — HAS → (M) RESERVATION** One table can have multiple reservations (at different times).

![[Basic ER.svg]]