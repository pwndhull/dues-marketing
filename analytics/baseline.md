# Dues — Performance Baseline

**Status:** Waiting for verified data
**Extraction date:** TBD
**Period:** TBD — suggested: app launch (2026-04-22) to latest complete week, plus the last 28 days
**Timezone:** TBD (confirm from export)
**Source(s):** App Store Connect and subscription analytics, if supplied
**Owner:** User supplies exports; Claude Code analyses aggregate data
**Definitions:** [`metric-definitions.md`](metric-definitions.md)

## Core metrics
| Metric | Value | Comparison period | Source / definition | Notes |
|---|---:|---|---|---|
| Impressions | Unknown | Unknown | Not supplied | Do not estimate |
| Product-page views | Unknown | Unknown | Not supplied | Do not estimate |
| First-time downloads | Unknown | Unknown | Not supplied | Do not estimate |
| Conversion rate | Unknown | Unknown | Not supplied | Apple: impressions → downloads |
| Top territories | Unknown | Unknown | Not supplied | Needed to prioritise English markets |
| Source type split (search / browse / referrer) | Unknown | Unknown | Not supplied | |
| Proceeds | Unknown | Unknown | Not supplied | Currency and period required |
| Active subscriptions / trials | Unknown | Unknown | Not supplied | Include only if available |
| Trial-to-paid / subscription conversion | Unknown | Unknown | Not supplied | Confirm metric definition |

## Public, non-analytics context (not performance data)
Publicly visible ratings counts on 2026-10-10: AU 3, IN 4, all other English storefronts checked 0 ([listing audit §1a](../aso/current-listing-audit.md#1a-regional-listings--verified-public)). These say nothing reliable about downloads.

## How to obtain the data
Claude has no App Store Connect access. The user can export (all free):

1. **App Analytics → Metrics** — Impressions, Product Page Views, Total Downloads, First-Time Downloads, Conversion Rate. Set date range; **View by: Territory**, then again by **Source Type**. Export CSV or screenshot the table.
2. **App Analytics → Sources → App Store Search / Browse** — downloads by source.
3. **Sales and Trends → Subscriptions** — active subscriptions, trials, conversions, cancellations by territory (if any).
4. **Payments and Financial Reports** or Trends proceeds — monthly proceeds with currency.
5. **App Store Connect → each English localization** — current name, subtitle, keyword field, promotional text (for Task 003).

Either paste **aggregate** numbers into a PR comment/issue, or place CSVs in `analytics/imports/` during a Claude Code session on a local machine (that folder is Git-ignored). Do not upload files that contain Apple IDs, emails, order IDs, or transaction rows to GitHub.

## Interpretation
No performance conclusions or numerical growth targets until a verified baseline exists. Note attribution limits, sample size, seasonality, product/version changes (1.2.0 shipped 2026-09-28), and regional metadata differences (US subtitle differs).

## Data handling
Keep original exports in the Git-ignored `analytics/imports/` directory. Commit only aggregated, reviewed summaries that do not contain personal or customer-level data.
