# User Stories — TEKINO

## 1. Purpose

This document defines five user stories for the TEKINO Digital Products E-Commerce System.

Each user story describes a user goal and its expected benefit. Acceptance criteria are included to make the expected behavior clear and testable.

The stories are linked to the functional requirements documented in `03-Requirements/functional-requirements.md`.

---

## US-01 — Browse and Search Products

**User Story**

As a customer, I want to browse and search for digital products so that I can quickly find products that meet my needs.

**Priority:** High

**Related Requirements:** FR-01, FR-02, FR-03

**Acceptance Criteria**

1. Given that the customer opens the product catalog, when the catalog loads successfully, then the system displays the available products.
2. Given that the customer enters a product name or keyword, when the search is submitted, then the system displays matching products.
3. Given that the customer applies a supported filter, when the filter is applied, then the system displays products matching the selected criteria.
4. Given that no products match the search or filters, when the results are displayed, then the system shows an appropriate no-results message.

---

## US-02 — View Product Details

**User Story**

As a customer, I want to view detailed product information so that I can make an informed purchasing decision.

**Priority:** High

**Related Requirements:** FR-04

**Acceptance Criteria**

1. Given that a product is available in the catalog, when the customer selects it, then the system displays its product details.
2. The product details include the product name, price, description, and availability.
3. Given that the product is unavailable, when the customer views its details, then the system clearly indicates its availability status.

---

## US-03 — Register and Log In

**User Story**

As a customer, I want to register an account and log in securely so that I can access account-related features and manage my purchases.

**Priority:** High

**Related Requirements:** FR-05, FR-06

**Acceptance Criteria**

1. Given that a customer provides the required valid registration information, when the registration form is submitted, then the system creates the account.
2. Given that required information is missing or invalid, when the registration form is submitted, then the system displays appropriate validation messages.
3. Given that a registered customer enters valid login credentials, when the login form is submitted, then the system authenticates the customer.
4. Given that the login credentials are invalid, when the login form is submitted, then the system rejects the login attempt and displays an appropriate message.

---

## US-04 — Manage Shopping Cart

**User Story**

As a customer, I want to add products to my shopping cart, change quantities, and remove items so that I can prepare my purchase before checkout.

**Priority:** High

**Related Requirements:** FR-07

**Acceptance Criteria**

1. Given that a product is available for purchase, when the customer adds it to the cart, then the product appears in the cart.
2. Given that a product is already in the cart, when the customer changes its quantity to a valid value, then the cart updates the quantity and total price.
3. Given that a product is in the cart, when the customer removes it, then the product is no longer included in the cart.
4. The system prevents quantities that are invalid or exceed the available stock from being accepted.
5. The system displays an updated cart total after cart contents change.

---

## US-05 — Place an Order and Make Payment

**User Story**

As an authenticated customer, I want to submit my shopping cart as an order and pay online so that I can complete my purchase.

**Priority:** High

**Related Requirements:** FR-08, FR-09, FR-10

**Acceptance Criteria**

1. Given that the customer is authenticated and the cart contains available products, when the customer proceeds to checkout, then the system requests the required shipping information.
2. Given that the required shipping information is valid, when the customer reviews the order, then the system displays the order items and total amount before confirmation.
3. Given that the customer confirms the order, when payment is initiated, then the system sends the payment request to the external Payment Gateway.
4. Given that the Payment Gateway confirms successful payment and the result is validated, when the system processes the response, then it creates the order record and displays an order confirmation.
5. Given that the payment fails or is declined, when the system receives the payment result, then it informs the customer and does not mark the order as paid.
6. The system must validate product availability before confirming the purchase.

---

## 2. Definition of Done

A user story can be considered complete when:

- Its acceptance criteria have been reviewed and satisfied.
- The implemented behavior has been tested.
- No known critical defect prevents the expected behavior.
- Relevant project documentation has been updated.
- The completed work has been reviewed according to the team's agreed process.

## 3. Agile Note

These five user stories form an initial set of Product Backlog candidates.

Their priorities are provisional and should be reviewed by the Product Owner. During backlog refinement and Sprint Planning, the team may clarify the stories, estimate their effort, identify dependencies, and select suitable stories for a Sprint.

The user stories describe intended functionality; they do not imply that the functionality has already been implemented.
