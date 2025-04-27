## Normalization Process

### First Normal Form (1NF)

To achieve 1NF, we eliminated repeating groups and ensured all attributes contain atomic values:

1. **Employee Table Split**:
    - Separated composite Name attribute into First_Name and Last_Name
    - Created separate Contact table to handle multiple phone numbers and emails
    - Created Employee_Role junction table to handle multiple roles per employee
2. **Address Normalization**:
    - Created separate Address entity to handle address information for multiple entity types
    - Entity_Type attribute distinguishes between Customer, Supplier, and other address owners
3. **Order Items Separation**:
    - Separated order items into Order_Item table to eliminate repeating groups of items in orders
4. **Menu Item Ingredients**:
    - Created Dish_Ingredients junction table to handle multiple ingredients per menu item

### Second Normal Form (2NF)

To achieve 2NF, we ensured that all non-key attributes are fully dependent on the entire primary key:

1. **Order Discount Separation**:
    - Created Order_Discount junction table where each discount application is fully dependent on both Order_ID and Discount_ID
2. **Stock Management**:
    - Created separate Stock entity where stock levels are dependent on both Ingredient_ID and Supplier_ID
3. **Employee Role Junction**:
    - Created Employee_Role junction table where role assignments are dependent on both Employee_ID and Role_ID
4. **Menu Categories**:
    - Separated Category table from Menu_Item to eliminate partial dependencies

### Third Normal Form (3NF)

To achieve 3NF, we eliminated transitive dependencies:

1. **Payment Processing**:
    - Separated Payment from Transaction to eliminate dependency between Payment_Method/Status and Transaction_ID
2. **Delivery Management**:
    - Created separate Delivery_Service and Delivery_Fee tables to eliminate transitive dependencies in delivery information
3. **Address Management**:
    - Centralized address information in Address table to prevent redundancy across Customer and Supplier entities
4. **Contact Information**:
    - Centralized contact information in Contact table to eliminate redundancy and transitive dependencies

## Detecting and Resolving Anomalies

### Insertion Anomalies Resolved

1. **Before Normalization**: Could not add a new supplier without associating with at least one ingredient. **After Normalization**: Can add suppliers independently in the Supplier table.
2. **Before Normalization**: Could not add a new menu item without assigning ingredients. **After Normalization**: Can add menu items independently in the Menu_Item table.
3. **Before Normalization**: Could not add a customer without an order. **After Normalization**: Can add customers independently in the Customer table.

### Update Anomalies Resolved

1. **Before Normalization**: Updating a supplier's address required changes in multiple places. **After Normalization**: Address updated once in the Address table.
2. **Before Normalization**: Changing a menu item's price required updates across multiple orders. **After Normalization**: Price stored only in Menu_Item table.
3. **Before Normalization**: Employee contact information updates required multiple changes. **After Normalization**: Contact information centralized in Contact table.

### Deletion Anomalies Resolved

1. **Before Normalization**: Deleting an order would lose customer information. **After Normalization**: Customer information preserved independently in Customer table.
2. **Before Normalization**: Removing a menu item would lose ingredient information. **After Normalization**: Ingredient information preserved independently in Ingredient table.
3. **Before Normalization**: Deleting an employee would lose role information. **After Normalization**: Role information preserved independently in Role table.

## Finalized Entities and Attributes

### Employee Management Module

#### Employee

|Attribute|Data Type|Constraint|
|---|---|---|
|Employee_ID|VARCHAR(10)|Primary Key|
|First_Name|VARCHAR(50)|Not Null|
|Last_Name|VARCHAR(50)|Not Null|
|Status|VARCHAR(20)|Default 'Active'|

#### Role

|Attribute|Data Type|Constraint|
|---|---|---|
|Role_ID|VARCHAR(10)|Primary Key|
|Role_Name|VARCHAR(50)|Unique, Not Null|
|Employee_Count|INT|Default 0|

#### Employee_Role

|Attribute|Data Type|Constraint|
|---|---|---|
|Employee_Role_ID|VARCHAR(10)|Primary Key|
|Employee_ID|VARCHAR(10)|Foreign Key|
|Role_ID|VARCHAR(10)|Foreign Key|

#### Shift

|Attribute|Data Type|Constraint|
|---|---|---|
|Shift_ID|VARCHAR(10)|Primary Key|
|Employee_ID|VARCHAR(10)|Foreign Key|
|Shift_Start|DATETIME|Not Null|
|Shift_End|DATETIME|Not Null|
|Shift_Type|VARCHAR(20)|Not Null|

### External Information Management Module

#### Address

|Attribute|Data Type|Constraint|
|---|---|---|
|Address_ID|VARCHAR(10)|Primary Key|
|Entity_ID|VARCHAR(10)|Not Null|
|Entity_Type|VARCHAR(30)|Not Null|
|City|VARCHAR(50)|Not Null|
|Area|VARCHAR(50)|Not Null|
|Street_Name|VARCHAR(100)|Not Null|
|Street_Number|VARCHAR(20)|Nullable|
|House_Number|VARCHAR(20)|Nullable|

#### Contact

|Attribute|Data Type|Constraint|
|---|---|---|
|Contact_ID|VARCHAR(10)|Primary Key|
|Entity_ID|VARCHAR(10)|Not Null|
|Entity_Type|VARCHAR(30)|Not Null|
|Contact_Type|VARCHAR(20)|Not Null|
|Contact_Value|VARCHAR(255)|Not Null|

### Menu and Ingredients Module

#### Category

|Attribute|Data Type|Constraint|
|---|---|---|
|Category_ID|VARCHAR(10)|Primary Key|
|Name|VARCHAR(50)|Unique, Not Null|

#### Menu_Item

|Attribute|Data Type|Constraint|
|---|---|---|
|Menu_Item_ID|VARCHAR(10)|Primary Key|
|Category_ID|VARCHAR(10)|Foreign Key|
|Name|VARCHAR(100)|Unique, Not Null|
|Description|VARCHAR(255)|Nullable|
|Price|DECIMAL(10,2)|Not Null|
|Availability|VARCHAR(20)|Default 'Available'|

#### Ingredient

|Attribute|Data Type|Constraint|
|---|---|---|
|Ingredient_ID|VARCHAR(10)|Primary Key|
|Name|VARCHAR(50)|Unique, Not Null|
|Availability|VARCHAR(20)|Default 'Available'|

#### Dish_Ingredients

|Attribute|Data Type|Constraint|
|---|---|---|
|Menu_Item_ID|VARCHAR(10)|Primary Key, Foreign Key|
|Ingredient_ID|VARCHAR(10)|Primary Key, Foreign Key|
|Quantity_Required|DECIMAL(10,2)|Not Null|
|Unit_Of_Measure|VARCHAR(20)|Not Null|

### Order Management Module

#### Order

|Attribute|Data Type|Constraint|
|---|---|---|
|Order_ID|VARCHAR(10)|Primary Key|
|Customer_ID|VARCHAR(10)|Foreign Key|
|Order_Date|DATETIME|Default CURRENT_TIMESTAMP|
|Order_Status|VARCHAR(30)|Default 'Pending'|
|Order_Type|VARCHAR(20)|Not Null|
|Items_Total|DECIMAL(10,2)|Default 0.00|
|Discounted_Amount|DECIMAL(10,2)|Default 0.00|
|Order_Total|DECIMAL(10,2)|Default 0.00|

#### Order_Item

|Attribute|Data Type|Constraint|
|---|---|---|
|Order_Item_ID|VARCHAR(10)|Primary Key|
|Order_ID|VARCHAR(10)|Foreign Key|
|Menu_Item_ID|VARCHAR(10)|Foreign Key|
|Quantity|INT|Default 1|
|Item_Subtotal|DECIMAL(10,2)|Calculated Field|

#### Discount

|Attribute|Data Type|Constraint|
|---|---|---|
|Discount_ID|VARCHAR(10)|Primary Key|
|Description|VARCHAR(255)|Not Null|
|Discount_Type|VARCHAR(20)|Not Null|
|Value_Type|VARCHAR(20)|Not Null|
|Value|DECIMAL(10,2)|Not Null|

#### Order_Discount

|Attribute|Data Type|Constraint|
|---|---|---|
|Apply_ID|VARCHAR(10)|Primary Key|
|Order_ID|VARCHAR(10)|Foreign Key|
|Discount_ID|VARCHAR(10)|Foreign Key|
|Applied_Amount|DECIMAL(10,2)|Not Null|

### Billing Management Module

#### Transaction

|Attribute|Data Type|Constraint|
|---|---|---|
|Transaction_ID|VARCHAR(10)|Primary Key|
|Order_ID|VARCHAR(10)|Foreign Key, Unique|
|Order_Total|DECIMAL(10,2)|Not Null|
|Delivery_Fee|DECIMAL(10,2)|Default 0.00|
|Transaction_Fee|DECIMAL(10,2)|Default 0.00|
|Final_Amount|DECIMAL(10,2)|Not Null|

#### Payment

|Attribute|Data Type|Constraint|
|---|---|---|
|Payment_ID|VARCHAR(10)|Primary Key|
|Transaction_ID|VARCHAR(10)|Foreign Key|
|Final_Amount|DECIMAL(10,2)|Not Null|
|Payment_Method|VARCHAR(30)|Not Null|
|Payment_Status|VARCHAR(20)|Default 'Pending'|

### Delivery Management Module

#### Delivery_Service

|Attribute|Data Type|Constraint|
|---|---|---|
|Service_ID|VARCHAR(10)|Primary Key|
|Name|VARCHAR(100)|Unique, Not Null|
|Service_Type|VARCHAR(20)|Not Null|

#### Delivery_Fee

|Attribute|Data Type|Constraint|
|---|---|---|
|Fee_ID|VARCHAR(10)|Primary Key|
|Fee_Amount|DECIMAL(10,2)|Not Null|
|Distance_Range|VARCHAR(50)|Not Null|

#### Delivery

|Attribute|Data Type|Constraint|
|---|---|---|
|Delivery_ID|VARCHAR(10)|Primary Key|
|Order_ID|VARCHAR(10)|Foreign Key, Unique|
|Service_ID|VARCHAR(10)|Foreign Key|
|Fee_ID|VARCHAR(10)|Foreign Key|
|Delivery_Status|VARCHAR(20)|Default 'Pending'|

### Inventory Management Module

#### Supplier

|Attribute|Data Type|Constraint|
|---|---|---|
|Supplier_ID|VARCHAR(10)|Primary Key|
|Address_ID|VARCHAR(10)|Foreign Key|
|Name|VARCHAR(50)|Unique, Not Null|

#### Stock

|Attribute|Data Type|Constraint|
|---|---|---|
|Stock_ID|VARCHAR(10)|Primary Key|
|Ingredient_ID|VARCHAR(10)|Foreign Key|
|Supplier_ID|VARCHAR(10)|Foreign Key|
|Stock_Level|DECIMAL(10,2)|Not Null|

#### Restock_Request

|Attribute|Data Type|Constraint|
|---|---|---|
|Restock_ID|VARCHAR(10)|Primary Key|
|Ingredient_ID|VARCHAR(10)|Foreign Key|
|Supplier_ID|VARCHAR(10)|Foreign Key|
|Quantity_Requested|DECIMAL(10,2)|Not Null|
|Requested_Date|DATE|Default CURRENT_DATE|
|Request_Status|VARCHAR(20)|Default 'Pending'|
|Expected_Arrival|DATE|Nullable|

### Tables and Reservation Module

#### Table

|Attribute|Data Type|Constraint|
|---|---|---|
|Table_ID|VARCHAR(10)|Primary Key|
|Capacity|INT|Not Null|
|Availability|VARCHAR(20)|Default 'Available'|

#### Reservation

|Attribute|Data Type|Constraint|
|---|---|---|
|Res_ID|VARCHAR(10)|Primary Key|
|Customer_ID|VARCHAR(10)|Foreign Key|
|Table_ID|VARCHAR(10)|Foreign Key|
|Res_Date|DATE|Not Null|
|Res_Time|TIME|Not Null|
|Request_Status|VARCHAR(20)|Default 'Pending'|

### Customer Management Module

#### Customer

|Attribute|Data Type|Constraint|
|---|---|---|
|Customer_ID|VARCHAR(10)|Primary Key|
|Address_ID|VARCHAR(50)|Foreign Key|
|First_Name|VARCHAR(50)|Not Null|
|Last_Name|VARCHAR(50)|Not Null|

## Advanced ERD (MySQL Workbench)

[Note: Insert your Advanced ERD here showing cardinalities and all relationships]

#Documentation