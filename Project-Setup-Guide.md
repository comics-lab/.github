# Project Setup Guide — comics-lab / comics-suite

**Date:** 2025-10-20  
**License:** MIT  
**Language:** Python 3 only

---

## Overview

The **comics-lab** organization is a suite of coordinated Python 3 utilities and connectors designed to manage and enrich comic book collections. It emphasizes **small, composable repositories**—each focused on one task but built on a shared core.

This document describes the project architecture, repository design, development conventions, GitHub governance, and security standards for initializing and maintaining the project ecosystem.

Documentation index

For a centralized list of conversation logs, bookmarks, and action logs found across the workspace, see: `../docs/DOCUMENTATION_INDEX.md` (or `docs/DOCUMENTATION_INDEX.md` from repo root). This index points to transcripts and summaries for integrated components such as `comic-file-organizer` and `org_level_Scripts`.

---

## Architecture — Option A (“Small-Packages” Multi-Repo)

### Philosophy

Each repository focuses on one responsibility and depends on a common shared core for data models, naming conventions, logging, and reporting. This modular layout simplifies maintenance, allows independent release cycles, and makes the entire ecosystem transparent.

### Repositories

| Repository | Purpose |
|-------------|----------|
| **comicbook-core** | Shared library providing common models, naming logic, CSV reporting, and logging utilities. |
| **mylar3-sanity** | Integrity checker for Mylar3’s database and filesystem; verifies DB integrity, file presence, naming consistency, and missing entries. |
| **comicmeta-comicvine** | Connector for ComicVine API; fetches and normalizes metadata for series and issues. |
| **comicmeta-metron** | Connector for Metron/Mokkari APIs to import/export XML metadata. |
| **comicmeta-gcd** | Loader for the Grand Comics Database dump; parses and normalizes data to shared models. |
| **cbz-doctor** | CBZ validator and repair tool that ensures valid archives, verifies or writes `ComicInfo.xml`, and can emit Metron XML. |
| **comic-file-organizer** | Directory scanner, renamer, and importer; converts `.cbr → .cbz`, renames per Mylar config, relocates files, and updates Mylar3 via API. |
| **comics-suite** | Meta-repository for documentation, standards, automation, and coordination of all component projects. |

---

## Shared Core Architecture

### Data Models (in `comicbook-core`)
- **Series**: id, title, year, publisher, volume, aliases  
- **Issue**: id, series_id, number, year, date, title, variant, barcode  
- **FileRecord**: path, size, extension, series_hint, issue_hint  
- **ComicInfo**: series, number, year, title, volume, publisher, web, notes, tags

### Naming Rules
Derived from Mylar3’s `config.ini`:
- Compiles `{series}`, `{issuenumber}`, `{year}` patterns to regex  
- Provides `render_series_dir()` and `render_issue_filename()` helpers  
- Supports strict and permissive validation modes  

### Connectors
Each connector normalizes data to shared models for consistent downstream processing.

### Common Features
- Unified CLI pattern (`--dry-run`, `--apply`, `--log-file`, `--report`)
- Reports with 1-based line numbering
- No non-breaking spaces
- Rotating log files and consistent log format
- CSV: `lineno,level,check,item,message,details`

---

## Repository Layout

```
repo-name/
├── README.md
├── LICENSE (MIT)
├── .gitignore
├── requirements.txt
├── Makefile
├── package_name/
│   └── __init__.py
├── tests/
└── docs/
```

### Standard Makefile Targets
- **venv** – create a virtual environment and install requirements  
- **test** – run placeholder tests or integration checks  
- **clean** – remove cache, logs, and artifacts  

### Branching Strategy
- **main** — always stable and releasable  
- **feature/*** — development branches  
- **release/*** — optional release versions  
- PRs required for all merges into `main`  

---

## Meta-Repository (`comics-suite`)

The meta-repo serves as governance and documentation center for the entire project. It includes:

- `docs/` — central documentation and standards  
- `.github/` — issue templates, PR templates  
- `scripts/` — GitHub CLI automation for repo setup and policy enforcement  
- `Action-Log.md` — chronological record of organizational actions  

---

## Development Standards

### General
- **Language:** Python 3 only  
- **License:** MIT for all repos  

### Logging & Reporting
- Rotating logs (default 5MB × 3 backups)
- Console + file output
- Uniform CSV output with 1-based rows

### CI / Quality
- Lightweight GitHub Actions per repo (build + test + CodeQL)
- Secret scanning and push protection enabled by default

### Documentation
Each repository maintains:
- `README.md` with a running **Action Log**
- Optional `docs/` folder for deeper design notes

---

## Organization: comics-lab

**Structure**
- Teams: `owners`, `maintainers`, `contributors`, `readers`
- Repos: private by default; public when stable
- PRs required for all merges into protected branches

**Baseline Security**
- Require 2FA
- Enable Secret Scanning and Protection
- Restrict GitHub Actions to approved sources
- Default GITHUB_TOKEN permissions: read-only
- Require PR review and status checks

---

## Implementation Roadmap

| Milestone | Description |
|------------|--------------|
| **M1** | Refactor `mylar3-sanity` to use `comicbook-core`. |
| **M2** | Finalize ComicVine + GCD connectors; develop Metron MVP. |
| **M3** | Build `cbz-doctor` validator and repair workflow. |
| **M4** | Implement `comic-file-organizer` for renaming and DB sync. |
| **M5** | Full integration testing and documentation. |

---

## Example Commands

```bash
# mylar3-sanity
mylar3-sanity --db mylar.db --library /mnt/comics --config config.ini --report sanity.csv

# comicmeta-comicvine
comicvine --query "Spider-Man" --out series.csv --cache .cache

# cbz-doctor
cbz-doctor scan --root /comics --fix-comicinfo --write-metron-xml --dry-run

# comic-file-organizer
organizer import --root /incoming --library /comics --config config.ini --convert-cbr --apply
```

---

# Appendix A — Security Checklist

### Organization-Level
- Require 2FA for all members
- Enable Secret Scanning, Secret Protection, and CodeQL defaults
- Restrict GitHub Actions and set GITHUB_TOKEN read-only
- Use Teams for access; audit bots and PATs
- Monitor Audit Log regularly

### Repository-Level
- Protect `main` and `release/*` with PR requirements
- Require 1+ approving review and passing checks
- Enable Secret Scanning and CodeQL per repo
- Restrict direct pushes
- Gate deployments via Environments

### Audit Routine
- Review 2FA compliance and security coverage
- Rotate secrets regularly
- Validate branch protection policies

---

# Appendix B — Repository Standards

- Required files: README, LICENSE, .gitignore, requirements, Makefile, main package folder
- Branch strategy: `main` (protected), `feature/*`, `release/*`
- Commits: descriptive and signed (recommended)
- PRs: one approval minimum, all conversations resolved
- CI: build/test + CodeQL + Secret scanning enabled

---

# Appendix C — Automation Scripts Overview

The **meta-kit** provides GitHub CLI automation scripts:

| Script | Function |
|---------|-----------|
| `seed_repos.sh` | Creates all repos in comics-lab |
| `lockdown_actions.sh` | Restricts GitHub Actions and sets read-only tokens |
| `enable_security.sh` | Enables Secret Scanning, Push Protection, CodeQL |
| `protect_branches.sh` | Enforces branch protection on main |
| `apply_all.sh` | Runs all setup scripts sequentially |
| `verify.sh` | Generates verification JSON summary |
| `setup_org.sh` | Guides manual UI security setup |

---

# Appendix D — Meta-Repo Structure

**`comics-suite`** should include:
```
docs/
  Security-Checklist.md
  Repo-Standards.md
  Architecture.md
  Action-Log.md
.github/
  ISSUE_TEMPLATE/
    bug_report.md
    feature_request.md
  pull_request_template.md
scripts/
  seed_repos.sh
  enable_security.sh
  lockdown_actions.sh
  protect_branches.sh
  apply_all.sh
  verify.sh
  setup_org.sh
```

---

# Appendix E — Action Log

1. 2025-10-20 — Initial compilation of architecture, repo structure, and security automation into `Project-Setup-Guide.md`.

---

*End of Document*
