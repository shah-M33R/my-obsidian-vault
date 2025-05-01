### 🔸 **Employee-Related**

1. **Employees → Roles**
    
    **M:N**
    
    - One employee can take multiple roles (e.g., Cashier & Trainer).
    - One role can be assigned to many employees.
    - ✅ Use **bridge table** (`Employee_Role`).
2. **Employees → Shifts**
    
    **1:M**
    
    - One employee can have many shifts.
    - Each shift is assigned to one employee.

---

### 🔸 **Customer-Related**

1. **Customers → Orders**
    
    **1:M**
    
    - A customer can place many orders.
    - Each order is placed by one customer.
2. **Customers → Reservation Requests**
    
    **1:M**
    
    - A customer can make multiple reservations.
    - Each reservation is linked to one customer.
3. **Customers → Addresses**
    
    **1:M**
    
    - One customer can have multiple addresses (e.g., home, work, etc.).
    - Each address is linked to one customer.

---

### 🔸 **Order-Related**

1. **Orders → Order_Items**
    
    **1:M**
    
    - One order contains multiple order items.
    - Each item belongs to one order.
2. **Order_Items → Menu_Items**
    
    **M:1**
    
    - Many order items can refer to the same menu item.
3. **Orders → Delivery Details**
    
    **1:1 (conditional)**
    
    - Each order can have **one** delivery detail if it's a delivery type.
    - Not all orders are deliveries, so it’s optional.
4. **Orders → Apply_Discounts**
    
    **1:M**
    
    - One order can have multiple discounts applied (combo or layered).
    - Each discount application refers to one order.
5. **Orders → Payments**
    
    **1:1**
    
    - Each order results in one payment (assuming payment in full).
6. **Orders → Discounts (via Apply_Discounts)**
    
    **M:N**
    
    - One order can have multiple discounts.
    - One discount can apply to many orders.

---

### 🔸 **Menu & Meal Prep**

1. **Menu_Items → Category**
    
    **M:1**
    
    - Many menu items belong to one category.
2. **Menu_Items → Meal_Prep**
    
    **1:M**
    
    - One menu item uses multiple ingredients via `Meal_Prep`.
3. **Meal_Prep → Ingredients**
    
    **M:1**
    
    - Each ingredient appears in many `Meal_Prep` records.

---

### 🔸 **Inventory & Supply**

1. **Ingredients → Stock**
    
    **1:1**
    
    - Each ingredient has one stock record.
2. **Stock → Supplier**
    
    **M:1**
    
    - One supplier can supply multiple ingredients.
    - Each stock entry refers to one supplier.
3. **Restock Requests → Ingredients**
    
    **M:1**
    
    - Multiple requests can be made for the same ingredient.
4. **Restock Requests → Supplier**
    
    **M:1**
    
    - Many requests can be made to a single supplier.

---

### 🔸 **Delivery System**

1. **Delivery Details → Orders**
    
    **1:1**
    
    - Each delivery record refers to one order.
    - Each delivery order has only one delivery detail.
2. **Delivery Details → Delivery Service**
    
    **M:1**
    
    - Many deliveries can be handled by one delivery service.
3. **Delivery Details → Delivery Fee**
    
    **1:1**
    
    - Each delivery detail refers to one delivery fee record, which may vary based on distance or other parameters.

---

### 🔸 **Reservations**

1. **Reservation Requests → Tables**
    
    **M:1**
    
    - Multiple reservations can be made for the same table (at different times).
    - Each reservation refers to one table.

---

### 🔸 **Payments and Discounts**

1. **Payments → Orders**
    
    **1:1**
    
    - One payment per order.
2. **Apply_Discounts → Discounts**
    
    **M:1**
    
    - Many applications of a discount can be linked to one discount record.
3. **Payments → Transactions**
    
    **1:1**
    
    - Each payment is linked to one transaction, which includes the order total, delivery fee, and final amount after discounts.
4. **Discounts → Apply_Discounts**
    
    **1:M**
    
    - One discount can be applied to many orders.
    - Many applications of the discount can happen, linked to each specific order.

---

### 🔸 **Additional Relationships and Considerations**

1. **Delivery Fee → Delivery Service**
    
    **M:1**
    
    - One delivery service can have multiple delivery fees (based on distance or other factors).
2. **Delivery Fee → Transactions**
    
    **1:M**
    
    - A transaction may include multiple delivery fee records based on different conditions (e.g., delivery type, distance).
3. **Transactions → Payments**
    
    **1:1**
    
    - Each transaction is associated with one payment, which completes the financial transaction.
4. **Order → Restock Request**
    
    **Indirect, Conditional**
    
    - A restock request can be triggered if the ingredients in the order are low in stock.
    - This is indirectly connected through inventory management.

#Stages