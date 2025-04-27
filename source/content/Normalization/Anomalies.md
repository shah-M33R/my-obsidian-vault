## 1. Anomalies in Core Business Entities

### Employees

- Multivalued attributes: Phone_Numbers (multiple values)
- Multivalued attributes: Emails (multiple values)
- Multivalued attributes: Roles (multiple values)

### Customers

- Multivalued attributes: Phone_Numbers (multiple values)
- Multivalued attributes: Emails (multiple values)
- Non-atomic attribute: Full Address (contains multiple components)

### Orders

- Non-atomic attribute: Customer_Info (contains multiple customer details)
- Multivalued attributes: Items_Info (contains multiple items)
- Derived attribute: Order_Total (calculated from other attributes)
- Derived attribute: Discounted_Amount (calculated from other attributes)

### Menu_Items

- Non-atomic attribute: Category (should be a separate entity)

### Ingredients

- Multivalued attributes: Menu_Items (multiple values)

### Stock

- Non-atomic attribute: Ingredient_Info (contains multiple details)
- Non-atomic attribute: Supplier_Info (contains multiple details)

### Supplier

- Non-atomic attribute: Address (contains multiple components)
- Nested attributes: Phone_Number and Email under Name

### Restock Request

- Non-atomic attribute: Ingredients (references another entity)
- Non-atomic attribute: Supplier (references another entity)

### Delivery Details

- Non-atomic attribute: Order (references another entity)
- Non-atomic attribute: Service (references another entity)
- Non-atomic attribute: Fee (references another entity)

### Delivery Service

- Non-atomic attribute: Contact (contains multiple components)

### Reservation Requests

- Non-atomic attribute: Customer (references another entity)
- Non-atomic attribute: Table (references another entity)

### Transactions

- Non-atomic attribute: Total_Info (contains multiple components)
- Derived attribute: Various totals (calculated from other values)

## 2. Anomalies Grouped by Normal Form Required

### 1NF Violations (Atomic Values)

- Multivalued attributes: Employee Phone_Numbers and Emails
- Multivalued attributes: Customer Phone_Numbers and Emails
- Non-atomic attribute: Customer Full Address
- Non-atomic attribute: Order Customer_Info
- Multivalued attributes: Order Items_Info
- Multivalued attributes: Ingredient Menu_Items
- Non-atomic attribute: Supplier Address
- Nested attributes: Supplier Phone_Number and Email under Name
- Non-atomic attribute: Delivery Service Contact

### 2NF Violations (Partial Dependencies)

- Menu_Items to Category (Category depends only on part of a potential composite key)
- Stock Ingredient_Info and Supplier_Info (depends on Ingredient_ID rather than the whole key)
- Restock Request Ingredients and Supplier (depends on partial keys)
- Delivery Details Order, Service, and Fee (depends on partial keys)
- Reservation Requests Customer and Table (depends on partial keys)

### 3NF Violations (Transitive Dependencies)

- Orders Order_Total (derived from Items_Info)
- Orders Discounted_Amount (derived from other data)
- Transactions Total_Info (derived from other data)

[[Normalization process]]