# Salesforce E-Commerce Automation Project

## Overview

This project is a Salesforce-based e-commerce application developed to automate order processing, customer management, product management, shipment tracking, and email notifications.

The project uses Salesforce declarative tools such as Flows and Validation Rules, along with Apex and SOQL, to create an efficient and scalable solution.

---

## Technologies Used

- Salesforce
- Apex
- SOQL
- Flow Builder
- Validation Rules
- Lightning Experience

---

## Objects Used

### Custom Objects

- Order__c
- Order_Item__c
- Category__c
- Payment__c
- Shipment__c

### Standard Objects

- Customer
- Product2

---

# Requirements Implemented

### Functional Requirements

- Create customer orders.
- Store product information.
- Validate customer details.
- Generate shipment records automatically.
- Send email notifications.
- Prevent invalid data entry.

---

# Flow Implementation

## 1. Automatic Order Date Assignment

### Flow Type

Before-Save Record-Triggered Flow

### Description

The flow automatically updates the order date whenever a new order is created.

### Implementation Steps

- Create a record-triggered flow.
- Select the Order object.
- Configure the flow to run before the record is saved.
- Assign the current date to the Order Date field.
- Save and activate the flow.

---

## 2. Email Notification Flow

### Flow Type

After-Save Record-Triggered Flow

### Description

The flow automatically sends an email notification whenever an order is created.

### Implementation Steps

- Create an after-save flow.
- Select the Order object.
- Add the Send Email action.
- Configure the recipient and email body.
- Save and activate the flow.

---

## 3. Shipment Creation Flow

### Flow Type

After-Save Record-Triggered Flow

### Description

The flow automatically creates a shipment record whenever an order is successfully created.

### Implementation Steps

- Create an after-save flow.
- Select the Order object.
- Add the Create Records element.
- Create the shipment record automatically.
- Save and activate the flow.

---

# Validation Rules

## Validation Rule 1 – Customer Validation

### Rule Name

Customer_Required

### Formula

```text
ISBLANK(Customer__c)
```

### Error Message

```text
Please select a customer.
```

---

## Validation Rule 2 – Product Validation

### Rule Name

Product_Required

### Formula

```text
ISBLANK(Product__c)
```

### Error Message

```text
Please select a product.
```

---

## Validation Rule 3 – Order Date Validation

### Rule Name

Order_Date_Validation

### Formula

```text
Order_Date__c > TODAY()
```

### Error Message

```text
Order date cannot be greater than today's date.
```

---

## Validation Rule 4 – Order Number Validation

### Rule Name

Order_Number_Validation

### Formula

```text
Order_Number__c <= 0
```

### Error Message

```text
Please enter a valid order number.
```

---

# Apex Implementation

Apex was used to create records and test the application.

```apex
Customer cust = [SELECT Id FROM Customer LIMIT 1];
Product2 prod = [SELECT Id FROM Product2 LIMIT 1];

Order__c ord = new Order__c();

ord.Name = 'Test Order';
ord.Order_Number__c = 1001;
ord.Customer__c = cust.Id;
ord.Product__c = prod.Id;
ord.Order_Date__c = Date.today();

insert ord;
```

---

# Questions and Answers

## Which requirements did you solve using Flow?

The following requirements were implemented using Salesforce Flow:

- Automatic order date assignment
- Shipment creation
- Email notification generation

---

## Which requirements required Validation Rules?

The following requirements required validation rules:

- Customer field validation
- Product field validation
- Order date validation
- Order number validation

---

## Which requirements still needed Apex?

The following requirements required Apex:

- Record creation
- Data retrieval
- SOQL query execution
- Application testing

---

## Why did you choose these solutions?

### Flow

Flow was selected because it reduces development time and simplifies automation.

### Validation Rules

Validation rules ensure data integrity and prevent users from entering invalid data.

### Apex

Apex provides flexibility for implementing complex business logic and performing advanced operations.

---

# Future Enhancements

- Payment gateway integration
- Inventory management
- Shipment tracking
- Dashboard creation
- Customer feedback management

---

# Conclusion

This project demonstrates the implementation of Salesforce automation by combining Flows, Validation Rules, SOQL, and Apex to create an efficient e-commerce management system.
