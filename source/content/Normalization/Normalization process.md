# Normalizing Your Restaurant Database: Pre-1NF to 3NF

I'll guide you through the normalization process starting with your unnormalized data and showing how we arrive at your specified normalized structure.

## Starting Point: Pre-1NF (Unnormalized Data)

Your unnormalized data has several issues that need addressing:

- Multi-valued attributes (Phone_Numbers, Emails, Roles)
- Composite attributes (Name, Address)
- Non-atomic values (Customer_Info, Items_Info)

## Step 1: First Normal Form (1NF)

To achieve 1NF, we need to:

- Eliminate repeating groups
- Ensure all attributes contain atomic values
- Identify primary keys

### Employees Table:

1. Split Name into First_Name and Last_Name
2. Create separate tables for Phone_Numbers and Emails
3. Create a linking table for Roles

```
Employees:
- Employee_ID (PK)
- First_Name
- Last_Name
- Status

Employee_Phones:
- Employee_ID (FK)
- Phone_Number

Employee_Emails:
- Employee_ID (FK)
- Email

Employee_Roles:
- Employee_ID (FK)
- Role_ID (FK)
```

### Customers Table:

1. Split Name into First_Name and Last_Name
2. Create separate tables for Phone_Numbers and Emails
3. Address handled through Address_ID reference

```
Customers:
- Customer_ID (PK)
- Address_ID (FK)
- First_Name
- Last_Name

Customer_Phones:
- Customer_ID (FK)
- Phone_Number

Customer_Emails:
- Customer_ID (FK)
- Email
```

### Orders Table:

1. Replace Customer_Info with Customer_ID
2. Move Items_Info to separate table

```
Orders:
- Order_ID (PK)
- Customer_ID (FK)
- Order_Date
- Order_Status
- Order_Type
- Items_Total
- Discounted_Amount
- Order_Total

Order_Items:
- Order_ID (FK)
- MenuItem_ID (FK)
- Quantity
- Item_Subtotal
```

Similar transformations for the remaining tables...

## Step 2: Second Normal Form (2NF)

To achieve 2NF, we need to:

- Ensure the database is in 1NF
- Remove partial dependencies (non-key attributes must depend on the entire primary key)

### Employee_Roles:

Already in 2NF as we've added a composite key structure.

```
Employee_Roles:
- Employee_Role_ID (PK)
- Employee_ID (FK)
- Role_ID (FK)
```

### Order_Items:

Add a dedicated primary key to uniquely identify each order item.

```
Order_Items:
- OrderItem_ID (PK)
- Order_ID (FK)
- MenuItem_ID (FK)
- Quantity
- Item_Subtotal
```

### Menu_Ingredients:

This linking table needs both keys to fully identify the relationship.

```
Menu_Ingredients:
- MenuItem_ID (FK)
- Ingredient_ID (FK)
- Quantity_Required
- Unit_Of_Measure
```

## Step 3: Third Normal Form (3NF)

To achieve 3NF, we need to:

- Ensure the database is in 2NF
- Remove transitive dependencies (non-key attributes shouldn't depend on other non-key attributes)

### Roles Table:

Extract role information to its own table.

```
Roles:
- Role_ID (PK)
- Role_Name
- Employee_Count
```

### Menu_Items:

Extract category information to its own table.

```
Menu_Items:
- MenuItem_ID (PK)
- Category_ID (FK)
- Name
- Description
- Price
- Availability

Category:
- Category_ID (PK)
- Name
```

### Stock:

Separate supplier information.

```
Stock:
- Stock_ID (PK)
- Ingredient_ID (FK)
- Stock_Level
- Supplier_ID (FK)

Supplier:
- Supplier_ID (PK)
- Address_ID (FK)
- Name
- Contact_Phone
- Contact_Email
```

### Delivery Details:

Separate service and fee information.

```
Delivery Details:
- Delivery_ID (PK)
- Order_ID (FK)
- Service_ID (FK)
- Fee_ID (FK)
- Delivery_Status

Delivery Service:
- Service_ID (PK)
- Name
- Service_Type
- Contact_Phone
- Contact_Email

Delivery_Fee:
- Fee_ID (PK)
- Fee_Amount
- Distance_Range
```

### Order_Discounts:

Create a linking table between Orders and Discounts.

```
Order_Discounts:
- Apply_ID (PK)
- Order_ID (FK)
- Discount_ID (FK)
- Applied_Amount
```

The final structure now matches your normalized design with:

- Appropriate primary keys (PK)
- Foreign key relationships (FK)
- No multi-valued attributes
- No partial dependencies
- No transitive dependencies

Each entity has been properly isolated, and relationships are clearly defined through foreign keys, exactly as shown in your normalized form.

[[Step-wise normal form]]