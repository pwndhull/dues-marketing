# Current App Store Listing Audit

**Snapshot date:** 2026-10-10 (fetched ~08:40 UTC)
**Captured by:** Claude Code (public sources only — no App Store Connect access)
**Storefronts checked:** 16 English-speaking or English-served storefronts — see [§1a Regional listings](#1a-regional-listings--verified-public)
**Status:** Public-listing portion complete. Keyword field, analytics, and in-app verification still require the user (see [Task 001](../tasks/in-progress/001-aso-baseline-audit.md)).

> Labels used: **Verified (public)** = observed directly on a public Apple/developer page on the snapshot date. **Listing claim** = the developer's own marketing statement; not yet verified in the build. **Hypothesis** = Claude's interpretation, untested. **Unknown** = not observable without the user.

## Sources
| ID | URL | Publisher | Accessed | What it establishes | Limitations |
|---|---|---|---|---|---|
| S1 | https://itunes.apple.com/lookup?id=6761047973&country=au (repeated per storefront code in §1a) | Apple (iTunes Search API) | 2026-10-10 | Name, seller, bundle ID, version, dates, genres, price, languages, rating counts, description, screenshot URLs | Does not expose subtitle, keyword field, IAP prices, privacy label |
| S2 | https://apps.apple.com/au/app/dues-bill-tracker-reminder/id6761047973 (and `https://apps.apple.com/<cc>/app/id6761047973` per storefront in §1a) | Apple | 2026-10-10 | Subtitle, IAP list and local prices, version history, App Privacy label, accessibility declaration, "You Might Also Like" | Web page; Apple may personalise or change it at any time |
| S3 | https://easy-bills.netlify.app/ | Developer website | 2026-10-10 | Privacy policy content (this URL is both "Developer Website" and "Privacy Policy" in the listing) | Point-in-time |
| S4 | https://easy-bills.netlify.app/terms | Developer website | 2026-10-10 | Returns HTTP 404 "Page not found" | Point-in-time; may be a deploy issue |
| S5 | https://developer.apple.com/help/app-store-connect/reference/app-information/app-information | Apple Developer | 2026-10-10 | Name ≤ 30 chars; subtitle ≤ 30 chars; privacy policy URL required | — |
| S6 | https://developer.apple.com/help/app-store-connect/reference/app-information/platform-version-information | Apple Developer | 2026-10-10 | Promotional text ≤ 170 chars; description ≤ 4000 chars; keywords ≤ 100 bytes, no app/company names, don't duplicate name | — |
| S7 | https://developer.apple.com/help/app-store-connect/reference/app-information/screenshot-specifications | Apple Developer | 2026-10-10 | 1–10 screenshots per device size | — |
| S8 | https://developer.apple.com/app-store/review/guidelines/ (last updated 2026-06-08) | Apple Developer | 2026-10-10 | 2.3.1 (no misleading marketing), 2.3.7 (metadata rules), 3.1.2(c) (subscription info; points to Schedule 2 of the DPLA), 5.1.1(i) (privacy policy must identify all data collected and its uses) | Schedule 2 text itself not reviewed |

## 1. Metadata — Verified (public)
Values below are shared by all storefronts checked **except where §1a shows a regional difference**.

| Field | Value | Length / limit | Source |
|---|---|---|---|
| App name | Dues: Bill Tracker & Reminder | 29 / 30 | S1, S5 |
| Subtitle | **Varies by region** — "Split Bills & Track Payments" (AU, GB, CA, NZ, IE, IN and others) / "Bill Payment Manager & Budget" (US). See §1a. | 28 / 30 and 29 / 30 | S2, S5 |
| Seller / developer | Pawan Kumar (developer ID 1633039939) | — | S1 |
| Bundle ID | `com.xx.easybills` | — | S1 |
| Primary / secondary category | Finance / Utilities | — | S1 |
| Price | Free with in-app purchases | — | S1, S2 |
| Current version | 1.2.0, released 2026-09-28 | — | S1 |
| First release | 1.0 on 2026-04-22 | — | S1 |
| Minimum OS | iOS/iPadOS 17.0 | — | S2 |
| Size | 23.2 MB | — | S2 |
| Languages | English only | — | S1 |
| Age rating | 4+ | — | S1 |
| Description | 3,216 characters (copy in S1) | 3216 / 4000 | S1, S6 |
| Promotional text | None observed | 0 / 170 | S2 |
| Keyword field | **Unknown** — not public; may differ per localization | ≤ 100 bytes each | needs App Store Connect |
| Accessibility label | "The developer has not yet indicated which accessibility features this app supports." | — | S2 |
| Family Sharing | Supported for some IAPs | — | S2 |

### In-app purchases (Australia storefront, AUD) — Verified (public)
| Product | Price |
|---|---|
| Monthly | $7.99 |
| Yearly | $59.99 |
| Family Plan – Monthly | $12.99 |
| Family Plan – Annual | $99.99 |

Other storefronts' prices: see §1a. Free-trial terms and the free-plan bill limit are **Unknown**.

### Ratings — Verified (public), per storefront
| Storefront | Ratings | Average |
|---|---:|---:|
| Australia | 3 | 5.0 |
| United States | 0 | — |
| United Kingdom | 0 | — |

Too few ratings to draw any conclusion. Written review text was not captured.

### Version history — Verified (public)
- **1.0** (2026-04-22) — initial release.
- **1.0.1** (2026-04-23) — dark mode, iOS 17 support, "fresh new app icon and name".
- **1.1.0** (2026-05-07) — voice entry, split bills, Family Plan tier, widgets, real-time sync, insights, notification preferences, Hindi voice recognition.
- **1.2.0** (2026-09-28) — Family Plan bill sharing live in real time; leave/remove from shared bill.

## 1a. Regional listings — Verified (public)
Checked 2026-10-10 via S1 lookup and S2 page for each storefront code. Text was compared field by field (description and screenshot URLs compared by hash).

**What differs by region (observable):**
| Storefront | Subtitle shown | Ratings (count / avg) | Monthly | Yearly | Family Monthly | Family Annual |
|---|---|---|---|---|---|---|
| United States (`us`) | **Bill Payment Manager & Budget** | 0 | US$4.99 | US$39.99 | US$7.99 | US$59.99 |
| United Kingdom (`gb`) | Split Bills & Track Payments | 0 | £4.99 | £39.99 | £7.99 | £59.99 |
| Australia (`au`) | Split Bills & Track Payments | 3 / 5.0 | A$7.99 | A$59.99 | A$12.99 | A$99.99 |
| Canada (`ca`) | Split Bills & Track Payments | 0 | C$6.99 | C$49.99 | C$9.99 | C$79.99 |
| New Zealand (`nz`) | Split Bills & Track Payments | 0 | NZ$9.99 | NZ$69.99 | NZ$14.99 | NZ$99.99 |
| Ireland (`ie`) | Split Bills & Track Payments | 0 | €5.99 | €44.99 | €8.99 | €69.99 |
| India (`in`) | Split Bills & Track Payments | 4 / 5.0 (3 written reviews visible) | ₹499 | ₹3,999 | ₹799 | ₹5,900 |
| Singapore (`sg`) | Split Bills & Track Payments | 0 | S$6.98 | S$59.98 | S$9.98 | S$89.98 |
| South Africa (`za`) | Split Bills & Track Payments | 0 | R99.99 | R799.99 | R149.99 | R1,199.99 |
| Philippines (`ph`) | Split Bills & Track Payments | 0 | ₱299 | ₱2,490 | ₱499 | ₱3,990 |
| Malaysia (`my`) | Split Bills & Track Payments | 0 | RM22.90 | RM199.90 | RM39.90 | RM299.90 |
| Nigeria (`ng`) | Split Bills & Track Payments | 0 | ₦7,900 | ₦69,900 | ₦12,900 | ₦99,900 |
| Kenya (`ke`) | Split Bills & Track Payments | 0 | US$5.99 | US$49.99 | US$9.99 | US$69.99 |
| Pakistan (`pk`) | Split Bills & Track Payments | 0 | Rs1,300 | Rs9,900 | Rs2,200 | Rs14,900 |
| UAE (`ae`) | Split Bills & Track Payments | 0 | AED19.99 | AED149.99 | AED29.99 | AED229.99 |

Hong Kong (`hk`) was also fetched; its page rendered in Chinese and IAP prices could not be parsed, so it is excluded.

**What is identical across all storefronts checked:** app name, description (3,216 chars, same hash), "What's New" text, the four iPhone screenshots (same image URLs), version, privacy label, Terms/Privacy links.

**Not observable — needs the user (App Store Connect → App Information / version page):**
- Which English localizations exist (en-US, en-GB, en-AU, en-CA) and which storefronts fall back to which one. The US subtitle proves at least one separate localization exists; the mapping for other storefronts is **NEEDS CONFIRMATION**.
- The **keyword field for each localization** — the main reason regional listings matter for ASO, and invisible publicly.
- Any per-localization promotional text, screenshots, or description not yet live.

**Observations (not conclusions):**
- The US subtitle positions Dues as "bill payment manager & budget"; elsewhere it leads with "split bills". This is effectively an untracked positioning variant. Without App Store Connect data by territory, nothing can be inferred about which performs better, and the two markets differ in many other ways (prices, competition, seasonality), so a comparison would not be a controlled test.
- Prices are not straight currency conversions (e.g. AU monthly A$7.99 vs US US$4.99). Whether these are deliberate or Apple's automatic equalisation is **Unknown**. Pricing is out of scope for marketing changes without explicit approval.
- Ratings exist only in AU (3) and IN (4). Written reviews in IN are not quoted here and must not be used as testimonials without the user's decision and the reviewer's context.
- India is not a priority English market in the brief, but it has the most ratings and the developer added Hindi voice recognition (1.1.0 notes). Whether India matters commercially is a question for App Store Connect territory data, not an assumption.

**"You Might Also Like" also varies by storefront** (US/CA add e.g. "BillPlex: Shared Budget", "Monthly Bill Reminder Tracker", "Offline Bills & Subs Tracker", "Worth: Private Net worth"). See [`competitor-research.md`](competitor-research.md).

## 2. Product claims in the description — Listing claims (verify in build)
Source: S1/S2. These are the developer's statements. Marketing copy may reuse them only after the user confirms each one in the current build.

| Claim | Status |
|---|---|
| Bill tracking for utilities, rent, subscriptions, loans; due-date reminders; mark paid | Listing claim — partially visible in screenshots (dashboard, reminders setting, add-bill form) |
| Recurring bills (weekly, monthly, yearly) | Listing claim |
| Voice entry ("Add $500 electricity bill due next Friday") | Listing claim |
| Split bills with push notification to each person; works before contacts join | Listing claim |
| Family Plan — up to 5 household members | Listing claim; Family Plan IAPs verified (S2) |
| Home Screen and Lock Screen widgets with quick-add | Listing claim |
| Real-time cloud sync across devices | Listing claim |
| Insights: monthly totals, trends, category breakdowns; CSV export | Listing claim — Insights screen visible in screenshot 2 |
| 150+ currencies | Listing claim |
| Works offline, syncs on reconnect | Listing claim — **NEEDS CONFIRMATION** (sign-in and cloud sync may limit this) |
| "Privacy first — we never sell your data; secure encryption, no third-party tracking" | Listing claim — **NEEDS CONFIRMATION** against SDKs and privacy label (§4) |
| Zero ads; dark mode | Listing claim; dark mode visible in screenshots |
| Premium: unlimited bills, unlimited archive, Family Plan, priority support | Listing claim; free-plan limit **Unknown** |

## 3. Screenshots — Verified (public)
4 iPhone (6.7" set) and 4 iPad (12.9" set) screenshots; Apple allows up to 10 per size (S7). iPhone set reviewed at reduced resolution:

| # | Shows | Observations |
|---|---|---|
| 1 | Dashboard: total due, upcoming, filters, bill list | No caption/headline. Visible bills show "270 days overdue", "180 days overdue", "120 days overdue" in red. Page title renders faintly. |
| 2 | Insights (week view) | No caption. Figures use lakh-style grouping with `$` (e.g. `$8,77,297.49`, `$10,00,000`) and very large sample amounts. Chart trends sharply downward. |
| 3 | Settings: profile, bill reminders toggle, reminder time, currency | No caption. **Appears to display a real email address and "Premium Member" badge.** The address is intentionally not reproduced here. |
| 4 | Add Bill: title, amount, category, due-date calendar | No caption. |

None of the four screenshots shows the subtitle's lead feature (split bills) or the 1.1.0/1.2.0 features (voice entry, Family Plan sharing, widgets). iPad screenshots not yet reviewed.

## 4. Privacy and legal links — Verified (public)
- Listing links Privacy Policy and Developer Website to the same URL (S3).
- S3 is titled **"Privacy Policy | BillFlow"**, last updated **2026-03-22** (before 1.0 shipped). It lists email, bill details, and preferences; third parties Firebase, Apple Sign In, Google Sign In.
- The App Privacy label (S2) declares data **linked to you** across: purchases, financial info, coarse location, contact info (email, name, phone number), contacts, user content (photos/videos, other), identifiers (user ID, device ID), usage data, diagnostics; including an **Analytics** purpose. No "Data Used to Track You" section was observed.
- Terms of Use URL in the description (S4) returns **HTTP 404**.

**Observation:** the privacy policy does not appear to mention several declared data types (e.g. contacts, phone number, location, photos). Guideline 5.1.1(i) (S8) requires the policy to identify all data collected and its uses. Whether this is non-compliant is a judgement for the user — Claude is not giving legal advice.

## 5. Store context — Verified (public)
"You Might Also Like" on the AU page (S2), 2026-10-10. This is Apple's recommendation list, **not** a measure of search competition:
BillWell: Bill Reminder · Bill Reminder: Due Dates · Bill Reminder: Bills Tracker · BillFlow · Mês Leve: Budget & Cash Flow · Bill Organizer - DueWise · Bills & Subscriptions Tracker · BillBell · SmartWallet AI Expense Tracker · BillLoop - Payment Tracker.
See [`competitor-research.md`](competitor-research.md).

## 6. Findings and opportunities
Priorities are Claude's recommendation; effort is a rough estimate; none of these outcomes is guaranteed.

| ID | Finding (evidence) | Type | Recommendation | Priority | Owner |
|---|---|---|---|---|---|
| L1 | Terms of Use link 404 (S4) | Verified | Restore/publish Terms page. Check Schedule 2 requirements. | P0 | User |
| L2 | Privacy policy branded "BillFlow", dated before launch, narrower than privacy label (S2, S3) | Verified + judgement | Update policy to match current app and label; give it its own URL. | P0 | User |
| L3 | Screenshot 3 shows an apparent real email address (S2) | Verified | Replace with demo account data. | P0 | User |
| L4 | Description section "NEW IN VERSION 1.1.0" is stale (S1) | Verified | Refresh in next metadata update. | P1 | Claude drafts, user approves |
| L5 | Screenshots have no captions and do not show split bills / voice / widgets / Family Plan | Verified observation; impact is a **hypothesis** | Draft a captioned screenshot narrative using real screens. | P1 | Claude drafts |
| L6 | Screenshots 1–2 lead with long-overdue bills, lakh grouping, very large sums | Verified observation; impact is a **hypothesis** | Use realistic demo data in the target locale's format. | P1 | User captures; Claude briefs |
| L7 | English only; ratings only in AU (3) and IN (4); US has a separate subtitle (§1a) | Verified | Decide priority markets from App Store Connect territory data, not assumption. | P1 | User exports |
| L8 | No promotional text; no accessibility declarations | Verified | Draft promo text; user to assess accessibility support honestly. | P2 | Claude drafts |
| L9 | Keyword field(s) unknown — see L11 for per-localization detail | Unknown | User to share each current keyword field. | P0 (blocks keyword work) | User |
| L10 | "BillFlow" naming overlap with another listed app | Verified; cause **Unknown** | User to confirm prior name/brand history. | P1 | User |
| L11 | Regional listings: keyword fields and localization-to-storefront mapping unknown (§1a) | Unknown | User exports each localization's name, subtitle, keywords, promo text into the repo; keyword research is done per localization. | P0 (blocks keyword work) | User |

## 7. Open questions for the user
1. Which English localizations exist in App Store Connect (en-US, en-GB, en-AU, en-CA…), and what are the name, subtitle, keyword field, and promotional text for **each**?
   Was the different US subtitle a deliberate choice, and since when?
2. Was "BillFlow" or "Easy Bills" a former name? Is `easy-bills.netlify.app` the intended long-term domain?
3. What does the free plan include (bill limit), and is there a free trial?
4. Is "works offline — full functionality" accurate with sign-in and sync?
5. Which third-party SDKs ship in 1.2.0 (analytics, crash reporting)? Needed to verify "no third-party tracking".
6. Is the email in screenshot 3 a real person's address?
