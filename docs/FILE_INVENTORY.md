---
layout: document
title: Source File Inventory
description: Roles, relationships, and public-release status of the supplied Raspberry Pi thesis project files.
---

# Source File Inventory

This inventory summarizes the supplied Raspberry Pi project folder. The files represent separate implementation paths; the inventory does not combine them into one runtime. Original source files, local records, and credentials remain outside this public portfolio.

## Python applications and utilities

| File | Role in the supplied project | Relationship and release status |
|---|---|---|
| `access_control_thesis_app_final.py` | Desktop Tkinter administration dashboard; reads serial data and uses a local JSON user file | Direct-serial desktop path, separate from the Pi TCP server. The original contains demo credentials, identifiers, and unsafe logging/configuration; it is not in this public repository. |
| `pi_access_control.py` | Pi-side access-control application | Separate implementation. Its filename does not establish chronology. |
| `pi_server.py` | TCP-to-serial relay | Baseline network path without database or user-authentication features. |
| `pi_server_with_db.py` | TCP server with SQLite event logging | Server path with local event persistence. |
| `pi_server_with_db_and_logport.py` | SQLite server with an additional log-related port | Separate network logging path. |
| `pi_server_auth_db_final.py` | TCP server variant with authentication and database behavior | Separate server implementation with demo authentication and network protections that are not suitable for public deployment. |
| `pi_server_auth_db_final_v2.py` | Authentication/database server labeled `v2` | The filename alone does not establish release order or canonical status. |
| `view_access_logs.py` | Local utility for viewing SQLite access events | Reads the local event database; output can expose event data. |
| `test_arduino.py` | Sends serial test messages to the Arduino interface | Hardware-oriented test utility, not Arduino firmware. |
| `thesis_logger/serial_logger.py` | Reads serial messages and writes events to PostgreSQL | Separate serial and event-storage path. |

## Data, configuration, and schema

| File or folder | Role | Public portfolio status |
|---|---|---|
| `access_logs.db` | SQLite access-event database; integrity check returned `ok` | Historical demonstration data; excluded |
| `access_logs.db-journal` | SQLite rollback journal | Transient database state; excluded with database, WAL, and SHM files |
| `rfid_users.json` | Local user and credential configuration | Contains user and credential material; excluded |
| `.venv/` | Machine-specific Python environment and installed dependencies | Excluded; no environment folder is part of the public package |
| `thesis_schema.sql` | PostgreSQL schema for users, devices, access logs, and security events | Describes a relational data model; the SQL file is not reproduced in the public portfolio |

## Architecture and version relationships

The reviewed files show three separate application paths:

1. **Desktop dashboard:** local JSON user data, direct serial access, and a Tkinter interface.
2. **TCP server variants:** network-to-serial communication with SQLite event logging in some versions.
3. **PostgreSQL logger:** direct serial access with PostgreSQL event storage.

The SQLite viewer reads the local SQLite database. The PostgreSQL logger writes to a separate event store. Each path owns serial access independently; the supplied folder does not contain a shared connection broker. These components are not shown as one combined runtime.

The suffixes `final` and `v2` are filenames, not reliable version history. The supplied files use separate serial formats, databases, ports, and configuration. The filenames do not identify which server variant powered the thesis demonstration.

## Review scope

- The supplied Pi copy does not contain Arduino `.ino` firmware. The available Python test script sends serial messages.
- The thesis PDF remains in the private archive. This portfolio uses an original written summary and a clean architecture redraw.
- The inventory describes source responsibilities. It does not represent a production deployment or an independent security assessment.
