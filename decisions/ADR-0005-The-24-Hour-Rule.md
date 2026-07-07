---
Version: 1.0
Owner: Atlas (ChatGPT) / Founder
Status: Accepted
Last Updated: 2026-07-06
Dependencies: ADR-0001-GitHub-Is-Canonical.md
---

# ADR-0005: The 24-Hour Rule for SOP Promotion

## Status

Accepted

## Context

ArbitrageOS Labs generates real operating knowledge through conversation —
between the Founder, Atlas, and Forge — faster than it gets written down.
The Candidate Discovery workflow is a clear example: it existed, evolved,
and was corrected twice in chat before anyone asked whether it should
become an official SOP. Without a trigger for *when* something graduates
from "conversation" to "documented procedure," valuable process knowledge
stays trapped in chat history, which isn't canonical (per
[ADR-0001](ADR-0001-GitHub-Is-Canonical.md)) and isn't reliably
retrievable by a future session of any AI teammate.

Note: ADR-0001 already establishes that SOPs, once written, are canonical
in GitHub — that part doesn't need restating here. What was missing was a
rule for *deciding when* a procedure is mature enough to write down in the
first place.

## Decision

**The 24-Hour Rule:** if the same operational task is done — or the same
process is discussed/refined — **twice**, the team asks: *"Should this
become an SOP?"*

If yes:

- **Forge** documents it as a numbered SOP in `/sops`
- **GitHub** stores it as the canonical version
- **Atlas** references it going forward rather than re-explaining the
  process in conversation
- **The Founder** follows the documented version, and treats deviations
  from it as something to discuss and formally update, not silently work
  around

This does not require waiting a literal 24 hours — the name refers to the
principle of promoting quickly once a pattern repeats, not a fixed timer.

## Consequences

- Reduces the risk of process knowledge existing only in chat transcripts,
  which are not canonical and not guaranteed to persist or be searchable
- Creates a lightweight, low-ceremony trigger (repetition) rather than a
  heavyweight one (e.g., "document everything up front," which tends to
  produce SOPs for processes that never stabilize)
- Requires actual follow-through: someone has to notice the repetition and
  ask the question — this is a discipline commitment, not an automated
  safeguard
- SOPs written this way should expect revision as reality corrects early
  assumptions (see SOP-001's own version history, which already reflects
  a toolset correction found before the SOP was even finalized)

## Alternatives Considered

- **Document every process the first time it's discussed** — rejected:
  produces premature documentation for processes that haven't stabilized
  yet, creating more revision churn than value
- **No formal trigger; document opportunistically** — rejected: this is
  effectively what was happening before, and it's exactly what let the
  Candidate Discovery workflow evolve twice in chat before being written
  down anywhere canonical
