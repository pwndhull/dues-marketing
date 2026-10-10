# Session Handoff

Updated at the end of every session (see [`CLAUDE.md`](../CLAUDE.md#finish-every-session)). This file holds the **latest** session; earlier versions are in Git history: bootstrap @ `82a306c`, Task 005 @ `ed1e080`.

## 1. Session
- **Date:** 2026-10-10 (about 09:05–09:30 UTC)
- **Agent:** Claude Code (cloud session)
- **Branch:** `claude/zen-turing-jrudn0` · PR [pwndhull/dues-marketing#1](https://github.com/pwndhull/dues-marketing/pull/1) (draft)
- **Objective:** Task 006 — the user asked Claude to check the "easy bills" app repository, which holds the real app code. Goal: use it to verify listing claims and resolve open questions.
- **Review status:** No one has reviewed this work yet (not ChatGPT, not the user).

## 2. Work completed
| SHA | Summary |
|---|---|
| `76b2919` | `aso/feature-verification.md` (new) holds claim-by-claim code evidence. Listing audit updated: §2 statuses, L1/L3/L4, §7 answers, new §9 with the pending 2.0 per-locale listing. Keyword table split into live and pending rows |
| `7726bfd` | Decision 0003 proposed. `CLAUDE.md` and the collaboration protocol now have rules for the app repos. Tasks 001–004 updated, Task 006 added in review. Plan, positioning, market research, experiment backlog and README updated |
| *(this commit)* | This handoff |

**Repos read (read-only; nothing changed or pushed there):**
- `pwndhull/Easy-bills-ios` @ `f676e19` (`main`), plus the estimated 1.2.0 commit `4c2f062`
- `pwndhull/Easy-bills-web` @ `071c199`

**Key results:**
- **Contradicted by code:**
  - "150+ currencies": the code has 20.
  - The listed categories (Utilities, Rent, Insurance, Subscriptions, Loans): the code has Entertainment, Utilities, Housing, Food, Transportation, Healthcare, Lifestyle, Tech, Other.
  - "Works offline": 1.2.0 uses a memory-only cache.
- **Ambiguous:** "No third-party tracking". Firebase Analytics and Crashlytics are linked, and there is no ATT prompt.
- **Supported by code:** voice entry (Hindi needs confirming), split bills with push, Family Plan (5 members + owner), widgets with quick-add, insights, dark mode, no ads, and a free plan of 5 active + 5 archived bills.
- **2.0.0 is waiting in App Store Connect** ("Prepare for Submission", per the app repo). It has 12 localized listings, and each English locale has its own subtitle and keywords (audit §9).
- **Terms 404:** the Netlify site serves an old "BillFlow" deploy. The app links to Google Sites pages instead, and the `Easy-bills-web` pages aren't deployed on Netlify.
- **Screenshot 3 email:** it matches a string in the app repo's history, so it's likely the owner's or a team account.
- **The app repo has its own marketing plan** (`docs/PLAN.md`). It conflicts with this repo on targets, outreach, and an Apple Ads test (~$140 per country) above the AUD $100/month ceiling. Proposed decision 0003 needs your choice.

## 3. Files changed
**Created:**
- `aso/feature-verification.md`
- `docs/decisions/0003-marketing-source-of-truth-across-repositories.md`
- `tasks/review/006-reconcile-with-app-repositories.md`

**Modified:**
- ASO: `aso/current-listing-audit.md`, `aso/keyword-research.md`
- Instructions and logs: `CLAUDE.md`, `README.md`, `docs/collaboration-protocol.md`, `docs/decisions/README.md`, `docs/handoff.md`, `experiments/backlog.md`
- Strategy: `strategy/30-day-plan.md`, `strategy/positioning.md`, `strategy/market-research.md`
- Tasks: `tasks/README.md`, `tasks/in-progress/001-…`, `tasks/inbox/002-…`, `003-…`, `004-…`

## 4. Validation performed
These checks were actually run:
- **Code facts:** each one came from `git show` / `git grep` at a named commit (`4c2f062` or `main`). That covered:
  - the currency enum count;
  - the category and recurrence enums;
  - `PremiumManager` limits;
  - Firestore cache settings;
  - linked SDK products in `project.pbxproj`;
  - `NS*UsageDescription` keys;
  - the speech recognizer locale;
  - widget deep links;
  - the in-app privacy and terms URLs.
- **Live URLs:** fetched with curl at 09:06–09:08 UTC; the HTTP results are recorded in the files.
- **Links:** 151 relative Markdown links resolve (0 broken). Every `current-listing-audit.md#…` anchor resolves.
- **Sensitive data:** the tree was searched for email addresses, the developer-email fragment, personal names from the app repo docs, Google API-key patterns, and Apple team IDs. None were found.
- **App repos:** `git status` is clean in both; nothing was modified.
- **Not done:**
  - No app build or run; this is code evidence only.
  - The Google Sites policy text wasn't read (it renders client-side).
  - The exact 1.2.0 build commit is unconfirmed.
  - No full SDK privacy audit.

## 5. Outstanding issues, assumptions, blockers
- **Blocker:** no App Store Connect data yet. The baseline must cover a period that ends **before** 2.0 is released.
- **Needs your decision:**
  - Decision 0003 (which repo owns the marketing plan) and the Apple Ads budget conflict.
  - Decision 0002 (task lifecycle and per-localization ASO).
  - Accepting Tasks 000, 005 and 006.
- **Assumptions:**
  - 1.2.0 was built from `4c2f062`. This is inferred from the app repo's STATUS saying later commits weren't compiled until 29 Sept.
  - App repo docs are your own statements and are treated as user-provided.
- **Open questions:**
  - Is the free trial live for 1.2.0 users?
  - Why does the privacy label list location and photos/videos when the app doesn't request those permissions?
  - Which website domain and policy URL is canonical?
  - Hindi voice recognition at runtime.
  - Is the screenshot 3 email your own account?

## 6. Next recommended task
**Task 001 — pre-2.0 baseline** ([file](../tasks/in-progress/001-aso-baseline-audit.md)). Export App Store Connect aggregates by territory and by source type for a period ending before the 2.0 release date ([instructions](../analytics/baseline.md#how-to-obtain-the-data)). Also provide the live 1.2.0 keyword field(s).

**Acceptance criteria:**
- `analytics/reports/YYYY-MM-DD-baseline.md` has the required header.
- The period ends before the 2.0 release.
- English storefronts are ranked by verified data.
- Nothing is fabricated, and no raw exports are committed.

In parallel, decision 0003 is yours to make.

## 7. Actions requiring explicit human approval
No live action was taken. These are yours:
- **Decision 0003:** choose an option. Also decide on the Apple Ads test (~$140 per country): raise the AUD $100 ceiling for it, shrink it, or defer it.
- **Releasing 2.0.0:** it's your call, but export the baseline first.
- **Legal pages:** confirm the App Store Connect Privacy Policy URL. Decide whether to take down or redirect `easy-bills.netlify.app`.
- **Privacy label:** review it against the SDKs and permissions.
- **iPad screenshots:** upload the 13" set for 2.0.
- **Outreach** in the app repo plan (emailing paying users, creators, communities) is yours to do. Under this repo's rules, Claude won't do any of it without explicit approval for that action.
- **Guard workflow (optional):** a read-only GitHub check, still not added.

## 8. ChatGPT review prompt
```text
You are reviewing the GitHub repository pwndhull/dues-marketing, branch claude/zen-turing-jrudn0 (PR #1).
You cannot see Claude's conversation or the private app repositories; rely on what this repository records and cites.
Read: docs/handoff.md, tasks/review/006-reconcile-with-app-repositories.md, aso/feature-verification.md, aso/current-listing-audit.md (sections 2, 6, 7, 9), docs/decisions/0003-marketing-source-of-truth-across-repositories.md.
Check:
1. Does feature-verification.md keep code evidence, user-provided app-repo statements, and runtime behaviour clearly separate? Flag any claim stated more strongly than its evidence.
2. Is the reasoning for treating commit 4c2f062 as the 1.2.0 build sound, and is it labelled as an estimate everywhere it is used?
3. Is decision 0003 a fair statement of the conflict, and are the options complete? Is the recommendation justified?
4. Are tasks 001–004 re-prioritised sensibly given that 2.0.0 is pending (especially the pre-2.0 baseline)?
5. Any privacy risk in what was copied from the app repositories?
Label each point Verified / Hypothesis / Recommendation / Unknown. Do not invent data.
Output: (a) blocking issues, (b) non-blocking suggestions, (c) questions for the user, (d) proposed task changes in the format of tasks/_template.md.
```
