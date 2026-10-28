---
layout: document
title: Next-Stage Roadmap
description: Future work from the thesis prototype through requirements, architecture, and controlled validation.
---

# Next-Stage Roadmap

**Scope:** This roadmap describes future work based on the thesis and source review. It is separate from the completed academic prototype and does not represent customer or production validation.

| Stage | Work | Evidence produced | Exit condition |
|---|---|---|---|
| 1. Problem context | Define the access-control setting, user roles, current process, and existing alternatives. | Process map, problem statement, user-role summary, alternatives review | A defined user problem and project scope |
| 2. Requirements and risk | Define functional, privacy, security, safety, accessibility, support, and failure-handling requirements. | Traceable requirements, threat model, data inventory, failure-mode analysis | Requirements and operating constraints documented |
| 3. Architecture and prototype | Assign one serial connection owner and one authoritative data store. Define credential enrollment and revocation. Build a synthetic simulator and documented setup workflow. | Architecture decision, interface contract, synthetic demo, setup guide, test scenarios | A reproducible prototype that addresses the defined requirements |
| 4. Verification and readiness | Test normal and failure scenarios. Review credential protection, event handling, privacy, physical safety, and support operations. | Test results, independent security review, operational plan, controlled-pilot scope | Safety, security, and operations criteria met before any real-world pilot |

## Decisions beyond the thesis evidence

- Target access-control setting and user roles
- Local-only or remote administration
- Access behavior during serial, database, or network failures
- Credential lifecycle, recovery, and administrator permissions
- Event purpose, required fields, and retention period
- Hardware tamper, installation, maintenance, and support controls
- Deployment costs, liability, and commercial viability

## Product boundary

The thesis and recordings document an academic demonstration. They do not establish customer demand, willingness to pay, production security, installation readiness, serviceability, legal compliance, or commercial viability. The prototype cost estimate is historical project material, not a current supplier quote or business case.

This roadmap separates the demonstrated thesis work from future product investigation and controlled testing.
