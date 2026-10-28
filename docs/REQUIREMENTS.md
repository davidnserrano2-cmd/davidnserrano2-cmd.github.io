---
layout: document
title: Requirements Analysis
description: Functional and nonfunctional requirements for a future version of the RFID access-control prototype.
---

# Requirements Analysis

**Scope:** These portfolio-developed requirements describe a successor version, based on the thesis and supplied code. They are not stakeholder-approved; the acceptance criteria below have not been tested in a new implementation.

## System actors

- **Person requesting access:** presents credentials and receives an outcome.
- **Administrator:** manages users and reviews access events.
- **Support technician:** investigates device, connection, and persistence failures.

Priorities use MoSCoW: **Must** is essential to the core workflow; **Should** improves operational usefulness; **Could** is optional to the initial scope.

## Functional requirements

| ID | Requirement | Priority | Acceptance criteria | Prototype evidence |
|---|---|---|---|---|
| FR-01 | Evaluate an access request using the configured factors for an active user. | Must | A valid request records an allow outcome; an invalid factor or inactive user records a deny outcome. | Allow and deny outcomes are shown in the thesis demonstration. |
| FR-02 | Present a clear outcome to the person requesting access and status to the administrator. | Must | Allow, deny, and unavailable states are distinguishable without revealing secret factors. | Device outcomes and dashboard status are shown in the recordings. |
| FR-03 | Record each access outcome with a timestamp, device reference, authentication method, result, and failure reason. | Must | An administrator can locate events for successful and unsuccessful scenarios. | Activity logging is shown; complete field coverage is not demonstrated. |
| FR-04 | Let an administrator review and filter recent access events. | Must | An administrator can filter by time range, device, result, and failure category. | The dashboard displays recent activity; filtering is not demonstrated. |
| FR-05 | Let an authorized administrator add, update, or deactivate a user. | Should | A deactivated user is denied access, and each user-management action is auditable. | User-management controls are present; audit behavior is not demonstrated. |
| FR-06 | Report device, serial-connection, and persistence failures to the administrator. | Should | Failure states are visible and include a documented recovery action. | Serial disconnection is visible in the dashboard; database failure handling is not demonstrated. |
| FR-07 | Provide a simulator for documented device messages without physical hardware. | Must | A clean installation demonstrates allow, deny, and device-error scenarios with synthetic records. | Not included in the supplied project copy. |
| FR-08 | Record tamper and repeated-failure events separately from ordinary access outcomes. | Could | Simulated tamper and repeated-failure scenarios are recorded as distinct event categories. | Not demonstrated in the supplied files. |

## Nonfunctional requirements

| ID | Requirement | Priority | Acceptance criteria | Prototype evidence |
|---|---|---|---|---|
| NFR-01 | Exclude PINs, admin passwords, and raw authentication messages from access logs and public examples. | Must | Logs and public demonstrations reveal no secret factors or live records. | Public recordings mask inputs; older source variants preserve raw messages in logs. |
| NFR-02 | Protect credential material in storage and configuration; keep application secrets out of source control. | Must | Local configuration stores secrets outside the repository; public examples contain no credentials. | Legacy source variants contain demo credentials and do not meet this requirement. |
| NFR-03 | Require authentication and restricted network configuration for network-accessible administration. | Must if network administration is selected | Unauthenticated clients cannot view logs or change users. | Legacy TCP variants have no client authentication or protocol encryption. |
| NFR-04 | Define system behavior during serial, database, or network outages. | Must | Each failure case defines access behavior, visible status, event handling, and recovery. | The supplied files do not define one shared failure policy. |
| NFR-05 | Allow a reviewer to run the synthetic demonstration from documented setup steps. | Must | The demonstration runs without the original database, credentials, or physical hardware. | A hardware-free simulator is not included in the supplied project copy. |
| NFR-06 | Retain only event information required for operations and investigation. | Should | A data dictionary defines purpose, sensitivity, and retention for each event field. | No event-retention policy is included in the supplied materials. |

## Traceability

FR-01 through FR-03 cover the thesis access and audit workflow. FR-04 through FR-06 map to administrator and status functions in the supplied dashboard and code. FR-07 and FR-08 define additional successor-version behaviors. NFR-01 and NFR-02 address credential handling observed in the legacy source paths; NFR-03 addresses their network exposure. The remaining requirements define failure, demonstration, and data-retention criteria for a consolidated version.

## Decisions outside the supplied evidence

- Required authentication factors and recovery policy
- Local-only or remote administration
- Access behavior during serial, database, or network failures
- Required event fields and retention period
- User-management roles and audit policy
- Security and support controls for any real-world pilot
