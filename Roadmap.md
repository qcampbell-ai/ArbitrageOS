---
Version: 1.0
Owner: Forge (Claude)
Status: Draft
Last Updated: 2026-07-05
Dependencies: Product_Requirements.md, Architecture.md
---

# Roadmap — ArbitrageOS

## Phasing Overview

| Phase | Focus | Core Deliverables |
|---|---|---|
| **Phase 1 — Business** | Operating discipline | Operating system (spreadsheet), SOPs, financial model, Decision Framework |
| **Phase 2 — Technology** | Automation | Airtable migration, n8n automations, AI agents (Scout first), standalone dashboard |
| **Phase 3 — Growth** | Scale | Wholesale sourcing, additional marketplaces, smarter/more autonomous automations, potential expansion into consulting/real estate/private equity |

Capital milestones track alongside phases, not strictly within them:
**$500 → $5,000 → $50,000 → a company that supports broader investment
goals.** Actual dollar figures are tracked live on the **Scoreboard** tab —
this document does not restate them.

## Sprint History

### Sprint 1 — Foundation
- GitHub repository created
- Amazon Operating Spreadsheet built (Dashboard, KPIs, Products, Inventory,
  Purchases, Sales, Suppliers, Expenses, Daily Log)
- Core tool accounts identified (Seller Central, Airtable, GitHub, n8n,
  Keepa, SellerAmp SAS, Discord)
- Company Scoreboard and Decision Framework defined and later integrated
  directly into the spreadsheet (as tabs with automation/color-coding,
  rather than as separate artifacts)

### Sprint 2 — Governance & Founder Kit (in progress)
- Document Governance policy established: GitHub = canonical docs,
  Sheets = operational data, Drive = temporary workspace
- Founder Kit build order set: README → Company_Bible → Product_Requirements
  → Architecture → Roadmap → ADRs (replacing a single Decision_Log)
- `/prompts` directory reserved for AI agent system prompts
- Team roles formalized: Founder / Atlas / Forge

### Sprint 3 — Scout Design (next)
- Design Scout v1: inputs (product URLs/UPCs/ASINs/retailer prices),
  decision logic (referencing the Decision Framework tab), output format,
  confidence scoring, and future integration points (Keepa, SellerAmp,
  n8n)
- First Scout system prompt committed to `/prompts/Scout.md`

## Upcoming Milestones (Draft — subject to Atlas's sprint planning)

- **Scout v1 operational**: can take a single product input and return a
  structured PASS/FAIL/Needs-Review recommendation
- **First automation live in n8n**: even a simple one (e.g., pulling a
  Keepa price history on demand) to validate the automation layer works
  end-to-end
- **SOP Library started**: sourcing, buying, prepping, shipping, and
  performance-review SOPs, committed to the repository (folder location
  TBD pending resolution of the folder-naming question noted in the root
  README)
- **Airtable migration evaluated**: a go/no-go decision, documented as an
  ADR, once the spreadsheet's limitations (if any) become concrete rather
  than theoretical

## Success Metrics (by Phase)

- **Phase 1:** Decision Framework is followed with zero exceptions;
  Scoreboard has zero missed weekly updates
- **Phase 2:** Scout reduces manual research time per product without
  reducing recommendation quality; at least one n8n automation running
  reliably in production
- **Phase 3:** Capital and product-line diversification targets (tracked
  on the Scoreboard) are being hit consistently, not sporadically

## Explicit Non-Goals (For Now)

- Building custom software before low-code tools (Sheets, Airtable, n8n)
  have been proven insufficient
- Expanding into consulting, real estate, or private equity before the
  Amazon arbitrage operating system is stable and profitable
- Renaming "ArbitrageOS Labs" — deferred deliberately until the company's
  direction is clearer
