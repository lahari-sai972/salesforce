#  E-Commerce Application using Salesforce LWC

##  Project Overview

This project is a Salesforce E-Commerce application developed using Lightning Web Components (LWC) and Apex.

The application allows users to view available products and perform product-related actions through a simple and interactive user interface.

The project focuses on component communication, Apex integration, business logic, error handling, and user interface state management.

---

##  Objectives

The main objectives of this project are:

- Build an interactive E-Commerce interface using Salesforce LWC
- Display available product information
- Implement reusable Lightning Web Components
- Implement Parent and Child component communication
- Handle user actions using Custom Events
- Integrate LWC with Apex
- Separate business logic from the UI
- Handle success and error scenarios
- Manage loading and processing states
- Prevent unnecessary repeated actions
- Refresh data after successful operations

---

##  Technologies Used

- Salesforce
- Lightning Web Components (LWC)
- Apex
- SOQL
- Salesforce Database
- JavaScript
- HTML
- CSS

---

##  Main Components

### ecommerceHome

`ecommerceHome` is responsible for managing the main application interface.

Responsibilities include:

- Managing the main UI
- Retrieving product information
- Displaying product information
- Handling user actions
- Receiving events from the child component
- Calling Apex
- Managing loading state
- Managing success and error messages
- Refreshing data when required

### productChild

`productChild` is responsible for displaying individual product information.

Responsibilities include:

- Receiving data from the parent component
- Displaying product information
- Handling user interaction
- Dispatching Custom Events
- Sending required information to the parent component

---

##  Component Communication

The project uses Salesforce LWC communication patterns.

### Parent to Child

The parent component passes information to the child component using `@api`.

### Child to Parent

The child component communicates with the parent using Custom Events.

This provides clear separation between the parent and child components.

---

##  Apex Integration

Apex is used to connect the LWC frontend with Salesforce backend operations.

The application uses Apex for:

- Retrieving data
- Processing user actions
- Applying business rules
- Performing database operations
- Returning results to the LWC

---

##  Apex Communication

### @wire

`@wire` is used for reactive data retrieval from Apex.

### Imperative Apex

Imperative Apex is used when an Apex method needs to be called as a result of an explicit user action.

---

## Business Logic

Business logic is handled on the backend instead of placing important business rules directly in the JavaScript code.

The backend is responsible for:

- Validating requests
- Validating available data
- Performing required business checks
- Processing operations
- Updating Salesforce records
- Returning the result

---

##  UI States

The application manages different states during user operations.

### Ready State

The user can perform the available action.

### Processing State

The requested operation is being processed.

The UI provides feedback and prevents unnecessary repeated actions.

### Success State

The operation completed successfully and the user receives a success message.

### Error State

The operation failed and an appropriate error message is displayed.

---

##  Error Handling

The application handles errors from both Apex and the LWC.

Errors are captured and converted into user-friendly messages.

The application avoids exposing unnecessary technical error details directly to the user.

---

##  Data Refresh

After a successful operation, the application refreshes the required data so that the UI displays the latest Salesforce information.

This helps keep the displayed data synchronized with the database.

---

## Testing

The application should be tested for the following scenarios:

- Data loads correctly
- Product information is displayed correctly
- User actions work correctly
- Correct information is passed between components
- Apex methods execute successfully
- Successful operations display the correct message
- Failed operations display an appropriate error message
- Processing state works correctly
- Repeated actions are prevented during processing
- Updated data is displayed after successful operations

---

## Key Concepts Learned

This project demonstrates the following Salesforce concepts:

- Lightning Web Components
- Parent and Child Components
- `@api`
- Custom Events
- Event Handling
- `@wire`
- Imperative Apex
- Apex Controllers
- Service Layer
- Business Logic Separation
- SOQL
- Salesforce Database Operations
- Loading State
- Success State
- Error Handling
- Data Refresh
- Component Reusability
- Separation of Responsibilities

---

##  Learning Outcome

This project provides practical understanding of how Salesforce LWC communicates with Apex and how frontend and backend responsibilities can be separated.

The main development flow is:

```text
User Action
    ↓
LWC
    ↓
JavaScript
    ↓
Apex
    ↓
Business Logic
    ↓
Salesforce Database
    ↓
Response
    ↓
LWC
    ↓
User Feedback
