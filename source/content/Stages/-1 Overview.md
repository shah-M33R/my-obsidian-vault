## **Project Title:**

Internal Management System for a Fast-Food Restaurant (McDonald's Branch Model)

## **Objective:**

Develop a **comprehensive** internal management system to optimize **order handling, staff workflow, inventory tracking, drive-thru operations, PlayPlace management, and delivery processes.**

## **Project Scope:**

- Rather than rebuilding McDelivery, we will **optimize** one existing component (such as the order queue system, supply chain tracking, or customer loyalty program).
- While each McDonald's franchise operates **independently** under corporate guidelines, our system will focus on a **single branch**.
- The system will optimize **order handling, staff workflow, inventory tracking, drive-thru operations, PlayPlace management, and delivery processes.**

---

# **Project Stages & Steps**

### **0: On-Site Visit (Observation & Data Collection)**

**Goal:** Gather real-world insights into McDonald's internal processes.

- Observe **order placement, processing, and fulfillment**.
- Analyze **staff scheduling and workflow management**.
- Understand **inventory monitoring and restocking procedures**.
- Identify **pain points** and potential improvements.
- Conduct **interviews with employees or managers** when possible.

### **1: Requirements Analysis**

**Goal:** Define core functionalities and system needs.

- List essential **features and automation opportunities**.
- Identify **key problems** in the current workflow.
- Determine **data needs for storage, tracking, and analysis**.

### **2: Identify Entities**

**Goal:** Establish key system components.

- Define **main entities** (e.g., Orders, Employees, Inventory, Sales, Suppliers).
- Understand entity interactions within the system.

### **3: Define Attributes**

**Goal:** Specify details for each entity.

- Orders: **Order_ID, Items, Total_Price, Status**.
- Employees: **ID, Name, Role, Shift Timing**.
- Inventory: **Ingredient_ID, Stock Level, Expiry Date, Supplier Info**.

### **4: Decision Flows

**Goal:** Map key decision points and process flows.

- Define **order status transitions** and handling rules.
- Establish **inventory thresholds** for reordering decisions.
- Map **staff allocation** decision processes based on demand.

### **5: Data Flow Diagram (DFD)**

**Goal:** Map the internal system's workflow.

- Visualize **data flow** from order placement to inventory update.
- Show interactions between **customers, staff, and backend processes**.

### **6: Define Relationships**

**Goal:** Map entity connections.

- Employees **manage** orders and handle inventory.
- Orders **affect** stock levels.
- Suppliers **restock** inventory.

### **7: Create an ER Diagram**

**Goal:** Create a **visual representation** of the database.

- Design the **Entity-Relationship Diagram (ERD)** to model the database structure.

### **8: Develop Database Tables**

**Goal:** Convert the ER diagram into database tables.

- Design normalized **tables** for efficient data management.
- Establish **primary and foreign keys**.

### **9: Documentation**

**Goal:** Create comprehensive project documentation.

- Document system **requirements, architecture, and processes**.
- Include **data models, diagrams, and functional descriptions**.

### **10: Normalization**

**Goal:** Apply normalization rules to optimize the database structure.

- Implement **1NF, 2NF, and 3NF** to eliminate data redundancy.
- Ensure **data integrity** and minimize update anomalies.
- Optimize table relationships for efficient querying.

---

## **🔹 Basic Ideas & Guidelines**

📌 **Scope:**

- Focus on **internal operations**, not customer-side features like mobile ordering.
- Simulate a **single McDonald's branch, not the entire chain.**

📌 **Main Objectives:**

✅ Optimize **order processing** (queueing, status updates, priority handling).

✅ Manage **staff scheduling** dynamically based on peak hours.

✅ Track **inventory levels** and automate restocking alerts.

✅ Improve **drive-thru speed & PlayPlace maintenance.**

✅ Ensure **seamless integration** with third-party delivery services.

📌 **What We Won't Cover:**

❌ Franchise-wide corporate systems.

❌ In-depth AI-based analytics (only basic performance tracking).

❌ Customer-side app features (McDelivery is already established).

---

## **🔹 Split Focus Areas**

Each team member will focus on a **specific section** to divide workload efficiently.

### **1️⃣ Order & Queue Management** _(Order Processing & Kitchen Operations)_

- Handle **dine-in, drive-thru, and delivery orders.**
- Optimize **order queue based on priority.**
- Auto-assign **orders to kitchen stations** dynamically.

### **2️⃣ Staff & Workflow Management** _(Employee Scheduling & Task Assignment)_

- Auto-generate **shift schedules** based on workload.
- Track **employee performance & efficiency.**
- Assign **tasks dynamically** based on real-time demand.

### **3️⃣ Inventory & Ingredient Management** _(Stock & Waste Control)_

- Monitor **inventory levels & restocking alerts.**
- Reduce **food waste through real-time tracking.**
- Automate **supplier order placement.**

### **4️⃣ Drive-Thru & PlayPlace Management** _(Customer Flow & Maintenance)_

- Optimize **drive-thru queue** to reduce wait times.
- Track **PlayPlace maintenance & safety schedules.**
- Manage **customer inflow and space occupancy.**

### **5️⃣ Delivery & Third-Party Integrations** _(External Order Handling & Logistics)_

- Integrate **McDelivery & third-party services** (Uber Eats, FoodPanda).
- Optimize **delivery routes** for efficiency.
- Handle **external order tracking in real-time.**

#Stages