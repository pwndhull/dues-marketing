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
From [`aso/current-listing-audit.md`](../../aso/current-listing-audit.md). First observed 2026-10-10 at ~08:40 UTC and re-confirmed at 08:59–09:00 UTC in [Task 005](../review/005-reconcile-listing-evidence.md):
| Finding | Evidence | Label |
|---|---|---|
| L1 Terms of Use link 404 | https://easy-bills.netlify.app/terms → HTTP 404 (both checks) | Verified fact, as of 2026-10-10 |
| L2 Privacy policy titled "BillFlow", last updated 2026-03-22. Its text does not mention phone number, contacts, coarse location, photos/videos, analytics or crash data, all of which the App Privacy label declares (developer-declared; not verified by Apple) | https://easy-bills.netlify.app/ vs the App Privacy section on https://apps.apple.com/au/app/dues-bill-tracker-reminder/id6761047973 and the `/us/` page (per-purpose table in audit §4) | Verified fact; compliance judgement is the user's (not legal advice). Guideline 5.1.1(i): https://developer.apple.com/app-store/review/guidelines/ |
| L3 iPhone screenshot 3 displays an email-format address | Screenshot 3 on the product page (same image URL in all 16 storefronts) | Verified observation; whether it is real is **Unknown** |
| L4 Description says "NEW IN VERSION 1.1.0"; live is 1.2.0 | iTunes lookup description | Verified fact |
| L10 "BillFlow" brand overlaps with another App Store app | AU "You Might Also Like" | Verified; history Unknown |

## Update 2026-10-10 — app repositories ([Task 006](../review/006-reconcile-with-app-repositories.md))
- **L1:** the app itself (1.2.0 and 2.0) links Terms and Privacy to Google Sites pages (HTTP 200; content not read). The live Netlify site serves an old "BillFlow" deploy, and the `Easy-bills-web` repo is **not** what is deployed there. The pending 2.0 description already uses the Google Sites URLs, so releasing 2.0 fixes the description link. The **Privacy Policy URL field** in App Store Connect still needs checking.
- **L2:** the label's location and photos entries have no matching permission in code (only contacts, microphone and speech). Review whether the label is over-declared or whether an SDK collects these. The app repo's 2.0 notes say "privacy label published (13 data types, none for tracking)", which matches the 13 types observed live.
- **L3:** the email likely belongs to the owner or a team account (it matches the app repo's history). The new 2.0 iPhone screenshots are uploaded for en-US, en-AU, en-CA, fr-CA and en-GB; the iPad 13" en-US slot still has the old set.
- **L4:** the pending 2.0 description removes the stale section and the code-contradicted claims (150+ currencies, wrong categories, offline).
- **Net:** releasing 2.0 resolves most of this task. What remains: confirm the App Store Connect privacy URL, review the label against SDKs, replace the iPad screenshots, and decide what happens to `easy-bills.netlify.app`.

## Steps
- [ ] User: restore a working Terms of Use page (or point the description to Apple's standard EULA if that is what is intended — NEEDS CONFIRMATION). Check Schedule 2 of the Apple Developer Program License Agreement for subscription-link requirements.
- [ ] User: update the privacy policy so it names Dues, matches the current App Privacy label and SDKs, and has its own URL; update the Privacy Policy URL in App Store Connect.
- [ ] User: confirm whether the address is real. Either way, consider replacing screenshot 3 with a clearly fictional demo account. Consider doing this together with Task 004 to avoid two screenshot uploads.
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
- Does the App Privacy label accurately reflect 1.2.0's data practices and SDKs? Update the policy or the label, whichever is wrong.
- Was "BillFlow" a previous name of this app? Is `easy-bills.netlify.app` the long-term domain?
- Is the email in screenshot 3 a real person's address?

## Next action
**User:** decide whether to fix L1–L3 now; tell Claude if a draft of the description fix is wanted.
