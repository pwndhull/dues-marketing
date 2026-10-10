# Task 001 — ASO and Performance Baseline Audit

| Field | Value |
|---|---|
| ID | 001 |
| Priority | P0 |
| Owner | Claude (public research, analysis, drafts) · User (App Store Connect exports, feature confirmation, approval) |
| Status | In progress — **Blocked** on user-provided exports and per-localization metadata (see Next action) |
| Opened | 2026-10-10 (originally created by the user; restructured 2026-10-10 by Claude) |
| Risk | Low — research and drafting only |
| Approval gates | None for this task. Any listing change it leads to needs separate explicit approval. |

## Objective
Create an evidence-backed snapshot of the current Dues listing **in each region** and of performance, before recommending any changes.

**Business reason:** without a baseline, no listing change or experiment can be evaluated, and no target can be set honestly.

## Current state
- Public listing audit done for 16 storefronts on 2026-10-10 → [`aso/current-listing-audit.md`](../../aso/current-listing-audit.md). Regional difference found: US subtitle differs from all others checked.
- Performance baseline template → [`analytics/baseline.md`](../../analytics/baseline.md) — all values Unknown.
- Metric definitions → [`analytics/metric-definitions.md`](../../analytics/metric-definitions.md).
- Seed competitor list → [`aso/competitor-research.md`](../../aso/competitor-research.md).

## Evidence and sources
See Sources table S1–S8 in [`aso/current-listing-audit.md`](../../aso/current-listing-audit.md#sources). All accessed 2026-10-10.

## Constraints
- Claude has **no** App Store Connect, subscription dashboard, or Search Ads access.
- Keyword fields are not public.
- Raw exports stay in `analytics/imports/` (Git-ignored); only aggregates are committed.

## Steps
Original steps (from the user's initial task) with progress:
- [x] Inspect current App Store listing and record the date checked. *(2026-10-10, 16 storefronts)*
- [x] Record title, subtitle, description, screenshots, price/subscription claims, privacy URL, supported locales. *(per storefront)*
- [ ] Record keyword field — **per localization** *(needs user)*
- [ ] Verify product claims against the current build or user-provided authoritative evidence. *(claims listed in audit §2; needs user confirmation)*
- [ ] Research relevant search phrases and a small competitor set; cite URLs and access dates. *(seed list done; continues in Task 003)*
- [ ] Use a user-provided App Store Connect aggregate export. Do not assume account access.
- [ ] Summarise impressions, page views, first-time downloads, conversion, territory, proceeds/subscription metrics only when present.
- [x] Identify prioritised opportunities with evidence, effort, and confidence. *(audit §6, L1–L11; revisit after analytics)*
- [ ] Propose one measurable next experiment without launching it. *(after baseline exists)*

## Deliverables
- [`aso/current-listing-audit.md`](../../aso/current-listing-audit.md) — done (public portion)
- [`analytics/baseline.md`](../../analytics/baseline.md) and `analytics/reports/YYYY-MM-DD-baseline.md` — pending export
- [`aso/keyword-research.md`](../../aso/keyword-research.md) — current keyword fields table filled (pending user)
- One experiment proposal in [`experiments/backlog.md`](../../experiments/backlog.md) based on the baseline

## Acceptance criteria
- No fabricated metrics or claims; unknowns explicitly labelled.
- Baseline report has date range, extraction date, timezone, source, definitions, comparison period, limitations.
- Territory breakdown identifies which English-speaking storefronts actually produce impressions/downloads.
- Raw exports remain untracked; nothing published or spent.

## Open questions (for the user)
1. Per-localization name, subtitle, keyword field, promo text (App Store Connect → your app → each English localization).
2. Exports listed in [`analytics/baseline.md` → How to obtain the data](../../analytics/baseline.md#how-to-obtain-the-data).
3. Feature confirmations listed in audit §2 and §7.

## Next action
**User:** provide items 1–2 above (paste aggregate numbers into a PR comment or drop CSVs into local `analytics/imports/` in a Claude session). **Claude** then writes the baseline report and updates this task.
