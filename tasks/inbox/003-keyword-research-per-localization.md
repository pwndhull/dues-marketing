# Task 003 — Keyword Research per English Localization

| Field | Value |
|---|---|
| ID | 003 |
| Priority | P1 |
| Owner | Claude (research) · User (current keyword fields; optional Search Ads popularity lookups) · ChatGPT review |
| Status | Ready once Task 001 provides current keyword fields and territory data |
| Opened | 2026-10-10 |
| Approval gates | None — research only. Any paid ASO tool needs approval and counts toward the AUD $100/month ceiling. |

## Objective
For each English localization that serves a priority storefront, record observable keyword evidence and propose a keyword map — without inventing search volume or difficulty.

**Business reason:** metadata changes should target phrases real users search for in that storefront, and the current listing already differs by region (US subtitle vs others).

## Current state
- Template and rules: [`aso/keyword-research.md`](../../aso/keyword-research.md)
- Regional listing differences: [`aso/current-listing-audit.md` §1a](../../aso/current-listing-audit.md#1a-regional-listings--verified-public)
- Competitor seed list (per storefront): [`aso/competitor-research.md`](../../aso/competitor-research.md)

## Constraints
- Priority storefronts must come from Task 001 territory data; until then, assume nothing about which market matters most.
- No volume/difficulty numbers without a named source.
- Only phrases describing verified features.

## Steps
- [ ] Fill the current keyword field table (from user).
- [ ] Pick 2–3 priority storefronts from territory data.
- [ ] Log candidate phrases with date, storefront, method, and observed results.
- [ ] Record competitors that actually appear for those phrases.
- [ ] Draft a keyword map per localization with rationale and risks.
- [ ] Hand off for ChatGPT review.

## Deliverables
Updated `aso/keyword-research.md` and `aso/competitor-research.md`.

## Acceptance criteria
Every phrase row has date, storefront, and method; no invented metrics; proposed keyword fields fit 100 bytes and exclude names already in the app name.

## Next action
Wait for Task 001 inputs. Then Claude starts with the storefront having the most impressions.
