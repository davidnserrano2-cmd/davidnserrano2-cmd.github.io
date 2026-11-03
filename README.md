# David N. Serrano — Portfolio

An about-first portfolio presenting my background, current IT responsibilities,
and two featured projects.

- **[About me](https://davidnserrano2-cmd.github.io/)** — IT support, documentation,
  education, practical skills, and contact information.
- **[IT Ticketing & Dashboard](https://davidnserrano2-cmd.github.io/projects/it-ticketing.html)** —
  n8n automation, PostgreSQL, and a read-only FastAPI dashboard.
- **[RFID Access Control](https://davidnserrano2-cmd.github.io/projects/rfid-access-control.html)** —
  an honors-thesis prototype with demonstrations and systems analysis.

## Site structure

GitHub Pages renders the HTML pages through Jekyll. Shared layouts are in
`_layouts/`; styling is in `assets/site.css` and `assets/portfolio.css`.
Project pages live in `projects/`. The RFID analysis documents remain in `docs/`.

The IT dashboard's application source is in its
[separate repository](https://github.com/davidnserrano2-cmd/IT-Ticketing-Dashboard).
It is a local MVP without visitor authentication; this portfolio hosts its
description and approved screenshots, not the running FastAPI application.

## RFID documents

- [Thesis foundation](docs/THESIS_FOUNDATION.md)
- [Current-state assessment](docs/CURRENT_STATE.md)
- [File inventory](docs/FILE_INVENTORY.md)
- [Requirements](docs/REQUIREMENTS.md)
- [Next-stage roadmap](docs/NEXT_STAGE_ROADMAP.md)
- [Public release scope](docs/PUBLIC_RELEASE.md)

The RFID recordings document an academic demonstration. Alternative source-code
paths and future plans are distinguished from the demonstrated prototype.
Credentials, private registries, identifiers, database files, and the thesis PDF
are excluded from this public repository.
