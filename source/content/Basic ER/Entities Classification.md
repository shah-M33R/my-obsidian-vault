# Entities:

- **Employee_Roles**
    - **Employee_Role_ID** is unique, but it depends on **Employee_ID** (from **Employees**) and **Role_ID** (from **Roles**) for identification. It cannot exist without these two strong entities.
- **Shifts**
    - **Shift_ID** depends on **Employee_ID** (from **Employees**) for identification. A shift cannot exist without a specific employee.
- **Addresses**
    - **Address_ID** is a weak entity that depends on the **Customer_ID** (from **Customers**) and can be considered part of the customer entity. An address doesn't have meaning without its customer context.
- **Order-Items**
    - **OrderItem_ID** depends on **Order_ID** (from **Orders**) for identification. An order item cannot exist without an associated order.
- **Menu_Ingredients**
    - **MenuItem_ID** (from **Menu_Items**) and **Ingredient_ID** (from **Ingredients**) form a composite key. This entity is dependent on both **Menu_Items** and **Ingredients**.
- **Restock Request**
    - **Restock_ID** depends on **Ingredient_ID** (from **Ingredients**) and **Supplier_ID** (from **Supplier**) for identification. It cannot exist without both entities.
- **Delivery Details**
    - **Delivery_ID** depends on **Order_ID** (from **Orders**) for identification. It is a weak entity since it depends on the existence of an order.
- **Order_Discounts**
    - **Apply_ID** depends on **Order_ID** (from **Orders**) and **Discount_ID** (from **Discounts**) for identification. It cannot exist without both an order and a discount.
- **Reservation Requests**
    - **Res_ID** depends on **Customer_ID** (from **Customers**) and **Table_ID** (from **Tables**) for identification. It cannot exist without both a customer and a table.
- **Delivery Fee**
    - **Fee_ID** depends on **Service_ID** (from **Delivery Service**) for identification. A delivery fee is tied to the service it is associated with.

[[Attributes classification]]