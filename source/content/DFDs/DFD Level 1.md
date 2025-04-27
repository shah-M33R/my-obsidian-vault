## 🔍 **Level 1 DFD – Internal Management System (IMS)**

We’ll break the system into **6 key subprocesses**:

1. **Order Management**
    
2. **Reservation Management**
    
3. **Inventory & Restocking**
    
4. **Delivery Management**
    
5. **Billing & Payments**
    
6. **Employee Management**
    

---

### 🟦 Processes (P1–P6):

|Process ID|Name|Description|
|---|---|---|
|P1|Order Management|Handles placing orders, selecting items, and applying discounts.|
|P2|Reservation Management|Manages dine-in table reservations.|
|P3|Inventory & Restocking|Handles stock level checks, ingredient tracking, and restocking.|
|P4|Delivery Management|Manages delivery details, services, and delivery status.|
|P5|Billing & Payments|Calculates totals, applies fees, processes transactions and payments.|
|P6|Employee Management|Manages shifts, roles, and employee availability.|

---

### 🗂️ Data Stores (Internal):

|Data Store ID|Name|
|---|---|
|D1|Customers|
|D2|Orders|
|D3|Menu_Items|
|D4|Ingredients & Stock|
|D5|Transactions|
|D6|Payments|
|D7|Reservations|
|D8|Employees|
|D9|Shifts|
|D10|Discounts|
|D11|Suppliers|
|D12|Delivery Details|

---

### 🟩 External Entities (Same as Level 0):

- **Customer**
    
- **Employee**
    
- **Supplier**
    
- **Delivery Service**
    
- **Payment Gateway (optional)**
    

---

### 🧩 Key Data Flows:

#### **P1: Order Management**

- Customer → Place Order → P1
    
- P1 → D2 (Orders)
    
- P1 → D3 (Menu_Items), D10 (Discounts)
    
- P1 → P5 (Billing)
    

#### **P2: Reservation Management**

- Customer → Reservation Request → P2
    
- P2 → D7 (Reservations)
    
- P2 → D1 (Customers), D12 (Tables)
    

#### **P3: Inventory & Restocking**

- P1/P4 → Ingredient Check → P3
    
- P3 → D4 (Ingredients, Stock)
    
- P3 → D11 (Suppliers)
    

#### **P4: Delivery Management**

- P1 → Trigger Delivery → P4
    
- P4 → D12 (Delivery Details)
    
- P4 → Delivery Service (Send/Receive Status)
    
- P4 → P5 (For Delivery Fee)
    

#### **P5: Billing & Payments**

- P1/P4 → Send Charges → P5
    
- P5 → D5 (Transactions), D6 (Payments)
    
- Customer → Payment → P5
    
- P5 → Payment Gateway (if used)
    

#### **P6: Employee Management**

- Employee → Shift/Status Input → P6
    
- P6 → D8 (Employees), D9 (Shifts)

![[DFD Level 1.png]]