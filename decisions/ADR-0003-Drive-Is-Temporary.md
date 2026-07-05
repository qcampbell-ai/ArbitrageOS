---
Version: 1.0
Owner: Atlas (ChatGPT) / Founder
Status: Accepted
Last Updated: 2026-07-05
Dependencies: ADR-0001-GitHub-Is-Canonical.md, ADR-0002-Google-Sheets-Is-Operations.md
---

# ADR-0003: Google Drive Is a Temporary Workspace Only

## Status

Accepted

## Context

Sprint 1 homework had the Founder create a 10-folder Google Drive
structure (`01 Strategy` through `10 Dashboard`). As GitHub (ADR-0001) and
Google Sheets (ADR-0002) were established as canonical homes for
documentation and operational data respectively, Drive's role needed to be
explicitly scoped down to avoid becoming a third, competing source of
truth.

## Decision

**Google Drive holds only non-canonical, working files.** Examples:
receipts, scanned PDFs, product photos, supplier catalogs, tax documents,
product manuals, raw meeting notes, and unstructured brainstorms.

Nothing in Drive is ever considered official. If something in Drive
becomes a stable rule, decision, or piece of operational data, it must be
promoted — written into GitHub (if it's documentation/decision) or the
operating spreadsheet (if it's operational data) — at which point the
Drive copy is a working draft/backup only, not the source of truth.

## Consequences

- The original 10-folder Drive structure from Sprint 1 homework remains
  useful as a working-file organizer but is not being formalized as a
  parallel documentation system
- Reduces risk of "which version is real" confusion between Drive docs and
  GitHub docs
- Requires a habit of promotion: when a Drive note turns into a real
  decision or rule, someone has to remember to move it into the canonical
  home — this is a process risk worth watching, not a solved problem

## Alternatives Considered

- **Drive as a secondary documentation system synced with GitHub** —
  rejected: adds sync complexity and reintroduces the two-sources-of-truth
  problem this ADR exists to prevent
- **Eliminating Drive entirely** — rejected: still useful for genuinely
  non-canonical working files (receipts, photos, catalogs) that don't
  belong in a code repository or a spreadsheet
