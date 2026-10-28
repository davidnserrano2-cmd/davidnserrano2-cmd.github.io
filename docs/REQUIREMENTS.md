---
layout: document
title: Requirements Catalogue
description: Portfolio-developed functional and nonfunctional requirements with acceptance conditions.
---

# Requirements Catalogue

**Status:** Portfolio analysis artifact derived from the thesis and supplied code. These requirements are not stakeholder-approved or implemented in the prototype.

## Stakeholders and priorities

- **Administrator:** manages authorized users and reviews events.
- **Person requesting access:** receives a clear, timely outcome.
- **Support technician:** identifies device, connection, and database problems.
- **Project sponsor:** needs a maintainable solution with an understandable operating cost and risk profile.

Priority uses MoSCoW: **Must** is required for the demonstration's core workflow; **Should** improves operational usefulness; **Could** is optional within the timebox.

## Functional requirements

| ID | Requirement | Priority | Acceptance condition (not executed) | Status |
|---|---|---|---|---|
| FR-01 | The system shall evaluate an access request using the configured authentication factors for an active user. | Must | Given an active synthetic user and valid required factors, the system records an allow outcome; an invalid factor or inactive user produces a deny outcome. | Not implemented |
| FR-02 | The system shall provide a clear outcome to the person requesting access and an explanatory status to the administrator. | Must | Allow, deny, and unavailable states are distinguishable in the demonstration without revealing secret factors. | Portfolio analysis |
| FR-03 | The system shall record each access outcome with a timestamp, device reference, authentication method, result, and an appropriate failure reason. | Must | A reviewer can locate the corresponding event for successful and unsuccessful synthetic scenarios. | Not implemented |
| FR-04 | The system shall allow an administrator to review and filter recent access events. | Must | An administrator can find events by time range, device, result, and failure category in the chosen interface. | Portfolio analysis |
| FR-05 | The system shall allow an authorized administrator to add, update, or deactivate a user. | Should | A deactivated synthetic user is denied access, and the user-management action is auditable. | Not implemented |
| FR-06 | The system shall report device, serial-connection, and persistence failures to the administrator. | Should | Disconnecting the simulator or database produces a visible degraded state and a documented recovery action. | Portfolio analysis |
| FR-07 | The demonstration shall support a simulator that emits documented device messages without requiring physical hardware. | Must | A clean install can demonstrate allow, deny, and device-error scenarios with synthetic records. | Portfolio requirement |
| FR-08 | The system shall record security-relevant events separately from ordinary access outcomes when appropriate. | Could | A simulated tamper or repeated-failure scenario is recorded as a distinct event category. | Not implemented |

## Nonfunctional requirements

| ID | Requirement | Priority | Acceptance condition (not executed) | Status |
|---|---|---|---|---|
| NFR-01 | The system shall not place PINs, admin passwords, or raw authentication messages in access logs or public examples. | Must | Sample records and displayed event details contain no secret factors; public repository review finds no live data files. | Security baseline |
| NFR-02 | Credential material shall be protected in storage and configuration; application secrets shall not be committed to source control. | Must | Setup instructions use local configuration outside the repository and provide only placeholder examples. | Security baseline |
| NFR-03 | Any network-accessible administrator function shall require authentication and use a documented, restricted network configuration. | Must if network UI selected | An unauthenticated client cannot view logs or change users; demo instructions describe the local-only default. | Depends on architecture choice |
| NFR-04 | The system shall have a documented failure policy for loss of serial communication, database access, or network connectivity. | Must | For each failure condition, the design states the access decision, visible status, event-handling behavior, and recovery step. | Not implemented |
| NFR-05 | A new reviewer shall be able to install and run the synthetic demonstration from documented steps. | Must | The documented setup reaches the demo workflow without the original database, credentials, or hardware. | Portfolio requirement |
| NFR-06 | The system shall retain only event information required for operations and investigation. | Should | The data dictionary identifies purpose and sensitivity; a retention period is not set. | Not implemented |

## Traceability and assumptions

- FR-01 through FR-03 describe the central access and audit workflow described by the thesis prototype; factor policy and event detail still require confirmation.
- FR-04 and FR-05 reflect administrator screens and functions in the supplied dashboard, not verified stakeholder approval.
- FR-06 and FR-07 address the serial-connection problems and hardware-free demonstration need identified during the portfolio review.
- NFR-01 and NFR-02 are public-release safeguards for the case study; they are not a claim that the existing prototype meets them.
- NFR-03 applies only if the future-state option exposes an interface over a network.
- No production service-level target, retention period, user count, or availability percentage is set yet. Those require discovery rather than invention.

## Open decisions

1. Which authentication factors are mandatory, and what is the approved recovery process when a factor is unavailable?
2. Should the future state be local-only or support remote administration?
3. What should happen during a database or serial-device outage: deny all access, use a limited offline policy, or use another approved behavior?
4. Which event fields are required for investigations, and what retention period is acceptable?
5. Who may manage users, and how should administrative changes be approved and audited?
