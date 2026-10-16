# Activity Diagram — Purchase Product

## Purpose
This UML Activity Diagram models the main TEKINO shopping process from product discovery through checkout and payment.

## Swimlanes
- **Customer:** browses and selects products, manages the cart, supplies shipping information, reviews the order, and chooses whether to retry a failed payment.
- **TEKINO System:** displays products, updates and validates the cart, checks authentication, validates shipping details and availability, calculates the total, sends payment requests, and creates an order only after successful payment confirmation.
- **Payment Gateway:** processes the payment transaction and returns its result.

## Main Flow
1. The customer browses or searches products and selects one.
2. TEKINO displays product details and updates the shopping cart.
3. The customer proceeds to checkout. If the customer is not authenticated, they register or log in.
4. The customer enters shipping details; TEKINO validates the cart, stock, and required details. Invalid details return to correction and validation.
5. TEKINO calculates and displays the total. The customer reviews and confirms the order.
6. TEKINO sends a payment request to the external Payment Gateway.
7. If payment is successful and the returned result is validated, TEKINO creates the order and displays a confirmation.
8. If payment fails, the customer may retry payment or cancel checkout.

## UML Notation
- Filled circle: initial node.
- Rounded rectangle: action.
- Diamond: decision / merge condition with Yes/No branches.
- Bullseye: activity final node.
- Arrows: control flows.
- Vertical partitions: swimlanes showing responsibility.

## Related Requirements
This diagram models the purchase and checkout workflow and is consistent with the current functional requirements for browsing and search (FR-01 to FR-03), product details (FR-04), account registration and login (FR-05 and FR-06), cart management (FR-07), checkout and shipping information (FR-08), payment processing (FR-09), and order creation following successful payment confirmation (FR-10).

Order tracking (FR-11) is represented separately in the Use Case Diagram because it is outside the main purchase workflow modeled by this Activity Diagram.

## Scope Note
This diagram represents the intended behavior of the proposed system. It does not claim the software has been implemented. Order creation occurs only after successful payment confirmation has been validated.
