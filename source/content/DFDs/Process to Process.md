## 🔁 **Process ↔ Process Interactions**

---

### ▶️ **P1: Order Management → P3: Inventory & Restocking**

|Direction|Data Flow|Meaning|
|---|---|---|
|P1 → P3|`Required Ingredients / Stock Check`|When a new order is placed, the system checks inventory to confirm if enough ingredients are available.|

---

### ▶️ **P1: Order Management → P5: Billing & Payments**

|Direction|Data Flow|Meaning|
|---|---|---|
|P1 → P5|`Order Charges (Items, Discounts)`|Sends total item cost, discount info, and order ID to be used in billing.|

---

### ▶️ **P1: Order Management → P4: Delivery Management**

|Direction|Data Flow|Meaning|
|---|---|---|
|P1 → P4|`Delivery Trigger (Order_ID + Address)`|If order type is Delivery, it activates P4 with delivery details.|

---

### ▶️ **P4: Delivery Management → P5: Billing & Payments**

|Direction|Data Flow|Meaning|
|---|---|---|
|P4 → P5|`Delivery Fee Info (Fee_ID, Fee_Amount)`|Delivery adds fee data to pass to Billing.|

---

### ▶️ **P5: Billing & Payments → P6: Employee Management (optional)**

|Direction|Data Flow|Meaning|
|---|---|---|
|P5 → P6|`Revenue Reports (optional)`|Can be used for payroll or financial summaries handled by managers. (Only if needed in your scope)|

---

### ▶️ **P2: Reservation Management → P6: Employee Management (optional)**

|Direction|Data Flow|Meaning|
|---|---|---|
|P2 → P6|`Table Load Info`|If needed, reservation load could inform shift planning. Optional, but realistic for busy branches.|

---

## 🧩 Summary Table – All Internal Process Links

| From Process               | To Process                 | Data Flow                                  |
| -------------------------- | -------------------------- | ------------------------------------------ |
| P1: Order Management       | P3: Inventory & Restocking | Ingredient check / requirement             |
| P1: Order Management       | P5: Billing & Payments     | Item total, discount info                  |
| P1: Order Management       | P4: Delivery Management    | Trigger delivery if order type is Delivery |
| P4: Delivery Management    | P5: Billing & Payments     | Delivery fee info                          |
| P2: Reservation Management | P6: Employee Management    | Table load data (optional)                 |
| P5: Billing & Payments     | P6: Employee Management    | Revenue/Payroll data (optional)            |
[[DFD Level 1]]