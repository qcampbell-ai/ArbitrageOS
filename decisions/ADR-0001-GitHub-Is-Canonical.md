---
Version: 1.0
Owner: Atlas (ChatGPT) / Founder
Status: Accepted
Last Updated: 2026-07-05
Dependencies: None
---

# ADR-0001: GitHub Is the Canonical Documentation & Code Repository

## Status

Accepted

## Context

Early in the project, documentation was being planned across multiple
possible homes — a Founder Kit of standalone documents, Google Drive
folders, and GitHub. Without a single canonical home, the same information
(company strategy, purchase rules, KPI definitions) risked being defined in
more than one place and drifting out of sync over time — the exact
"two sources of truth" risk flagged during Sprint 1–2 review.

## Decision

**GitHub is the single canonical source of truth for all permanent
documentation and code.** This includes: the Company Bible, Product
Requirements Document, Architecture documentation, Roadmap, Architecture
Decision Records, AI agent system prompts, Standard Operating Procedures,
and any source code produced as the company builds custom tooling.

Nothing in this category is considered "official" unless it lives in this
repository. Google Drive and Google Sheets are explicitly *not* canonical
for these artifact types (see ADR-0002 and ADR-0003 for their roles).

## Consequences

- Every document has one editable, versioned, diffable home
- Documents can cross-reference each other reliably via relative links
- AI teammates without cross-session memory can reconstruct full context by
  reading this repository in a defined order (README → Company Bible → PRD
  → Architecture → Roadmap)
- Requires discipline: any new "official" artifact must be committed here,
  not left in a chat transcript, a Google Doc, or a Drive file
- Folder structure within the repo is still evolving (see the open note in
  the root README) — this ADR establishes *that* GitHub is canonical, not
  the final internal folder scheme

## Alternatives Considered

- **Google Drive as canonical documentation home** — rejected: poor
  version history, no native issue tracking, harder to enforce
  cross-referencing discipline
- **A standalone "Founder Kit" of disconnected documents** — rejected:
  this was the original Sprint 1 plan, but it risked becoming a static
  snapshot rather than a living, versioned knowledge base
