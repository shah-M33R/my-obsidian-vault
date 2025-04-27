## Employee Management

1. **Employee - Employee_Role**
    - Employee → Employee_Role: CASCADE
    - Employee_Role → Employee: RESTRICT
    - _Rationale_: When an employee is deleted, all their role assignments should be removed. However, an employee role record should prevent deletion of the reference role.
2. **Role - Employee_Role**
    - Role → Employee_Role: RESTRICT
    - Employee_Role → Role: RESTRICT
    - _Rationale_: A role that is assigned to employees should not be deletable.
3. **Employee - Shift**
    - Employee → Shift: RESTRICT
    - Shift → Employee: RESTRICT
    - _Rationale_: Employees with assigned shifts should not be deletable; historical shift records should be preserved.

## Customer Management

4. **Address - Customer**
    - Address → Customer: RESTRICT
    - Customer → Address: RESTRICT
    - _Rationale_: An address used by customers should not be deletable, and customers with valid addresses should be preserved.

## Menu and Ingredients

5. **Category - Menu_Item**
    - Category → Menu_Item: RESTRICT
    - Menu_Item → Category: RESTRICT
    - _Rationale_: Categories with menu items should not be deletable.
6. **Menu_Item - Dish_Ingredients**
    - Menu_Item → Dish_Ingredients: CASCADE
    - Dish_Ingredients → Menu_Item: RESTRICT
    - _Rationale_: When a menu item is deleted, its ingredient requirements should be removed.
7. **Ingredient - Dish_Ingredients**
    - Ingredient → Dish_Ingredients: RESTRICT
    - Dish_Ingredients → Ingredient: RESTRICT
    - _Rationale_: Ingredients used in dishes should not be deletable.
8. **Ingredient - Stock**
    - Ingredient → Stock: CASCADE
    - Stock → Ingredient: RESTRICT
    - _Rationale_: When an ingredient is deleted (which should only happen if not used in dishes), its stock records should be removed.

## Order Management

9. **Customer - Order**
    - Customer → Order: RESTRICT
    - Order → Customer: RESTRICT
    - _Rationale_: Customers with orders should not be deletable for financial history.
10. **Order - Order_Item**
    - Order → Order_Item: CASCADE
    - Order_Item → Order: RESTRICT
    - _Rationale_: When an order is deleted, all its items should be removed.
11. **Menu_Item - Order_Item**
    - Menu_Item → Order_Item: RESTRICT
    - Order_Item → Menu_Item: RESTRICT
    - _Rationale_: Menu items referenced in orders should not be deletable.
12. **Order - Order_Discount**
    - Order → Order_Discount: CASCADE
    - Order_Discount → Order: RESTRICT
    - _Rationale_: When an order is deleted, its discount applications should be removed.
13. **Discount - Order_Discount**
    - Discount → Order_Discount: RESTRICT
    - Order_Discount → Discount: RESTRICT
    - _Rationale_: Discounts used in orders should not be deletable for financial history.

## Billing Management

14. **Order - Transaction**
    - Order → Transaction: CASCADE
    - Transaction → Order: RESTRICT
    - _Rationale_: When an order is deleted, its transaction should be removed (though orders with transactions should typically be preserved).
15. **Transaction - Payment**
    - Transaction → Payment: CASCADE
    - Payment → Transaction: RESTRICT
    - _Rationale_: When a transaction is deleted, its payment records should be removed.

## Delivery Management

16. **Order - Delivery**
    - Order → Delivery: CASCADE
    - Delivery → Order: RESTRICT
    - _Rationale_: When an order is deleted, its delivery record should be removed.
17. **Delivery_Service - Delivery**
    - Delivery_Service → Delivery: RESTRICT
    - Delivery → Delivery_Service: RESTRICT
    - _Rationale_: Delivery services with active deliveries should not be deletable.
18. **Delivery_Fee - Delivery**
    - Delivery_Fee → Delivery: RESTRICT
    - Delivery → Delivery_Fee: RESTRICT
    - _Rationale_: Fee structures used in deliveries should not be deletable for financial history.

## Inventory Management

19. **Ingredient - Restock_Request**
    - Ingredient → Restock_Request: RESTRICT
    - Restock_Request → Ingredient: RESTRICT
    - _Rationale_: Ingredients with pending restock requests should not be deletable.
20. **Supplier - Restock_Request**
    - Supplier → Restock_Request: RESTRICT
    - Restock_Request → Supplier: RESTRICT
    - _Rationale_: Suppliers with pending restock requests should not be deletable.
21. **Supplier - Stock**
    - Supplier → Stock: SET NULL
    - Stock → Supplier: RESTRICT
    - _Rationale_: If a supplier is deleted, stock records can remain but without supplier association.
22. **Address - Supplier**
    - Address → Supplier: RESTRICT
    - Supplier → Address: RESTRICT
    - _Rationale_: Addresses used by suppliers should not be deletable.

## Tables and Reservation

23. **Customer - Reservation**
    - Customer → Reservation: RESTRICT
    - Reservation → Customer: RESTRICT
    - _Rationale_: Customers with active reservations should not be deletable.
24. **Table - Reservation**
    - Table → Reservation: RESTRICT
    - Reservation → Table: RESTRICT
    - _Rationale_: Tables with active reservations should not be deletable.
25. **Entity - Contact**
    - Entity → Contact: CASCADE
    - Contact → Entity: RESTRICT
    - _Rationale_: When an entity (Customer/Employee/Supplier) is deleted, its contact information should be removed.

## General Principles Applied:

1. **RESTRICT** is used when:
    - Preserving data integrity is critical
    - Referenced records represent important business data
    - Historical records need to be maintained
2. **CASCADE** is used when:
    - Child records have no meaning without their parent
    - Detailed components should be removed with their container
3. **SET NULL** is used when:
    - The relationship is optional
    - Historical data should be preserved but can exist without the parent