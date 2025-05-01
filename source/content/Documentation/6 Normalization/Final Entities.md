# Final Database Structure

The final database structure achieves 3NF normalization with properly separated entities, clear relationships, eliminated redundancies, and protection against the three types of anomalies. The structure allows for:

1. Independent management of core business entities
2. Flexible relationship modeling through junction tables
3. Centralized management of common attributes like addresses and contacts
4. Proper historical tracking of transactions and orders
5. Scalable inventory and stock management
## Employee Management Module

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

## External Information Management Module

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

## Menu and Ingredients Module

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

## Order Management Module

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

## Billing Management Module

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

## Delivery Management Module

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

## Inventory Management Module

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

## Tables and Reservation Module

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

## Customer Management Module

#### Customer

|Attribute|Data Type|Constraint|
|---|---|---|
|Customer_ID|VARCHAR(10)|Primary Key|
|Address_ID|VARCHAR(50)|Foreign Key|
|First_Name|VARCHAR(50)|Not Null|
|Last_Name|VARCHAR(50)|Not Null|
