# Dues — Initial 30-Day Marketing Plan

**Period:** starts 2026-10-10 (week 1) — dates shift if inputs arrive later.
**Budget ceiling:** AUD $100/month. Organic-first. Planned spend this period: **AUD $0**. No paid spend without explicit approval.
**Principle:** establish a trustworthy baseline before setting numeric growth targets. Any target is a hypothesis, not a guarantee.

This file is the source of truth for **current priorities**. Task status lives in [`tasks/`](../tasks/README.md).

## Current priorities
| # | Priority | Task | Owner | Blocked on |
|---|---|---|---|---|
| 1 | P0 | [002 Listing trust and compliance fixes](../tasks/inbox/002-listing-trust-and-compliance-fixes.md) — broken Terms link, privacy policy mismatch, personal data in screenshot | User (Claude drafts) | User decision |
| 2 | P0 | [001 ASO and performance baseline](../tasks/in-progress/001-aso-baseline-audit.md) — public listing done; analytics + per-localization keywords pending | User exports → Claude | Exports |
| 3 | P1 | [003 Keyword research per localization](../tasks/inbox/003-keyword-research-per-localization.md) | Claude | 001 |
| 4 | P1 | [004 Screenshot narrative brief](../tasks/inbox/004-screenshot-narrative-brief.md) | Claude → User | Feature confirmation |

## Week 1 — Establish the baseline
- [x] Verify current public listing in every English storefront, including regional differences (2026-10-10).
- [ ] User: fix or decide on live trust issues (Task 002).
- [ ] User: export App Store Connect data and per-localization metadata (instructions in [`analytics/baseline.md`](../analytics/baseline.md#how-to-obtain-the-data)).
- [ ] User: confirm listed features in 1.2.0 (audit §2).
- [ ] Claude: aggregate baseline report; rank English storefronts by verified data.
- Deliver: baseline report, evidence-backed ASO audit, prioritised task list.

## Week 2 — Prepare ASO improvements
- Keyword research for the top 1–2 localizations (Task 003); record sources and dates.
- Draft name/subtitle/keyword/promo-text changes per localization within current Apple limits.
- Screenshot storyboard using real screens and verified claims (Task 004).
- Deliver: listing drafts, keyword map, screenshot brief, measurement plan. Do not submit without approval.

## Week 3 — Organic content and one controlled test
- Draft a small batch of helpful content (see [`content/calendar.csv`](../content/calendar.csv)); actual app UI only.
- Choose **one** measurable experiment from [`experiments/backlog.md`](../experiments/backlog.md) based on baseline evidence; define metric, comparison, duration, and decision rule before launch.
- Public posting or listing changes require explicit approval.

## Week 4 — Review and decide
- Compare with the pre-change baseline; account for sample size, seasonality, the 1.2.0 release, and regional metadata differences.
- Record what worked, what didn't, and what's inconclusive in [`experiments/results.md`](../experiments/results.md).
- Write the next 30-day plan from evidence.
- Paid tests only with hypothesis, AUD cost, stop condition, and approval.

## Metrics to collect if available
Impressions, product-page views, first-time downloads, conversion rate — by territory and source type; proceeds, active subscriptions, trials, conversions, cancellations, refunds; content reach and clicks from platform analytics. Definitions: [`analytics/metric-definitions.md`](../analytics/metric-definitions.md).

Do not set a numeric target until a verified baseline exists.
