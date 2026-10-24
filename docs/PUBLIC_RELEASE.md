---
layout: document
title: Public Release and Cleanup Plan
description: Safe, reversible plan for preparing the thesis project for public GitHub and Pages.
---

# Public Release and Cleanup Plan

## Current release boundary

The public portfolio contains analysis documents, a static case-study page, and a clean architecture redraw based on the thesis. It does not include the original Python applications, database files, user configuration, environment folder, thesis PDFs, thesis screenshots, or raw records. This keeps the current release useful as proof of systems analysis without exposing identifiers or presenting an academic demo as deployment-ready.

The legacy source variants remain private for this first application-focused release. A later source release should wait until the thesis demo path is identified, credential/message handling is corrected, configuration is externalized, and the final diff is reviewed for secrets and private data. The portfolio currently makes the design and analysis work reviewable without presenting unverified code as a safe product.

## Before adding implementation artifacts

1. Preserve the original folder as a private, read-only archive. Work only from a separate sanitized copy.
2. Compare the Python variants and identify the exact thesis demo path. Record differences in serial protocol, ports, authentication, storage, and logging.
3. Search the working copy for passwords, PINs, usernames, RFID UIDs, hostnames, tokens, database connection strings, and raw message logging. Replace them with synthetic values and environment-based configuration.
4. Review event output and screenshots. Remove identifiers and avoid printing or retaining authentication factors.
5. Review `thesis_schema.sql` independently for sample identities or secrets before publishing a schema-only copy.
6. Replace historical databases with a newly generated synthetic dataset. Do not sanitize by editing the only copy of the original database.
7. Build a hardware-free walkthrough with synthetic records, explicit limitations, and setup steps; do not expose the legacy unauthenticated TCP service to a shared or public network.
8. Keep the full thesis PDF and its screenshots in the private archive. Use original summary text and a clean redraw for the public case study; attribute the thesis as the design source.
9. Keep job-search trackers, application notes, and private planning outside the public portfolio.
10. Inspect the final repository contents and commit diff for excluded files and secret-like values before making the repository public.

## Suggested clean repository structure

```text
rfid-access-control-case-study/
├── README.md
├── index.html
├── _config.yml
├── _layouts/
├── assets/
├── docs/
│   ├── CURRENT_STATE.md
│   ├── FILE_INVENTORY.md
│   ├── REQUIREMENTS.md
│   ├── PUBLIC_RELEASE.md
│   └── THESIS_FOUNDATION.md
├── demo/
│   ├── README.md
│   └── synthetic-data/       # generated examples only
├── diagrams/
└── src/                      # only after sanitization and version selection
```

Keep the job-search tracker, personal application notes, private logs, raw database, and original thesis archive outside the public repository. Do not move or delete the original files as part of this cleanup plan.

## Pages publishing checklist

- Review the site in a browser at the eventual repository URL; verify every page and asset path.
- Confirm the repository is intended to be public before enabling Pages. A Pages website is publicly viewable.
- Select GitHub Pages publishing from the repository's `main` branch and root (the site uses Jekyll Markdown layouts).
- Confirm the public repository contains only the reviewed portfolio package and synthetic data.
- Add the published Pages URL to the resume and applications after checking it from a signed-out browser.
