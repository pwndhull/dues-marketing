# Task 006 — Reconcile Marketing Repo with App Repositories

| Field | Value |
|---|---|
| ID | 006 |
| Priority | P0 |
| Owner | Claude (evidence and corrections) · ChatGPT review · User (decisions) |
| Status | In review — awaiting ChatGPT review and user decisions |
| Opened | 2026-10-10 (the user asked Claude to check the "easy bills" app repository) |
| Approval gates | None for read-only inspection and documentation. Nothing was pushed to the app repositories. |

## Objective
Use the app's source code and the app repo's own documents to verify or correct the listing claims and open questions in this repository, and to surface overlaps with existing marketing work.

**Business reason:** marketing claims must match what the app does. Two repositories planning marketing separately would produce duplicated or conflicting work.

## Evidence and sources
| ID | Source | Ref / accessed | Establishes | Limitations |
|---|---|---|---|---|
| R1 | `pwndhull/Easy-bills-ios` (private) | `4c2f062` (estimated 1.2.0) and `main` @ `f676e19`; read 2026-10-10 | Features, SDKs, permissions, URLs, version | Code is not runtime behaviour. The 1.2.0 commit is an estimate |
| R2 | `Easy-bills-ios/docs/{STATUS,PLAN,APP-STORE-LISTING,RELEASE-2.0}.md`, `docs/strategy/ACQUISITION.md` | `main` @ `f676e19` | App Store Connect state of 2.0, existing marketing plan, prior listing critique | Written in the app repo by the owner or AI sessions. Counts as **user-provided**, not verified |
| R3 | `Easy-bills-ios/fastlane/metadata/*` | commit `4fb412f` (2026-10-08) | Pending 2.0 per-locale metadata | Not live; "accepted" by App Store Connect per the commit message |
| R4 | `pwndhull/Easy-bills-web` | `071c199` (2026-04-03) | Static site files | Not what `easy-bills.netlify.app` serves |
| R5 | `https://easy-bills.netlify.app/{,index.html,privacy-policy.html,Terms-of-service.html,support.html,terms,privacy}` | 2026-10-10 09:06 UTC | Only `/` and `/index.html` return 200 (BillFlow page); the rest return 404 | Point-in-time |
| R6 | `https://sites.google.com/view/easy-bills-pplc/privacy-policy`, `/tnc` | 2026-10-10 09:08 UTC, both 200 | The pages exist | Content renders client-side and was not read |
| R7 | `https://studio-7588909326-4b14f.web.app/`, `/bas-due-dates` | 2026-10-10 09:08 UTC, both 200 | A Firebase-hosted Dues site is live | — |

## What was found
1. **Feature claims:** checked one by one → [`aso/feature-verification.md`](../../aso/feature-verification.md).
   - Contradicted by code: "150+ currencies" (20), the listed categories, and "works offline" in 1.2.0.
   - Ambiguous: "no third-party tracking" (Firebase Analytics and Crashlytics are linked; there is no ATT prompt).
   - Free plan: 5 active + 5 archived bills.
2. **Pending 2.0 listing:** 12 locales are entered in App Store Connect, and each English locale has its own subtitle and keywords → [audit §9](../../aso/current-listing-audit.md#9-pending-200-listing--not-live). It fixes most of Task 002's description issues.
3. **Terms 404 root cause (hypothesis):**
   - The Netlify site serves an old "BillFlow" deploy, not `Easy-bills-web`.
   - The app links to Google Sites instead.
   - The 2.0 description uses the Google Sites URLs.
4. **Privacy label vs permissions:** the code requests only contacts, microphone and speech. Location and photos on the label need checking.
5. **Screenshot 3 email:** it matches a string in the app repo's history, so it is likely the owner's or a team account.
6. **Overlapping marketing plan:** the app repo's `docs/PLAN.md` conflicts with this repo on targets, an Apple Ads test above AUD $100, and outreach → [decision 0003](../../docs/decisions/0003-marketing-source-of-truth-across-repositories.md) (proposed).
7. **Timing:** a pre-2.0 baseline must be captured before 2.0 is released (Task 001).

## Deliverables
- **New:** [`aso/feature-verification.md`](../../aso/feature-verification.md) and [decision 0003](../../docs/decisions/0003-marketing-source-of-truth-across-repositories.md) (proposed).
- **Updated ASO files:**
  - [`aso/current-listing-audit.md`](../../aso/current-listing-audit.md): §2 statuses, L1/L3/L4, §7 answers, new §9.
  - [`aso/keyword-research.md`](../../aso/keyword-research.md).
- **Updated tasks:** 001 (timing), 002 (root causes and what 2.0 resolves), 003 (blocked and re-scoped), 004 (largely superseded).
- **Updated strategy:** `strategy/{30-day-plan,positioning,market-research}.md`.
- **Updated instructions and logs:**
  - `CLAUDE.md`: rules for the app repos.
  - `docs/collaboration-protocol.md`.
  - `docs/decisions/README.md`.
  - `experiments/backlog.md`: the budget conflict.
  - `README.md`.
  - `tasks/README.md`.
  - `docs/handoff.md`.

## Acceptance criteria — self-check (not yet reviewed by anyone else)
- [x] Each code claim cites a repo, path and commit. Code evidence is labelled as not runtime evidence.
- [x] `main` (2.0, unreleased) is kept separate from the estimated 1.2.0 commit.
- [x] App repo documents are labelled user-provided, not verified.
- [x] No secrets, config files, personal emails or names were copied into this repo. The staged diff was scanned.
- [x] Nothing was pushed to or changed in the app repositories.
- [x] Conflicts are flagged for the user, not resolved silently.

## Open questions (user)
1. **Decision 0003:** which repo owns the marketing plan? What about the Apple Ads test (about $140 per country) versus the AUD $100/month ceiling?
2. When will 2.0.0 be submitted or released? The baseline export must come first.
3. Which commit or build was 1.2.0 (to confirm `4c2f062`)?
4. Is the free trial live for current 1.2.0 users?
5. Why does the App Privacy label list coarse location and photos/videos when the app requests neither permission?
6. Which domain is canonical for the website and policies: Google Sites, Firebase Hosting, or Netlify? Should the stale Netlify "BillFlow" site be taken down or redirected? (That's a live change, so it's yours to make.)
7. Is the screenshot 3 email your own account?

## Next action
**User:** decide 0003, and export the pre-2.0 baseline before releasing 2.0. **ChatGPT:** review `aso/feature-verification.md` and decision 0003.

## Handoff
See [`docs/handoff.md`](../../docs/handoff.md).
