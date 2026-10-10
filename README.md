# Dues — Marketing Workspace

Shared, evidence-driven workspace for marketing **Dues: Bill Tracker & Reminder** — an iOS bill tracker and reminder app ([App Store ID 6761047973](https://apps.apple.com/app/id6761047973)), free with monthly/yearly and Family Plan subscriptions, English only, live since 2026-04-22 (v1.2.0 on 2026-09-28).

## Goals
Increase qualified App Store impressions, product-page conversion, downloads, and sustainable subscription revenue in English-speaking markets — organic-first (ASO, useful content, low-cost experiments), with markets prioritised by verified data. Marketing spend ceiling **AUD $100/month**, only with explicit approval. No outcome is promised.

## Current status (2026-10-10)
- Public listing audited in 16 English-served storefronts → [`aso/current-listing-audit.md`](aso/current-listing-audit.md). **The listing differs by region** (US subtitle "Bill Payment Manager & Budget" vs "Split Bills & Track Payments" elsewhere; prices per storefront).
- Live trust issues found and re-confirmed on 2026-10-10 ([Task 005](tasks/review/005-reconcile-listing-evidence.md)):
  - the Terms of Use link returns HTTP 404;
  - the privacy policy is branded "BillFlow" and omits data types the App Privacy label declares;
  - a screenshot shows an email-format address (whether it is real is unknown).

  See [Task 002](tasks/inbox/002-listing-trust-and-compliance-fixes.md).
- Performance baseline: **no data yet** — waiting for App Store Connect exports → [Task 001](tasks/in-progress/001-aso-baseline-audit.md).
- Current priorities: [`strategy/30-day-plan.md`](strategy/30-day-plan.md). Latest session handoff: [`docs/handoff.md`](docs/handoff.md).

## Who does what
| | Role |
|---|---|
| **User** | Priorities, account exports, confirmations, approvals, and every live action |
| **Claude Code** | Research, drafts, analysis, documentation, commits, draft PRs — see [`CLAUDE.md`](CLAUDE.md) |
| **ChatGPT** | Reviews repo state and handoffs; proposes changes as tasks |

GitHub is the only shared memory; the models don't see each other's conversations. Protocol: [`docs/collaboration-protocol.md`](docs/collaboration-protocol.md).

## Task workflow
`tasks/inbox/ → tasks/in-progress/ → tasks/review/ → tasks/done/` — the folder is the status; blocked tasks stay in `in-progress/` with a blocker note. P0/P1/P2 priorities. See [`tasks/README.md`](tasks/README.md) and the [template](tasks/_template.md).

## Where things are
| Folder | Contents |
|---|---|
| `strategy/` | Positioning, audience, market research, 30-day plan |
| `tasks/` | Task files by status |
| `aso/` | Listing audit, keyword research, competitor research, listing drafts (per localization) |
| `content/` | `calendar.csv`, `scripts/` (drafts), `assets/`, `approved/` |
| `analytics/` | `baseline.md`, `metric-definitions.md`, `reports/` (aggregates); `imports/` is local-only and Git-ignored |
| `experiments/` | `backlog.md`, `active.md`, `results.md` |
| `docs/` | Operating manual, collaboration protocol, handoff, `decisions/` |
| `.github/` | Issue templates, PR template (no workflows) |

## Guardrails
- Never invent features, testimonials, ratings, downloads, revenue, search volume, or experiment results. Label facts, hypotheses, and unknowns.
- No publishing, App Store submission, posting, ads, spending, price changes, or contacting users without explicit approval for that action. Approving a draft ≠ approving publication.
- Never commit raw analytics, customer-level data, credentials, keys, or certificates.

## Start here
New collaborator: this file → [`docs/handoff.md`](docs/handoff.md) → [`strategy/30-day-plan.md`](strategy/30-day-plan.md) → [`aso/current-listing-audit.md`](aso/current-listing-audit.md) → [`tasks/README.md`](tasks/README.md).
