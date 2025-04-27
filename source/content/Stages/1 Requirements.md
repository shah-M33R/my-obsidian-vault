### **1. Introduction**

### **1.1 Purpose**

This document defines the requirements for the **Internal Management System** of a fast-food restaurant. The system will support operations ranging from employee management to customer orders, inventory management, delivery tracking, and payment processing. The purpose of this system is to streamline daily operations, reduce human error, and enhance customer service.

### **1.2 Scope**

The system will focus on the following core operations:

- **Employee Management** (Roles, Shifts, and Employee Details)
- **Customer Management** (Orders, Reservations, and Communication)
- **Menu Management** (Items, Categories, Ingredients)
- **Inventory Management** (Stock, Suppliers, and Restocks)
- **Order Processing and Payments** (Order Creation, Payment Methods, and Discount Handling)
- **Delivery Management** (Delivery Orders, Tracking, and Delivery Fees)
- **Reservation Management** (Table Reservation and Management)

This system will be used by restaurant staff, managers, and customers (for orders and reservations).

### **1.3 Stakeholders**

- **Restaurant Manager**: Will use the system for employee management, order processing, inventory tracking, and managing reservations.
- **Employees**: Will interact with the system for shift management, role assignments, and customer interaction.
- **Customers**: Will use the system for placing orders and making reservations.
- **Suppliers**: Will interact with the system to manage ingredient restocks.

---

### **2. Functional Requirements**

### **2.1 Employee and Customer Management**

- **Employee Roles and Shifts**:
    - Employees should be assigned specific roles (e.g., Cashier, Cook, Manager).
    - Employees can have multiple roles at the same time.
    - Shifts should be tracked, and each employee can have many shifts.
    - Managers should be able to assign, modify, and track shifts.
- **Customer Management**:
    - Customers can create accounts, place orders, and make reservations.
    - Customer details (e.g., name, contact information, and addresses) will be stored.
    - Customers can view order history and reservation status.

### **2.2 Menu and Order Items**

- **Menu Item Creation**:
    - Menu items should be categorized (e.g., Burgers, Fries, Drinks).
    - Each menu item should include a name, description, price, and availability status.
    - Ingredients required for each menu item should be tracked.
- **Order Items**:
    - Customers can select multiple items for an order.
    - The system will calculate the order total by multiplying the quantity of items by their respective prices.
    - Discounts and special offers should be applied to eligible items.

### **2.3 Ingredients and Inventory Management**

- **Stock Tracking**:
    - Each ingredient must have a stock record indicating quantity on hand.
    - Stock levels should be monitored, and when quantities fall below a set threshold, the system will generate restock requests.
- **Supplier Management**:
    - Each supplier should have details (name, contact information, and address).
    - Suppliers can provide ingredients to the restaurant, and restock requests will be sent to them for fulfillment.

### **2.4 Delivery and Payment**

- **Order Delivery**:
    - Orders placed with a delivery option will have additional details like delivery fees, delivery status, and tracking.
    - Delivery fees should be dynamically calculated based on delivery range.
- **Payments**:
    - Payments will be processed via various methods (credit card, debit card, cash).
    - Payment status will be tracked (Pending, Completed, Failed).
    - Delivery fees should be added to the total transaction amount for delivery orders.

### **2.5 Supplier and Restock Management**

- **Restock Requests**:
    - The system should allow the creation of restock requests based on ingredient levels.
    - Suppliers will receive requests for specific ingredients, including quantities needed and expected delivery dates.
    - The status of the restock request (Pending, Delivered) will be tracked.

### **2.6 Reservation and Table Management**

- **Table Reservation**:
    - Customers can make reservations for tables based on availability.
    - The system should allow customers to choose a date and time for their reservation.
    - Reservations should be confirmed, and customers should be notified.
    - Table capacity and availability should be updated in real-time.

---

### **3. Non-Functional Requirements**

### **3.1 Usability**

- The system should be user-friendly and intuitive, with an easy-to-navigate interface for employees, managers, and customers.

### **3.2 Performance**

- The system should support real-time updates of orders, payments, reservations, and inventory.
- The system must handle up to 500 simultaneous users without significant slowdowns.

### **3.3 Security**

- Sensitive data such as customer contact information, payment details, and employee information must be stored securely.
- Role-based access control should be implemented to ensure that only authorized personnel can access certain features.

### **3.4 Reliability**

- The system should be available 24/7, with minimal downtime. Any system outages should be resolved within 24 hours.

### **3.5 Scalability**

- The system should be scalable to accommodate future growth, such as adding new menu items, suppliers, or more locations.

---

### **4. Use Cases**

### **4.1 Use Case: Employee Shift Management**

- **Actors**: Restaurant Manager, Employees
- **Description**: A restaurant manager schedules shifts for employees. Employees can view their shift schedules and mark them as completed.
- **Precondition**: Manager must be logged in to the system.
- **Postcondition**: Employees’ shift statuses are updated, and shifts are tracked in the system.

### **4.2 Use Case: Order Placement**

- **Actors**: Customer, System
- **Description**: A customer places an order, selects menu items, applies discounts (if applicable), and checks out.
- **Precondition**: Customer is logged into the system.
- **Postcondition**: Order is placed, and the customer is billed accordingly.

### **4.3 Use Case: Table Reservation**

- **Actors**: Customer, System
- **Description**: A customer reserves a table for a specific date and time.
- **Precondition**: The system must show available tables for the selected time and date.
- **Postcondition**: Reservation is confirmed and stored in the system.

---

### **5. System Architecture and Design Considerations**

### **5.1 Database Design**

- A detailed ERD (Entity-Relationship Diagram) is needed, including all entities (Employees, Orders, Menu Items, etc.), their attributes, and relationships.

### **5.2 Data Flow Diagrams (DFD)**

- A DFD should be created to show how information flows between entities (e.g., orders, payments, inventory, deliveries) and help with decision-making processes.

---

### **6. Conclusion**

This Requirements Engineering document outlines the essential operations and features for the internal management system of the restaurant. The system is designed to support employees, streamline orders and reservations, track inventory and deliveries, and handle payments efficiently. With a clear understanding of these requirements, the system will be able to meet the needs of both customers and restaurant staff.

#Stages