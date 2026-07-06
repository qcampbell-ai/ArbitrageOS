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
| Forge | Engineering lead: data ingestion (licensed sources only), spreadsheet/automation builds, documentation | Active — see [`Forge.md`](Forge.md) |
| Atlas | Strategy and capital allocation: scores candidates, recommends Buy/Wait/Reject, manages roadmap | Active — prompt maintained on the ChatGPT side; referenced here for completeness |
| Sentinel | Monitoring: inventory aging, cash runway, account health, margin drops, concentration risk | Planned — not yet scoped or built (see [ADR-0004](../decisions/ADR-0004-Agent-Role-Separation.md)) |
| ~~Scout~~ | ~~Originally: find and score products~~ | **Retired** — split into Forge (data) + Atlas (scoring) per [ADR-0004](../decisions/ADR-0004-Agent-Role-Separation.md) |

Additional narrow-scope agents (Accountant, Inventory Manager, Research,
Developer, Marketing, Analyst) remain ideas for future sprints, not yet
designed. Add a prompt file here only once an agent is actually built —
this folder should never contain more "planned" placeholders than active
prompts.
