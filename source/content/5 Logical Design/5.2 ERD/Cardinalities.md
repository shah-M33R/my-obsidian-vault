# Cardinalities / Relationships
## Employee Management

1. **Employee to Employee_Role**: (1,N) ← (1,1)
    - An Employee must have at least one Role (1 min)
    - An Employee can have many Roles (N max)
    - Each Employee_Role record belongs to exactly one Employee (1,1)
2. **Role to Employee_Role**: (0,N) ← (1,1)
    - A Role may have no employees assigned (0 min)
    - A Role can be assigned to many employees (N max)
    - Each Employee_Role record must reference exactly one Role (1,1)
3. **Employee to Shift**: (0,N) ← (1,1)
    - An Employee may have no shifts (0 min)
    - An Employee can have many shifts (N max)
    - Each Shift must be assigned to exactly one Employee (1,1) 

## Menu and Ingredients

5. **Category to Menu_Item**: (0,N) ← (1,1)
    - A Category may have no Menu Items (0 min)
    - A Category can have many Menu Items (N max)
    - Each Menu Item must belong to exactly one Category (1,1)
6. **Menu_Item to Dish_Ingredients**: (1,N) ← (1,1)
    - A Menu Item must have at least one ingredient (1 min)
    - A Menu Item can have many ingredients (N max)
    - Each Dish_Ingredients record must belong to exactly one Menu Item (1,1)
7. **Ingredient to Dish_Ingredients**: (0,N) ← (1,1)
    - An Ingredient may not be used in any dishes (0 min)
    - An Ingredient can be used in many dishes (N max)
    - Each Dish_Ingredients record must reference exactly one Ingredient (1,1)
8. **Ingredient to Stock**: (0,N) ← (1,1)
    - An Ingredient may have no Stock records (0 min)
    - An Ingredient can have only one stock record for maintenance purposes (1  max)
    - Each Stock record must reference exactly one Ingredient (1,1)

## Order Management

9. **Customer to Order**: (0,N) ← (1,1)
    - A Customer may have placed no Orders (0 min)
    - A Customer can place many Orders (N max)
    - Each Order must belong to exactly one Customer (1,1)
10. **Order to Order_Item**: (1,N) ← (1,1)
    - An Order must contain at least one Order Item (1 min)
    - An Order can contain many Order Items (N max)
    - Each Order Item must belong to exactly one Order (1,1)
11. **Menu_Item to Order_Item**: (0,N) ← (1,1)
    - A Menu Item may not appear in any Order Items (0 min)
    - A Menu Item can appear in many Order Items (N max)
    - Each Order Item must reference exactly one Menu Item (1,1)
12. **Order to Order_Discount**: (0,N) ← (1,1)
    - An Order may have no discounts applied (0 min)
    - An Order can have multiple discounts applied (N max)
    - Each Order Discount must belong to exactly one Order (1,1)
13. **Discount to Order_Discount**: (0,N) ← (1,1)
    - A Discount may not be applied to any Orders (0 min)
    - A Discount can be applied to many Orders (N max)
    - Each Order Discount must reference exactly one Discount (1,1)

## Billing Management

14. **Order to Transaction**: (0,1) ← (1,1)
    - An Order may not have a Transaction (0 min)
    - An Order can have at most one Transaction (1 max)
    - Each Transaction must belong to exactly one Order (1,1)
15. **Transaction to Payment**: (1,N) ← (1,1)
    - A Transaction must have at least one Payment (1 min)
    - A Transaction can have multiple Payments (N max)
    - Each Payment must belong to exactly one Transaction (1,1)

## Delivery Management

16. **Order to Delivery**: (0,1) ← (1,1)
    - An Order may not have a Delivery (0 min)
    - An Order can have at most one Delivery (1 max)
    - Each Delivery must belong to exactly one Order (1,1)
17. **Delivery_Service to Delivery**: (1,N) ← (1,1)
    - A Delivery Service must handle at least one Delivery (1 min)
    - A Delivery Service can handle many Deliveries (N max)
    - Each Delivery must be handled by exactly one Delivery Service (1,1)
18. **Delivery_Fee to Delivery**: (1,N) ← (1,1)
    - A Delivery Fee must be applied to at least one Delivery (1 min)
    - A Delivery Fee can apply to many Deliveries (N max)
    - Each Delivery must have exactly one Delivery Fee applied (1,1)

## Inventory Management

19. **Ingredient to Restock_Request**: (0,N) ← (1,1)
    - An Ingredient may have no Restock Requests (0 min)
    - An Ingredient can have many Restock Requests (N max)
    - Each Restock Request must be for exactly one Ingredient (1,1)
20. **Supplier to Restock_Request**: (0,N) ← (1,1)
    - A Supplier may have received no Restock Requests (0 min)
    - A Supplier can receive many Restock Requests (N max)
    - Each Restock Request must be assigned to exactly one Supplier (1,1)
21. **Supplier to Stock**: (0,N) ← (1,1)
    - A Supplier may not be associated with any Stock records (0 min)
    - A Supplier can provide many Stock items (N max)
    - Each Stock record must be associated with exactly one Supplier (1,1)
22. **Address to Supplier**: (0,N) ← (1,1)
    - An Address may not be associated with any Suppliers (0 min)
    - An Address can be associated with many Suppliers (N max)
    - Each Supplier must have exactly one Address (1,1)

## Tables and Reservation

23. **Customer to Reservation**: (0,N) ← (1,1)
    - A Customer may have made no Reservations (0 min)
    - A Customer can make many Reservations (N max)
    - Each Reservation must belong to exactly one Customer (1,1)
24. **Table to Reservation**: (0,N) ← (1,1)
    - A Table may have no Reservations (0 min)
    - A Table can have many Reservations (N max)
    - Each Reservation must be for exactly one Table (1,1)

## Contact Management

#### **Employee – Contact**

- **Employee side**: (1,1) → Each employee must have exactly one contact.
- **Contact side**: (0,1) → Each contact belongs to at most one employee.

#### **Customer – Contact**

- **Customer side**: (1,1) → Each contact must be linked to one customer.
- **Contact side**: (0,N) → A customer can have multiple contact persons.


#### **Supplier – Contact**

- **Supplier side**: (1,1) → Each contact must be linked to one supplier.
- **Contact side**: (0,N) → A supplier can have multiple contact persons.


#### **Employee – Address**

- **Employee side**: (1,1) → Each employee must have exactly one address.
- **Address side**: (0,1) → Each address is tied to at most one employee.


#### **Customer – Address**

- **Customer side**: (1,1) → Each address must be linked to one customer.
- **Address side**: (0,N) → A customer can have multiple addresses.


#### **Supplier – Address**

- **Supplier side**: (1,1) → Each address must be linked to one supplier.
- **Address side**: (0,N) → A supplier can have multiple addresses.