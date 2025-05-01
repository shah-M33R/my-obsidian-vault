
# Original Unnormalized Data Structure

### Identifying Anomalies in Unnormalized Form

1. **Repeating Groups**:
    
    - Employee data contained multiple contact details (phone numbers, emails)
    - Menu items contained multiple ingredients
    - Orders contained multiple menu items
    - Multiple payment methods could be associated with a single order
2. **Insertion Anomalies**:
    
    - Cannot add a new menu item without associating it with an order
    - Cannot add a supplier without associating it with at least one ingredient
    - Cannot add a role until an employee is assigned to it
3. **Update Anomalies**:
    
    - Updating a supplier's address requires changes in multiple records
    - Updating a menu item's price requires changes across all orders containing that item
    - Changing an employee's role requires updates in multiple tables
4. **Deletion Anomalies**:
    
    - Deleting an order would lose information about menu items ordered
    - Removing an employee would lose role definition information
    - Deleting a customer might lose address information that could be shared

# First Normal Form (1NF)

### Applying 1NF:

1. Eliminate repeating groups by creating separate tables
2. Create a separate column for each value
3. Identify each record with a unique identifier (primary key)

### Specific 1NF Changes:

1. **Employee Contact Information**:
    
    - Created separate `Contact` table with attributes:
        - Contact_ID (PK)
        - Entity_ID (Employee_ID)
        - Entity_Type (value: "Employee")
        - Contact_Type (phone, email, etc.)
        - Contact_Value (the actual phone number or email)
2. **Menu Items and Ingredients**:
    
    - Created `Dish_Ingredients` junction table with attributes:
        - Menu_Item_ID (PK, FK)
        - Ingredient_ID (PK, FK)
        - Quantity_Required
        - Unit_Of_Measure
3. **Order Items**:
    
    - Created `Order_Item` table with attributes:
        - Order_Item_ID (PK)
        - Order_ID (FK)
        - Menu_Item_ID (FK)
        - Quantity
        - Item_Subtotal
4. **Employee Roles**:
    
    - Created `Employee_Role` junction table with attributes:
        - Employee_Role_ID (PK)
        - Employee_ID (FK)
        - Role_ID (FK)

### Remaining Anomalies After 1NF:

1. **Partial Dependencies**:
    
    - In `Dish_Ingredients`, item preparation instructions depend only on Menu_Item_ID, not the full PK
    - In `Order_Item`, item price depends only on Menu_Item_ID, not on Order_ID
2. **Update Anomalies**:
    
    - Menu item price still duplicated across multiple order items
    - Employee information duplicated across multiple role assignments
3. **Deletion Anomalies**:
    
    - Removing all orders for a customer would still lose customer data
    - Removing all order items with a specific menu item would lose menu item details

# Second Normal Form (2NF)

### Applying 2NF:

1. Meet all requirements of 1NF
2. Remove partial dependencies by ensuring non-key attributes depend on the entire primary key

### Specific 2NF Changes:

1. **Menu Items and Pricing**:
    
    - Created separate `Menu_Item` table with:
        - Menu_Item_ID (PK)
        - Category_ID (FK)
        - Name
        - Description
        - Price
        - Availability
    - `Order_Item` now references Menu_Item_ID and calculates Item_Subtotal based on Menu_Item price
2. **Role Management**:
    
    - Enhanced `Role` table with:
        - Role_ID (PK)
        - Role_Name
        - Employee_Count (derived attribute)
    - `Employee_Role` junction table now only contains the relationship information
3. **Discount Application**:
    
    - Created `Discount` table with:
        - Discount_ID (PK)
        - Description
        - Discount_Type
        - Value_Type
        - Value
    - Created `Order_Discount` junction table with:
        - Apply_ID (PK)
        - Order_ID (FK)
        - Discount_ID (FK)
        - Applied_Amount

### Remaining Anomalies After 2NF:

1. **Transitive Dependencies**:
    
    - Customer contact information depends on Customer_ID, which depends on Order_ID
    - Supplier address depends on Supplier_ID, not directly on ingredient stock levels
    - Delivery fee calculation depends on distance range, not directly on delivery ID
2. **Update Anomalies**:
    
    - Address information potentially duplicated across customers and suppliers
    - Transaction details redundantly stored with payment information
3. **Deletion Anomalies**:
    
    - Removing a transaction record could lose payment method information
    - Removing supplier could lose address information

# Third Normal Form (3NF)

### Applying 3NF:

1. Meet all requirements of 2NF
2. Remove transitive dependencies by ensuring all non-key attributes depend directly on the primary key

### Specific 3NF Changes:

1. **Address Management**:
    
    - Created centralized `Address` table with:
        - Address_ID (PK)
        - Entity_ID (FK)
        - Entity_Type
        - City
        - Area
        - Street_Name
        - Street_Number
        - House_Number
    - Customer and Supplier tables now reference Address_ID
2. **Payment Processing**:
    
    - Separated `Transaction` and `Payment` tables:
        - Transaction contains order total, fees, and final amount
        - Payment contains payment method, status, and links to Transaction_ID
3. **Delivery Management**:
    
    - Created separate tables:
        - `Delivery_Service` with service details
        - `Delivery_Fee` with fee structures by distance
        - `Delivery` table linking orders to services and fee structures
4. **Stock Management**:
    
    - Created `Stock` table:
        - Stock_ID (PK)
        - Ingredient_ID (FK)
        - Supplier_ID (FK)
        - Stock_Level

### Anomalies Resolved in 3NF:

1. **Insertion Anomalies Resolved**:
    
    - Can add suppliers, customers, employees, roles, ingredients, and menu items independently
    - Can add new discount types without applying them to any order
    - Can register new delivery services before assigning deliveries
2. **Update Anomalies Resolved**:
    
    - Addresses updated in one place through Address table
    - Menu item prices updated once in Menu_Item table
    - Employee details updated once in Employee table
    - Role definitions maintained separately from employee assignments
3. **Deletion Anomalies Resolved**:
    
    - Deleting orders doesn't affect customer information
    - Removing menu items doesn't affect ingredient information
    - Deleting employees doesn't affect role definitions
    - Removing transactions doesn't lose payment method types

# Final Database Structure

The final database structure achieves 3NF normalization with properly separated entities, clear relationships, eliminated redundancies, and protection against the three types of anomalies. The structure allows for:

1. Independent management of core business entities
2. Flexible relationship modeling through junction tables
3. Centralized management of common attributes like addresses and contacts
4. Proper historical tracking of transactions and orders
5. Scalable inventory and stock management

#Documentation