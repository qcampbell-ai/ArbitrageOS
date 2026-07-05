---
Version: 1.0
Owner: Atlas (ChatGPT) / Founder
Status: Accepted
Last Updated: 2026-07-05
Dependencies: ADR-0001-GitHub-Is-Canonical.md
---

# ADR-0002: Google Sheets Is the Operational System of Record

## Status

Accepted

## Context

The business needs one live, low-code place to run day-to-day operations:
tracking products, inventory, purchases, sales, suppliers, expenses, and
KPIs. GitHub is well-suited to documents and code (ADR-0001) but poorly
suited to live, frequently-updated transactional data with formulas and
conditional formatting. A separate operational tool was needed, and the
question was which one — and how it relates to the documentation in
GitHub.

## Decision

**Google Sheets (the Amazon Operating Spreadsheet) is the operational
system of record** for all live business data: Dashboard, KPIs, Products,
Inventory, Purchases, Sales, Suppliers, Expenses, Daily Log, Scoreboard,
and the Decision Framework.

Documentation in GitHub must **reference** these tabs by name (e.g., "see
the Decision Framework tab") rather than **restate** their contents (e.g.,
re-listing the 9 purchase tests in prose). This is the direct fix for the
duplicated-source-of-truth risk identified in Sprint 2.

## Consequences

- Anyone editing purchase rules, KPI formulas, or scoreboard metrics only
  ever edits them in one place: the spreadsheet
- GitHub documents stay shorter and don't go stale when operational rules
  change
- Requires discipline from whoever writes future documentation (human or
  AI) to check before restating anything that might already exist as a
  spreadsheet tab
- This is explicitly a **current-state** decision, not a permanent one —
  see Architecture.md's note on a possible future Airtable migration if the
  spreadsheet's relational limitations become a real constraint

## Alternatives Considered

- **Airtable as the operational system of record from day one** — deferred:
  adds complexity before the manual process is proven; reserved for Phase 2
  per the Roadmap
- **A custom database** — rejected for now: violates the low-code-first
  principle in Architecture.md at this stage of the company
