# Final Project Review Checklist — TEKINO

## 1. Purpose

This document provides a final review checklist for the TEKINO Digital Products E-Commerce System academic project.

The checklist evaluates documentation coverage, consistency between requirements and UML models, and alignment with the planned Agile approach.

Items should be marked complete only after the corresponding files and artifacts have been reviewed.

## 2. Project Documentation Checklist

- [ ] Project overview and product vision are documented in README.md.
- [ ] Stakeholders and their needs are documented.
- [ ] Functional requirements are documented and have unique identifiers.
- [ ] Non-functional requirements include verification methods or measurable targets where appropriate.
- [ ] Five user stories are documented with acceptance criteria.
- [ ] The Product Backlog includes priorities, Story Points, and statuses.
- [ ] Sprint 1 includes a Sprint Goal, selected user stories, tasks, and a Definition of Done.
- [ ] Use Case analysis identifies the system boundary and actors.
- [ ] The Use Case Diagram is available as PNG and editable draw.io files.
- [ ] The Activity Diagram models the main purchasing process.
- [ ] The Requirements Traceability Matrix links requirements, stories, and use cases.
- [ ] README.md links to the relevant documentation and displays the diagrams correctly.

## 3. Requirements Consistency

- [ ] FR-01 through FR-04 are represented by US-01 and US-02.
- [ ] FR-05 and FR-06 are represented by US-03.
- [ ] FR-07 is represented by US-04.
- [ ] FR-08 through FR-10 are represented by US-05.
- [ ] FR-11 through FR-14 are identified as requirements requiring additional user stories or further backlog refinement.
- [ ] The deferred Manage Users use case is not presented as a fully specified feature.
- [ ] Non-functional requirements are treated as quality requirements rather than ordinary user actions.

## 4. UML Diagram Review

### Use Case Diagram

- [ ] The Customer, Administrator, and Payment Gateway actors are shown.
- [ ] Actors are outside the TEKINO system boundary.
- [ ] Use cases are inside the system boundary.
- [ ] Actor associations use solid lines.
- [ ] Include relationships use dashed arrows pointing toward the included use case.
- [ ] The diagram is readable and does not contain unintended overlaps.

### Activity Diagram

- [ ] The diagram includes an initial node and appropriate final nodes.
- [ ] The main purchasing process is represented.
- [ ] Customer, TEKINO System, and Payment Gateway responsibilities are distinguishable.
- [ ] Decision branches are labeled clearly.
- [ ] Invalid cart or shipping information is handled.
- [ ] Successful payment leads to validated order creation and confirmation.
- [ ] Failed payment does not result in an order being marked as paid.
- [ ] Retry and cancellation paths are understandable.

## 5. Agile Process Review

- [ ] The Product Vision defines the intended value of the system.
- [ ] The Product Backlog is ordered by priority.
- [ ] Story Points are treated as relative estimates rather than hours.
- [ ] Sprint 1 has a clear Sprint Goal.
- [ ] Selected Sprint items are identifiable in the Product Backlog.
- [ ] Tasks are associated with the selected user stories.
- [ ] The Definition of Done is documented.
- [ ] Sprint Review and Retrospective activities are documented as planned activities.
- [ ] Work is not marked Done unless it has actually been completed and reviewed.

## 6. Remaining Work and Limitations

The initial five user stories do not cover every functional requirement.

Additional backlog refinement should address:

- Viewing order history and tracking order status.
- Administrator product management.
- Inventory management.
- Order fulfillment management.

Implementation and test execution remain separate from the documentation and modeling work unless the course instructor specifically requires a working software increment.

The non-functional requirements contain proposed targets. Their actual achievement must not be claimed until suitable verification has been performed.

## 7. Final Assessment

The project should be considered ready for academic submission only after the applicable checklist items have been reviewed, the GitHub links have been checked, and the required artifacts are available in the repository.

This document is a review checklist, not evidence that every item has already been completed.
