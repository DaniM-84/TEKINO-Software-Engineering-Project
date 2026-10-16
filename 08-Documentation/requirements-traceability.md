# Requirements Traceability Matrix — TEKINO

## 1. Purpose

This document establishes traceability between the functional requirements, user stories, Product Backlog items, UML use cases, and the main purchasing activity of the TEKINO Digital Products E-Commerce System.

The purpose is to identify which requirements are covered by the current project artifacts, which items are planned for the first Sprint, and which requirements still need detailed user stories and implementation planning.

## 2. Functional Requirements Traceability

| Requirement ID | Requirement Summary | User Story | Use Case | Sprint / Planning Status |
|---|---|---|---|---|
| FR-01 | Browse products | US-01 | UC-01 Browse Products | Sprint 1 planned |
| FR-02 | Search products | US-01 | UC-02 Search Products | Sprint 1 planned |
| FR-03 | Filter products | US-01 | UC-03 Filter Products | Sprint 1 planned |
| FR-04 | View product details | US-02 | UC-04 View Product Details | Sprint 1 planned |
| FR-05 | Register an account | US-03 | UC-05 Register | Product Backlog |
| FR-06 | Log in | US-03 | UC-06 Log In | Product Backlog |
| FR-07 | Manage the shopping cart | US-04 | UC-07 Manage Shopping Cart | Product Backlog |
| FR-08 | Submit checkout and shipping information | US-05 | UC-08 Checkout / Place Order | Product Backlog |
| FR-09 | Process online payments | US-05 | UC-09 Process Payment | Product Backlog |
| FR-10 | Create an order after successful payment | US-05 | UC-08 Checkout / Place Order | Product Backlog |
| FR-11 | View order history and track order status | Future user story required | UC-10 Track Order | Not yet included in the five initial stories |
| FR-12 | Manage product information | Future user story required | UC-11 Manage Products | Not yet included in the five initial stories |
| FR-13 | Manage inventory | Future user story required | UC-12 Manage Inventory | Not yet included in the five initial stories |
| FR-14 | Manage order fulfillment status | Future user story required | UC-13 Manage Orders | Not yet included in the five initial stories |

## 3. User Story and Sprint Traceability

| User Story | Product Backlog | Selected for Sprint 1 | Related UML Elements |
|---|---|---|---|
| US-01 — Browse and Search Products | Yes | Yes | UC-01, UC-02, UC-03 |
| US-02 — View Product Details | Yes | Yes | UC-04 |
| US-03 — Register and Log In | Yes | No | UC-05, UC-06 |
| US-04 — Manage Shopping Cart | Yes | No | UC-07 |
| US-05 — Place an Order and Make Payment | Yes | No | UC-08, UC-09 |

Sprint 1 has a planned total of 8 Story Points. Its selected items are US-01 and US-02. The status represents planning, not completed implementation.

## 4. Non-Functional Requirements Verification

Non-functional requirements describe system-wide quality attributes. They are generally verified through suitable testing, reviews, monitoring, or operational procedures rather than by creating a separate use case for every quality attribute.

| Requirement ID | Quality Attribute | Planned Verification |
|---|---|---|
| NFR-01 | Performance | Measure response times under agreed test conditions |
| NFR-02 | Security | Review password storage and authentication implementation |
| NFR-03 | Access Control | Test authorization for administrative functions |
| NFR-04 | Reliability | Test payment failure, successful payment confirmation, and order-state handling |
| NFR-05 | Usability | Conduct usability testing of the main shopping workflow |
| NFR-06 | Availability | Monitor service availability after deployment |
| NFR-07 | Compatibility | Test supported browser versions |
| NFR-08 | Maintainability | Review code structure and documentation |
| NFR-09 | Data Integrity | Test stock validation, quantity validation, and order consistency |
| NFR-10 | Privacy | Review access restrictions on customer and order data |
| NFR-11 | Responsiveness | Test the interface at mobile, tablet, and desktop viewport sizes |
| NFR-12 | Recovery | Test the documented backup and recovery procedure |

These verification activities are planned. No test results are claimed until the tests have actually been performed.

## 5. UML Model Traceability

### Use Case Diagram

The Use Case Diagram represents the identified actors and the services they interact with.

- Customer interactions include product discovery, account access, shopping cart management, checkout, and order tracking.
- Administrator interactions include product management, inventory management, and order management.
- Payment Gateway participates in the payment interaction.

### Activity Diagram

The Activity Diagram models the principal purchase workflow:

1. Search for and select a product.
2. Add the product to the shopping cart.
3. Proceed to checkout.
4. Authenticate the customer when required.
5. Validate the cart and product availability.
6. Calculate the order total.
7. Submit a payment request.
8. Handle successful or failed payment results.
9. Create the order following validated successful payment.

The diagram should show that an unsuccessful payment does not result in an order being marked as paid.

## 6. Coverage Gaps and Next Actions

The five initial user stories do not cover every functional requirement. The following items require further Product Backlog refinement:

- Create a user story for viewing order history and tracking order status.
- Create a user story for administrator product management.
- Create a user story for inventory management.
- Create a user story for order fulfillment management.
- Refine the Manage Users use case only after its functional requirements have been defined.
- Add test cases for the non-functional requirements as implementation progresses.

These gaps are recorded intentionally so that future work can be prioritized instead of being treated as already completed.

## 7. Agile Maintenance

This traceability matrix should be updated whenever a requirement changes, a new user story is created, a backlog item is reprioritized, a UML model is revised, or a Sprint result changes the project status.

The Product Backlog remains the prioritized source of planned product work. Sprint Backlog items describe the work selected for a particular Sprint.

## 8. Current Project Status

- Project overview: Documented
- Stakeholders: Identified
- Functional requirements: Documented
- Non-functional requirements: Documented
- Five initial user stories: Documented with acceptance criteria
- Initial Product Backlog: Created
- Sprint 1: Planned
- Use Case Diagram: Created
- Purchase Activity Diagram: Created
- Requirements traceability: Documented in this file
- Implementation and test execution: Not claimed as completed
