# Feature Verification — Code Evidence

**Checked:** 2026-10-10, by Claude Code ([Task 006](../tasks/review/006-reconcile-with-app-repositories.md))
**Method:** read-only inspection of the app source code. This is **code evidence**: it shows what the code contains, not how the shipped app behaves on a device. Runtime behaviour is still **NEEDS CONFIRMATION** where marked.

## Sources
| ID | Source | Ref | Notes |
|---|---|---|---|
| C1 | `pwndhull/Easy-bills-ios` (private) | `4c2f062` (2026-09-27, "Bump EasyBillsWidget version to 1.2.0") | **Best estimate of the live 1.2.0 build.** The app repo's `docs/STATUS.md` says everything committed after 2026-09-27 19:37 UTC was not compiled until 2026-09-29, and 1.2.0 was released 2026-09-28. The exact build commit is **NEEDS CONFIRMATION**. |
| C2 | same repo | `main` @ `f676e19` (2026-10-09) | Version **2.0.0**, unreleased. App Store Connect status per the app repo's `docs/STATUS.md` (written 2026-10-09): "Prepare for Submission" |
| C3 | `pwndhull/Easy-bills-ios` `docs/APP-STORE-LISTING.md` | `main` | A code-checked critique of the live listing, written 2026-10-06 in the app repo. Its claims were re-checked here against C1 |
| C4 | `pwndhull/Easy-bills-ios` `fastlane/metadata/*` | `main` (commit `4fb412f`, 2026-10-08, "ASO: match what App Store Connect accepted") | The **2.0 listing** text for 12 locales. **Not live.** |
| C5 | `pwndhull/Easy-bills-web` | `071c199` (2026-04-03) | Static site with `index.html`, `privacy-policy.html`, `Terms-of-service.html`, `support.html` |

Nothing secret or personal was copied from these repos into this repository.

## Listing claims vs code (live 1.2.0 = C1)
| Listing claim (live description) | Code evidence at C1 | Verdict for marketing use |
|---|---|---|
| Track bills; due-date reminders; mark paid | Bill model, notification service, pay actions present | **Supported by code** |
| Recurring bills "(monthly, weekly, yearly)" | `weekly`, `fortnightly`, `monthly`, `yearly` (`ModelsExpense.swift`) | **Supported.** Fortnightly also exists; quarterly is added only in 2.0 (C2) |
| Voice entry | `VoiceInputView`, `VoiceParseService`, using `SFSpeechRecognizer(locale: "en-IN")` | **Supported.** Hindi: the UI text says "English or Hindi", but the recognizer locale is en-IN. Hindi recognition **NEEDS CONFIRMATION** on a device |
| Split bills; push notification to each person | `BillSplitView`; Cloud Function sends multicast push (`functions/src/index.ts`) | **Supported by code**; runtime not tested |
| Family Plan, "up to 5 household members" | `Household.maxMembers = 5`; UI shows `members + 1` / `maxMembers + 1` | **Supported**: 5 members plus the owner (6 people). Wording "up to 5 others" is the precise version |
| Home and Lock Screen widgets with quick-add | `EasyBillsHomeWidget`, `EasyBillsLockScreenWidget`; home widget links to `easybills://add-expense` | **Supported** |
| Real-time sync across devices | Firestore | **Supported by code**; runtime not tested |
| Insights, monthly totals, category breakdown | `InsightsView` present | **Supported** |
| CSV export (listed under core features) | `ExportService`, CSV only at C1; `exportData` is listed as a Premium feature in `PremiumManager` | **Partly wrong**: export appears to be Premium. C3 says the same |
| **"150+ currencies"** | `PreferencesService.Currency` has **20** cases (USD, EUR, GBP, JPY, CAD, AUD, INR, CHF, CNY, KRW, BRL, MXN, SGD, NZD, HKD, SEK, NOK, DKK, ZAR, RUB) | **Contradicted by code.** Do not reuse |
| **"Filter by category: Utilities, Rent, Insurance, Subscriptions, Loans"** | Categories: Entertainment, Utilities, Housing, Food, Transportation, Healthcare, Lifestyle, Tech, Other | **Contradicted by code** |
| **"Works offline — full functionality"** | Firestore `MemoryCacheSettings()` at C1, so data is kept in memory only for the session | **Contradicted / overstated** at C1. On `main` (C2) it is `PersistentCacheSettings()` and paying or deleting works offline, but that is **not released** |
| **"No third-party tracking"** | Firebase Analytics and Crashlytics are linked at C1 and C2. There is no `NSUserTrackingUsageDescription`, so the app cannot request ATT permission | **Ambiguous.** Third-party analytics SDKs are present. The App Privacy label declares no "Data Used to Track You". C3 recommends replacing the line with "No ads. We never sell your data." Do not reuse "no third-party tracking" |
| "Privacy first — we never sell your data; secure encryption" | Not verifiable from code (a business practice) | **User-provided claim**; keep it only if the user confirms it |
| Zero ads | No ad SDK product is linked. `google-ads-on-device-conversion` appears in `Package.resolved` as a Firebase dependency, not as a linked product | **Supported** (no ad display code found); a full SDK review was not done |
| Dark mode | `AppTheme`, `ThemePickerView` | **Supported** |
| Premium: unlimited bills; free limit | `freeActiveBillLimit = 5`, `freeArchivedBillLimit = 5` | **Supported**: free plan has up to 5 active and 5 archived bills |
| Premium: "Priority support and early access" | `prioritySupport` exists as an enum case. C3 says it was removed from the paywall in 2.0 | **Do not reuse.** It is not a real service commitment |
| Monthly / yearly subscription | Products `com.billflow.monthly.subscription`, `com.billflow.yearly.subscription`, `family.monthly`, `family.annual` | **Supported** |
| Free trial (not claimed in the live listing) | Local StoreKit config has $0 intro entries. The app repo's STATUS says "1-week free trial on both plans (175 countries)" was set in App Store Connect on 2026-10-09 | **User-provided via app repo**; whether it applies to live 1.2.0 users now is **NEEDS CONFIRMATION** |
| AI assistant (not in the live listing) | `AIAssistantService` uses Apple FoundationModels (on-device), with an `aiAssistant` premium feature | Exists in code; device and OS requirements apply |

## In-app languages
- **C1 (1.2.0):** no String Catalog, so the app UI is English only.
- **C2 (2.0):** `Localizable.xcstrings` has en, es, hi, fr, de, pt-BR, ar. The app repo flags all translations as `needs_review`.

## Permissions requested (both C1 and C2)
- **Requested:** contacts, microphone, speech recognition.
- **Not requested:** location, camera, photo library, or tracking (ATT).

The App Privacy label's "Coarse Location" and "Photos or Videos" entries therefore **NEEDS CONFIRMATION**. They may come from SDK behaviour or be over-declared. This is a question for the developer, not a conclusion.

## Legal and website URLs
| Where | Privacy | Terms | Observed 2026-10-10 |
|---|---|---|---|
| App code (C1 and C2) | `https://sites.google.com/view/easy-bills-pplc/privacy-policy` | `https://sites.google.com/view/easy-bills-pplc/tnc` | Both HTTP 200 at 09:08 UTC. The page text renders client-side, so its content was **not read** |
| Live listing description (1.2.0) | `https://easy-bills.netlify.app/` | `https://easy-bills.netlify.app/terms` | 200 ("Privacy Policy \| BillFlow") / **404** |
| 2.0 listing text (C3/C4) | Google Sites URLs above | Google Sites URLs above | Not live yet |
| `Easy-bills-web` repo (C5) | `privacy-policy.html` ("Easy Bills", 2026-04-03) | `Terms-of-service.html` | **Not deployed** on `easy-bills.netlify.app`: `/privacy-policy.html`, `/Terms-of-service.html`, `/support.html` all returned 404 at 09:06 UTC. The live Netlify root serves a different "BillFlow" page |
| App repo root (C1/C2) | `privacy-policy.html` ("Privacy Policy – Dues", effective 2026-04-16) | `terms-and-conditions.html` | Files in the repo; where they are hosted is Unknown |
| Firebase-hosted site (app repo `website/`) | — | — | `https://studio-7588909326-4b14f.web.app/` returned 200, titled "Dues: bill tracker & reminder for iPhone"; `/bas-due-dates` returned 200 |

**Root-cause hypothesis for the Terms 404:** the Netlify site serves an old "BillFlow" deploy, not the `Easy-bills-web` repo. Even if that repo were deployed, its file is `Terms-of-service.html`, not `/terms`. The 2.0 listing switches to the Google Sites URLs the app already uses, so shipping 2.0 would remove the broken link from the description. **NEEDS CONFIRMATION** that the Privacy Policy URL field in App Store Connect is also updated.

## Screenshot 3 email
The email-format string visible in the live iPhone screenshot 3 also appears in a file path committed to the app repo's early history, apparently from the developer's own machine. That suggests it is the **owner's or a team member's account, not a customer's**. This is still **NEEDS CONFIRMATION**, and it remains personal data. It is not reproduced here. Per the app repo's STATUS, new iPhone screenshots for 2.0 are uploaded for en-US, en-AU, en-CA, fr-CA and en-GB; the iPad 13" en-US slot still shows the old 1.2 screenshots.
