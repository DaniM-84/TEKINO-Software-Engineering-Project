# Functional Requirements — TEKINO

## 1. Purpose

This document defines the initial functional requirements of the TEKINO Digital Products E-Commerce System.

Functional requirements describe the services and behaviors that the system must provide to its users and external systems.

These requirements are initial and may be refined as the team receives feedback and develops the Product Backlog using an Agile approach.

## 2. Functional Requirements

| ID | Functional Requirement | Priority | Related Stakeholder |
|---|---|---|---|
| FR-01 | The system shall allow customers to browse the available product catalog. | High | Customer |
| FR-02 | The system shall allow customers to search for products by name or keyword. | High | Customer |
| FR-03 | The system shall allow customers to filter products by category, price range, and availability. | Medium | Customer |
| FR-04 | The system shall display product details, including name, price, description, and availability. | High | Customer |
| FR-05 | The system shall allow customers to register an account using the required information. | High | Customer |
| FR-06 | The system shall allow registered customers to log in to their accounts. | High | Customer |
| FR-07 | The system shall allow customers to add products to their shopping carts, change quantities, and remove items. | High | Customer |
| FR-08 | The system shall allow authenticated customers to submit shipping information and review their orders before confirmation. | High | Customer |
| FR-09 | The system shall send payment requests to the external Payment Gateway and handle the returned payment status. | High | Customer, Payment Gateway |
| FR-10 | The system shall create an order record after successful payment confirmation. | High | Customer, Administrator |
| FR-11 | The system shall allow customers to view their order history and the current status of each order. | Medium | Customer |
| FR-12 | The system shall allow administrators to add new products and update or remove existing product information. | High | Administrator |
| FR-13 | The system shall allow authorized administrators to update product stock quantities and availability. | High | Administrator, Inventory Staff |
| FR-14 | The system shall allow administrators to view customer orders and update their fulfillment status. | High | Administrator, Customer Support Staff |

## 3. Priority Definitions

- **High:** Essential for the initial usable version of the system.
- **Medium:** Valuable functionality that can be scheduled according to capacity and stakeholder feedback.
- **Low:** Functionality that is useful but not essential for the initial version.

Priorities are provisional and may change during Product Backlog refinement.

## 4. Initial Business Rules

- Customers may browse the product catalog without logging in.
- Customers must log in or register before submitting an order.
- The system must check product availability before an order is confirmed.
- An order must not be marked as paid unless the payment result has been confirmed.
- Product and inventory management operations must be restricted to authorized staff.
- Customers may view only their own order information.

## 5. Relationship to Agile Development

These functional requirements provide input for the creation and refinement of user stories and Product Backlog items.

During Sprint Planning, the team may select high-priority requirements for implementation. Each selected item should have clear acceptance criteria and should be tested against its expected behavior.

The requirements may be updated based on stakeholder feedback, technical findings, and the results of Sprint Reviews.

## 6. Scope Note

The requirements describe the intended behavior of the proposed TEKINO system. They do not indicate that the functionality has already been implemented.

The payment gateway and delivery service are treated as external systems or organizations.
