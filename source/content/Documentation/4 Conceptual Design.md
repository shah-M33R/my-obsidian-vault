
## Core Business Entities and Attributes

### Employee

- Employee_ID (Unique identifier for each employee)
- First_Name (Employee's first name)
- Last_Name (Employee's last name)
- Status (Employment status - Active/Inactive)

### Role

- Role_ID (Unique identifier for each role)
- Role_Name (Name of the role, e.g., Cashier)
- Employee_Count (Number of employees with this role)

### Customer

- Customer_ID (Unique identifier for each customer)
- Address_ID (Reference to customer's address)
- First_Name (Customer's first name)
- Last_Name (Customer's last name)

### Order

- Order_ID (Unique identifier for each order)
- Customer_ID (Reference to customer placing order)
- Order_Date (Date and time order was placed)
- Order_Status (Current status of the order)
- Order_Type (Type of order - Dine-in/Drive-Thru/Delivery)
- Items_Total (Total cost of all items before discounts)
- Discounted_Amount (Total discount applied to order)
- Order_Total (Final amount after discounts)

### Menu Item

- Menu_Item_ID (Unique identifier for menu item)
- Category_ID (Reference to item's category)
- Name (Name of the menu item)
- Description (Description of the menu item)
- Price (Item's price)
- Availability (Whether item is currently available)

### Ingredient

- Ingredient_ID (Unique identifier for ingredient)
- Name (Name of the ingredient)
- Availability (Availability status of ingredient)

### Stock

- Stock_ID (Unique identifier for stock record)
- Ingredient_ID (Reference to ingredient tracked)
- Supplier_ID (Reference to supplier of ingredient)
- Stock_Level (Current quantity available)

### Supplier

- Supplier_ID (Unique identifier for supplier)
- Address_ID (Reference to supplier's address)
- Name (Name of the supplier)

### Transaction

- Transaction_ID (Unique identifier for transaction)
- Order_ID (Reference to associated order)
- Order_Total (Total amount from order)
- Delivery_Fee (Fee charged for delivery if applicable)
- Transaction_Fee (Processing fee if applicable)
- Final_Amount (Final amount to be paid)

### Payment

- Payment_ID (Unique identifier for payment)
- Transaction_ID (Reference to associated transaction)
- Final_Amount (Amount paid)
- Payment_Method (Method of payment - cash, card, etc.)
- Payment_Status (Status of payment - completed, failed)

### Delivery

- Delivery_ID (Unique identifier for delivery record)
- Order_ID (Reference to associated order)
- Service_ID (Reference to delivery service)
- Fee_ID (Reference to applicable delivery fee)
- Delivery_Status (Current status of delivery)

### Table

- Table_ID (Unique identifier for table)
- Capacity (Number of seats at table)
- Availability (Current availability status)

### Reservation

- Res_ID (Unique identifier for reservation)
- Customer_ID (Reference to customer making reservation)
- Table_ID (Reference to reserved table)
- Res_Date (Date of reservation)
- Res_Time (Time of reservation)
- Request_Status (Status of reservation request)

## Entity Relationships

### Primary Relationships

1. **Employee-Role Relationship**
    - Employees can have multiple roles
    - Each role can be assigned to multiple employees
    - Implemented through Employee_Role junction table
2. **Customer-Order Relationship**
    - A customer can place multiple orders
    - Each order is associated with exactly one customer
3. **Order-Menu Item Relationship**
    - An order can contain multiple menu items in varying quantities
    - A menu item can be part of many different orders
    - Implemented through Order_Item junction table
4. **Menu Item-Ingredient Relationship**
    - A menu item can require multiple ingredients
    - An ingredient can be used in multiple menu items
    - Implemented through Dish_Ingredients junction table
5. **Order-Transaction Relationship**
    - Each order generates exactly one transaction
    - A transaction is associated with exactly one order
6. **Transaction-Payment Relationship**
    - A transaction can have multiple payments (e.g., split payment)
    - Each payment is associated with exactly one transaction
7. **Ingredient-Stock Relationship**
    - Each ingredient has a corresponding stock level record
    - Stock table tracks current levels of each ingredient
8. **Supplier-Ingredient Relationship**
    - A supplier can provide multiple ingredients
    - An ingredient can be sourced from multiple suppliers
    - Relationship managed through the Stock table

### Secondary Relationships

1. **Order-Discount Relationship**
    - An order can have multiple discounts applied
    - A discount can be applied to multiple orders
    - Implemented through Order_Discount junction table
2. **Order-Delivery Relationship**
    - An order can have at most one delivery record
    - Each delivery record is associated with exactly one order
3. **Customer-Reservation Relationship**
    - A customer can make multiple reservations
    - Each reservation is associated with exactly one customer
4. **Reservation-Table Relationship**
    - A reservation can be for exactly one table
    - A table can be reserved multiple times (at different times)

## Basic ER Diagram

[Note: Insert your Basic ER diagram here showing entity relationships]

## Data Flow Diagrams

### DFD Level 0

[Note: Insert your Level 0 DFD here]

The Level 0 DFD represents the McDonald's Restaurant Management System as a single process interacting with external entities:

- Customers (placing orders, making reservations)
- Employees (processing orders, managing inventory)
- Suppliers (providing ingredients and supplies)
- Management (receiving reports, making decisions)

Data flows between these entities and the central system represent the major information exchanges in the restaurant operations.

### DFD Level 1

[Note: Insert your Level 1 DFD here]

The Level 1 DFD breaks down the restaurant management system into its major subsystems:

1. **Order Processing Subsystem**
    - Handles customer orders across all three transaction types
    - Manages order items, customizations, and pricing
    - Communicates orders to kitchen staff
2. **Inventory Management Subsystem**
    - Tracks ingredient stock levels
    - Processes restock requests
    - Manages supplier information
    - Updates menu item availability based on ingredient status
3. **Employee Management Subsystem**
    - Handles employee information
    - Manages roles and shift assignments
    - Tracks employee availability
4. **Customer Management Subsystem**
    - Maintains customer profiles
    - Processes reservations
    - Handles delivery information
5. **Payment Processing Subsystem**
    - Creates transactions from orders
    - Processes payments
    - Handles discounts and special offers
6. **Reporting Subsystem**
    - Generates operational reports
    - Provides management dashboards
    - Analyzes sales and inventory data

#Documentation