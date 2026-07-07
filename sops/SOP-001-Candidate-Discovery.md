---
Version: 1.0
Owner: Atlas (authored) / Forge (documented)
Status: Active
Last Updated: 2026-07-06
Dependencies: ../README.md, ../docs/Architecture.md, Google Sheets — Decision Framework tab, Products tab, Retailers tab
---

# SOP-001: Candidate Discovery

## Purpose

To define a repeatable, disciplined process for finding, validating, and
entering product candidates into the operating spreadsheet — so every
opportunity reaches the Founder and Atlas in a consistent, evaluable
format, regardless of who found it or which day it was found.

## Scope

Applies to Phase 1 of ArbitrageOS Labs: Amazon FBA retail arbitrage,
sourced from physical and online retail. It does not cover wholesale,
liquidation, or non-Amazon marketplaces — those are future-phase
extensions of the same underlying discipline (finding mispriced assets),
not covered by this version of the SOP.

This SOP reflects the Founder's **actual current toolset**: SellerAmp SAS
(active) and **free-tier Keepa** (no Keepa Pro / Product Finder). It does
not assume access to paid discovery tools. If the toolset changes (e.g.,
Keepa Pro is purchased later), this SOP should be revised — see Version
History.

## Prerequisites

- Amazon Seller Central account active for at least one marketplace
  (as of this SOP's authoring: US live; additional country reactivations
  pending)
- SellerAmp SAS subscription active
- A free Keepa account (for chart/price-history viewing only — no
  subscription required for this SOP)
- The **Retailers** tab populated with at least a starting list of
  approved sourcing retailers
- Familiarity with the Decision Framework tab (this SOP feeds candidates
  into it; it does not redefine its 9 tests — see that tab for the
  authoritative rules)

## Required Tools

| Tool | Tier Used | Role in This SOP |
|---|---|---|
| SellerAmp SAS | Paid (active) | Profitability, fee, and eligibility scan |
| Keepa | **Free** (chart view only) | Price-history and sales-rank **validation** — not discovery |
| Amazon Seller App | Free | On-the-go barcode scanning at retail locations |
| Google Sheets — Products tab | N/A | Candidate record-keeping |
| Google Sheets — Retailers tab | N/A | Approved sourcing sources |

**Not required for this SOP:** Keepa Product Finder, Keepa saved
searches/alerts, Keepa API/bulk export. These are Keepa Pro features.
Phase 1 does not depend on them.

## Definitions

- **Candidate** — any product entered into the Products tab for
  evaluation, regardless of how early-stage
- **Discovery** — the act of noticing a potential candidate (this SOP's
  main subject)
- **Validation** — confirming a candidate's profitability and price
  stability before it's ready for Atlas's review
- **Framework Verdict** — the automatic PASS-GO / FAIL-SKIP / Needs Review
  result computed from the 9-test Decision Framework (see the Decision
  Framework tab — not redefined here)
- **Atlas Recommendation** — Atlas's separate, judgment-based Buy / Wait /
  Reject call, which can differ from the Framework Verdict (see
  [ADR-0004](../decisions/ADR-0004-Agent-Role-Separation.md))
- **CAS (Capital Allocation Scorecard)** — Atlas's 100-point scoring model
  (see the Products tab's CAS columns) — not part of this SOP's process,
  only referenced as the next step after discovery

## Step-by-Step Procedure

### 1. Deal Discovery

Look for price discrepancies at the source, not on Amazon. Approved
starting points:

- Physical retail stores (see the **Retailers** tab for the approved list)
- Retailer clearance sections, both in-store and online
- Retailer apps showing current markdowns/promotions
- Weekly retailer sales ads
- Reputable deal communities (e.g., Slickdeals)

**Goal for a single session: 2–4 quality candidates, not an exhaustive
sweep.** Quality over volume.

For each candidate, note (mentally or on paper, before touching the
spreadsheet): product name, retailer, retail cost, and where you found it
(URL or store location).

### 2. SellerAmp Scan

Scan the barcode or search the ASIN in SellerAmp SAS. Check:

- Estimated Amazon fees and profit
- Amazon eligibility / any restrictions on your account for this listing

**If SellerAmp shows the product is unprofitable or restricted, reject it
here and move on.** Do not proceed to Keepa for a candidate that's already
failed on profitability or eligibility.

### 3. Keepa Chart Validation (Free Tier)

For candidates that pass Step 2, open the product's **Keepa chart page**
(no Product Finder, no paid features needed) and check:

- **Price stability** — does the chart show a relatively flat/gently
  sloped line, or wild swings?
- **Sales rank trend** — is it reasonably steady, or one isolated spike?

**If the price history is unstable or the sales rank trend looks like a
one-off spike, reject it here.**

### 4. Enter Into the Products Tab

The moment a candidate survives Steps 2–3 (or even earlier, if you want to
log it while still deciding), create its row in the **Products** tab:

- Set **Opportunity Status** to `Found` as soon as you jot it down at all
- Move it to `Researching` once you begin Steps 2–3 in earnest
- Fill in: Product Name, ASIN, Category, Retailer, Product URL, Retail
  Cost, Amazon Price, Amazon Eligibility, Sales Rank, and a short Keepa
  Summary note (e.g., "stable 90-day price, steady rank")
- Missing required fields will highlight orange automatically — fill
  those before moving the status forward

### 5. Ready for Review

Once all required fields are filled and the **Framework Verdict** column
reads `PASS - GO` (or any `Needs Review` items have been resolved), set
**Opportunity Status** to `Ready for Review`.

### 6. Hand Off to Atlas

Bring the candidate(s) to Atlas. Atlas scores the Capital Allocation
Scorecard, sets the **Atlas Recommendation** (Buy/Wait/Reject) and
**Atlas Rationale**, and moves the status to `Recommended`.

### 7. Founder Decision

Review Atlas's recommendation and rationale. Decide, and update
**Opportunity Status** to `Approved` or leave it at `Recommended` if you're
waiting, or note the reason if rejecting despite a Buy recommendation.

## Candidate Acceptance Criteria

A candidate is ready to leave `Researching` and enter `Ready for Review`
only when:

1. All required Products tab fields are complete (no orange highlights)
2. **Framework Verdict = PASS - GO** (see the Decision Framework tab for
   the 9 underlying tests — not restated here)
3. SellerAmp has confirmed profitability and Amazon eligibility
4. Keepa's free chart shows acceptable price stability and sales rank trend

A `Needs Review` or `FAIL - SKIP` Framework Verdict means the candidate
does not advance — go back to Step 1.

## Spreadsheet Workflow (Quick Reference)

| Stage | Opportunity Status | Primary Tab Touched |
|---|---|---|
| Just noticed | `Found` | Products |
| Actively scanning/validating | `Researching` | Products |
| All fields complete, Verdict = PASS | `Ready for Review` | Products |
| Atlas has scored and recommended | `Recommended` | Products (CAS + Atlas columns) |
| Founder has decided to buy | `Approved` → `Purchased` | Products → Purchases |

## Common Mistakes

- **Starting on Keepa or Amazon instead of at the retail source.** Arbitrage
  opportunities begin where the price discrepancy begins — searching
  Amazon first starts from the wrong end.
- **Assuming Keepa Product Finder is required.** It isn't, for Phase 1.
  Free chart access is sufficient for validation.
- **Skipping straight to Keepa before SellerAmp.** Check profitability and
  eligibility first — it's the faster reject, and there's no point
  validating price history on a product that's already unprofitable or
  restricted.
- **Forgetting to set Opportunity Status.** An un-tracked candidate is
  invisible to Atlas and easy to lose.
- **Confusing Framework Verdict with Atlas Recommendation.** A PASS-GO
  verdict does not automatically mean "buy" — Atlas's CAS score and
  judgment call still apply.
- **Letting a candidate sit in `Found`/`Researching` too long.** Rows
  stuck more than 14 days will highlight orange automatically as a
  reminder to move them forward or archive them.

## Version History

| Version | Date | Author | Change |
|---|---|---|---|
| 1.0 | 2026-07-06 | Atlas (authored) / Forge (documented) | Initial version. Written directly against the Founder's actual toolset (free-tier Keepa, no Product Finder) — supersedes an earlier informal, chat-only workflow draft that assumed Keepa Pro access, which was never committed to the repository. |
