# Day 1 – Lightning Web Components (LWC)

## Project Title

E-Commerce Home Component Using Lightning Web Components (LWC)

---

## Objective

The objective of this task is to understand the fundamentals of Lightning Web Components (LWC) and create a simple component for an e-commerce application. The component displays information related to products, orders, and payment status.

---

## Learning Objectives

By the end of this activity, I was able to:

- Understand the Salesforce architecture.
- Understand the purpose of Lightning Web Components (LWC).
- Create an LWC component.
- Understand the structure of an LWC component.
- Deploy an LWC component to Salesforce.
- Implement data binding.
- Display dynamic data.
- Understand communication between LWC and Apex.

---

## Salesforce Architecture

```text
USER
 │
 ▼
Lightning Web Component (LWC)
 │
 ▼
Apex Classes
 │
 ▼
SOQL
 │
 ▼
Salesforce Database
```

---

## Technologies Used

- Salesforce Developer Edition
- Lightning Web Components (LWC)
- HTML
- CSS
- JavaScript
- Salesforce CLI
- Visual Studio Code

---

## Component Name

```text
ecommerceHome
```

---

## Component Structure

```text
ecommerceHome
│
├── ecommerceHome.html
├── ecommerceHome.js
├── ecommerceHome.css
└── ecommerceHome.js-meta.xml
```

---

## HTML File

### ecommerceHome.html

```html
<template>

    <lightning-card title="E-Commerce Dashboard">

        <div class="container">

            <h2>Order Information</h2>

            <p>
                Product Name: {productName}
            </p>

            <p>
                Order Number: {orderNumber}
            </p>

            <p>
                Payment Status: {paymentStatus}
            </p>

        </div>

    </lightning-card>

</template>
```

---

## JavaScript File

### ecommerceHome.js

```javascript
import { LightningElement } from 'lwc';

export default class EcommerceHome extends LightningElement {

    productName = 'Laptop';

    orderNumber = '1001';

    paymentStatus = 'Paid';

}
```

---

## CSS File

### ecommerceHome.css

```css
.container {
    padding: 15px;
}

h2 {
    font-size: 20px;
    font-weight: bold;
}

p {
    margin-top: 10px;
}
```

---

## XML Metadata File

### ecommerceHome.js-meta.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>

<LightningComponentBundle
    xmlns="http://soap.sforce.com/2006/04/metadata">

    <apiVersion>67.0</apiVersion>

    <isExposed>true</isExposed>

    <targets>

        <target>lightning__HomePage</target>
        <target>lightning__AppPage</target>
        <target>lightning__RecordPage</target>

    </targets>

</LightningComponentBundle>
```

---

## Deployment Steps

### Step 1

Create the component.

### Step 2

Write the HTML code.

### Step 3

Write the JavaScript code.

### Step 4

Write the CSS code.

### Step 5

Configure the metadata file.

### Step 6

Deploy the component.

```bash
sf project deploy start
```

### Step 7

Open the Salesforce organization.

```bash
sf org open
```

### Step 8

Open Lightning App Builder.

```text
Setup
   ↓
Lightning App Builder
   ↓
Home Page
```

### Step 9

Drag and drop the component onto the page.

### Step 10

Save and activate the page.

---

## Data Binding

Data binding is used to display JavaScript variables dynamically inside HTML elements.

```text
JavaScript
     │
     ▼
HTML
     │
     ▼
User Interface
```

---

## Expected Output

```text
E-Commerce Dashboard

Order Information

Product Name : Laptop

Order Number : 1001

Payment Status : Paid
```

---

## Challenges Faced

- Network connectivity issues
- Deployment errors
- Lightning App Builder errors
- Metadata configuration issues

---

## Learning Outcomes

- Learned the basics of Lightning Web Components (LWC).
- Understood the architecture of Salesforce.
- Implemented data binding.
- Learned to deploy components to Salesforce.
- Understood communication between LWC and Apex.

---

## Conclusion

This task provided practical experience in creating and deploying Lightning Web Components in Salesforce. It also improved understanding of component structure, deployment, and data binding.
