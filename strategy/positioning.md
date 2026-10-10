# Dues positioning

**Status:** Working hypothesis — not validated with users or data. Updated 2026-10-10 from the public listing.
**Product:** Dues: Bill Tracker & Reminder (App Store ID 6761047973), iPhone/iPad, iOS 17+, English only, free with subscriptions.

## What the listing says today (Verified — public listing, 2026-10-10)
- Name: "Dues: Bill Tracker & Reminder" (all storefronts).
- Subtitle differs by region: **"Split Bills & Track Payments"** (AU, GB, CA, NZ, IE, IN and others) vs **"Bill Payment Manager & Budget"** (US).
- Description headline: "Never miss a bill again"; describes bill tracking + reminders, split bills, Family Plan, voice entry, widgets, insights.
- Source: [`aso/current-listing-audit.md`](../aso/current-listing-audit.md).

So the live listing currently carries **two positionings**: shared/split bills (most regions) and bill payment management/budget (US). Neither has been tested.

## Feature basis (checked against code 2026-10-10 — see [`aso/feature-verification.md`](../aso/feature-verification.md))
Supported by code in 1.2.0: bill tracking and reminders; weekly, fortnightly, monthly and yearly recurrence; voice entry; split bills; Family Plan (5 members + owner); widgets; Firestore sync; insights; dark mode; no ads; free plan with 5 active bills. **Contradicted:** "150+ currencies" (20), the listed category names, "works offline" (1.2.0). **Ambiguous:** "no third-party tracking" (Firebase Analytics and Crashlytics). Pending 2.0 positions each English locale on local bills (council tax, rego, hydro) with a "due dates & alerts" subtitle ([audit §9](../aso/current-listing-audit.md#9-pending-200-listing--not-live)).

### Original note (2026-10-10, before the code check — superseded above)
Bill tracking with due-date reminders and recurring bills · split bills with others · Family Plan (up to 5 members) · voice entry · Home/Lock Screen widgets · insights and CSV export · 150+ currencies · dark mode · no ads. Full list and status: audit §2. Free-plan limits and trial terms: **Unknown**.

## Positioning hypotheses to test
Each is a hypothesis; none is recommended over the others until baseline and keyword evidence exist.
| ID | Core message | Primary audience (hypothesis) | Evidence for | Evidence needed |
|---|---|---|---|---|
| P-A | Simple bill tracker that reminds you before due dates | Individuals managing their own recurring bills | Name; 7/10 recommended competitor subtitles use bill/due/reminder language (AU, 2026-10-10) | Search-term evidence per storefront; conversion by territory |
| P-B | Shared household bills — everyone sees what's due | Couples, families, housemates | 1.1.0–1.2.0 releases focus on split bills and Family Plan; non-US subtitle | Whether Family Plan/split features are used; family-plan subscription share |
| P-C | Bill payments + budget overview | Budget-conscious individuals | US subtitle | Whether insights are strong enough to compete with budget apps |

## Guardrails
- Use "Dues: Bill Tracker & Reminder" (with `&`) — not "Bill Tracker Reminder".
- No claims about bank connections, automatic bill detection, or automatic payment — none are claimed in the listing.
- "Never miss a bill", "privacy first", and "works offline" need confirmation before reuse in new copy (unsupported absolutes / NEEDS CONFIRMATION).
- Never invent testimonials, ratings, downloads, or capabilities. Public review text must not be reused as testimonials without the user's decision.
