### 🌐 **High-Level Decision Flows (Level 0 DFD Concepts)**

### 1. **Customer Interaction**

- **Customer → Places → Order**
- **Order → Contains → Order_Items**
- **Order_Items → Refer → Menu_Items**
- **Menu_Items → Belong to → Category**
- **Order → May Apply → Discounts**
- **Discounts → Applied through → Apply_Discounts**
- **Order → Generates → Transaction**
- **Transaction → Includes → Delivery Fee (if Order_Type = Delivery)**
- **Transaction → Calculates → Final_Amount (Total + Delivery Fee - Discount)**
- **Order → May Trigger → Payment (based on Transaction)**
- **Order → May Trigger → Delivery Details (if Order_Type = Delivery)**
- **Order → May Trigger → Reservation (if Order_Type = Dine-In)**

---

### 🧑‍🍳 **Menu & Kitchen Operations**

- **Menu_Items → Prepared using → Meal_Prep (Bridge)**
- **Meal_Prep → Uses → Ingredients**
- **Ingredients → Checked from → Stock**
- **Low Stock → Creates → Restock Request**
- **Restock Request → Sent to → Supplier**
- **Supplier → Supplies → Ingredients**

---

### 🚚 **Delivery System**

- **Delivery Details → Linked to → Orders (if Order_Type = Delivery)**
- **Delivery Details → Managed by → Delivery Service**
- **Delivery Service → Type → In-house / Third-party**
- **Delivery Details → Uses → Delivery Fee**
- **Delivery Fee → Applied to → Transaction**

---

### 🪑 **Table & Reservation Flow**

- **Customer → Makes → Reservation Requests**
- **Reservation Requests → Linked to → Tables**
- **Tables → Have → Availability**
- **Reservation → Influences → Table Availability**

---

### 💳 **Billing & Payment Flow**

- **Order → Has → Total_Amount**
- **Discounts → Applied → Applied_Amount → Amount_Due**
- **Transaction → Generates → Final_Amount (Total + Delivery Fee - Discount)**
- **Payment → Recorded for → Transaction**
- **Payment → Has → Final_Amount (Total - Discount + Delivery Fee)**
- **Payment → Has → Status, Method**

---

### 👨‍💼 **Employee Management**

- **Employees → Assigned → Roles**
- **Employees → Assigned → Shifts**
- **Shifts → Indicate → Start, End, Type**
- **Employee → Has → Status (Present, Absent, etc.)**

---

### 🔁 **Integrated Example Decision Flow**

> A customer places a delivery order → system creates an order → adds order_items → references menu_items → calculates subtotal → applies discounts (if any) → calculates final amount → generates transaction → includes delivery fee in transaction → generates payment → payment processed → delivery details triggered → selects delivery partner → order triggers kitchen meal prep → stock checked → restock requested if needed → delivery dispatched.


#Stages