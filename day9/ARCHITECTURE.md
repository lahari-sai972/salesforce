# 🛒 E-Commerce LWC Project

## 📌 About the Project

This project is a simple E-Commerce application built using Salesforce Lightning Web Components (LWC) and Apex.

The user can view available products and click the **Buy Now** button to place an order.

---

## 🏗️ Architecture

```text
User
  ↓
ecommerceHome
  ↓
productChild
  ↓
Buy Now
  ↓
Custom Event
  ↓
Apex Controller
  ↓
Service Layer
  ↓
Salesforce Database
  ↓
Success / Error
  ↓
UI Refresh

🔄 Component Communication
Parent → Child

The parent sends product information to the child using @api.

ecommerceHome
      ↓
   @api product
      ↓
productChild
Child → Parent

The child sends the selected Product Id using a Custom Event.

productChild
      ↓
 Custom Event
      ↓
ecommerceHome
⚡ Apex Flow

When the user clicks Buy Now:

Buy Now
   ↓
JavaScript
   ↓
Apex Controller
   ↓
Service Layer
   ↓
Check Product
   ↓
Check Stock
   ↓
Create Order
   ↓
Update Stock
   ↓
Return Response
🧠 Service Layer

The Service Layer contains the main business logic.

It:

Checks whether the product exists
Checks whether the product is available
Checks stock
Creates the order
Reduces the product stock
Returns the Order Id
⏳ UI States

The application has four main states:

Ready
[ BUY NOW ]
Processing
Placing Order...
Success
✓ Order placed successfully
Error
❌ Product is out of stock
🛡️ Duplicate Click Protection

When the user clicks Buy Now, the button is disabled while the request is processing.

This prevents unnecessary repeated clicks.

Click Buy
   ↓
Processing
   ↓
Button Disabled
   ↓
Order Complete
   ↓
Button Enabled
🔄 Refresh

After an order is successfully created, the product data is refreshed.

Example:

Before Order:
Stock = 5

After Order:
Stock = 4

The updated stock is then displayed on the screen.

📁 Project Structure
force-app/
└── main/
    └── default/
        ├── classes/
        │   └── ProductController.cls
        │
        └── lwc/
            ├── ecommerceHome/
            │   ├── ecommerceHome.html
            │   ├── ecommerceHome.js
            │   ├── ecommerceHome.css
            │   └── ecommerceHome.js-meta.xml
            │
            └── productChild/
                ├── productChild.html
                ├── productChild.js
                └── productChild.js-meta.xml
🎯 Key Concepts Used
Salesforce LWC
Parent and Child Components
@api
Custom Events
@wire
Imperative Apex
Apex Controller
Service Layer
Salesforce Database
Loading State
Success State
Error Handling
Data Refresh
🔑 Main Flow
User
 ↓
View Products
 ↓
Click Buy Now
 ↓
Send Product Id
 ↓
Call Apex
 ↓
Validate Product
 ↓
Check Stock
 ↓
Create Order
 ↓
Update Stock
 ↓
Show Success/Error
 ↓
Refresh Product List
✅ Conclusion

This project demonstrates how Salesforce LWC can be used to create an interactive E-Commerce application where the frontend communicates with Apex, business logic is handled in the service layer, and the user receives clear feedback after placing an order.


### For your GitHub

Keep it simple like this:

```text
Sprint-09-Ecommerce/
│
├── README.md
├── force-app/
├── architecture/
│   └── ecommerce-architecture.png
└── screenshots/
    ├── products.png
    ├── processing.png
    ├── success.png
    └── error.png
