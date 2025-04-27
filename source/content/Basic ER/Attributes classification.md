
# Entity and Attribute Classification

## Strong Entities

Strong entities have independent existence and can be identified uniquely by their attributes:

1. Employees
2. Customers
3. Menu_Items
4. Ingredients
5. Supplier
6. Delivery Service
7. Tables
8. Discounts

## Weak Entities

Weak entities depend on the existence of other entities and cannot be uniquely identified by their attributes alone:

1. Shifts (dependent on Employees)
2. Orders (dependent on Customers)
3. Stock (dependent on Ingredients)
4. Restock Request (dependent on Ingredients and Supplier)
5. Delivery Details (dependent on Orders)
6. Reservation Requests (dependent on Customers and Tables)
7. Transactions (dependent on Orders)
8. Payments (dependent on Transactions)

## Attribute Classifications

### Simple Attributes

Single-valued attributes that cannot be divided further:

- Employee_ID, Status
- Shift_ID, Shift_Start, Shift_End, Shift_Type
- Customer_ID, Address_ID, Name
- Order_ID, Order_Date, Order_Status, Order_Type, Discounted_Amount, Order_Total
- MenuItem_ID, Category, Name, Description, Price, Availability
- Ingredient_ID, Name, Availability
- Stock_ID, Stock_Level
- Supplier_ID, Name
- Restock_ID, Quantity_Requested, Requested_Date, Request_Status, Expected_Arrival_Date
- Delivery_ID, Fee, Delivery_Status
- Service_ID, Name, Service_Type
- Table_ID, Capacity, Availability
- Res_ID, Res_Date, Res_Time, Request_Status
- Discount_ID, Description, Discount_Type, Value_Type, Value
- Transaction_ID, Total_Info
- Payment_ID, Final_Amount, Payment_Method, Payment_Status

### Composite Attributes

Attributes that can be divided into smaller sub-attributes:

- Full Address (composed of street, city, state, zip code)
- Contact (likely composed of name, phone, email)

### Multi-valued Attributes

Attributes that can have multiple values for a single entity:

- Phone_Numbers (for Employees, Customers, and potentially Suppliers)
- Emails (for Employees, Customers, and potentially Suppliers)
- Roles (for Employees)

### Derived Attributes

Attributes whose values can be calculated from other attributes:

- Order_Total (derived from sum of Items_Info prices minus Discounted_Amount)
- Total_Info (likely derived from Order_Total and other fees)

### Relationship Attributes

These appear to represent relationships between entities rather than direct attributes:

- Employee (in Shifts)
- Customer_Info (in Orders)
- Items_Info (in Orders)
- Menu_Items (in Ingredients)
- Ingredient_Info (in Stock)
- Supplier_Info (in Stock)
- Ingredients (in Restock Request)
- Supplier (in Restock Request)
- Order (in Delivery Details)
- Service (in Delivery Details)
- Customer (in Reservation Requests)
- Table (in Reservation Requests)
- Order_ID (in Transactions)
- Transaction_ID (in Payments)

# Attribute Classification by Entity

## Employees

- Employee_ID: Simple, PK
- Name: Simple
- Phone_Numbers: Multi-valued
- Emails: Multi-valued
- Roles: Multi-valued
- Status: Simple

## Shifts

- Shift_ID: Simple, PK
- Employee_ID: Simple, FK
- Shift_Start: Simple
- Shift_End: Simple
- Shift_Type: Simple

## Customers

- Customer_ID: Simple, PK
- Name: Simple
- Phone_Numbers: Multi-valued
- Emails: Multi-valued
- Full Address: Composite

## Orders

- Order_ID: Simple, PK
- Customer_ID: Simple, FK
- Order_Date: Simple
- Order_Status: Simple
- Order_Type: Simple
- Items_Info: Multi-valued, FK
- Discounted_Amount: Simple
- Order_Total: Derived

## Menu_Items

- MenuItem_ID: Simple, PK
- Category: Simple
- Name: Simple
- Description: Simple
- Price: Simple
- Availability: Simple

## Ingredients

- Ingredient_ID: Simple, PK
- Name: Simple
- Availability: Simple
- Menu_Items: Multi-valued, FK

## Stock

- Stock_ID: Simple, PK
- Ingredient_Info: Simple, FK
- Stock_Level: Simple
- Supplier_Info: Simple, FK

## Supplier

- Supplier_ID: Simple, PK
- Name: Simple
- Phone_Number: Simple
- Email: Simple
- Address: Composite

## Restock Request

- Restock_ID: Simple, PK
- Ingredients: Multi-valued, FK
- Supplier: Simple, FK
- Quantity_Requested: Simple
- Request_Date: Simple
- Request_Status: Simple
- Expected_Arrival: Simple

## Delivery

- Delivery_ID: Simple, PK
- Order: Simple, FK
- Service: Simple, FK
- Fee: Simple
- Delivery_Status: Simple

## Delivery Service

- Service_ID: Simple, PK
- Name: Simple
- Service_Type: Simple
- Contact: Composite

## Tables

- Table_ID: Simple, PK
- Capacity: Simple
- Availability: Simple

## Reservations

- Res_ID: Simple, PK
- Customer: Simple, FK
- Table: Simple, FK
- Res_Date: Simple
- Res_Time: Simple
- Request_Status: Simple

## Discounts

- Discount_ID: Simple, PK
- Description: Simple
- Discount_Type: Simple
- Value_Type: Simple
- Value: Simple

## Transactions

- Transaction_ID: Simple, PK
- Order_ID: Simple, FK
- Total_Info: Derived

## Payments

- Payment_ID: Simple, PK
- Transaction_ID: Simple, FK
- Final_Amount: Simple
- Payment_Method: Simple
- Payment_Status: Simple

[[Core Relationships]]