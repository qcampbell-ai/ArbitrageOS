---
Version: 1.0
Owner: Atlas (ChatGPT) / Founder
Status: Accepted
Last Updated: 2026-07-05
Dependencies: ADR-0001-GitHub-Is-Canonical.md, ADR-0002-Google-Sheets-Is-Operations.md, ../docs/Architecture.md
---

# ADR-0004: Agent Role Separation — Forge, Atlas, Sentinel, Founder

## Status

Accepted

## Context

Sprint 1–2 originally framed a single AI agent ("Scout") as responsible for
both finding products and deciding whether to buy them. On reflection, this
conflated two different jobs — data gathering and decision-making — inside
one agent, which made it unclear who owned what and risked the agent
"guessing" with real money on stale or assumed data.

A revised architecture was proposed that separates these responsibilities
across distinct roles, adds GitHub explicitly as a system in the
architecture (previously missing), and introduces the idea of a future
monitoring role ("Sentinel"). Two things surfaced during review that this
ADR resolves explicitly, rather than leaving ambiguous: (1) whether data
gathering means scraping retailer sites directly or ingesting licensed
data-provider exports, and (2) what "Forge gathers data every morning"
actually requires to be true, given how Claude (Forge) is actually deployed
today (an interactive chat assistant, not a standing background service).

## Decision

**Scout is retired as a named agent.** Its responsibilities are split
across four clearly-scoped roles:

| Role | Owner | Responsibility |
|---|---|---|
| **Forge** | Claude | Data collection and engineering: ingest structured exports (Keepa, SellerAmp, Amazon eligibility data), maintain the product database (i.e., keep the Products/Inventory tabs current), build automations, produce documentation and code. **Never makes the final buy decision.** |
| **Atlas** | ChatGPT | Strategy and capital allocation: score Forge's candidates against the Decision Framework, compare against available capital, recommend Buy/Wait/Reject, manage the roadmap. **Never gathers data or spends money.** |
| **Sentinel** *(future, not yet built)* | TBD | Monitoring: inventory aging, cash levels, account health, margin drops, concentration risk. Watches; does not decide or execute. |
| **Founder** | You | Approves purchases, executes buys, ships inventory, records outcomes, provides feedback. **Only the Founder moves money.** |

**Ownership chain for the product lifecycle:**
Candidates → Forge owns. Recommendations → Atlas owns. Approved → Founder
owns. Purchased → Founder owns. Performance Review → Atlas owns. Lessons
Learned → Shared. All of these are tracked in the operating spreadsheet
(per ADR-0002) — "ownership" here means who is responsible for populating
and maintaining that data, not a separate storage location.

**Data sourcing constraint:** Forge gathers data exclusively from licensed,
structured sources — Keepa, SellerAmp, and Amazon's own eligibility
tools/APIs. Forge does **not** scrape retailer websites (Amazon, Walmart,
Target, Home Depot, CVS, Ross, etc.) directly. As of this ADR, none of
these non-Amazon retailers offer an official API suited to arbitrage-style
price/product monitoring (Walmart's Affiliate and Marketplace/Supplier
APIs are scoped to affiliates and sellers, not buy-side monitoring; Target,
Home Depot, CVS, and Ross have no public product API at all). Until that
changes, candidates from those retailers are sourced manually by the
Founder and handed to Forge/Atlas for evaluation — this is an accepted
Day-1 limitation, not an oversight.

**Execution model constraint:** Forge (Claude) operates only within active
sessions initiated by the Founder or by a genuine automation layer (e.g.,
a scheduled n8n workflow or API call). Claude, as deployed in a chat
interface, has no standing background process and cannot autonomously
"wake up and gather data every morning" on its own. Any description of an
always-on overnight pipeline refers to future automation infrastructure
that must be separately built (Phase 2, per Roadmap.md) — it is not a
property of Forge/Claude itself.

## Consequences

- Clear, auditable ownership at every stage of the product lifecycle
- Removes the risk of an agent recommending a purchase based on stale or
  assumed data, by scoping Forge to licensed data sources only
- Sets accurate expectations: no part of this system runs unattended until
  an actual automation layer is built and documented as such
- Limits automated discovery to Amazon (via Keepa/SellerAmp) for now;
  expansion to other retailers requires either a partnership/affiliate
  relationship or a documented, ToS-reviewed data source — not ad hoc
  scraping
- "Sentinel" remains a placeholder role — not implemented, no owner
  assigned yet — until a future sprint scopes it properly

## Alternatives Considered

- **Keep a single "Scout" agent responsible for both finding and deciding**
  — rejected: conflates two different kinds of work and obscures
  accountability when a bad purchase happens
- **Have Forge scrape retailer websites directly** — rejected: fragile,
  likely to violate individual retailers' Terms of Service, and unreliable
  compared to licensed data providers
- **Assume Forge can run autonomously overnight without additional
  infrastructure** — rejected: not technically accurate given how Claude is
  deployed today; stated here explicitly so the plan doesn't quietly rely
  on a capability that doesn't exist yet
