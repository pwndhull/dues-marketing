# Task 002 — Listing Trust and Compliance Fixes

| Field | Value |
|---|---|
| ID | 002 |
| Priority | P0 |
| Owner | User (all live changes) · Claude (draft text and checklists on request) |
| Status | Ready |
| Opened | 2026-10-10 |
| Approval gates | Website changes, screenshot replacement, and App Store Connect metadata updates are **live actions — user only**. Claude drafts only. |

## Objective
Fix publicly visible problems found in the 2026-10-10 listing audit that can undermine trust, and may raise App Review or privacy concerns, regardless of any growth strategy.

**Business reason:** these issues affect every storefront and every visitor; they are cheap to fix and do not depend on analytics.

## Evidence and sources
From [`aso/current-listing-audit.md`](../../aso/current-listing-audit.md) (accessed 2026-10-10):
| Finding | Evidence | Label |
|---|---|---|
| L1 Terms of Use link 404 | https://easy-bills.netlify.app/terms → HTTP 404 | Verified fact |
| L2 Privacy policy titled "BillFlow", last updated 2026-03-22, does not mention several data types declared in the App Privacy label | https://easy-bills.netlify.app/ vs App Privacy section on https://apps.apple.com/au/app/id6761047973 | Verified fact; compliance judgement is the user's (not legal advice). Guideline 5.1.1(i): https://developer.apple.com/app-store/review/guidelines/ |
| L3 iPhone screenshot 3 appears to show a real email address | Screenshot 3 on the product page (all storefronts) | Verified observation; whose address is Unknown |
| L4 Description says "NEW IN VERSION 1.1.0"; live is 1.2.0 | iTunes lookup description | Verified fact |
| L10 "BillFlow" brand overlaps with another App Store app | AU "You Might Also Like" | Verified; history Unknown |

## Steps
- [ ] User: restore a working Terms of Use page (or point the description to Apple's standard EULA if that is what is intended — NEEDS CONFIRMATION). Check Schedule 2 of the Apple Developer Program License Agreement for subscription-link requirements.
- [ ] User: update the privacy policy so it names Dues, matches the current App Privacy label and SDKs, and has its own URL; update the Privacy Policy URL in App Store Connect.
- [ ] User: replace screenshot 3 with a demo account (no real email). Consider doing this together with Task 004 to avoid two screenshot uploads.
- [ ] Claude (on request): draft corrected description sections (remove stale "NEW IN VERSION 1.1.0") using only verified claims → `aso/listing-drafts.md`.
- [ ] Claude: re-check the live links and listing after the user reports changes; record date and result in the listing audit.

## Deliverables
- Working Terms and Privacy URLs (user)
- Updated screenshot 3 (user)
- Draft description fix in `aso/listing-drafts.md` (Claude, if requested)
- Re-check entry in `aso/current-listing-audit.md`

## Acceptance criteria
- Both URLs return HTTP 200 with Dues-branded, current content on re-check.
- No personal data visible in any storefront's screenshots.
- No new unverified claims introduced.

## Open questions
- Was "BillFlow" a previous name of this app? Is `easy-bills.netlify.app` the long-term domain?
- Is the email in screenshot 3 a real person's address?

## Next action
**User:** decide whether to fix L1–L3 now; tell Claude if a draft of the description fix is wanted.
