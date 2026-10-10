# Dues — Marketing Workspace

Shared workspace for planning, executing, and measuring marketing for **Dues: Bill Tracker Reminder** (App Store ID: 6761047973).

## Operating model

- **ChatGPT:** strategy, research briefs, prioritisation, and review.
- **Claude Code:** scoped implementation, content drafts, documentation, and analysis.
- **GitHub:** source of truth for tasks, approved copy, experiments, decisions, and reviewed aggregate reports.

This repository is a handoff workspace, not a continuous autonomous conversation between models. Every task should have a clear owner, deliverable, and approval status.

## Guardrails

- Never invent app features, testimonials, ratings, download counts, revenue, or experiment results.
- Label assumptions and hypotheses clearly; cite sources for external research and note the date checked.
- Do not publish App Store metadata, post content, start ads, spend money, or change live accounts without explicit human approval.
- Do not commit raw analytics exports, customer-level data, credentials, API keys, certificates, or private reports.
- Prefer low-cost, organic-first growth. Monthly marketing spend ceiling: **AUD $100**, subject to explicit approval before any spend.
- Keep drafts separate from approved assets. Approval in GitHub does not itself authorize publishing.

## Start here

1. Read [Claude instructions](CLAUDE.md).
2. Review [positioning](strategy/positioning.md) and the [30-day plan](strategy/30-day-plan.md).
3. Start with the ASO audit task in `tasks/inbox/`.
4. Add current metrics only from verified App Store Connect / subscription analytics exports; keep raw files local and use aggregate summaries in `analytics/reports/`.
5. Record every experiment, its hypothesis, metric, dates, result, and decision under `experiments/`.

## Repository structure

- `strategy/` — positioning and marketing plan
- `tasks/inbox/`, `tasks/in-progress/`, `tasks/done/` — task workflow
- `aso/` — keyword research and listing drafts
- `content/` — calendar, scripts, and approved assets
- `analytics/imports/` — local-only raw exports (Git-ignored)
- `analytics/reports/` — reviewed aggregate reports
- `experiments/` — active tests and outcomes
- `docs/decisions/` — dated decisions and rationale

## Status

Initial workspace setup. Baseline performance and product claims are intentionally marked as unknown until verified.
