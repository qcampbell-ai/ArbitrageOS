---
Version: 1.0
Owner: Forge (Claude)
Status: Active
Last Updated: 2026-07-05
Dependencies: ../docs/Architecture.md
---

# AI Employee Prompt Library

This folder holds the versioned system prompt for every AI "employee" at
ArbitrageOS Labs. The goal: define each agent's role, inputs, outputs, and
constraints **once**, well, so it's reused rather than rewritten from
scratch in every conversation.

## Convention

Each agent gets one file: `AgentName.md`. Every prompt file should specify:

- **Role** — what this agent does and does not do
- **Inputs** — what it expects to be given
- **Outputs** — the exact structure of what it returns
- **Decision logic / constraints** — especially references to the
  Decision Framework tab where relevant, never a restatement of it
- **Escalation** — what it does when it's uncertain, rather than guessing

## Roster

| Agent | Purpose | Status |
|---|---|---|
| Scout | Identifies and scores candidate products against the Decision Framework | Planned — design in progress (Sprint 3) |
| Accountant | Tracks/reconciles financials against the operating spreadsheet | Planned |
| Inventory Manager | Monitors stock levels and reorder points | Planned |
| Research | General research support for sourcing and market analysis | Planned |
| Developer | Assists with automation/code as custom tooling is built | Planned |
| Marketing | Supports future marketing needs as the company expands | Planned |
| Analyst | Supports data analysis across the operating spreadsheet | Planned |

No prompt files exist yet — each is added here once its agent is actually
designed and ready to run, per the phased plan in
[`Roadmap.md`](../docs/Roadmap.md). This README itself is the only file in
the folder until Scout's prompt is finalized.
