# Non-Functional Requirements — TEKINO

## 1. Purpose

This document defines the initial non-functional requirements of the TEKINO Digital Products E-Commerce System.

Non-functional requirements describe the quality attributes, operational constraints, and performance expectations of the system.

The requirements below are proposed initial targets for the academic project. They may be refined as the project scope, architecture, and technical constraints become clearer.

## 2. Non-Functional Requirements

| ID | Quality Attribute | Requirement | Verification Method |
|---|---|---|---|
| NFR-01 | Performance | Under the agreed normal-load test conditions, at least 95% of product browsing and search requests shall receive a response within 2 seconds. | Performance testing |
| NFR-02 | Security | User passwords shall not be stored as plaintext; an appropriate password-hashing mechanism shall be used. | Code and configuration review |
| NFR-03 | Access Control | Only authenticated and authorized staff shall be able to access administrative functions. | Authorization testing |
| NFR-04 | Reliability | The system shall not create a paid order unless successful payment confirmation has been received and validated. | Integration and scenario testing |
| NFR-05 | Usability | Customers shall be able to identify the product search, shopping cart, and checkout options from the main shopping interface. | Usability testing |
| NFR-06 | Availability | The target availability shall be at least 99% per calendar month, excluding agreed maintenance windows. | Availability monitoring |
| NFR-07 | Compatibility | The web interface shall support the latest stable versions of Chrome, Firefox, Edge, and Safari at the time of release. | Browser compatibility testing |
| NFR-08 | Maintainability | The project shall organize requirements, application components, and tests into clearly named and documented sections or modules. | Documentation and code review |
| NFR-09 | Data Integrity | The system shall validate order quantities and product availability before confirming an order. | Functional and integration testing |
| NFR-10 | Privacy | The system shall restrict access to personal and order information to authorized users with a legitimate need. | Access-control and privacy review |
| NFR-11 | Responsiveness | The shopping interface shall remain usable at mobile, tablet, and desktop viewport sizes. | Responsive interface testing |
| NFR-12 | Recovery | The system shall have a documented backup and recovery procedure for critical order and product data before production release. | Recovery procedure test |

## 3. Quality Attribute Categories

### Performance

The system should respond quickly to customer actions, particularly product searches, browsing, and checkout operations.

### Security and Privacy

The system must protect authentication credentials, customer information, order records, and administrative functions.

### Reliability and Data Integrity

The system must preserve consistent order and payment states and prevent invalid or duplicate operations from corrupting transaction records.

### Usability and Responsiveness

Customers should be able to use the main shopping functions across common device sizes without unnecessary difficulty.

### Compatibility

The interface should behave consistently across the supported browsers.

### Maintainability and Recovery

The project should remain understandable and modifiable, and critical data should be recoverable through a documented procedure.

## 4. Relationship to Agile Development

Non-functional requirements must be considered while creating and refining Product Backlog items, planning Sprints, designing the system, and defining acceptance criteria.

Some requirements may apply to the entire system rather than to a single user story. For example, security and performance must be considered across multiple features.

The team should verify applicable non-functional requirements during development and testing instead of leaving all quality checks until the end.

## 5. Assumptions and Validation

- The response-time and availability values are initial project targets, not verified results.
- The supported browser versions will be confirmed when a release is planned.
- Security and privacy controls will be refined according to the selected technology and payment integration.
- Backup, recovery, and performance expectations will be reviewed as implementation constraints become known.

No requirement in this document implies that the system has already been implemented or tested.
