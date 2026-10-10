# Task 000 — Repository Bootstrap & Collaboration Setup

| Field | Value |
|---|---|
| ID | 000 |
| Priority | P0 |
| Owner | Claude (implementation) → ChatGPT review → user approval |
| Status | In review — awaiting ChatGPT review and user acceptance |
| Opened | 2026-10-10 |
| Branch | `claude/zen-turing-jrudn0` |
| Approval gates | None for drafting/docs. Merging the PR is the user's decision. |

## Objective
Turn the repository into an evidence-driven marketing workspace that Claude Code, ChatGPT, and the user can share through GitHub, without fabricating data or overwriting useful existing work.

**Business reason:** every later marketing decision (ASO, content, experiments) depends on a trustworthy shared record of what is known, what is assumed, and what has been approved.

## Repository audit (2026-10-10)

### State at start
- Branch `claude/zen-turing-jrudn0`, identical to `main` (18 commits, all by the repository owner on 2026-10-10). Working tree clean.
- 17 tracked files: `README.md`, `CLAUDE.md`, `.gitignore`, `strategy/{30-day-plan,positioning}.md`, `tasks/inbox/001-aso-baseline-audit.md`, `analytics/baseline.md`, `content/calendar.csv`, `content/scripts/{002,003}-*.md`, `docs/decisions/0001-workspace-and-guardrails.md`, `experiments/{active,results}.md`, plus `.gitkeep` files in `analytics/imports`, `analytics/reports`, `content/approved`, `tasks/done`, `tasks/in-progress`.
- No `.github/` directory, no workflows, no issue templates, no `aso/` directory.

### Useful existing work (preserved)
- `CLAUDE.md` guardrails (truth/evidence, approval gates, analytics privacy) — sound; restructured, not weakened.
- `README.md` operating model and guardrails.
- `strategy/30-day-plan.md` — correct "baseline before targets" principle.
- `tasks/inbox/001-aso-baseline-audit.md` — correct first task; kept and extended.
- `analytics/baseline.md` — correctly shows every metric as Unknown.
- Decision 0001 — kept unchanged.
- Content drafts 002 and 003 and `content/calendar.csv` — kept; drafts remain unapproved.
- `.gitignore` already ignores `analytics/imports/*`, `.env*`, `*.p8`, `*.pem`, `*.key`, `secrets/`, `credentials/`.

### Gaps, inconsistencies, and errors found
| # | Finding | Type | Action taken |
|---|---|---|---|
| A1 | `content/calendar.csv` row 1 references `content/scripts/001-bill-checkup.md`, which never existed in history (checked `git log --all --diff-filter=D`). | Broken reference | Calendar row annotated; file not invented. |
| A2 | README refers to `aso/` but the directory did not exist. | Missing | Created `aso/` with audit + templates. |
| A3 | No `tasks/review/` stage; task file had no ID/owner/next-action schema. | Missing process | Lifecycle + template in `tasks/README.md`. |
| A4 | No collaboration protocol or operating manual; ChatGPT handoff format undefined. | Missing process | `docs/collaboration-protocol.md`, `docs/operating-manual.md`. |
| A5 | No metric dictionary; baseline lacked export instructions. | Missing | `analytics/metric-definitions.md`; baseline updated. |
| A6 | No experiment backlog/template beyond prose. | Missing | `experiments/backlog.md`. |
| A7 | Repo uses the name "Dues: Bill Tracker Reminder"; the live App Store name is **"Dues: Bill Tracker & Reminder"** (with `&`). | Inaccuracy | Docs now use the live name; see `aso/current-listing-audit.md`. |
| A8 | `strategy/positioning.md` listed features as entirely unknown although the public listing describes them. | Outdated | Positioning now cites listing claims, labelled "listing claim — verify in build". |
| A9 | `.gitignore` did not cover `*.p12`, `*.cer`, `*.mobileprovision` variants, service-account JSON, or spreadsheet exports dropped outside `analytics/imports/`. | Security gap | `.gitignore` extended. |
| A10 | No decision index or decision template. | Missing | `docs/decisions/README.md`. |
| A11 | Repo treated the App Store listing as one global listing; the live listing differs by region (US subtitle; per-storefront prices). Raised by the user mid-session. | Inaccuracy | Audited 16 storefronts; ASO files now per localization (`aso/current-listing-audit.md` §1a, decision 0002). |
| A12 | No end-of-session handoff file. | Missing (user instruction) | `docs/handoff.md`, required by `CLAUDE.md`. |

### Capabilities verified in this session
| Capability | Available? | Evidence |
|---|---|---|
| Read/write this repo, push to the designated branch, open PRs | Yes | Git + GitHub MCP tools |
| Public App Store listing (iTunes Lookup API + apps.apple.com page) | Yes | Fetched 16 storefronts 2026-10-10 (some requests rate-limited with HTTP 429, retried successfully) |
| Developer website `easy-bills.netlify.app` | Yes (public) | Fetched 2026-10-10 |
| Apple developer documentation | Yes (public) | Fetched 2026-10-10 |
| App Store Connect (analytics, sales, keyword field, subscriptions) | **No** | No credentials; must not be assumed |
| RevenueCat / other subscription dashboards | **No** | None configured |
| Social, ads, or email accounts | **No** | None configured |
| Search-volume / keyword-difficulty data | **No** | No paid ASO tool; Apple Search Ads popularity requires the user's account |

### Live listing findings that need the user's attention
Full detail and sources: [`aso/current-listing-audit.md`](../../aso/current-listing-audit.md).
- **L1 — Terms of Use link returns HTTP 404** (`https://easy-bills.netlify.app/terms`).
- **L2 — Privacy policy page is titled "BillFlow"**, last updated 22 March 2026, and does not appear to describe data types declared in the App Privacy label (e.g. contacts, phone number, coarse location). "BillFlow" is also the name of a different app shown in "You Might Also Like".
- **L3 — Screenshot 3 appears to display a real email address.** Not reproduced in this repo.
- **L4 — Description still headed "NEW IN VERSION 1.1.0"** while the live version is 1.2.0.

These are tracked in [Task 002](../inbox/002-listing-trust-and-compliance-fixes.md). Claude has not changed anything live.

## Deliverables
- [x] Audit recorded (this file)
- [x] `aso/current-listing-audit.md` public listing snapshot
- [x] Collaboration protocol, operating manual, task lifecycle
- [x] Metric dictionary, baseline export instructions, `.gitignore` hardening
- [x] Strategy updates and templates (ASO, experiments, decisions)
- [x] README and CLAUDE.md rewrite
- [x] Handoff with ChatGPT review prompt → [`docs/handoff.md`](../../docs/handoff.md)

## Acceptance criteria
- No fabricated metrics, features, reviews, search volumes, or results.
- Every external fact has a URL and access date.
- Existing useful work preserved; no files deleted.
- No secrets or personal data committed (staged diff inspected before each commit).

## Handoff
- **Changed:** see [`docs/handoff.md`](../../docs/handoff.md) for the commit list and files.
- **Why:** audit gaps A1–A12 above.
- **Evidence:** public sources S1–S8 in [`aso/current-listing-audit.md`](../../aso/current-listing-audit.md#sources), Apple metric docs in [`analytics/metric-definitions.md`](../../analytics/metric-definitions.md#sources).
- **Needs review:** accuracy of the listing audit vs live pages; whether task priorities are right; whether decision 0002 should be accepted; the proposed guard workflow in `docs/handoff.md`.
- **Next:** user actions in Task 002 and exports for Task 001.
