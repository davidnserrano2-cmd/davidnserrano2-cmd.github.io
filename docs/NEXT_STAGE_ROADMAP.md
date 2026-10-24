---
layout: document
title: Responsible Next-Stage Roadmap
description: A discovery-first path from thesis prototype to a product that could be evaluated for real-world use.
---

# Responsible Next-Stage Roadmap

**Status:** Proposed sequence for future investigation. This is not an approved company plan, funded roadmap, or claim of customer validation.

The thesis identifies future directions including stronger device communication and credential protection, multiple access points, remote administration, and expanded usability. The next step is to determine which problems matter to a real user before selecting features or building a larger system.

| Stage | Questions and work | Evidence to produce | Exit decision |
|---|---|---|---|
| 1. Problem discovery | Which setting has a specific access-management problem? Who uses the door, administers credentials, supports the system, and pays for it? What existing solution is used? | Interview notes, workflow map, problem statement, alternative/competitor scan, assumptions list | Continue only if a clear user problem and plausible buyer emerge |
| 2. Requirements and risk | What must happen during power, network, database, reader, or Pi failure? What privacy, physical-safety, accessibility, audit, and support needs apply? | Validated requirements, threat model, data inventory/retention proposal, failure-mode analysis | Decide whether a prototype is safe and useful enough for a controlled lab iteration |
| 3. Architecture and prototype | Which device owns serial communication? Which data store is authoritative? How are credentials enrolled/revoked? Is local-only administration sufficient? | Selected architecture, interface/protocol contract, synthetic demo, setup/runbook, test scenarios | Build only the smallest testable workflow that addresses validated needs |
| 4. Verification and pilot design | Can expected flows and failure cases be repeated? Can credentials and event data be protected? Who monitors and supports a pilot? What approvals and controls are required? | Test evidence, independent security review, operational playbook, pilot scope and rollback plan | Do not move into a real access-control setting until safety, security, and operations gates are met |

## Decisions that remain open

- Target customer and access-control use case
- Local-only versus networked administration
- Offline behavior and safe response to each component failure
- Credential lifecycle, recovery, revocation, and administrator roles
- Event purpose, visibility, retention, export, and deletion
- Hardware tamper and physical-installation requirements
- Deployment, maintenance, support, and replacement model
- Current component costs, installation costs, liability, and commercial viability

## Why the prototype is not the product

The thesis documents a single academic/demo system and recommends future work. It does not establish demand, customer willingness to pay, production security, installation readiness, serviceability, legal compliance, or commercial economics. The old prototype cost-estimate document is not a current supplier quote or a business case. Those questions need new research and evidence.

The goal of this roadmap is to preserve the original project as credible proof of systems work while giving future development a disciplined path from idea to validated requirements and controlled testing.
