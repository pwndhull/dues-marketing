# Task 004 — Screenshot Narrative Brief

| Field | Value |
|---|---|
| ID | 004 |
| Priority | P1 |
| Owner | Claude (brief) · User (feature confirmation, capturing real screens, approval) |
| Status | **Largely superseded — user decision needed.** The app repo already has a captioned screenshot plan (`docs/APP-STORE-LISTING.md`, `docs/strategy/ACQUISITION.md`), a Debug screenshot mode with demo data, and per-region capture and framing scripts (`tools/aso/`). New iPhone screenshots for 2.0 are uploaded for 5 locales. What remains: iPad 13" screenshots, and a review of the 2.0 set once it is public. Propose closing this task or narrowing it to that review |
| Opened | 2026-10-10 |
| Approval gates | Uploading screenshots to App Store Connect is a live action — user only, with explicit approval. |

## Objective
Write a captioned screenshot storyboard using real Dues screens and verified features only, with realistic demo data appropriate for the target storefront.

**Business reason:** current screenshots have no captions, don't show the subtitle's lead feature, and show long-overdue bills, lakh-grouped dollar figures, and an email-format address that may or may not be real ([audit §3](../../aso/current-listing-audit.md#3-screenshots--verified-public)). Whether better screenshots improve conversion is a **hypothesis**, to be measured.

## Constraints
- Real UI only; no mock features. Demo data only — no personal data.
- Number/currency format should match the storefront (e.g. `$1,250.00` for US/AU, `£` for GB).
- Captions must not include prices or unverifiable superlatives (Guideline 2.3.7).
- The US localization's subtitle differs; the narrative may need a variant per localization.

## Deliverables
A storyboard draft in `aso/listing-drafts.md`: up to 10 slots, each with caption, screen, feature, verification status, and demo-data notes; plus a measurement plan.

## Acceptance criteria
Every slot maps to a feature confirmed by the user; measurement plan names metric, baseline period, and confounders.

## Next action
**User:** confirm which listed features (audit §2) are live in 1.2.0. **Claude:** then drafts the storyboard.
