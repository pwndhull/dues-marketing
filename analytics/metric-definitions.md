# Metric Definitions

Report a metric **only if the source export actually contains it**. Definitions below quote or paraphrase the source; where a definition has not been confirmed from a primary source, it is marked NEEDS CONFIRMATION — confirm from the export's own documentation before reporting.

## Sources
| ID | URL | Publisher | Accessed | Establishes |
|---|---|---|---|---|
| M1 | https://developer.apple.com/help/app-store-connect-analytics/acquisition/acquisition | Apple Developer | 2026-10-10 | Definitions of impressions, product page views, total/first-time downloads, redownloads, conversion rate, source types |

## App Store Connect — App Analytics (acquisition)
| Metric | Definition | Source | Notes |
|---|---|---|---|
| Impressions (unique) | Unique devices that viewed the app on the App Store (search results, browse, product page, etc.) in the period | M1 | Unique per day/week/month — don't sum daily uniques into a monthly unique |
| Product page views (unique) | Unique devices that viewed the product page | M1 | |
| Total downloads | Times the app was downloaded; split into first-time downloads and redownloads. iCloud restores and auto-downloads to linked devices are excluded | M1 | |
| First-time downloads | Downloads by accounts that had never downloaded the app | M1 | Preferred acquisition metric |
| Redownloads | Downloads by accounts that previously downloaded the app | M1 | |
| Conversion rate | How often unique impressions turn into total downloads | M1 | Apple's definition uses **impressions**, not page views. If you compute downloads ÷ page views, name it "page-view conversion" |
| Source type | App Store search, App Store browse, app referrer, web referrer, etc. | M1 | Key for ASO: report search vs browse separately |
| Territory | Storefront country | ASC export | Needed to prioritise English markets |
| Sessions, active devices, deletions | Engagement metrics; availability depends on users sharing analytics with developers | ASC | NEEDS CONFIRMATION of exact definitions; opt-in sample only |

## App Store Connect — Sales, proceeds and subscriptions
| Metric | Working definition | Status |
|---|---|---|
| Proceeds | Amount the developer receives after Apple's commission and taxes, in a stated currency | NEEDS CONFIRMATION from Sales/Trends or Payments documentation |
| Sales | Customer price × units before commission | NEEDS CONFIRMATION |
| Active subscriptions | Paid subscriptions active at a point in time | NEEDS CONFIRMATION (Subscriptions report) |
| Free trials / introductory offers | Subscriptions in a free-trial or intro period | NEEDS CONFIRMATION; Dues' trial terms Unknown |
| Trial-to-paid conversion | Trials that converted to paid ÷ trials that ended in the period | Derived — state numerator, denominator and cohort |
| Cancellations / auto-renew off | Subscriptions with auto-renew turned off in the period | NEEDS CONFIRMATION |
| Refunds | Refunded transactions in the period | NEEDS CONFIRMATION |

If a third-party dashboard (e.g. RevenueCat) is used, record its own definitions here — they differ from Apple's. Claude currently has no access to any subscription dashboard.

## Content / social
Reach, views, saves, link clicks — use each platform's definitions, record which platform and date. Store clicks from social cannot be reliably attributed to downloads without campaign links; App Store campaign links (`ct=` / provider token) can add attribution in App Analytics — setting them up is allowed, but adding third-party tracking is not without approval.

## Report header (required for every report in `analytics/reports/`)
```markdown
# <Title>
- **Date range:** YYYY-MM-DD to YYYY-MM-DD
- **Comparison period:** …
- **Timezone:** … (App Store Connect default is Pacific Time — confirm in export)
- **Extraction date:** YYYY-MM-DD, by <user>
- **Source(s):** App Store Connect → … (report name, filters)
- **Territories:** all / list
- **Metric definitions:** link to this file; note any deviation
- **Limitations:** sample size, opt-in data, seasonality, releases or listing changes in the period, missing values
- **Recommendations:** each labelled Hypothesis or Recommendation
```

Aggregate tables may be committed as `analytics/reports/YYYY-MM-DD-<topic>-aggregate.csv` (the only CSV pattern under `analytics/` that `.gitignore` allows), after the staged diff is checked.

Small numbers: with a new app, many daily counts will be tiny. Prefer weekly/monthly aggregates, show absolute counts alongside rates, and don't claim changes that small samples cannot support.
