[[DFD Level 1]]
### 🌐 **Level 0 DFD: Context Diagram for Internal Management System**

This diagram represents **your entire system as a single process** and shows **how external entities interact** with it.

---

### 🟦 **Main Process:**

- **Process 0: Internal Management System (IMS)**
    

---

### 🟥 **External Entities:**

1. **Customer**
    
2. **Employee**
    
3. **Supplier**
    
4. **Delivery Service**
    
5. **Payment Gateway** _(optional – for online or integrated card payments)_
    

---

### 🔄 **Data Flows:**

#### **Customer ↔ IMS**

- Sends:
    
    - Place Order
        
    - Make Reservation
        
    - Make Payment
        
    - View Menu
        
- Receives:
    
    - Order Confirmation
        
    - Reservation Status
        
    - Bill / Invoice
        
    - Delivery Updates
        

#### **Employee ↔ IMS**

- Sends:
    
    - Status Update
        
    - Shift Input
        
    - Role Assignments
        
- Receives:
    
    - Shifts
        
    - Role Details
        
    - Order Assignments
        
    - Low Stock Alerts
        

#### **Supplier ↔ IMS**

- Sends:
    
    - Ingredient Deliveries
        
    - Restock Confirmation
        
- Receives:
    
    - Restock Requests
        

#### **Delivery Service ↔ IMS**

- Sends:
    
    - Delivery Updates
        
- Receives:
    
    - Delivery Assignment
        

#### **Payment Gateway ↔ IMS** _(if used externally)_

- Sends:
    
    - Payment Confirmation
        
- Receives:
    
    - Payment Request

![[DFD Level 0.png]]