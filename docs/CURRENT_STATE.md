---
layout: document
title: Current-State Assessment
description: Application paths, data stores, integration boundaries, and security findings from the supplied thesis project files.
---

# Current-State Assessment

**Scope:** This assessment reviews the supplied Raspberry Pi project folder and compares its code paths with the architecture described in the thesis.

## Executive summary

The thesis describes an Arduino Nano 33 IoT connected to a Raspberry Pi Zero 2 W. The Arduino reads RFID, keypad, and tamper inputs and drives local feedback. The Pi evaluates access requests, records events in SQLite, and supports a Tkinter administrator dashboard.

The supplied Pi folder contains separate implementations rather than one integrated runtime. The dashboard, TCP server variants, and PostgreSQL logger each open the serial device directly. The code snapshot does not identify which server variant powered the thesis demonstration.

## System context

The intended workflow reads an access credential, evaluates the required factors, returns an allow or deny outcome, and makes the event available to an administrator. The thesis architecture names an RC522 reader, ZRX543 keypad, endstop tamper switch, 9600-baud serial link, SQLite store, Tkinter dashboard, LCD, RGB LED, and buzzer.

The Arduino firmware is not present in the supplied Pi folder. The available Python test script sends serial messages; it is not firmware. See the [thesis foundation and system walkthrough](THESIS_FOUNDATION.md) for the distinction between the thesis design and the supplied code.

## Observed software paths

| Path | Serial ownership | Data path |
|---|---|---|
| Desktop dashboard | Dashboard opens the Arduino serial connection | Local JSON user file |
| TCP server variants | Pi server opens the Arduino serial connection | SQLite event log in database variants |
| PostgreSQL logger | Logger opens the Arduino serial connection | PostgreSQL event store |

Each path opens serial independently. The supplied folder contains no shared connection broker and does not document a combined deployment.





## Component inventory

| Component | Observed responsibility | Current-state finding |
|---|---|---|
| Desktop dashboard | Admin login, status and log screens, user management, direct serial connection, local JSON user storage | Separate desktop path; it does not use the Pi TCP server or PostgreSQL logger interface |
| Minimal TCP server | Relays network-client messages to the serial device | No user store or event database |
| SQLite server variants | Provide network access and add SQLite event logging; later variants add authentication behavior and a separate log port | Bind to all interfaces; the legacy protocol has no client authentication or encryption |
| PostgreSQL serial logger | Reads serial messages and writes access and security events to PostgreSQL | Separate event-logging path; it does not provide dashboard user administration |
| SQLite database and viewer | Stores access events and displays local rows | Contains historical demonstration activity; the database and journal are excluded from the public package |
| PostgreSQL schema | Defines users, devices, access logs, and security events | Separate data model from the SQLite server variants; the supplied files do not map it to the demonstrated workflow |
| Python serial test sender | Sends test messages over a fixed serial connection | Hardware-oriented utility that requires the Arduino device |
| Local virtual environment | Captures a machine-specific Python installation | Machine-specific dependency environment; excluded from the public package |

## Data, integration, and security findings

- **Separate application paths:** the desktop dashboard uses a local JSON user file; SQLite server variants store events in SQLite; the PostgreSQL logger writes events to PostgreSQL.
- **Serial ownership:** the dashboard, TCP server variants, and PostgreSQL logger each open serial directly. The supplied folder contains no shared connection broker.
- **Credential handling:** older serial and server paths preserve raw messages in logs. The public demonstration excludes raw messages and secret factors.
- **Network security:** the legacy TCP server variants listen on all interfaces without client authentication or protocol encryption. Their network exposure is unsafe for public or shared networks.
- **Configuration:** serial paths, ports, user data, and database choices are embedded in separate programs and differ across variants.
- **Database status:** the SQLite database contains historical demonstration activity. The PostgreSQL schema defines a different persistence model.

## Design decisions not established by the supplied files

- Deployment scope: one local door or administrator access from another computer
- Administrator roles for adding, deactivating, and reviewing users
- Access behavior during database, network, or serial-device outages
- Required event fields and retention period
- Required authentication factors and approved alternate paths
- Location of the Arduino firmware; it is not in the supplied Pi folder
- Authoritative database and local-versus-networked deployment model

## Deployment patterns represented in the code

**Local-first:** one Pi application owns serial, uses one local database, and provides an administrator interface on the same machine. This keeps the operating path on the device.

**Service and dashboard:** one Pi service owns serial and database access; a separately authenticated dashboard uses a documented API. This supports remote administration and adds network, authentication, and deployment requirements.

These are architecture patterns for comparison, not a claim that either is a production design. The thesis demo recordings show the demonstrated application and physical outcomes; the source snapshot does not establish that the alternative server paths ran together.
