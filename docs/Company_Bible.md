---
Version: 1.0
Owner: Forge (Claude)
Status: Draft
Last Updated: 2026-07-05
Dependencies: README.md
---

# ArbitrageOS Labs — Company Bible

## Mission

To build a disciplined, systems-driven capital allocation company — starting
with Amazon retail arbitrage and compounding into consulting, real estate,
and private equity — using AI-assisted operations as the core operating
advantage rather than a novelty.

## Vision

In five years, ArbitrageOS Labs is not "an Amazon seller." It is a capital
allocation company with a repeatable operating system: a documented process
for finding, vetting, and executing opportunities across multiple asset
classes, run by a small human team supported by a bench of AI "employees"
(Scout, Accountant, Inventory Manager, and others as they're built).

The Amazon arbitrage business is the **proving ground** for that operating
system, not the end state. Every SOP, decision framework, and automation
built here is designed to generalize to the next asset class.

## Values

- **Discipline over hustle.** We follow the Decision Framework every time,
  even when a "deal" feels exciting. See the *Decision Framework* tab in the
  operating spreadsheet for the actual rules — they are not restated here.
- **One source of truth.** Every fact lives in exactly one place. See
  [ADR-0001](../decisions/ADR-0001-GitHub-Is-Canonical.md),
  [ADR-0002](../decisions/ADR-0002-Google-Sheets-Is-Operations.md), and
  [ADR-0003](../decisions/ADR-0003-Drive-Is-Temporary.md).
- **Documented over remembered.** If it isn't written down, it didn't
  happen. This is doubly true because our AI teammates have no memory
  between sessions — the repository *is* their memory.
- **Compounding over one-off wins.** Every dollar and every hour is judged
  by whether it builds a reusable system (an automation, a template, an
  SOP) or just moves one transaction forward.
- **Consistency over intensity.** Small, daily progress beats sporadic
  bursts. This is a stated commitment from both Atlas and the Founder.

## Operating Model

ArbitrageOS Labs runs on a three-role team, described in full in the root
[README.md](../README.md):

- **Founder** — vision, decisions, execution, capital
- **Atlas** — strategy, architecture, sprint planning, QA
- **Forge** — documentation, spreadsheet/automation builds, code

Work happens in **sprints**, not open-ended tasks. Each sprint defines
objectives, deliverables (per-role), a Definition of Done, and a sprint
review. See [Roadmap.md](Product_Requirements.md) and the sprint history for
specifics — this document defines the philosophy, not the schedule.

## Decision-Making Philosophy

1. **Rules before judgment calls.** Purchasing decisions run through the
   Decision Framework (spreadsheet) before any subjective "this looks good"
   reasoning is allowed to apply.
2. **Record the reasoning, not just the outcome.** Non-trivial architectural
   or business decisions get an ADR in [`/decisions`](../decisions/), so the
   *why* survives even if the person who made the call isn't in the room.
3. **Default to reversible.** Prefer decisions that are cheap to undo
   (a $500 test buy, a low-code automation) over irreversible ones (long
   contracts, large capital commitments) until the system has proven itself.
4. **Escalate ambiguity, don't guess silently.** If a rule doesn't clearly
   apply to a new situation, that's a signal to write a new ADR or update
   the Decision Framework — not to quietly make an exception.

## Long-Term Strategy

Capital compounds in stated stages: **$500 → $5,000 → $50,000 → a company
that supports broader investment goals** (consulting, real estate, private
equity). Each stage is expected to unlock the next phase of the roadmap
(see [Roadmap.md](Roadmap.md)): Phase 1 (Business systems), Phase 2
(Technology/automation), Phase 3 (Growth into wholesale, new marketplaces,
smarter automation, and eventually new asset classes entirely).

The underlying bet: a business that treats **decision discipline and
documentation as infrastructure** will outlast any single marketplace,
supplier relationship, or product trend.
