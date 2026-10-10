# Claude Code Instructions — Dues Marketing

## Mission
Grow **Dues: Bill Tracker & Reminder** (iOS, App Store ID `6761047973`) — qualified impressions, product-page conversion, downloads, and sustainable subscription revenue — through accurate ASO, useful content, and low-cost measurable experiments in English-speaking markets, prioritised by verified data. Marketing budget ceiling: **AUD $100/month**; never spend without explicit approval. Never promise rankings, downloads, conversion, or revenue.

## Sources of truth
| What | Where |
|---|---|
| Current priorities | [`strategy/30-day-plan.md`](strategy/30-day-plan.md) |
| Strategy | `strategy/` (positioning, audience, market) |
| Tasks and status | `tasks/` — folder = status ([lifecycle](tasks/README.md)) |
| Verified metrics | `analytics/` ([definitions](analytics/metric-definitions.md), [baseline](analytics/baseline.md)) |
| Listing evidence and drafts | `aso/` — **per localization**; the live listing differs by region |
| Content | `content/` (drafts in `scripts/`, approved in `approved/`) |
| Experiments | `experiments/` (backlog → active → results) |
| Decisions | [`docs/decisions/`](docs/decisions/README.md) |
| Procedures | [`docs/operating-manual.md`](docs/operating-manual.md) |
| Collaboration with ChatGPT | [`docs/collaboration-protocol.md`](docs/collaboration-protocol.md) |
| Latest session handoff | [`docs/handoff.md`](docs/handoff.md) |
| App code and release docs (read-only evidence) | `pwndhull/Easy-bills-ios`, `pwndhull/Easy-bills-web` — see below and [decision 0003](docs/decisions/0003-marketing-source-of-truth-across-repositories.md) |

## Start every session
1. `git status`, current branch, `git log --oneline -10`. Never discard uncommitted changes you didn't make — ask.
2. Read `docs/handoff.md`, then `strategy/30-day-plan.md`, then `tasks/in-progress/`, `tasks/review/`, `tasks/inbox/`.
3. Read every file the chosen task links. Don't rely on memory of earlier sessions or on what ChatGPT "said" — only on what is in the repo or a cited source.

## Execute a task
- One task at a time; highest unblocked priority first. `git mv` it to `tasks/in-progress/`, set Status. Blocked → `Status: Blocked — reason, who unblocks`.
- Treat ChatGPT proposals as hypotheses: re-read current files, verify claims, then implement.
- Small commits (`area: what changed`); don't touch unrelated files; never force-push or rewrite history.
- Detail: [operating manual §2](docs/operating-manual.md#2-choosing-and-running-a-task).

## Evidence
- Record for each finding: URL, publisher, date accessed, what it establishes, locale, limitations.
- Label statements: **Verified fact / User-provided / Hypothesis / Recommendation / Unknown (NEEDS CONFIRMATION)**.
- Never invent features, integrations, pricing, privacy claims, testimonials, ratings, review quotes, downloads, revenue, conversion, rankings, search volume, keyword difficulty, competitor data, or experiment results. Correlation ≠ causation.
- Use only verified features; don't infer from the category.

## App repositories (read-only evidence)
- `pwndhull/Easy-bills-ios` holds the app code, its own marketing plan (`docs/PLAN.md`, `docs/strategy/`), the 2.0 listing (`fastlane/metadata/`), and screenshot tooling. `pwndhull/Easy-bills-web` is a static site. Feature checks: [`aso/feature-verification.md`](aso/feature-verification.md).
- Read only; never push to them from marketing work. Cite them as repo + path + commit SHA.
- `main` is **not** the live build. Check what shipped (1.2.0 ≈ `4c2f062`, NEEDS CONFIRMATION) before treating a feature as live.
- Code evidence is not runtime evidence. Docs written in the app repo are user-provided, not verified.
- Never copy secrets, config files (e.g. `GoogleService-Info.plist`), personal emails, names, or user data from them.
- Where the app repo plan conflicts with this repo's guardrails (budget, approvals, targets), flag it to the user; don't silently follow either.

## Keep docs current (same change as the work)
Task file · any doc made stale (plan, positioning, listing audit, baseline) · decision record if the choice constrains future work · experiment files · README status if priorities changed.

## Analytics and privacy
Raw exports only in `analytics/imports/` (Git-ignored). Commit only reviewed aggregates. Before every analytics commit inspect `git diff --cached` for emails, IDs, transaction rows, keys. Never fill missing values. Every report uses the header in [`metric-definitions.md`](analytics/metric-definitions.md#report-header-required-for-every-report-in-analyticsreports). Claude has **no** App Store Connect, subscription-dashboard, social, or ads access unless the user grants it in-session.

## ASO and content
Order: verify listing (per localization) → verify features → keyword research → competitor evidence → drafts with reasoning, risks, measurement → user review. Respect current Apple limits (re-verify). No keyword stuffing, competitor names, or unsupported superlatives. Drafts and approved assets stay separate.

## Approval gates — explicit user approval for that exact action
- Submit/publish App Store metadata, screenshots, builds, or Product Page tests
- Post or schedule public content
- Activate ads, increase spend, buy anything, subscribe to tools
- Change pricing, subscriptions, paywalls, product functionality, or live account/website settings
- Reply to reviews as the developer; contact users, influencers, or press; send marketing email
- Add third-party tracking, API keys, scheduled jobs, or GitHub workflows; disclose user data

Drafts, research, local analysis, commits, and draft PRs are allowed. **Approval of a draft is not approval to publish it.**

## Finish every session
1. Validate: links resolve, numbers trace to sources, no fabricated values, no sensitive data in the diff. Don't claim checks passed unless you ran them.
2. Update the task file (Handoff section) and move it to `tasks/review/` if ready.
3. **Update [`docs/handoff.md`](docs/handoff.md)** — session date and objective; work completed with commit SHAs; files changed and validation performed; outstanding issues, assumptions, blockers; next recommended task with acceptance criteria; actions needing explicit human approval. Factual only; commit it with the related work. Assume nobody (including ChatGPT or another AI) has reviewed the changes unless the repo records it.
4. Push, open/update a draft PR, and report to the user using [collaboration protocol §8](docs/collaboration-protocol.md#8-end-of-session-summary-substantial-sessions), including a ChatGPT review prompt when useful.

A task is **done** only when its deliverable exists, evidence and assumptions are documented, and the user has accepted it.
