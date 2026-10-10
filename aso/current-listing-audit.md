# Current App Store Listing Audit

**Snapshot date:** 2026-10-10, two capture passes:
- **Pass 1** (~08:40 UTC): 16 storefronts, lookup API + product page.
- **Pass 2 — reconciliation, [Task 005](../tasks/review/005-reconcile-listing-evidence.md)** (08:59–09:00 UTC): AU, US, GB, CA, NZ, IE, IN re-fetched; Terms and privacy URLs re-fetched. Apple responses were uncached at the edge (`x-cache: MISS`, `age: 0`), so these are current observations, not cached snapshots.

**Captured by:** Claude Code (public sources only — no App Store Connect access)
**Storefronts checked:** 16 in pass 1; 7 re-checked in pass 2. The pass column in [§1a](#1a-regional-listings--verified-public) shows which.
**Status:** Public-listing portion complete and reconciled (see [§8](#8-reconciliation-log--task-005-2026-10-10)). Keyword field, analytics, and in-app verification still require the user (see [Task 001](../tasks/in-progress/001-aso-baseline-audit.md)).

> Labels used: **Verified (public)** = observed directly on a public Apple/developer page on the snapshot date. **Listing claim** = the developer's own marketing statement; not yet verified in the build. **Hypothesis** = Claude's interpretation, untested. **Unknown** = not observable without the user.

## Sources
| ID | URL | Publisher | Accessed | What it establishes | Limitations |
|---|---|---|---|---|---|
| S1 | https://itunes.apple.com/lookup?id=6761047973&country=au — and the same URL with `country=us`, `gb`, `ca`, `nz`, `ie`, `in`, `sg`, `za`, `ph`, `my`, `ng`, `ke`, `pk`, `ae`, `hk` | Apple (iTunes Search API) | 2026-10-10 pass 1 (all); pass 2 08:59 UTC (au, us, gb, ca, nz, ie, in) — all HTTP 200 | Name, seller, bundle ID, version, dates, genres, price, languages, rating counts, description, screenshot URLs | Does not expose subtitle, keyword field, IAP prices, privacy label |
| S2 | https://apps.apple.com/au/app/dues-bill-tracker-reminder/id6761047973 · https://apps.apple.com/us/app/dues-bill-tracker-reminder/id6761047973 · same path for `gb`, `ca`, `nz`, `ie`, `in` (pass 2); `https://apps.apple.com/<cc>/app/id6761047973` for the other storefronts (pass 1 only) | Apple | 2026-10-10 pass 1; pass 2 08:59 UTC — all HTTP 200, uncached | Subtitle, IAP list and local prices, version history, App Privacy label, accessibility declaration, "You Might Also Like" | Web page; Apple may personalise or change it at any time |
| S3 | https://easy-bills.netlify.app/ | Developer website | 2026-10-10 pass 1; pass 2 09:00 UTC — HTTP 200 | Privacy policy content (this URL is both "Developer Website" and "Privacy Policy" in the listing) | Point-in-time |
| S4 | https://easy-bills.netlify.app/terms | Developer website | 2026-10-10 pass 1 and pass 2 (08:59 UTC) | Returned **HTTP 404** "Page not found" both times | Point-in-time; availability may change |
| S5 | https://developer.apple.com/help/app-store-connect/reference/app-information/app-information | Apple Developer | 2026-10-10 | Name ≤ 30 chars; subtitle ≤ 30 chars; privacy policy URL required | — |
| S6 | https://developer.apple.com/help/app-store-connect/reference/app-information/platform-version-information | Apple Developer | 2026-10-10 | Promotional text ≤ 170 chars; description ≤ 4000 chars; keywords ≤ 100 bytes, no app/company names, don't duplicate name | — |
| S7 | https://developer.apple.com/help/app-store-connect/reference/app-information/screenshot-specifications | Apple Developer | 2026-10-10 | 1–10 screenshots per device size | — |
| S8 | https://developer.apple.com/app-store/review/guidelines/ (last updated 2026-06-08) | Apple Developer | 2026-10-10 | 2.3.1 (no misleading marketing), 2.3.7 (metadata rules), 3.1.2(c) (subscription info; points to Schedule 2 of the DPLA), 5.1.1(i) (privacy policy must identify all data collected and its uses) | Schedule 2 text itself not reviewed |

## 1. Metadata — Verified (public)
Values below are shared by all storefronts checked **except where §1a shows a regional difference**.

| Field | Value | Length / limit | Source |
|---|---|---|---|
| App name | Dues: Bill Tracker & Reminder | 29 / 30 | S1, S5 |
| Subtitle | **Differs by storefront** — "Bill Payment Manager & Budget" (US) / "Split Bills & Track Payments" (every other storefront checked). Seen in both passes. See §1a. | 29 / 30 and 28 / 30 | S2, S5 |
| Seller / developer | Pawan Kumar (developer ID 1633039939) | — | S1 |
| Bundle ID | `com.xx.easybills` | — | S1 |
| Primary / secondary category | Finance / Utilities | — | S1 |
| Price | Free with in-app purchases | — | S1, S2 |
| Current version | 1.2.0, `currentVersionReleaseDate` 2026-09-28T09:56:15Z | — | S1 (pass 2: AU, US, GB, CA, NZ, IE, IN) |
| First release | 1.0 on 2026-04-22 | — | S1 |
| Minimum OS | iOS/iPadOS 17.0 | — | S2 |
| Size | 23.2 MB (page); 23,203,840 bytes (lookup) | — | S1, S2 (pass 2: 7 storefronts) |
| Languages | English only | — | S1 |
| Age rating | 4+ | — | S1 `contentAdvisoryRating`; S2 (pass 2: 7 storefronts) |
| Description | 3,216 characters (copy in S1); identical hash in all 16 storefronts | 3216 / 4000 | S1, S6 |
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
| India | 4 | 5.0 |
| United States | 0 | — |
| United Kingdom | 0 | — |

The counts come from S1 `userRatingCount`, and the page matched in pass 2. Every other storefront checked had 0 ratings (§1a).

Too few ratings to draw any conclusion. Written review text was not captured.

### Version history — Verified (public)
Sources: S2 "Version History", and S1 for the 1.0 and 1.2.0 dates. The page shows only day and month for older versions ("23 Apr", "7 May"). The year 2026 is **inferred** from S1 `releaseDate` 2026-04-22.
- **1.0** (2026-04-22) — initial release.
- **1.0.1** (2026-04-23) — dark mode, iOS 17 support, "fresh new app icon and name".
- **1.1.0** (2026-05-07) — voice entry, split bills, Family Plan tier, widgets, real-time sync, insights, notification preferences, Hindi voice recognition.
- **1.2.0** (2026-09-28) — Family Plan bill sharing live in real time; leave/remove from shared bill.

## 1a. Regional listings — Verified (public)
Checked 2026-10-10 via S1 lookup and S2 page for each storefront code. Pass 1 compared description, release notes and screenshot URLs by hash for all 16 storefronts. Pass 1 diffed the full page text against GB only for US, AU, CA, IN and NZ. Pass 2 re-extracted the subtitle, ratings, IAP prices and privacy label for the 7 storefronts marked "1+2".

**Caching caveat:** Apple pages can update at different times. The US subtitle difference appeared in both passes on uncached responses, which is consistent with a separate US localization. That is still an inference: the cause is **NEEDS CONFIRMATION** from App Store Connect.

**What differs by region (observable):**
| Storefront | Pass | Subtitle shown | Ratings (count / avg) | Monthly | Yearly | Family Monthly | Family Annual |
|---|---|---|---|---|---|---|---|
| United States (`us`) | 1+2 | **Bill Payment Manager & Budget** | 0 | US$4.99 | US$39.99 | US$7.99 | US$59.99 |
| United Kingdom (`gb`) | 1+2 | Split Bills & Track Payments | 0 | £4.99 | £39.99 | £7.99 | £59.99 |
| Australia (`au`) | 1+2 | Split Bills & Track Payments | 3 / 5.0 | A$7.99 | A$59.99 | A$12.99 | A$99.99 |
| Canada (`ca`) | 1+2 | Split Bills & Track Payments | 0 | C$6.99 | C$49.99 | C$9.99 | C$79.99 |
| New Zealand (`nz`) | 1+2 | Split Bills & Track Payments | 0 | NZ$9.99 | NZ$69.99 | NZ$14.99 | NZ$99.99 |
| Ireland (`ie`) | 1+2 | Split Bills & Track Payments | 0 | €5.99 | €44.99 | €8.99 | €69.99 |
| India (`in`) | 1+2 | Split Bills & Track Payments | 4 / 5.0 (written reviews visible; not quoted) | ₹499 | ₹3,999 | ₹799 | ₹5,900 |
| Singapore (`sg`) | 1 | Split Bills & Track Payments | 0 | S$6.98 | S$59.98 | S$9.98 | S$89.98 |
| South Africa (`za`) | 1 | Split Bills & Track Payments | 0 | R99.99 | R799.99 | R149.99 | R1,199.99 |
| Philippines (`ph`) | 1 | Split Bills & Track Payments | 0 | ₱299 | ₱2,490 | ₱499 | ₱3,990 |
| Malaysia (`my`) | 1 | Split Bills & Track Payments | 0 | RM22.90 | RM199.90 | RM39.90 | RM299.90 |
| Nigeria (`ng`) | 1 | Split Bills & Track Payments | 0 | ₦7,900 | ₦69,900 | ₦12,900 | ₦99,900 |
| Kenya (`ke`) | 1 | Split Bills & Track Payments | 0 | US$5.99 | US$49.99 | US$9.99 | US$69.99 |
| Pakistan (`pk`) | 1 | Split Bills & Track Payments | 0 | Rs1,300 | Rs9,900 | Rs2,200 | Rs14,900 |
| UAE (`ae`) | 1 | Split Bills & Track Payments | 0 | AED19.99 | AED149.99 | AED29.99 | AED229.99 |

Hong Kong (`hk`) was also fetched; its page rendered in Chinese and IAP prices could not be parsed, so it is excluded.

**What is identical:**
- **All 16 storefronts:** app name, description (3,216 chars, same hash), "What's New" text, the four iPhone screenshot URLs, version, and the Terms/Privacy URLs inside the description. All from S1.
- **The 7 storefronts in pass 2:** App Privacy label data types and purposes, the Privacy Policy link target, age rating and size.
- **Not compared:** the privacy label for the 8 pass-1-only storefronts.

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

## 2. Product claims in the description — Listing claims, now checked against code
Source: S1/S2. These are the developer's statements. On 2026-10-10 each one was checked against the app source code at the estimated 1.2.0 commit; details are in [`feature-verification.md`](feature-verification.md). Code evidence is not runtime evidence: items marked "supported by code" are still unverified on a device.

| Claim | Status |
|---|---|
| Bill tracking for utilities, rent, subscriptions, loans; due-date reminders; mark paid | Supported by code |
| Recurring bills (weekly, monthly, yearly) | Supported by code (fortnightly too) |
| Voice entry ("Add $500 electricity bill due next Friday") | Supported by code; Hindi recognition NEEDS CONFIRMATION |
| Split bills with push notification to each person; works before contacts join | Supported by code (split + push); "before contacts join" not checked |
| Family Plan — up to 5 household members | Supported: 5 members + owner; Family Plan IAPs verified (S2) |
| Home Screen and Lock Screen widgets with quick-add | Supported by code |
| Real-time cloud sync across devices | Supported by code (Firestore) |
| Insights: monthly totals, trends, category breakdowns; CSV export | Insights supported; **CSV export appears to be Premium**, not core |
| 150+ currencies | **Contradicted: 20 currencies in code** |
| Works offline, syncs on reconnect | **Overstated in 1.2.0** (memory-only cache); improved on unreleased `main` |
| "Privacy first — we never sell your data; secure encryption, no third-party tracking" | "No third-party tracking" is **ambiguous**: Firebase Analytics and Crashlytics are linked, and there is no ATT prompt. "Never sell" is a user claim |
| Zero ads; dark mode | Supported by code (no ad SDK linked; theme picker) |
| Premium: unlimited bills, unlimited archive, Family Plan, priority support | Free plan: 5 active + 5 archived bills (code). "Priority support" should not be reused |

## 3. Screenshots — Verified (public)
4 iPhone (6.7" set) and 4 iPad (12.9" set) screenshots; Apple allows up to 10 per size (S7). iPhone set reviewed at reduced resolution:

| # | Shows | Observations |
|---|---|---|
| 1 | Dashboard: total due, upcoming, filters, bill list | No caption/headline. Visible bills show "270 days overdue", "180 days overdue", "120 days overdue" in red. Page title renders faintly. |
| 2 | Insights (week view) | No caption. Figures use lakh-style grouping with `$` (e.g. `$8,77,297.49`, `$10,00,000`) and very large sample amounts. Chart trends sharply downward. |
| 3 | Settings: profile, bill reminders toggle, reminder time, currency | No caption. **Displays an email-format address** in the profile area, with a "Premium Member" badge. Whether it is a real person's address is **Unknown (NEEDS CONFIRMATION from the user)**. It cannot be determined from the image, and it is intentionally not reproduced here. |
| 4 | Add Bill: title, amount, category, due-date calendar | No caption. |

Screenshot image URLs were unchanged between pass 1 and pass 2 (S1). None of the four screenshots shows the subtitle's lead feature (split bills) or the 1.1.0/1.2.0 features (voice entry, Family Plan sharing, widgets). iPad screenshots not yet reviewed.

## 4. Privacy and legal links — Verified (public)
- **Links:** the listing's Privacy Policy link and Developer Website both point to `https://easy-bills.netlify.app/`. This is the `href` in S2, pass 2, for all 7 storefronts.
- **Privacy policy (S3, pass 2, 09:00 UTC):**
  - Titled **"Privacy Policy | BillFlow"**, "Last Updated: March 22, 2026". That is a month before 1.0 shipped on 2026-04-22.
  - About 1,660 characters of text.
  - Lists email, bill details and app preferences. Names Firebase, Apple Sign In and Google Sign In as third parties.
  - A text search found **no** mention of "Dues", phone, location, photo, voice/speech, analytics, crash, purchase, split, or family. Its "contact" matches are a "Contact Us" heading, not contacts data.
- **App Privacy label (S2, pass 2, 08:59 UTC):**
  - Present in AU and US, and identical in the other 5 storefronts re-checked. Apple's page states it is the developer's declaration and "has not been verified by Apple".
  - Only a **"Data Linked to You"** section appears. There is no "Data Used to Track You" or "Data Not Linked to You" section.
  - Data types, by purpose, as shown:

  | Purpose | Data category → type |
  |---|---|
  | Analytics | Location → Coarse Location · Identifiers → User ID, Device ID · Usage Data → Product Interaction |
  | App Functionality | Purchases → Purchase History · Financial Info → Other Financial Info · Contact Info → Email Address, Name, Phone Number · Contacts → Contacts · User Content → Photos or Videos, Other User Content · Identifiers → User ID · Diagnostics → Crash Data |

  - The label shows what the developer **declared**. It does not prove the app's actual data flows.
- **Terms of Use:** the URL in the description (S4) returned **HTTP 404** in pass 1 and again at 08:59 UTC in pass 2.

**Observation:** the policy text does not mention several data types the label declares, such as phone number, contacts, coarse location, and photos or videos. Guideline 5.1.1(i) (S8) requires the policy to identify all data collected and its uses. Whether this is non-compliant is a judgement for the user — Claude is not giving legal advice.

## 5. Store context — Verified (public)
"You Might Also Like" on the AU page (S2), 2026-10-10. This is Apple's recommendation list, **not** a measure of search competition:
BillWell: Bill Reminder · Bill Reminder: Due Dates · Bill Reminder: Bills Tracker · BillFlow · Mês Leve: Budget & Cash Flow · Bill Organizer - DueWise · Bills & Subscriptions Tracker · BillBell · SmartWallet AI Expense Tracker · BillLoop - Payment Tracker.
See [`competitor-research.md`](competitor-research.md).

## 6. Findings and opportunities
Priorities are Claude's recommendation; effort is a rough estimate; none of these outcomes is guaranteed.

| ID | Finding (evidence) | Type | Recommendation | Priority | Owner |
|---|---|---|---|---|---|
| L1 | Terms of Use link HTTP 404, observed in passes 1 and 2 on 2026-10-10 (S4). The app itself links to Google Sites pages; the Netlify site serves an old "BillFlow" deploy | Verified | The 2.0 description switches to the Google Sites URLs. Confirm the App Store Connect Privacy Policy URL field as well | P0 | User |
| L2 | Privacy policy branded "BillFlow", dated before launch; its text omits several data types the App Privacy label declares (§4) | Verified (policy text and declared label, pass 2); compliance is the user's judgement | Update policy to match current app and label; give it its own URL. | P0 | User |
| L3 | Screenshot 3 shows an email-format address (S2). It matches a string in the app repo's history (developer machine path), so it is likely the owner's or a team account, not a customer's | Verified observation; owner **NEEDS CONFIRMATION** | Replace with demo account data. | P0 | User |
| L4 | Description section "NEW IN VERSION 1.1.0" is stale (S1); the description also contains claims the code contradicts (150+ currencies, category list, offline) | Verified (code: [`feature-verification.md`](feature-verification.md)) | The pending 2.0 description (§9) already removes them. Ship it, or correct 1.2.0's description sooner | P0 | User |
| L5 | Screenshots have no captions and do not show split bills / voice / widgets / Family Plan | Verified observation; impact is a **hypothesis** | Draft a captioned screenshot narrative using real screens. | P1 | Claude drafts |
| L6 | Screenshots 1–2 lead with long-overdue bills, lakh grouping, very large sums | Verified observation; impact is a **hypothesis** | Use realistic demo data in the target locale's format. | P1 | User captures; Claude briefs |
| L7 | English only; ratings only in AU (3) and IN (4); US has a separate subtitle (§1a) | Verified | Decide priority markets from App Store Connect territory data, not assumption. | P1 | User exports |
| L8 | No promotional text; no accessibility declarations | Verified | Draft promo text; user to assess accessibility support honestly. | P2 | Claude drafts |
| L9 | Keyword field(s) unknown — see L11 for per-localization detail | Unknown | User to share each current keyword field. | P0 (blocks keyword work) | User |
| L10 | "BillFlow" naming overlap with another listed app | Verified; cause **Unknown** | User to confirm prior name/brand history. | P1 | User |
| L11 | Regional listings: keyword fields and localization-to-storefront mapping unknown (§1a) | Unknown | User exports each localization's name, subtitle, keywords, promo text into the repo; keyword research is done per localization. | P0 (blocks keyword work) | User |

## 7. Open questions for the user
Update 2026-10-10: questions 2–6 are partly answered by the app repositories (see [`feature-verification.md`](feature-verification.md)). The remaining parts are marked.

1. Which English localizations exist in App Store Connect (en-US, en-GB, en-AU, en-CA…), and what are the name, subtitle, keyword field, and promotional text for **each**?
   Was the different US subtitle a deliberate choice, and since when?
2. Was "BillFlow" or "Easy Bills" a former name? Is `easy-bills.netlify.app` the intended long-term domain? → The code has both names (subscription IDs `com.billflow.*`, repo names `Easy-bills-*`, display name "Dues"). The app links to Google Sites, and a Firebase-hosted Dues site also exists. **Which domain is canonical NEEDS CONFIRMATION.**
3. What does the free plan include (bill limit), and is there a free trial? → **Free plan: 5 active + 5 archived bills (code).** Trial: the app repo says a 1-week trial was set in App Store Connect on 2026-10-09. Whether it is live for 1.2.0 users NEEDS CONFIRMATION.
4. Is "works offline — full functionality" accurate with sign-in and sync? → **Answered by code: no, not in 1.2.0** (memory-only cache).
5. Which third-party SDKs ship in 1.2.0? → **Firebase (Analytics, Crashlytics, Auth, Firestore, Messaging, Remote Config, Storage, Database) and Google Sign-In** (code). There is no ATT prompt.
6. Is the email in screenshot 3 a real person's address? → Likely the owner's or a team account (it matches the app repo's history). Please confirm.
7. Does the App Privacy label accurately reflect 1.2.0's actual data practices and SDKs? (The label shown is your own declaration; Claude can't verify data flows.)

## 8. Reconciliation log — Task 005 (2026-10-10)
Each material claim from pass 1 was re-checked against a current source in pass 2.

| Claim (pass 1) | Pass 2 source and time | Result | Change made |
|---|---|---|---|
| App Privacy label declares linked data across many categories | S2 AU and US, 08:59 UTC, uncached; also GB, CA, NZ, IE, IN | **Confirmed.** All listed types present under the Analytics and App Functionality purposes | Rewrote §4 as a per-purpose table. Added "developer-declared, not verified by Apple" |
| US subtitle differs from other storefronts | S2 US vs AU/GB/CA/NZ/IE/IN, 08:59 UTC | **Confirmed** (US: "Bill Payment Manager & Budget") | Added a caching caveat. The cause stays NEEDS CONFIRMATION |
| IAP prices per storefront | S2, 7 storefronts | **Confirmed**, unchanged | Added a pass column. 8 storefronts are marked pass 1 only |
| Version 1.2.0, 2026-09-28; age 4+; size 23.2 MB; English only; Finance/Utilities | S1 and S2, 7 storefronts | **Confirmed** | Added source detail |
| Ratings: AU 3, IN 4, others 0 | S1 and S2, 7 storefronts | **Confirmed** | Added India to the §1 ratings table |
| Terms URL returns 404 | S4, 08:59 UTC | **Confirmed**, HTTP 404 | Added observation dates |
| Privacy policy titled "BillFlow", dated 2026-03-22 | S3, 09:00 UTC | **Confirmed** | Added the text-search results |
| Screenshot 3 shows "a real email address" | S1 screenshot URLs unchanged | **Overstated.** An email-format string is visible, but whether it is real can't be known | Relabelled as Unknown |
| "Identical across all storefronts" included the privacy label | Pass 1 method review | **Overstated.** The label was compared only on pages that were diffed | Scoped each "identical" statement to the storefronts actually compared |
| Version history dates with years | S2 shows day and month only | **Partly inferred** | Labelled the year as inferred |
| Feature claims | — | Still **listing claims**, not verified in the build | No change |

## 9. Pending 2.0.0 listing — not live
**Source:** app repo `pwndhull/Easy-bills-ios`, `fastlane/metadata/<locale>/*.txt` at `main` @ `f676e19`. The commit adding them (`4fb412f`, 2026-10-08) is titled "ASO: match what App Store Connect accepted". The app repo's `docs/STATUS.md` (2026-10-09) says version 2.0.0 is "Prepare for Submission" with 12 localized listings.
**Status:** user-provided (via the app repo). **Not observable publicly until 2.0.0 is released.** The live values in §1/§1a still apply today.

| Locale | Subtitle (2.0) | Keywords (2.0) | Keyword bytes |
|---|---|---|---|
| en-US | Due dates, alerts & renewals | payment,budget,expense,split,subscription,organizer,planner,calendar,overdue,recurring,rent,utility | 99 |
| en-GB | Council tax, rent & due dates | organiser,planner,calendar,overdue,recurring,payment,budget,expense,split,subscription,direct,debit | 99 |
| en-AU | Due dates, rent & rego alerts | bpay,strata,council,rates,organiser,overdue,payment,budget,expense,split,subscription,bas,flatmate | 98 |
| en-CA | Hydro, rent & due date alerts | organizer,calendar,overdue,recurring,payment,budget,expense,split,subscription,utility,roommate | 95 |

- The name stays "Dues: Bill Tracker & Reminder" in all four.
- Other 2.0 locales: fr-CA, fr-FR, es-MX, es-ES, de-DE, pt-BR, ar-SA, hi.
- The 2.0 description removes the stale and contradicted claims in L4 and links to the Google Sites privacy and terms pages.

**Measurement implication:** releasing 2.0 changes the subtitle, keywords, description and screenshots in every English storefront at once, together with the app itself. **A pre-2.0 baseline must be captured before release** (Task 001). Any later change cannot be attributed to a single variable.
