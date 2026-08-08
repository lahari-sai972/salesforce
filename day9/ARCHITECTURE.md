# 🏗️ Architecture

The application follows a layered architecture that separates the user interface, component communication, backend processing, business logic, and database operations.

## Architecture Flow

```text
                         USER
                           │
                           ▼
                 ┌───────────────────┐
                 │   LWC UI Layer    │
                 │                   │
                 │  ecommerceHome    │
                 │     Parent        │
                 │        │          │
                 │        │ @api     │
                 │        ▼          │
                 │   productChild    │
                 │      Child        │
                 │        │          │
                 │        │ Custom   │
                 │        │ Event    │
                 └────────┼──────────┘
                          │
                          ▼
                 ┌───────────────────┐
                 │ Apex Controller   │
                 │                   │
                 │ Receives Request  │
                 │ Calls Service     │
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │  Service Layer    │
                 │                   │
                 │ Business Logic    │
                 │ Validation        │
                 │ Processing        │
                 │ Data Operations   │
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │ Salesforce        │
                 │ Database          │
                 │                   │
                 │ Store Data        │
                 │ Update Data       │
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │     Response      │
                 │                   │
                 │ Success / Error   │
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │     LWC UI        │
                 │                   │
                 │ Loading State     │
                 │ Success State     │
                 │ Error State       │
                 │ Data Refresh      │
                 └───────────────────┘
1. User Layer

The user interacts with the application through the Lightning Web Component interface.

Responsibilities:

View the available information
Perform user actions
Receive operation results
View success or error messages
2. LWC UI Layer

The LWC layer is responsible for the user interface and user interaction.

ecommerceHome

ecommerceHome acts as the parent component.

Responsibilities:

Manage the main UI
Retrieve and maintain data
Pass data to the child component
Handle events from the child component
Initiate backend requests
Manage loading state
Manage success and error states
Refresh data when required
productChild

productChild acts as the child component.

Responsibilities:

Display individual data
Receive data from the parent
Handle user interaction
Dispatch events to the parent
3. Component Communication
Parent to Child

The parent communicates with the child using public properties with @api.

Parent Component
       │
       │ @api
       ▼
Child Component
Child to Parent

The child communicates with the parent using Custom Events.

Child Component
       │
       │ Custom Event
       ▼
Parent Component
4. Apex Controller Layer

The Apex Controller acts as the entry point between the LWC layer and backend logic.

Responsibilities:

Receive requests from LWC
Accept required parameters
Call the service layer
Return the result to LWC

The controller should remain focused on request handling and delegation.

5. Service Layer

The Service Layer contains the application's business logic.

Responsibilities:

Validate incoming requests
Apply business rules
Perform required processing
Perform database operations
Handle successful processing
Return the required result

Keeping business logic in the service layer improves maintainability and separation of responsibilities.

6. Salesforce Database Layer

The Salesforce database is responsible for storing and managing application data.

Responsibilities:

Store records
Retrieve records
Update records
Maintain data consistency

The service layer communicates with the database to perform required operations.

7. Response Layer

After backend processing is completed, the result is returned to the LWC.

The response can represent:

Successful operation
Validation failure
Business error
Processing error

The LWC uses the response to update the user interface.

8. UI State Management

The application manages different UI states throughout the operation.

READY
  │
  ▼
PROCESSING
  │
  ├──────────────► SUCCESS
  │
  └──────────────► ERROR
Ready State

The user can perform the available action.

Processing State

The operation is being processed.

The UI provides feedback and prevents unnecessary repeated actions.

Success State

The operation completed successfully and the UI displays the result.

Error State

The operation failed and the UI displays an appropriate error message.

9. Data Refresh

After a successful data-changing operation:

Operation Completed
        │
        ▼
Data Changed
        │
        ▼
Refresh Data
        │
        ▼
Update UI

This ensures that the displayed information remains synchronized with the latest Salesforce data.

10. Apex Communication

The application uses different Apex communication patterns based on the requirement.

Data Retrieval
LWC
 │
 └── @wire
       │
       ▼
     Apex
User-Initiated Action
User Action
     │
     ▼
JavaScript Handler
     │
     ▼
Imperative Apex
     │
     ▼
Apex Controller
11. Complete Request Flow
User
  ↓
LWC
  ↓
User Interaction
  ↓
Child Component
  ↓
Custom Event
  ↓
Parent Component
  ↓
Imperative Apex
  ↓
Apex Controller
  ↓
Service Layer
  ↓
Business Logic
  ↓
Salesforce Database
  ↓
Response
  ↓
LWC
  ↓
Success / Error
  ↓
Data Refresh
  ↓
Updated UI

