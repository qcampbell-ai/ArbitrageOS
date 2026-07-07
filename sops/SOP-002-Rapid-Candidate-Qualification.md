---
Version: 1.0
Owner: Atlas (authored) / Forge (documented)
Status: Active
Last Updated: 2026-07-06
Dependencies: SOP-001-Candidate-Discovery.md, ../decisions/ADR-0004-Agent-Role-Separation.md, Google Sheets — Products tab, Daily Log tab, Decision Framework tab
---

# SOP-002: Rapid Candidate Qualification (Daily Sourcing Operations)

## Purpose

To give every sourcing session a clear objective, a fast way to discard
weak candidates before they consume analysis time, and a consistent way
to close out the session so the business learns from it. This SOP defines
**how the Founder qualifies candidates quickly**, distinct from how Atlas
formally evaluates them (see [ADR-0004](../decisions/ADR-0004-Agent-Role-Separation.md)
— Founder qualifies, Atlas evaluates).

## Scope

Governs the operational rhythm of a single sourcing session, from mission
assignment through session close-out. It does **not** redefine how a
candidate is discovered or validated in detail — see
[SOP-001](SOP-001-Candidate-Discovery.md) for that — and it does **not**
redefine the 9-test Decision Framework or the Capital Allocation Scorecard,
both of which live in the operating spreadsheet.

## Daily Mission Assignment

Every sourcing session starts with a specific, measurable objective —
never "go find some products." A mission is defined by **one** of:

- **One retailer** ("Visit Walmart, find 5 clearance candidates")
- **One category spread** ("Find one toy, one home improvement item, one
  grocery item")
- **A fixed candidate count** ("Find 3 candidates before stopping")

The mission for the next session is recorded in the existing **Daily
Log** tab's `Tomorrow's Priorities` field — no separate "Mission" tracking
is needed, since that field already exists and serves this purpose.

> **Category note:** if a mission includes grocery/consumable items, check
> Amazon category-specific eligibility (not just general ASIN eligibility)
> before treating a grocery candidate the same as a toy or hard-goods
> candidate — grocery listings can carry additional approval and
> expiration-date requirements that a standard SellerAmp eligibility check
> may not fully surface.

## Rapid Candidate Qualification

This is the Founder's fast, pre-analysis filter — applied *before* a
candidate reaches the full SellerAmp/Keepa validation in SOP-001, and
*before* it necessarily earns a row in the Products tab.

### The Quick Reject Filter

Reject immediately, no further analysis, if any of these are true at a
glance:

- ❌ Restricted brand or category you already know you can't sell
- ❌ Obviously negative or razor-thin margin at first glance
- ❌ Wild, obvious price volatility (if you already happen to know the
  product's history)
- ❌ Known IP complaint history
- ❌ Oversized/bulky item (deprioritized for Phase 1, not a permanent ban)
- ❌ Hazmat-labeled packaging (deprioritized for Phase 1, not a permanent ban)

If none of these obviously apply, move to SOP-001's SellerAmp scan.

### The Three-Minute Rule

If, after three minutes of looking at a single product, you still can't
tell whether it's promising — **skip it.** There are millions of
products; don't spend the session's time budget on one uncertain item.

### Minimum Information Before a Products Tab Entry

A candidate only earns a row in the Products tab once it has survived the
Quick Reject Filter **and** the SellerAmp scan from SOP-001. At that
point, minimum required fields are the same required fields already
enforced by conditional formatting on the Products tab (ASIN, Category,
Retail Cost, Amazon Price, Retailer, Amazon Eligibility) — not restated
here. Two additional fields introduced by this SOP:

- **Source Type** — how you found it (Retail Clearance, Slickdeals, Weekly
  Ad, etc.) — this is business intelligence for later, not a decision input
- **Founder Confidence** — your gut read (High/Medium/Low) recorded
  *before* Atlas scores it, so intuition can be compared against outcomes
  over time

## Session Completion

At the end of every sourcing session, log a row in the **Daily Log** tab
with:

| Field | How it's captured |
|---|---|
| Retailers Visited | Manual — type the retailer(s) |
| Candidates Found | **Automatic** — counts Products tab rows with today's Date Added |
| Candidates Rejected | Manual — a simple tally. Most rejects happen at the Quick Reject Filter stage and never get a spreadsheet row by design, so this number can't be pulled from the sheet automatically. That's expected, not a bug. |
| Candidates Submitted for Review | **Automatic** — counts today's Products tab rows that have moved past `Found`/`Researching` |
| Lessons Learned | Manual — one or two honest sentences. This is the field that compounds into institutional knowledge over time. |

Hours spent sourcing uses the Daily Log's existing `Hours Worked` field —
no separate column, to avoid tracking the same thing twice.

## Metrics

The two automatic Daily Log fields above (`Candidates Found`,
`Candidates Submitted for Review`) are the daily metrics — they are
formulas reading directly from the Products tab, so they can never drift
out of sync with it. No new KPIs tab entries or Dashboard cards are
required for Phase 1; if a rolling weekly/monthly view becomes useful
later, it should be a formula reading these same Daily Log columns, not a
newly hand-tracked number.

## Common Mistakes

- Starting a session with no defined mission — leads to unfocused browsing
- Spending 20 minutes deliberating on one uncertain product instead of
  applying the Three-Minute Rule and moving on
- Logging "Founder Confidence" *after* seeing Atlas's score instead of
  before — this defeats the purpose of comparing intuition to outcomes
- Forgetting to log a session at all — a missed Daily Log entry means the
  Daily Log staleness banner (already built into that tab) will flag it

## Version History

| Version | Date | Author | Change |
|---|---|---|---|
| 1.0 | 2026-07-06 | Atlas (authored) / Forge (documented) | Initial version. References SOP-001 rather than repeating discovery/validation steps; adds Products tab fields (Source Type, Founder Confidence) and Daily Log fields (Retailers Visited, Candidates Found/Submitted — automatic, Candidates Rejected — manual, Lessons Learned) required to support this SOP. |
