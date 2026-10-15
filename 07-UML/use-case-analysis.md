# Use Case Analysis — TEKINO

## 1. Purpose

This document identifies the actors and use cases of the TEKINO Digital Products E-Commerce System as a preparation for the UML Use Case Diagram.

The analysis is based on the project's current stakeholder analysis, functional requirements, and user stories.

## 2. System Boundary

The system boundary is named **TEKINO Digital Products E-Commerce System**.

The TEKINO system includes product discovery, account access, shopping cart management, checkout, order tracking, administrative functions, and interaction with the external Payment Gateway.

External services are not considered internal components of the TEKINO system.

## 3. Actors

### ACT-01 — Customer

**Type:** Primary Actor

**Description:** A customer interacts with TEKINO to discover products and make purchases.

**Goals:**
- Browse, search, and filter products.
- View product details.
- Register and log in.
- Manage shopping cart items.
- Submit orders and pay online.
- Track order status.

### ACT-02 — Administrator

**Type:** Primary Actor

**Description:** An authorized administrator manages the main operational data of TEKINO.

**Goals:**
- Manage product information.
- Manage inventory quantities and availability.
- View and update order fulfillment status.
- Manage user accounts.

### ACT-03 — Payment Gateway

**Type:** External Supporting Actor

**Description:** An external service that processes payment requests and returns transaction results.

**Responsibilities:**
- Receive payment requests.
- Process payment transactions.
- Return payment status to TEKINO.

## 4. Identified Use Cases

| ID | Use Case | Primary Actor | Related Requirements |
|---|---|---|---|
| UC-01 | Browse Products | Customer | FR-01 |
| UC-02 | Search Products | Customer | FR-02 |
| UC-03 | Filter Products | Customer | FR-03 |
| UC-04 | View Product Details | Customer | FR-04 |
| UC-05 | Register | Customer | FR-05 |
| UC-06 | Log In | Customer | FR-06 |
| UC-07 | Manage Shopping Cart | Customer | FR-07 |
| UC-08 | Checkout / Place Order | Customer | FR-08, FR-10 |
| UC-09 | Process Payment | Payment Gateway | FR-09 |
| UC-10 | Track Order | Customer | FR-11 |
| UC-11 | Manage Products | Administrator | FR-12 |
| UC-12 | Manage Inventory | Administrator | FR-13 |
| UC-13 | Manage Orders | Administrator | FR-14 |
| UC-14 | Manage Users | Administrator | To be specified |

## 5. Main Use Case: Checkout / Place Order

The customer reviews the shopping cart, provides the required shipping information, reviews the order total, and confirms the purchase.

The system validates the cart and product availability before submitting the payment request to the external Payment Gateway.

If the payment result is confirmed as successful and validated, the system creates the order record and provides a confirmation to the customer.

If payment fails, the system informs the customer and does not mark the order as paid.

## 6. Actor–Use Case Associations

- Customer interacts with UC-01 through UC-08 and UC-10.
- The Payment Gateway participates in UC-09.
- Administrator interacts with UC-11 through UC-14.

The final UML diagram should show each actor outside the system boundary and the relevant use cases inside it.

## 7. Potential Use Case Relationships

The following relationships may be represented in the diagram when supported by the detailed process:

- Checkout / Place Order includes validating the shopping cart.
- Checkout / Place Order includes calculating the order total.
- Checkout / Place Order includes processing the payment.
- The Payment Gateway interacts with the Process Payment use case.

The `<<include>>` relationships indicate behavior required as part of the base use case. Optional or conditional behavior should not be represented using `<<include>>` unless it is always required.

## 8. Consistency and Scope Notes

- Product browsing and discovery are available without requiring registration.
- Checkout requires an authenticated customer under the current requirements.
- Payment processing is handled through an external Payment Gateway.
- An order must not be marked as paid before successful payment confirmation.
- Order tracking refers to viewing order history and order status.
- The Manage Users use case requires more detailed functional requirements before its behavior can be fully specified.
- Delivery Service is currently identified as a stakeholder, but its direct software interactions have not yet been defined in the functional requirements. It will not be added as an actor unless the scope is expanded.

## 9. Next Step

Use this analysis as the basis for drawing the UML Use Case Diagram, showing the TEKINO system boundary, actors, use cases, associations, and only the relationships justified by the requirements.
