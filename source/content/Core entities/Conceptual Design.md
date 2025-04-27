## 2. Core Business Entities

### Customer

Represents individuals who place orders at the restaurant.

- Key attributes: Customer identification, name, contact information

### Employee

Represents staff members working at the restaurant.

- Key attributes: Employee identification, name, contact information, status

### Role

Represents job positions within the restaurant.

- Key attributes: Role identification, title, description

### Order

Represents customer purchases.

- Key attributes: Order identification, date, status, type, total amount

### Menu Item

Represents food and beverage options available for purchase.

- Key attributes: Item identification, name, description, price, availability

### Ingredient

Represents raw materials used to prepare menu items.

- Key attributes: Ingredient identification, name, availability

### Category

Represents groupings of similar menu items.

- Key attributes: Category identification, name

### Stock

Represents inventory of ingredients.

- Key attributes: Stock identification, level

### Supplier

Represents vendors providing ingredients to the restaurant.

- Key attributes: Supplier identification, name, contact information

### Address

Represents physical locations for customers, suppliers, and the restaurant.

- Key attributes: Address components (city, street, number)

### Table

Represents seating arrangements in the restaurant.

- Key attributes: Table identification, capacity, availability

### Reservation

Represents bookings for dining.

- Key attributes: Reservation identification, date, time, status

### Discount

Represents price reductions for orders.

- Key attributes: Discount identification, description, type, value

### Delivery

Represents order transport to customers.

- Key attributes: Delivery identification, status

### Transaction

Represents financial exchanges.

- Key attributes: Transaction identification, amount

### Payment

Represents methods of settling transactions.

- Key attributes: Payment identification, method, status

## 3. High-Level Relationships

- **Customer places Order**: A customer can place multiple orders; an order belongs to one customer.
- **Employee fulfills Role**: An employee can have multiple roles; a role can be assigned to multiple employees.
- **Order contains Menu Items**: An order can include multiple menu items; a menu item can appear in multiple orders.
- **Menu Item requires Ingredients**: A menu item can require multiple ingredients; an ingredient can be used in multiple menu items.
- **Supplier provides Ingredients**: A supplier can provide multiple ingredients; an ingredient can be sourced from multiple suppliers.
- **Stock tracks Ingredients**: Stock levels are maintained for each ingredient.
- **Order may have Delivery**: An order may be associated with delivery details.
- **Customer makes Reservation**: A customer can make multiple reservations; a reservation belongs to one customer.
- **Reservation assigns Table**: A reservation can include one or more tables; a table can be part of multiple reservations over time.
- **Order may apply Discounts**: An order can have multiple discounts applied; a discount can be applied to multiple orders.
- **Order generates Transaction**: An order results in one transaction; a transaction is associated with one order.
- **Transaction receives Payment**: A transaction can receive multiple payments; a payment is associated with one transaction.


[[Unnormalized Form]]