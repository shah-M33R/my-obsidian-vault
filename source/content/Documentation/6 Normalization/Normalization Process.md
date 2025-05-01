# First Normal Form (1NF)

**Goal**: Eliminate repeating groups and ensure atomic values

#### Identified 1NF Violations:

- Multivalued attributes in Employee and Customer entities
- Non-atomic addresses across multiple entities
- Multiple items per order
- Multiple ingredients per menu item
- Multiple roles per employee

#### 1NF Resolution Steps:

1. **Employee Data Restructuring**:
    
    - Split composite Name attribute into First_Name and Last_Name
    - Created `Contact` table to handle multiple contact points:
        
        ```
        Contact (Contact_ID, Entity_ID, Entity_Type, Contact_Type, Contact_Value)
        ```
        
    - Created `Employee_Role` junction table:
        
        ```
        Employee_Role (Employee_Role_ID, Employee_ID, Role_ID)
        ```
        
2. **Address Centralization**:
    
    - Created unified `Address` entity:
        
        ```
        Address (Address_ID, Entity_ID, Entity_Type, City, Area, Street_Name, Street_Number, House_Number)
        ```
        
    - Entity_Type indicates whether address belongs to Customer, Supplier, etc.
3. **Order Items Separation**:
    
    - Created `Order_Item` table:
        
        ```
        Order_Item (Order_Item_ID, Order_ID, Menu_Item_ID, Quantity, Item_Subtotal)
        ```
        
4. **Menu Item Ingredients Junction**:
    
    - Created `Dish_Ingredients` junction table:
        
        ```
        Dish_Ingredients (Menu_Item_ID, Ingredient_ID, Quantity_Required, Unit_Of_Measure)
        ```
        

#### Remaining Anomalies After 1NF:

- Partial dependencies in junction tables
- Menu item price duplicated across order items
- Employee information duplicated across role assignments
- Customer data lost if all orders are deleted
- Menu item details lost if all linked orders are removed

# Second Normal Form (2NF)

**Goal**: Remove partial dependencies by ensuring non-key attributes depend on the entire primary key

#### Identified 2NF Violations:

- Menu item attributes dependent on only part of composite keys
- Stock information dependent on partial keys
- Discount information applied partially to orders
- Employee information duplicated across role assignments

#### 2NF Resolution Steps:

1. **Menu Item Restructuring**:
    
    - Enhanced `Menu_Item` table:
        
        ```
        Menu_Item (Menu_Item_ID, Category_ID, Name, Description, Price, Availability)
        ```
        
    - Created separate `Category` table:
        
        ```
        Category (Category_ID, Name)
        ```
        
    - Order_Item now references Menu_Item_ID for pricing
2. **Role Management Enhancement**:
    
    - Improved `Role` table:
        
        ```
        Role (Role_ID, Role_Name, Employee_Count)
        ```
        
    - Employee_Role junction now contains only relationship information
3. **Discount Application Separation**:
    
    - Created standalone `Discount` table:
        
        ```
        Discount (Discount_ID, Description, Discount_Type, Value_Type, Value)
        ```
        
    - Created `Order_Discount` junction table:
        
        ```
        Order_Discount (Apply_ID, Order_ID, Discount_ID, Applied_Amount)
        ```
        
4. **Stock Management Improvement**:
    
    - Created proper `Stock` entity:
        
        ```
        Stock (Stock_ID, Ingredient_ID, Supplier_ID, Stock_Level)
        ```
        

#### Remaining Anomalies After 2NF:

- Customer contact information dependent on Customer_ID, not directly on Order_ID
- Supplier address dependent on Supplier_ID, not directly on ingredient stocks
- Delivery fee calculation dependent on distance range, not directly on delivery ID
- Address information duplicated across multiple entities
- Transaction details redundantly stored with payment information

# Third Normal Form (3NF)

**Goal**: Remove transitive dependencies by ensuring non-key attributes depend only on the primary key

#### Identified 3NF Violations:

- Address information transitively dependent through customer or supplier ID
- Payment details transitively dependent through transaction ID
- Delivery information transitively dependent through multiple relationships
- Fee structures transitively dependent on delivery service

#### 3NF Resolution Steps:

1. **Address Management Centralization**:
    
    - Finalized `Address` table structure with clear entity references
    - Updated Customer and Supplier tables to reference Address_ID
    - Eliminated address redundancy across entities
2. **Payment Processing Separation**:
    
    - Split into `Transaction` and `Payment` tables:
        
        ```
        Transaction (Transaction_ID, Order_ID, Order_Total, Delivery_Fee, Transaction_Fee, Final_Amount)
        Payment (Payment_ID, Transaction_ID, Final_Amount, Payment_Method, Payment_Status)
        ```
        
3. **Delivery System Restructuring**:
    
    - Created specialized tables:
        
        ```
        Delivery_Service (Service_ID, Name, Service_Type)
        Delivery_Fee (Fee_ID, Fee_Amount, Distance_Range)
        Delivery (Delivery_ID, Order_ID, Service_ID, Fee_ID, Delivery_Status)
        ```
        
4. **Contact Information Centralization**:
    
    - Finalized `Contact` table for all entity types
    - Eliminated contact redundancy across the database
