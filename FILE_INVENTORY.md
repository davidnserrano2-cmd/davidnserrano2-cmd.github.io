---
layout: document
title: Source File Inventory
description: Evidence-based inventory of the supplied Raspberry Pi thesis project files.
---

# Source File Inventory

This inventory describes the supplied Pi-folder copy reviewed for the portfolio. It does not claim every file was part of one deployed runtime. Several files are alternative implementations. The original files remain unchanged and are not copied into this public portfolio.

## Python applications and utilities

| File | Likely role | Relationship / release note |
|---|---|---|
| `access_control_thesis_app_final.py` | Desktop Tkinter administration application; handles serial access and local user data in JSON. | Desktop path appears independent of the TCP server path. Treat as the dashboard implementation, not a client of the Pi service. Do not publish the original before removing demo credentials, identifiers, and unsafe logging/configuration. |
| `pi_access_control.py` | Earlier or alternate Pi-side access-control application. | Likely predecessor/parallel implementation; exact chronology cannot be established from filenames alone. Compare behavior and interfaces before selecting a canonical version. |
| `pi_server.py` | Minimal TCP-to-serial relay. | Baseline network server path; lacks the database/authentication features added by later variants. |
| `pi_server_with_db.py` | Server variant adding SQLite event logging. | Extends the relay approach with local event persistence; still a legacy network service and not ready for public deployment. |
| `pi_server_with_db_and_logport.py` | SQLite server variant with an additional log-related port/path. | Appears to add a separate log channel; review protocol and port ownership before any reuse. |
| `pi_server_auth_db_final.py` | Server variant combining authentication/database behavior. | A later iteration by naming, but `final` does not prove it supersedes all others. Demo authentication and network protections require remediation. |
| `pi_server_auth_db_final_v2.py` | Revised authentication/database server variant. | Likely a revision of the preceding server, but verify changes with a source diff and runtime configuration before declaring it canonical. |
| `view_access_logs.py` | Local utility to inspect SQLite access events. | Useful operational support script; raw output can expose sensitive event data. A public example should use synthetic rows and redact identifiers. |
| `test_arduino.py` | Serial test sender for exercising the Arduino interface. | Hardware-oriented test utility, not a hardware-free demo. The supplied Pi copy did not include the corresponding Arduino firmware source. |
| `thesis_logger/serial_logger.py` | Separate serial-reading logger that writes events to PostgreSQL. | Alternative persistence path; it also opens the serial connection directly, so it conflicts with other simultaneous serial owners unless deliberately brokered. |

## Data and configuration

| File | Likely role | Release note |
|---|---|---|
| `access_logs.db` | SQLite access-event database (reviewed as a local historical database; integrity check reported `ok`). | Private operational/demo data. Do not publish, even if it appears to contain only test activity. |
| `access_logs.db-journal` | SQLite rollback journal associated with database activity. | Transient database state; never publish. Exclude all SQLite database, journal, WAL, and SHM files. |
| `rfid_users.json` | Local user/credential configuration used by one or more Python paths. | Contains sensitive user/credential material. Do not publish; provide a placeholder template only after schema-only review. |
| `.venv/` | Machine-specific Python environment and installed dependencies. | Do not publish. Replace with a reviewed dependency manifest and clean setup instructions. |
| `thesis_schema.sql` | PostgreSQL schema for users, devices, access logs, and security events. | Best candidate for a sanitized technical artifact after a line-by-line scan for inline credentials, sample identifiers, and personal data. Current portfolio describes it but does not reproduce it. |

## Architecture and version relationship

The evidence supports at least three alternative application paths: (A) desktop dashboard + local JSON + direct serial; (B) one of several TCP server versions + SQLite; and (C) a PostgreSQL serial logger + PostgreSQL schema. The SQLite viewer reads the local SQLite path. These are not demonstrated as one integrated application. In particular, multiple programs directly opening the same serial device would compete for the connection if run together.

The suffixes `final` and `v2` suggest iteration, but file names are not reliable version history. A defensible public timeline would require comparing code, serial message formats, database schemas, ports, and configuration, then recording what actually ran for the thesis demonstration.

## Evidence limits

- The Pi copy reviewed for this inventory did not contain Arduino `.ino` firmware.
- The thesis PDFs remain in the private archive. The public portfolio uses an original written summary and a clean architecture redraw; it does not reproduce the source screenshots or include the full thesis.
- File roles above describe observed responsibilities at a high level; they do not imply a production deployment or validated security controls.
