# Employees:

- Employee_ID
- Name
    - First
    - Last
- Status

# Roles:

- Role_ID
- Role_Name
- Employee_Count

# Employee_Roles:

- Employee_Role_ID
- Employee_ID
- Role_ID

# Shifts:

- Shift_ID
- Employee_ID
- Shift_Start
- Shift_End
- Shift_Type

# Customers:

- Customer_ID
- Address_ID
- Name
    - First
    - Last

# Addresses:

- Address_ID
- City
- Area/District
- Street_Name
- Street_Number
- Apartment/Unit/House_Number

# Contacts:
- Contact_ID 
- Entity_ID (FK to Employee, Customer, or Supplier) 
- Entity_Type (Employee, Customer, Supplier) 
- Contact_Type (Phone, Email, etc.) 
- Contact_Value 

# Orders:

- Order_ID
- Customer_ID
- Order_Date
- Order_Status (Pending, Preparing, Ready for Pickup/Delivery, Completed, Cancelled)
- Order_Type (Dine-in, Drive-Thru, Delivery)
- Items_Total
- Discounted_Amount
- Order_Total

# Order-Items:

- Order_Item_ID
- Order_ID
- MenuItem_ID
- Quantity
- Item_Subtotal

# Menu_Items:

- Menu_Item_ID
- Category_ID
- Name
- Description
- Price
- Availability

# Category:

- Category_ID
- Name

# Ingredients:

- Ingredient_ID
- Name
- Availability

# Dish_Ingredients:

- Menu_Item_ID
- Ingredient_ID
- Quantity_Required
- Unit_Of_Measure

# Stock:

- Stock_ID
- Ingredient_ID
- Stock_Level
- Supplier_ID

# Supplier:

- Supplier_ID
- Address_ID
- Name

# Restock Request:

- Restock_ID
- Ingredient_ID
- Supplier_ID
- Quantity_Requested
- Requested_Date
- Request_Status (Pending, Approved, Scheduled, Cancelled)
- Expected_Arrival

# Delivery:

- Delivery_ID
- Order_ID
- Service_ID
- Fee_ID
- Delivery_Status (Assigned, Picked Up, In Transit, Delivered, Failed)

# Delivery Service:

- Service_ID
- Name
- Service_Type (Third-Party or In-House)
- Contact (For third-Party)
    - Phone_Number
    - Email

# Delivery Fee:

- Fee_ID
- Fee_Amount
- Distance_Range

# Tables:

- Table_ID
- Capacity
- Availability

# Reservation Requests:

- Res_ID
- Customer_ID
- Table_ID
- Res_Date
- Res_Time
- Request_Status

# Discounts:

- Discount_ID
- Description
- Discount_Type (Order, Delivery)
- Value_Type (Fixed, Percentage)
- Value

# Order_Discounts:

- Apply_ID
- Order_ID
- Discount_ID
- Applied_Amount

# Transactions:

- Transaction_ID
- Order_ID
- Order_Total
- Delivery_Fee
- Transaction_Fee
- Final_Amount

# Payments:

- Payment_ID
- Transaction_ID
- Final_Amount
- Payment_Method
- Payment_Status

#Stages