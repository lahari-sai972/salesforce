# Sprint 11 – Crossing the Salesforce Boundary

## External Integration: Shipment Sync, Coupon Validation & Nightly Stock Sync

This sprint extends the Placement/E-commerce Salesforce application to communicate with external systems.

The goal is to move the application from a self-contained Salesforce solution to an integration-enabled system that can securely communicate with external APIs.

The sprint implements three major Salesforce integration patterns:

1. Asynchronous Shipment Sync with Retry
2. Synchronous Coupon Validation
3. Scheduled + Batch Nightly Stock Synchronization

---

# 1. Business Problem

Our e-commerce system does not directly manage deliveries. A third-party courier partner is responsible for shipment processing.

Previously, Salesforce had no mechanism to:

- Notify the courier when a shipment was created
- Validate coupon codes against an external service
- Receive stock updates from a warehouse system
- Automatically recover from temporary integration failures

This sprint solves these problems by introducing Salesforce-to-external-system integrations.

---

# 2. Integration Requirements

| Task | Business Need | Integration Pattern |
|------|---------------|---------------------|
| Task 1 & 2 | Notify courier when shipment is created and retry if notification fails | Asynchronous Callout + Retry |
| Task 3 | Validate coupon code while customer waits | Synchronous Callout |
| Task 4 | Synchronize stock for active products every night | Scheduled Apex + Batch Apex + Callout |

---

# 3. External System

For this sprint, a mock REST API was used instead of a real courier or warehouse API.

### Mock API

`https://httpbin.org`

HTTPBin is useful for integration testing because it can:

- Echo HTTP requests
- Return HTTP status codes
- Simulate successful responses
- Help test error handling
- Help validate request and response processing

> **Note:** This is a mock integration created for learning and development purposes. In production, the HTTPBin endpoint would be replaced with the actual courier, warehouse, or validation service endpoint.

---

# 4. Architecture

The sprint contains three independent integration flows.

## Shipment Synchronization

```text
Shipment__c Created
        |
        v
ShipmentSyncQueueable
        |
        v
Named Credential
(Courier_API)
        |
        v
HTTP POST
        |
        v
External Courier API
        |
        v
Response Processing
        |
        v
Integration_Status__c Updated
        |
        +----------------------+
        |                      |
      Sent               Retry Required
                               |
                               v
                     ShipmentRetryBatch
                               |
                               v
                     ShipmentSyncQueueable
