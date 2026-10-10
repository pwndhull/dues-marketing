# Decision 0001 — Workspace and Marketing Guardrails

**Status:** Accepted as initial operating defaults  
**Date:** 2026-10-10

## Context
The Dues marketing workflow needs a shared, reviewable source of truth for strategy, drafts, tasks, experiments, and aggregate reporting, while keeping costs low and preventing accidental publication or exposure of analytics.

## Decisions
- GitHub is the shared workspace for durable artifacts and task handoffs.
- ChatGPT is used for strategy, research briefs, prioritisation, and review.
- Claude Code is used for scoped repository work, drafting, and analysis.
- The default strategy is organic-first, with a maximum planned monthly marketing budget of AUD $100.
- No paid campaign, purchase, public post, or live App Store change occurs without explicit user approval.
- Raw analytics exports and customer-level data are not committed.
- Claims must be supported by current evidence; unknowns stay marked as unknown.
- Drafts and approved assets remain separate.

## Consequences
The workflow is auditable and low-cost but not a fully autonomous model-to-model loop. Humans must move work through review and approval gates. Any automation should be added only after its permissions, data handling, and cost are understood.
