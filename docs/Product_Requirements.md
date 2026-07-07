---
Version: 1.0
Owner: Forge (Claude)
Status: Draft
Last Updated: 2026-07-05
Dependencies: Company_Bible.md, Architecture.md
---

# Product Requirements Document — ArbitrageOS

## What "The Product" Is

ArbitrageOS is not a single app. It is an **operating system for capital
allocation**, currently instantiated as an Amazon retail arbitrage
operation. The "product" is the combination of:

- A live operational database (Google Sheets today; see
  [Architecture.md](Architecture.md) for the upgrade path to Airtable)
- A documented decision framework that gates every purchase
- A growing bench of AI agents ("AI employees") that automate specific
  operational functions
- The documentation in this repository, which makes the whole system
  legible and reproducible

## MVP Definition

The MVP is **not** a piece of software in the traditional sense — it is a
working, disciplined Amazon arbitrage operation with:

1. A single canonical operating spreadsheet (Dashboard, KPIs, Products,
   Inventory, Purchases, Sales, Suppliers, Expenses, Daily Log, Scoreboard,
   Decision Framework)
2. A documented, enforced Decision Framework — see the *Decision Framework*
   tab in the operating spreadsheet for the current rules (not restated
   here; this document references it rather than duplicating it)
3. One functioning AI agent ("Scout") that assists in identifying
   candidate products against the Decision Framework criteria
4. A weekly reporting rhythm (the Scoreboard tab + daily standups)

## Success Criteria

- Every dollar of the initial $500 is deployed only against products that
  pass the Decision Framework
- The Scoreboard is updated every week without a missed entry
- Scout v1 can take a product input (URL/ASIN/UPC) and return a structured
  recommendation referencing the Decision Framework criteria
- No operational fact exists in two places at once (see Document
  Governance in the root [README.md](../README.md))

## Users / Personas

- **The Founder** — the primary operator, sourcing and purchasing products,
  reviewing Scout's recommendations, making final calls
- **Atlas (ChatGPT)** — strategic planning, sprint design, QA of Forge's
  output
- **Forge (Claude)** — documentation and artifact generation, spreadsheet
  and automation builds
- **Future AI agents** (Scout, Accountant, Inventory Manager, etc.) —
  narrow-scope automations defined in `/prompts` as they're built

## Functional Requirements

- The operating spreadsheet must support the full product lifecycle:
  discovery → validation → decision → purchase → inventory → sale → profit
  calculation, per the process documented in
  [`sops/SOP-001-Candidate-Discovery.md`](../sops/SOP-001-Candidate-Discovery.md)
- The Decision Framework must be enforceable (i.e., visibly gate a
  purchase decision) rather than just informational
- The Scoreboard must be updatable on a weekly cadence with minimal
  friction (a single row per week)
- AI agent prompts must be versioned and stored in `/prompts` so they can
  be reused and improved without being rewritten from scratch each time

## Non-Functional Requirements

- **Low-code first.** Every system chosen (Sheets, Airtable, n8n) should be
  operable by a single non-engineer founder before any custom code is
  introduced.
- **No duplicated sources of truth.** Enforced via the Document Governance
  policy in the root README and the ADRs in `/decisions`.
- **AI continuity via documentation.** Because AI teammates don't retain
  memory between sessions, this repository must contain enough context
  that any future session (of Claude, ChatGPT, or another model) can
  onboard by reading README → Company_Bible → Product_Requirements →
  Architecture, in that order.
- **Auditability.** Every non-trivial decision has a corresponding ADR.

## Assumptions

- The Founder has ~1 hour/day minimum to commit to operations
- Amazon Seller Central, **free-tier Keepa** (chart/validation use, not
  Product Finder), and SellerAmp SAS remain viable/available sourcing
  tools for the Amazon arbitrage phase
- Google Sheets is sufficient as the operational system of record through
  at least the first phase (see [ADR-0002](../decisions/ADR-0002-Google-Sheets-Is-Operations.md))

## Risks

- **Tool sprawl.** Adding Airtable, n8n, and multiple AI agents before the
  manual process is proven could create complexity without proportional
  value. Mitigation: phased rollout per [Roadmap.md](Roadmap.md).
- **Documentation drift.** If docs in this repo are edited without
  updating cross-references, the "one source of truth" model breaks.
  Mitigation: every doc lists its `Dependencies` in its header block.
- **Decision Framework erosion.** Under time pressure, purchase rules can
  get quietly bent. Mitigation: the framework is enforced in the
  spreadsheet itself (colored PASS/FAIL/Needs Review verdicts), not just
  described in prose.
- **Folder/structure drift between sprints.** Early sprints proposed
  different repository folder schemes. See the note in the root
  [README.md](../README.md) — this is a known open item, not yet resolved
  by an ADR.

## Phased Roadmap (Summary)

See [Roadmap.md](Roadmap.md) for the full detail. In brief: **Phase 1 —
Business** (operating system, SOPs, financial model) → **Phase 2 —
Technology** (Airtable, n8n, AI agents, dashboards) → **Phase 3 — Growth**
(wholesale, additional marketplaces, smarter automation, new asset
classes).
