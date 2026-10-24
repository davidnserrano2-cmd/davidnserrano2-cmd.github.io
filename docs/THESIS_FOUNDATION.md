---
layout: document
title: Thesis Foundation and System Walkthrough
description: Thesis-backed architecture, user workflow, and the boundary between the academic prototype and future product ideas.
---

# Thesis Foundation and System Walkthrough

**Project origin:** David N. Serrano, *Design of a Scalable RFID-Based Multi-Factor Access System*, honors thesis, Arizona State University, W. P. Carey School of Business. This page summarizes the paper and its diagrams; the thesis PDF itself is not included in this public portfolio.

## What the thesis describes

The prototype combines an RFID credential and keypad PIN with an Arduino Nano 33 IoT, a Raspberry Pi Zero 2 W, a local SQLite database, and a custom Tkinter administration dashboard. The Arduino handles the attached input and feedback hardware. The Pi is described as the controller for authentication, event logging, serial reconnection, and the admin interface.

The paper's architecture figure names an RC522 RFID reader, ZRX543 keypad, endstop tamper switch, 9600-baud serial communication, SQLite, and an LCD 1602, RGB LED, and buzzer for user feedback. The recreated diagram below conveys the paper's design without reproducing its screenshots or any example identifiers.

![Recreated system architecture from the thesis description. The Arduino handles RFID, keypad, tamper, and physical feedback; the Raspberry Pi handles authentication, SQLite logging, serial recovery, and the Tkinter admin UI.]({{ '/assets/thesis-architecture.svg' | relative_url }})

## Access-request workflow

1. A person presents an RFID card and enters a PIN at the device.
2. The Arduino reads the hardware inputs, handles tamper input, and exchanges messages with the Pi over serial.
3. The Pi evaluates the request and records an access outcome in the local data store described in the thesis.
4. The system returns a result for on-device feedback; the dashboard gives an administrator visibility into status, users, and events.

The thesis reports work on inconsistent reads, serial interruption and reconnection, and component-by-component hardware debugging. It also includes prototype photos, dashboard/status screenshots, a database diagram, and a demonstration sequence. The claims in the paper are project-reported results, not an independent production or security assessment.

## The paper and the supplied code are related evidence, not a perfect match

The paper presents one intended system architecture. The Pi folder contains multiple code variants and storage paths. In the files reviewed for this case study, the dashboard and network/server paths appear to open serial themselves, with local JSON, SQLite, and PostgreSQL represented in different alternatives. Those variants should not be depicted as components that all ran together.

This documentation-to-implementation gap is a useful systems-analysis finding: verify which build was used for a given demonstration, identify the authoritative user and event stores, and assign one owner to the serial connection before designing a consolidated next version. File names such as `final` and `v2` do not establish chronology by themselves.

## Proposed data concepts in the thesis diagram

The paper's ERD separates four concepts:

| Entity | Purpose described by the diagram | Analysis question for a future version |
|---|---|---|
| Users | Display identity, role, active status, and credential references | How are credentials enrolled, revoked, recovered, and protected? |
| Devices | Device identity, name, location, and creation time | How are device ownership and location changes audited? |
| Access logs | Time, device/user references, method, result, and failure reason | Which fields are necessary, and how long should events be retained? |
| Security events | Time, device, event type, severity, and notes | Which events require escalation, and who can review them? |

This is a summary of the thesis data model, not a claim that every table was implemented in the demonstrated application. Public examples should use synthetic identities and must never contain card UIDs, PINs, passwords, raw authentication messages, or live event history.

## Prototype today; product direction later

The completed work is an academic/demo prototype. The thesis itself identifies secure device communication, stronger credential handling, multiple access points, remote administration, and broader usability as future work. These items are opportunities for a next-stage product investigation; they are not current features.

If this idea is developed toward a production company, the next steps are problem and customer discovery, threat modeling, privacy and safety requirements, operational failure policies, support/maintenance planning, and controlled validation in a non-critical environment. A physical access-control system should not be represented as production-ready until those requirements are implemented and independently reviewed.

## Evidence boundary

- The thesis PDF is retained in the private archive and is not republished here.
- The Arduino firmware was not present in the supplied Pi folder copy reviewed for the code inventory.
- Hardware and dashboard images in the paper were not copied into this portfolio; this diagram is a clean redraw of the paper's architecture figure.
- The portfolio's current-state observations come from the supplied Pi files; the thesis provides design intent and reported demo behavior.
