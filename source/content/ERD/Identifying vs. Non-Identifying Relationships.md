
## Identifying Relationships

In these relationships, the child entity's primary key contains the foreign key to the parent entity (partial or complete dependency).

1. **Order to Order_Item**
    - Order_Item's primary key likely contains Order_ID as part of its composite key
    - Each Order_Item cannot exist without its parent Order
2. **Menu_Item to Dish_Ingredients**
    - Dish_Ingredients likely has Menu_Item_ID as part of its primary key
    - Each ingredient record for a dish cannot exist without the menu item
3. **Order to Order_Discount**
    - Order_Discount likely contains Order_ID as part of its composite key
    - A discount application record cannot exist without its parent order
4. **Employee to Employee_Role**
    - Employee_Role likely contains Employee_ID as part of its composite key
    - A role assignment cannot exist without the employee
5. **Role to Employee_Role**
    - Employee_Role likely contains Role_ID as part of its composite key
    - A role assignment also cannot exist without the role
6. **Ingredient to Dish_Ingredients**
    - Dish_Ingredients likely has Ingredient_ID as part of its composite key
    - An ingredient record for a dish cannot exist without the ingredient itself
7. **Order to Transaction**
    - Transaction likely uses Order_ID as part of its identifier
    - A transaction cannot exist without an order
8. **Transaction to Payment**
    - Payment contains Transaction_ID as part of its identity
    - A payment cannot exist without a transaction
9. **Order to Delivery**
    - Delivery uses Order_ID as part of its identification
    - A delivery record cannot exist without an order
10. **Entity to Contact**
    - Contact contains Entity_ID as part of its identity
    - A contact record cannot exist independently of its parent entity

## Non-Identifying Relationships

In these relationships, the child entity references the parent but maintains its own independent primary key.

1. **Employee to Shift**
    - A Shift has its own Shift_ID primary key
    - It references Employee_ID as a foreign key but not as part of its primary key
2. **Address to Customer**
    - Customer has its own Customer_ID primary key
    - It references Address_ID as a foreign key but not as part of its identity
3. **Category to Menu_Item**
    - Menu_Item has its own Menu_Item_ID primary key
    - It references Category_ID as a foreign key
4. **Ingredient to Stock**
    - Stock has its own Stock_ID primary key
    - It references Ingredient_ID as a foreign key
5. **Customer to Order**
    - Order has its own Order_ID primary key
    - It references Customer_ID as a foreign key
6. **Menu_Item to Order_Item**
    - While Order_Item includes Order_ID in its primary key, the Menu_Item_ID is just a foreign key
    - The relationship from Menu_Item to Order_Item is non-identifying
7. **Discount to Order_Discount**
    - While Order_Discount likely includes Order_ID in its primary key, the Discount_ID is just a foreign key
    - The relationship from Discount to Order_Discount is non-identifying
8. **Delivery_Service to Delivery**
    - Delivery has Order_ID as its primary key (or part of it)
    - Service_ID is a foreign key but not part of the primary key
9. **Delivery_Fee to Delivery**
    - Delivery has Order_ID as its primary key (or part of it)
    - Fee_ID is a foreign key but not part of the primary key
10. **Ingredient to Restock_Request**
    - Restock_Request has its own Restock_ID primary key
    - It references Ingredient_ID as a foreign key
11. **Supplier to Restock_Request**
    - Restock_Request has its own Restock_ID primary key
    - It references Supplier_ID as a foreign key
12. **Supplier to Stock**
    - Stock has its own Stock_ID primary key
    - It references Supplier_ID as a foreign key
13. **Address to Supplier**
    - Supplier has its own Supplier_ID primary key
    - It references Address_ID as a foreign key
14. **Customer to Reservation**
    - Reservation has its own Res_ID primary key
    - It references Customer_ID as a foreign key
15. **Table to Reservation**
    - Reservation has its own Res_ID primary key
    - It references Table_ID as a foreign key