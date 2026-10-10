# Task 005 — Reconcile App Store Listing Evidence

| Field | Value |
|---|---|
| ID | 005 |
| Priority | P0 |
| Owner | Claude (evidence collection and corrections) · ChatGPT review · User (account-only confirmations) |
| Status | In review — awaiting ChatGPT review and user acceptance |
| Opened | 2026-10-10 (task text provided by the user; added to the repo by Claude) |
| Approval gates | None for public-source research and documentation. App Store Connect changes require explicit user approval. |

## Objective
Reconcile the claims in `aso/current-listing-audit.md` against accessible, current Apple sources before the repository bootstrap is accepted.

**Business reason:** Tasks 001–004 depend on accurate listing facts. An incorrect privacy-label finding or stale storefront metadata could cause unnecessary work and lead to incorrect marketing or compliance decisions.

## Current state
- Listing audit: [`aso/current-listing-audit.md`](../../aso/current-listing-audit.md) — reconciliation log in [§8](../../aso/current-listing-audit.md#8-reconciliation-log--task-005-2026-10-10)
- User-facing priorities: [`strategy/30-day-plan.md`](../../strategy/30-day-plan.md) (unchanged — evidence did not change priorities)
- Listing trust fixes: [`tasks/inbox/002-listing-trust-and-compliance-fixes.md`](../inbox/002-listing-trust-and-compliance-fixes.md)
- ASO baseline: [`tasks/in-progress/001-aso-baseline-audit.md`](../in-progress/001-aso-baseline-audit.md)
- Handoff: [`docs/handoff.md`](../../docs/handoff.md)

## Evidence and sources
All accessed 2026-10-10 (UTC).

| ID | URL | Publisher | Accessed | Establishes | Locale | Limitations |
|---|---|---|---|---|---|---|
| E1 | https://apps.apple.com/au/app/dues-bill-tracker-reminder/id6761047973 | Apple | 08:59 UTC — HTTP 200, `x-cache: MISS`, `age: 0` | Subtitle, ratings, IAP prices, App Privacy label, version history, privacy link target | AU | Apple may update storefronts at different times |
| E2 | https://apps.apple.com/us/app/dues-bill-tracker-reminder/id6761047973 | Apple | 08:59 UTC — HTTP 200, `x-cache: MISS`, `age: 0` | Same fields for US | US | As E1 |
| E3 | https://itunes.apple.com/lookup?id=6761047973&country=au | Apple | 08:59 UTC — HTTP 200 | Name, version, release dates, age rating, size, ratings count, languages, genres, description, screenshot URLs | AU | No subtitle, keywords, IAP or privacy label |
| E4 | https://easy-bills.netlify.app/terms | Developer website | 08:59 UTC — **HTTP 404** (also 404 in pass 1, ~08:40 UTC) | Terms URL unavailable at those times | Global | Point-in-time |
| E5 | https://easy-bills.netlify.app/ | Developer website | 09:00 UTC — HTTP 200 | Privacy policy title, date and text | Global | Says nothing about actual in-app data flows |
| E6 | `https://apps.apple.com/{gb,ca,nz,ie,in}/app/dues-bill-tracker-reminder/id6761047973` and `https://itunes.apple.com/lookup?id=6761047973&country={gb,ca,nz,ie,in}` | Apple | 08:59 UTC — all HTTP 200 | Same fields as E1–E3 | GB, CA, NZ, IE, IN | As E1 |

Not re-checked in this task: SG, ZA, PH, MY, NG, KE, PK, AE, and HK. The audit marks these as "pass 1 only".

## Steps
- [x] Recheck the current US and Australian Apple pages and lookup API. Record access date and the exact values returned. *(Also GB, CA, NZ, IE, IN.)*
- [x] Recheck the privacy label on accessible Apple storefront pages. **Result:** the label does declare the listed linked-data categories in all 7 re-checked storefronts. I parsed the HTML headings to record them per purpose (Analytics / App Functionality). The claim stays, now with a per-purpose table and the note "developer-declared; not verified by Apple".
- [x] Check version, release date, age rating, app size, rating count, subtitle and IAP prices per storefront. All matched pass 1.
- [x] Recheck the Terms URL. Result: HTTP 404 at 08:59 UTC.
- [x] Review the screenshot observations. The address in screenshot 3 is now labelled **Unknown** (real/not real). It is not reproduced.
- [x] Update the audit and correct dependent statements in `README.md`, `docs/handoff.md`, Task 000, Task 002 and Task 004.
- [x] Keep listing claims separate from features verified in the build. Audit §2 is unchanged; no feature was promoted to "verified".
- [x] `strategy/30-day-plan.md` — not changed, because priorities are unaffected.
- [x] Re-run the relative-link, `.gitignore` and sensitive-data checks (results in `docs/handoff.md` §4).
- [x] Hand off for ChatGPT review (this file and `docs/handoff.md` §8).

## Deliverables
- [`aso/current-listing-audit.md`](../../aso/current-listing-audit.md) — corrected; adds a pass column, per-purpose privacy table, caching caveat, and the §8 reconciliation log
- [`tasks/inbox/002-listing-trust-and-compliance-fixes.md`](../inbox/002-listing-trust-and-compliance-fixes.md) — findings restated to match the evidence
- [`docs/handoff.md`](../../docs/handoff.md) — updated
- This file

## Acceptance criteria — self-check (not yet reviewed by anyone else)
- [x] Every material listing fact has a direct source, access time, and storefront.
- [x] The App Privacy description is supported by a current, uncached source (E1, E2) and is labelled as developer-declared.
- [x] HTTP status claims record the observed status and time.
- [x] No stale or inaccessible page is presented as current. Pass-1-only storefronts are marked.
- [x] Listing claims are not presented as verified features.
- [x] No fabricated values or sensitive data were committed. The staged diff was scanned before commit.
- [x] The task is in `tasks/review/`, not Done.

## Open questions and assumptions
- Q (User): Does the App Privacy declaration accurately reflect the app's data practices and SDKs?
- Q (User): Is the email in screenshot 3 a real person's address?
- Q (User): Is the US subtitle a deliberate separate en-US localization?
- Assumption: Apple storefront pages can update at different times. The US subtitle difference was seen twice on uncached responses, but its cause is still NEEDS CONFIRMATION.

## Handoff
- **Changed:**
  - `aso/current-listing-audit.md`: header, sources, §1, §1a, §3, §4, §6 (L1–L3), §7, and the new §8
  - Task 002, Task 000 and Task 004: wording corrections
  - `README.md`: status bullets
  - `tasks/README.md`: index
  - `docs/handoff.md`
- **Why:** to make sure the bootstrap's listing facts are current, sourced and not overstated before it is accepted.
- **Evidence:** E1–E6 above.
- **What changed in substance:**
  - No finding was reversed.
  - Two statements were overstated and are now corrected: the screenshot email being "real", and "identical across all storefronts" including the privacy label.
  - One fact is now marked as inferred: the year in the version-history dates.
- **Needs review:**
  - Does §8 cover every material claim?
  - Is the per-purpose privacy table an accurate transcription?
  - Should the 9 pass-1-only storefronts be re-checked before acceptance?
- **Next:** the user answers the open questions and decides on PR [#1](https://github.com/pwndhull/dues-marketing/pull/1). Task 002 (user) and Task 001 exports (user) remain the next work.
