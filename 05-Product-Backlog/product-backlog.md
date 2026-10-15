# Product Backlog — TEKINO

## 1. Purpose

The Product Backlog contains the prioritized features and work items required to develop the TEKINO Digital Products E-Commerce System.

The backlog is initially based on the five user stories documented in `04-User-Stories/user-stories.md`.

It is an evolving artifact that may be refined as stakeholder needs, technical constraints, and feedback become clearer.

## 2. Product Backlog Items

| Rank | ID | Product Backlog Item | Related Requirements | Priority | Story Points | Status |
|---:|---|---|---|---|---:|---|
| 1 | US-01 | Browse and Search Products | FR-01, FR-02, FR-03 | High | 5 | To Do |
| 2 | US-02 | View Product Details | FR-04 | High | 3 | To Do |
| 3 | US-03 | Register and Log In | FR-05, FR-06 | High | 5 | To Do |
| 4 | US-04 | Manage Shopping Cart | FR-07 | High | 5 | To Do |
| 5 | US-05 | Place an Order and Make Payment | FR-08, FR-09, FR-10 | High | 8 | To Do |

## 3. Backlog Ordering

The initial ordering considers customer value, dependencies between features, and the need to establish the main shopping journey.

1. **US-01 — Browse and Search Products:** Enables customers to discover available products.
2. **US-02 — View Product Details:** Gives customers the information needed to evaluate a product.
3. **US-03 — Register and Log In:** Provides account access needed for authenticated purchasing.
4. **US-04 — Manage Shopping Cart:** Enables customers to prepare and review their intended purchases.
5. **US-05 — Place an Order and Make Payment:** Completes the main purchasing process and depends on several preceding capabilities.

All priorities and ranks are initial proposals. The Product Owner may change the ordering when business needs or stakeholder feedback change.

## 4. Story Point Estimation

Story Points are relative estimates of the effort, complexity, and uncertainty associated with a backlog item. They do not represent hours or exact calendar days.

For this initial academic backlog, the following values are proposed:

- 3 points: relatively small and straightforward work.
- 5 points: moderate work or uncertainty.
- 8 points: more complex work involving several steps or external integration.

The estimates should be reviewed by the development team during backlog refinement.

## 5. Dependencies and Considerations

- US-02 builds on the product catalog introduced by US-01.
- US-03 is needed before a customer can complete an authenticated checkout.
- US-04 depends on the availability of product information and valid product selections.
- US-05 depends on checkout information, shopping cart behavior, and integration with the external Payment Gateway.

These dependencies help inform Sprint Planning. They do not prevent the team from researching or designing later features earlier.

## 6. Backlog Refinement

During backlog refinement, the team may:

- Clarify requirements and user-story details.
- Review and update acceptance criteria.
- Reassess priorities and Story Points.
- Identify dependencies and technical risks.
- Split large stories into smaller, testable stories when appropriate.
- Add new items based on stakeholder feedback.

## 7. Relationship to Agile Sprints

The Product Backlog is the source from which work items are selected during Sprint Planning.

The team should select items according to priority, dependencies, available capacity, and the Sprint Goal. The selected stories and their supporting tasks will form the Sprint Backlog.

The current statuses indicate that these items are planned but not yet implemented. A status should only change when the corresponding work has actually progressed.

## 8. Current Status

The initial Product Backlog contains five user stories.

No Sprint commitment or completed implementation is claimed at this stage.
