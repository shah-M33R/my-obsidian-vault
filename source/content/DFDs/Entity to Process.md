## 🔗 **Entity ↔ Process Interactions in Level 1**

---

### 👤 **Customer ↔ P1: Order Management**

|Direction|Data Flow|Meaning|
|---|---|---|
|✅ Send →|`Order Details`|Customer places order (items, type, etc.)|
|📥 Receive ←|`Order Confirmation`|System responds with order status/ID|

---

### 👤 **Customer ↔ P2: Reservation Management**

|Direction|Data Flow|Meaning|
|---|---|---|
|✅ Send →|`Reservation Request`|Customer reserves a table (date, time, pax)|
|📥 Receive ←|`Reservation Status`|Confirmed, pending, or declined response|

---

### 👤 **Customer ↔ P5: Billing & Payments**

|Direction|Data Flow|Meaning|
|---|---|---|
|✅ Send →|`Payment Info`|Customer provides payment method (cash/card)|
|📥 Receive ←|`Receipt / Payment Status`|Confirmation of success or failure|

---

### 👤 **Customer ↔ P4: Delivery Management**

|Direction|Data Flow|Meaning|
|---|---|---|
|✅ Send →|`Delivery Address`|For delivery orders|
|📥 Receive ←|`Delivery Tracking / Status`|Ongoing updates or final delivery confirmation|

---

### 🧍 **Employee ↔ P6: Employee Management**

|Direction|Data Flow|Meaning|
|---|---|---|
|✅ Send →|`Availability / Shift Info`|Employees enter availability or clock in|
|📥 Receive ←|`Assigned Shifts / Roles`|Get shift schedules or role updates|

---

### 🚚 **Delivery Service ↔ P4: Delivery Management**

|Direction|Data Flow|Meaning|
|---|---|---|
|✅ Send →|`Status Updates`|Picked up, in transit, delivered, failed|
|📥 Receive ←|`Delivery Assignment`|Order details assigned to delivery provider|

---

### 🧑‍💼 **Supplier ↔ P3: Inventory & Restocking**

|Direction|Data Flow|Meaning|
|---|---|---|
|✅ Send →|`Stock Delivery Confirmation`|Confirms fulfillment of a restock request|
|📥 Receive ←|`Restock Request`|System sends request to supplier for ingredients|

---

### 💳 **Payment Gateway (optional) ↔ P5: Billing & Payments**

|Direction|Data Flow|Meaning|
|---|---|---|
|✅ Send →|`Transaction Request`|IMS sends card data to gateway|
|📥 Receive ←|`Approval / Rejection`|Gateway responds with success or failure|

---

## ✅ Summary Table of Entity–Process Links

|Entity|Connected Process(es)|Purpose|
|---|---|---|
|Customer|P1, P2, P4, P5|Place order, reserve table, track delivery, make payment|
|Employee|P6|Manage shifts and availability|
|Supplier|P3|Fulfill restock requests|
|Delivery Service|P4|Deliver orders, update delivery status|
|Payment Gateway|P5|Handle secure payment transactions|
[[DFD Level 1]]