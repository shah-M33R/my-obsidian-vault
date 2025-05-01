# Detected Anomalies in Core Business Entities

1. **Employee Entity Anomalies**:
    - Multivalued attributes: Phone numbers and emails
    - Composite attribute: Name (first and last)
    - Multivalued attributes: Employee roles
2. **Customer Entity Anomalies**:
    - Multivalued attributes: Phone numbers and emails
    - Non-atomic attribute: Full address containing multiple components
    - Composite attribute: Name (first and last)
3. **Order Entity Anomalies**:
    - Non-atomic attribute: Customer information
    - Multivalued attributes: Multiple items per order
    - Derived attributes: Order total and discounted amount
    - Redundant price information across orders
4. **Menu Item Entity Anomalies**:
    - Non-atomic attribute: Category information
    - Multivalued attributes: Multiple ingredients per item
    - Redundant item information across orders
5. **Inventory and Supplier Anomalies**:
    - Non-atomic attribute: Supplier address
    - Nested attributes: Contact information under supplier name
    - Non-atomic attributes: Ingredient and supplier information in stock records
6. **Delivery and Transaction Anomalies**:
    - Non-atomic attributes: Service and fee information
    - Derived attributes: Various calculated totals
    - Redundant payment and delivery information