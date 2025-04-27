## 🗂️ **Process ↔ Data Store Interactions**

Here’s a full breakdown, organized by each process:

---

### 🔵 **P1: Order Management**

|Direction|Data Store|Data Flow|
|---|---|---|
|→ D2 (Orders)|Store Order|Save new order with items, type, status|
|← D3 (Menu_Items)|Get Menu|Show available menu items|
|← D10 (Discounts)|Get Discounts|Retrieve available discounts|
|← D1 (Customers)|Get Customer Info|Lookup by customer ID (for registered users)|

---

### 🟢 **P2: Reservation Management**

|Direction|Data Store|Data Flow|
|---|---|---|
|→ D7 (Reservations)|Store Reservation|Save new table booking|
|← D1 (Customers)|Get Customer Info|Verify customer making reservation|
|← D12 (Tables)|Check Availability|Get table capacity/status|

---

### 🟡 **P3: Inventory & Restocking**

|Direction|Data Store|Data Flow|
|---|---|---|
|← D4 (Ingredients & Stock)|Check Ingredient Levels|Read stock levels for menu item requirements|
|→ D4 (Ingredients & Stock)|Update Stock|After restocking or usage|
|← D11 (Suppliers)|Get Supplier Info|Find supplier details for restock request|

---

### 🟠 **P4: Delivery Management**

|Direction|Data Store|Data Flow|
|---|---|---|
|→ D12 (Delivery Details)|Store Delivery Record|Save assigned delivery details|
|← D5 (Transactions)|Get Order Total|Use for distance-based fee calculation|
|← D1 (Customers)|Get Delivery Address|Retrieve address info using customer ID|

---

### 🔴 **P5: Billing & Payments**

|Direction|Data Store|Data Flow|
|---|---|---|
|→ D5 (Transactions)|Store Transaction|Save billing and fee breakdown|
|→ D6 (Payments)|Record Payment|Save payment info (amount, method, status)|
|← D2 (Orders)|Get Order Info|Retrieve ordered items and status|
|← D10 (Discounts)|Get Discount Value|Apply discounts (if not already passed from P1)|
|← D4 (Ingredients & Stock)|(Optional) Ingredient Cost|Only if costing includes live ingredient pricing|

---

### 🟣 **P6: Employee Management**

|Direction|Data Store|Data Flow|
|---|---|---|
|→ D8 (Employees)|Add/Update Employee|Store employee details, availability, contact|
|→ D9 (Shifts)|Save Shift Info|Assign or update shift records|
|← D8 (Employees)|Get Employee Info|For dashboard or HR checks|
|← D9 (Shifts)|View Shift Schedules|For calendar view, duty allocations|

---

## ✅ Summary Table

|Process|Data Store|Direction|Purpose|
|---|---|---|---|
|P1|D2|→|Save Order|
|P1|D3|←|Retrieve Menu Items|
|P1|D10|←|Retrieve Discounts|
|P1|D1|←|Retrieve Customer Info|
|P2|D7|→|Save Reservation|
|P2|D1|←|Retrieve Customer Info|
|P2|D12|←|Check Table Availability|
|P3|D4|↔|Check/Update Stock|
|P3|D11|←|Supplier Info|
|P4|D12|→|Save Delivery Record|
|P4|D5|←|Order Total for Delivery Fee|
|P4|D1|←|Get Delivery Address|
|P5|D5|→|Save Transaction|
|P5|D6|→|Save Payment|
|P5|D2|←|Order Info|
|P5|D10|←|Discount Value|
|P6|D8|↔|Employee Info|
|P6|D9|↔|Shifts Info|
[[DFD Level 1]]