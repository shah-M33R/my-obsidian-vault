## Step 1: Identify Core Entities and Apply 1NF

### First Normal Form (1NF) Rules:

- Each table cell should contain a single value
- Each record needs to be unique
- No repeating groups or arrays

### Analysis and Transformation:

#### Employees:

**Anomalies in core entity:**

- Repeating groups: Multiple phone numbers and emails
- The "Roles" attribute contains multiple values

**Applied 1NF:**

```
Employees:
- Employee_ID (PK)
- First_Name
- Last_Name
- Status

Employee_Phones:
- Employee_Phone_ID (PK)
- Employee_ID (FK)
- Phone_Number

Employee_Emails:
- Employee_Email_ID (PK)
- Employee_ID (FK)
- Email

Employee_Roles:
- Employee_Role_ID (PK)
- Employee_ID (FK)
- Role_Name
```

#### Customers:

**Anomalies in core entity:**

- Repeating groups: Multiple phone numbers and emails
- "Full Address" contains multiple atomic values

**Applied 1NF:**

```
Customers:
- Customer_ID (PK)
- First_Name
- Last_Name
- Address_ID (FK)

Customer_Phones:
- Customer_Phone_ID (PK)
- Customer_ID (FK)
- Phone_Number

Customer_Emails:
- Customer_Email_ID (PK)
- Customer_ID (FK)
- Email
```

#### Orders:

**Anomalies in core entity:**

- "Customer_Info" contains multiple values
- "Items_Info" contains multiple values

**Applied 1NF:**

```
Orders:
- Order_ID (PK)
- Customer_ID (FK)
- Order_Date
- Order_Status
- Order_Type
- Discounted_Amount
- Order_Total

Order_Items:
- Order_Item_ID (PK)
- Order_ID (FK)
- Menu_Item_ID (FK)
- Quantity
- Item_Subtotal
```

#### Menu_Items:

**Anomalies in core entity:**

- "Category" contains a non-atomic value

**Applied 1NF:**

```
Menu_Items:
- MenuItem_ID (PK)
- Category_ID (FK)
- Name
- Description
- Price
- Availability

Categories:
- Category_ID (PK)
- Name
```

#### Ingredients:

**Anomalies in core entity:**

- "Menu_Items" contains multiple values

**Applied 1NF:**

```
Ingredients:
- Ingredient_ID (PK)
- Name
- Availability

Menu_Ingredients:
- Menu_Ingredient_ID (PK)
- MenuItem_ID (FK)
- Ingredient_ID (FK)
- Quantity_Required
```

#### Stock:

**Anomalies in core entity:**

- "Ingredient_Info" contains multiple values
- "Supplier_Info" contains multiple values

**Applied 1NF:**

```
Stock:
- Stock_ID (PK)
- Ingredient_ID (FK)
- Stock_Level
- Supplier_ID (FK)
```

#### Supplier:

**Anomalies in core entity:**

- "Phone_Number" and "Email" need to be separate attributes
- "Address" contains multiple values

**Applied 1NF:**

```
Supplier:
- Supplier_ID (PK)
- Name
- Phone_Number
- Email
- Address_ID (FK)
```

#### Addresses:

**Adding proper structure:**

```
Addresses:
- Address_ID (PK)
- Street_Number
- Street_Name
- Area
- City
- Postal_Code
- Country
```

## Step 2: Apply 2NF

### Second Normal Form (2NF) Rules:

- Must be in 1NF
- All non-key attributes must depend on the entire primary key

### Analysis and Transformation:

#### Employee_Roles:

**Anomalies:**

- If we're tracking role details, they would be duplicated across employees

**Applied 2NF:**

```
Roles:
- Role_ID (PK)
- Role_Name
- Description

Employee_Roles:
- Employee_Role_ID (PK)
- Employee_ID (FK)
- Role_ID (FK)
```

#### Order_Items:

**Anomalies:**

- Item price information would be duplicated across orders

**Applied 2NF:**

```
Order_Items:
- Order_Item_ID (PK)
- Order_ID (FK)
- Menu_Item_ID (FK)
- Quantity
- Item_Subtotal
```

(Menu_Items already contains price information)

#### Menu_Ingredients:

**Anomalies:**

- No issues found, as the table depends on both parts of the composite key

#### Restock_Request:

**Anomalies:**

- "Ingredients" and "Supplier" contain multiple values

**Applied 2NF:**

```
Restock_Request:
- Restock_ID (PK)
- Ingredient_ID (FK)
- Supplier_ID (FK)
- Quantity_Requested
- Requested_Date
- Request_Status
- Expected_Arrival_Date
```

#### Delivery_Details:

**Anomalies:**

- "Order", "Service", and "Fee" contain multiple values

**Applied 2NF:**

```
Delivery_Details:
- Delivery_ID (PK)
- Order_ID (FK)
- Service_ID (FK)
- Fee_ID (FK)
- Delivery_Status
```

#### Reservation_Requests:

**Anomalies:**

- "Customer" and "Table" contain multiple values

**Applied 2NF:**

```
Reservation_Requests:
- Res_ID (PK)
- Customer_ID (FK)
- Table_ID (FK)
- Res_Date
- Res_Time
- Request_Status
```

## Step 3: Apply 3NF

### Third Normal Form (3NF) Rules:

- Must be in 2NF
- No transitive dependencies (non-key attributes depending on other non-key attributes)

### Analysis and Transformation:

#### Orders:

**Anomalies:**

- "Order_Total" is calculated from other fields (transitive dependency)

**Applied 3NF:**

```
Orders:
- Order_ID (PK)
- Customer_ID (FK)
- Order_Date
- Order_Status
- Order_Type
```

#### Order_Items:

**Anomalies:**

- "Item_Subtotal" is calculated from quantity and menu item price

**Applied 3NF:**

```
Order_Items:
- Order_Item_ID (PK)
- Order_ID (FK)
- Menu_Item_ID (FK)
- Quantity
```

#### Stock:

**Anomalies:**

- Supplier information is indirectly related to stock

**Applied 3NF:**

```
Stock:
- Stock_ID (PK)
- Ingredient_ID (FK)
- Stock_Level

Ingredient_Suppliers:
- Ingredient_Supplier_ID (PK)
- Ingredient_ID (FK)
- Supplier_ID (FK)
- Is_Primary_Supplier
```

#### Transactions:

**Anomalies:**

- "Total_Info" contains calculated values

**Applied 3NF:**

```
Transactions:
- Transaction_ID (PK)
- Order_ID (FK)
- Transaction_Date
- Transaction_Status

Order_Totals:
- Order_ID (PK)
- Items_Total
- Discounted_Amount
- Delivery_Fee
- Tax_Amount
- Order_Total
```

#### Delivery_Service:

**Anomalies:**

- "Contact" contains multiple values

**Applied 3NF:**

```
Delivery_Service:
- Service_ID (PK)
- Name
- Service_Type

Service_Contacts:
- Contact_ID (PK)
- Service_ID (FK)
- Contact_Type
- Contact_Value
```


[[Anomalies]]