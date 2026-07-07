---
Version: 1.0
Owner: Forge (Claude)
Status: Active
Last Updated: 2026-07-05
Dependencies: None
---

# ArbitrageOS Labs

**ArbitrageOS Labs** is a capital allocation company that starts with Amazon
arbitrage and expands into consulting, real estate, and private equity. This
repository is the canonical, version-controlled source of truth for every
permanent artifact the company produces — strategy, architecture, decisions,
and (eventually) code.

If you are a human or an AI teammate picking this project up for the first
time, **read the documents in this order:**

1. This README (you're here)
2. [`docs/Company_Bible.md`](docs/Company_Bible.md) — mission, values, operating principles
3. [`docs/Product_Requirements.md`](docs/Product_Requirements.md) — what we're building and why
4. [`docs/Architecture.md`](docs/Architecture.md) — how the systems fit together
5. [`docs/Roadmap.md`](docs/Roadmap.md) — the phased plan and milestones
6. [`decisions/`](decisions/) — every architectural decision, in ADR format
7. [`sops/`](sops/) — Standard Operating Procedures for day-to-day execution, starting with [`SOP-001-Candidate-Discovery.md`](sops/SOP-001-Candidate-Discovery.md)

## Document Governance v1.0

ArbitrageOS Labs has exactly **one canonical source per artifact type.**
Nothing is ever duplicated across systems — everything else *links* to the
canonical copy.

| System | Role | Contains |
|---|---|---|
| **GitHub** (this repo) | Official source of truth | PRD, Company Bible, Architecture, Roadmap, ADRs, SOPs, AI agent prompts, code |
| **Google Sheets** | Operational system of record | Live business data: Dashboard, KPIs, Products, Inventory, Retailers, Purchases, Sales, Suppliers, Expenses, Daily Log, Scoreboard, Decision Framework |
| **Google Drive** | Temporary workspace | Receipts, PDFs, supplier catalogs, tax docs, brainstorms — nothing here is ever "official" |

**Rule:** if a number, rule, or metric already lives in the spreadsheet
(e.g. the 9 purchase tests on the *Decision Framework* tab, or KPI formulas
on the *KPIs* tab), documents in this repo reference it by name — they never
restate it. This is the fix for the "two sources of truth" risk identified
early in the project: one home per fact, always.

## Repository Structure

```
ArbitrageOS/
├── README.md              ← you are here
├── docs/                  ← permanent company documentation
│   ├── Company_Bible.md
│   ├── Product_Requirements.md
│   ├── Architecture.md
│   └── Roadmap.md
├── decisions/             ← Architecture Decision Records (ADRs)
│   ├── ADR-template.md
│   ├── ADR-0001-GitHub-Is-Canonical.md
│   ├── ADR-0002-Google-Sheets-Is-Operations.md
│   ├── ADR-0003-Drive-Is-Temporary.md
│   ├── ADR-0004-Agent-Role-Separation.md
│   └── ADR-0005-The-24-Hour-Rule.md
├── prompts/                ← system prompts for each AI "employee"
│   ├── README.md
│   └── Forge.md
├── sops/                    ← Standard Operating Procedures
│   └── SOP-001-Candidate-Discovery.md
├── database/                 ← (existing — see note below)
├── automations/                ← (existing — see note below)
├── dashboard/                    ← (existing — see note below)
├── ai-agents/                      ← (existing — see note below)
├── finance/                          ← (existing — see note below)
└── sourcing/                           ← (existing — see note below)
```

> **Note on `database/`, `automations/`, `dashboard/`, `ai-agents/`,
> `finance/`:** these were created in Sprint 1 and are intentionally left
> as-is here. `sops/` was also a Sprint 1 folder — it's now shown populated
> above since SOP-001 lives there. A later ADR should decide whether to
> rename/consolidate the still-empty ones — that decision hasn't been made
> yet, so this README doesn't presume an answer.

## The Team

| Role | Who | Responsibilities |
|---|---|---|
| **Founder** | You | Vision, decisions, execution, capital |
| **Atlas** | ChatGPT | Strategy, product direction, architecture, sprint planning, QA |
| **Forge** | Claude | Documentation, markdown/spreadsheet artifacts, automation builds, code |

## Company Identity

Working name: **ArbitrageOS Labs** (subject to change as the company grows
beyond Amazon arbitrage — this is a placeholder, not a legal decision).

## Status

This repository was bootstrapped in Sprint 1–3. See
[`docs/Roadmap.md`](docs/Roadmap.md) for what happens next.
