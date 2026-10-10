# Keyword Research

**Status:** Not started here. The app repo already contains per-locale keyword sets for the pending 2.0 release, and the reasoning behind them (`pwndhull/Easy-bills-ios` `docs/strategy/ACQUISITION.md` §2: no volume data, rules-based). The **live 1.2.0** keyword fields are still unknown.
**Task:** [003 — Keyword research per English localization](../tasks/inbox/003-keyword-research-per-localization.md)

## Rules
- Research is done **per localization** (e.g. en-US, en-GB, en-AU, en-CA). Dues already has at least two different subtitles by region, so one global keyword list is wrong.
- **Never invent search volume, popularity, or difficulty.** If a number is recorded, it must come from a named tool, with the date and storefront. Without a tool, use only observable evidence (what appears in App Store search results and autocomplete on a date).
- Apple's keyword field: ≤ 100 bytes, comma-separated, words > 2 characters, no app or company names, don't repeat words already in the name ([Apple: platform version information](https://developer.apple.com/help/app-store-connect/reference/app-information/platform-version-information), accessed 2026-10-10). Re-verify limits before finalising any draft.
- Don't keyword-stuff or use competitor names (App Review Guideline 2.3.7).
- Only target terms that describe **verified** Dues features.

## Evidence sources available
| Source | Cost | What it gives | Limitation |
|---|---|---|---|
| App Store search on a device set to the target storefront | Free | Which apps rank for a phrase on that date | Personalised; one point in time; manual |
| App Store search autocomplete | Free | Phrases Apple suggests | No volume data |
| Apple Search Ads keyword popularity (user's account) | Free to view; **spending requires approval** | Apple's relative popularity score | Requires user's account; Claude has no access |
| App Store Connect → App Analytics → Sources (App Store Search) | Free | Downloads from search per territory | Not per keyword |
| Third-party ASO tools | Usually paid | Estimated volume/difficulty | Estimates; any subscription needs approval and counts toward the AUD $100 budget |

## Current keyword fields (user-provided)
| Localization | Storefronts it serves | Name | Subtitle | Keyword field (verbatim) | Bytes | Provided on |
|---|---|---|---|---|---|---|
| en-US (**live 1.2.0**) | United States (confirm) | Dues: Bill Tracker & Reminder | Bill Payment Manager & Budget | NEEDS CONFIRMATION | — | — |
| NEEDS CONFIRMATION (**live 1.2.0**) | AU, GB, CA, NZ, IE, IN, … | Dues: Bill Tracker & Reminder | Split Bills & Track Payments | NEEDS CONFIRMATION | — | — |
| en-US (**pending 2.0, not live**) | US | Dues: Bill Tracker & Reminder | Due dates, alerts & renewals | see [audit §9](current-listing-audit.md#9-pending-200-listing--not-live) | 99 | app repo fastlane, 2026-10-08 |
| en-GB (**pending 2.0**) | UK (others? confirm) | same | Council tax, rent & due dates | see audit §9 | 99 | same |
| en-AU (**pending 2.0**) | Australia | same | Due dates, rent & rego alerts | see audit §9 | 98 | same |
| en-CA (**pending 2.0**) | Canada | same | Hydro, rent & due date alerts | see audit §9 | 95 | same |

Phrase evidence for the pending sets: none recorded with dates or search observations. They are reasoned choices, not measured ones. After 2.0 ships, the phrase log below is how to check them.

## Candidate phrase log (template)
One row per phrase per storefront per date. Leave cells empty rather than guessing.

| Phrase | Localization / storefront | Date checked | Method | Dues appears? (position if visible) | Top results observed (names only) | Popularity (tool + score) | Relevance to verified features | Notes |
|---|---|---|---|---|---|---|---|---|
| | | | | | | | | |

## Keyword map (template — fill only after the phrase log)
| Localization | Field (name / subtitle / keywords) | Proposed terms | Evidence rows | Rationale | Risk |
|---|---|---|---|---|---|
| | | | | | |
