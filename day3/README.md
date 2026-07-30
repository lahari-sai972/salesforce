# Salesforce Order Automation Assignment

## Project Title

Salesforce Order Management Automation Using Flows and Validation Rules

---

## Project Description

This project focuses on automating the order management process by using Salesforce declarative tools. Instead of depending entirely on Apex code, the application uses Record-Triggered Flows, Validation Rules, and SOQL to automate repetitive tasks and maintain data quality.

The system automatically updates order information, creates shipment records, sends notifications, and validates user input.

---

## Project Objectives

- Automate the order management process.
- Improve data accuracy.
- Reduce manual work.
- Create shipment records automatically.
- Understand the use of Flow, Validation Rules, and Apex.

---

## Tools and Technologies

- Salesforce Developer Edition
- Flow Builder
- Validation Rules
- Apex
- SOQL
- Lightning Experience

---

## Objects Used

### Custom Objects

- Order__c
- Shipment__c
- Order_Item__c
- Category__c
- Payment__c

### Standard Objects

- Customer
- Product2

---

# Flow Implementation

## Flow Type

Record-Triggered Flow

---

## Trigger Event

The flow is executed whenever a new order record is created.

---

## Actions Performed

### Automatic Date Assignment

The system automatically populates the Order Date field with the current date.

---

### Email Notification

The administrator receives an email whenever a customer places an order.

---

### Shipment Creation

A shipment record is automatically created after the order is successfully saved.

---

# Flow Process

```text
Start
  ↓
Assignment
  ↓
Update Record
  ↓
Email Notification
  ↓
Create Shipment Record
  ↓
End
```

---

# Validation Rules

## Rule 1

### Rule Name

Validate_Order_Number

### Formula

```text
Order_Number__c <= 0
```

### Error Message

```text
Enter a valid order number.
```

---

## Rule 2

### Rule Name

Validate_Order_Date

### Formula

```text
Order_Date__c > TODAY()
```

### Error Message

```text
Future dates are not allowed.
```

---

## Rule 3

### Rule Name

Validate_Customer

### Formula

```text
ISBLANK(Customer__c)
```

### Error Message

```text
Please select a customer.
```

---

## Rule 4

### Rule Name

Validate_Product

### Formula

```text
ISBLANK(Product__c)
```

### Error Message

```text
Please select a product.
```

---

# Apex Implementation

Apex was used to retrieve records and verify the application's functionality.

```apex
Customer cust = [SELECT Id FROM Customer LIMIT 1];
Product2 prod = [SELECT Id FROM Product2 LIMIT 1];

Order__c orderRecord = new Order__c();

orderRecord.Name = 'Test Order';
orderRecord.Order_Number__c = 1001;
orderRecord.Customer__c = cust.Id;
orderRecord.Product__c = prod.Id;
orderRecord.Order_Date__c = Date.today();

insert orderRecord;
```

---

# Assignment Questions

## Which requirements were solved using Flow?

The following tasks were completed using Record-Triggered Flows:

- Automatic order date assignment
- Email notifications
- Shipment creation

---

## Which requirements required Validation Rules?

The following validations were implemented:

- Customer validation
- Product validation
- Order number validation
- Order date validation

---

## Which requirements required Apex?

Apex was used for:

- Record creation
- SOQL queries
- Application testing
- Complex operations

---

## Why were these solutions selected?

### Flow

Flows simplify automation and reduce development effort.

### Validation Rules

Validation rules ensure data accuracy and prevent invalid data entry.

### Apex

Apex provides greater flexibility for implementing advanced business logic.

---

# Learning Outcomes

Through this project, I learned:

- Flow Builder implementation
- Validation Rule creation
- SOQL queries
- Apex programming
- Salesforce automation concepts

---

# Conclusion

This project demonstrates how Salesforce declarative features and Apex programming can work together to create an efficient order management system.
