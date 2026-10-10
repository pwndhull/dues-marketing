# Operating Manual

Detailed procedures referenced from [`CLAUDE.md`](../CLAUDE.md). For how the user, Claude, and ChatGPT hand work to each other, see [`collaboration-protocol.md`](collaboration-protocol.md).

## 1. Session start checklist
1. `git status`, `git branch --show-current`, `git log --oneline -10`. Stop and ask if there are uncommitted changes you didn't make.
2. Read `README.md` → `CLAUDE.md` → `strategy/30-day-plan.md` → `tasks/in-progress/` → `tasks/review/` → `tasks/inbox/` (P0 first).
3. Read the decisions index `docs/decisions/README.md` for anything affecting the task.
4. Read the specific files the chosen task links.

## 2. Choosing and running a task
- Pick the highest-priority unblocked task in `tasks/in-progress/` first, then `tasks/inbox/`. Prefer tasks that unblock evidence-based decisions.
- Move the file with `git mv` to `tasks/in-progress/` and set Status. One task at a time unless they're trivially related.
- If blocked, keep it in `in-progress/` with `Status: Blocked — <what, who resolves it>` and pick another task.
- Work in small commits. Update the task's checklist as you go.

## 3. Recording research
For each important finding, record in the deliverable's Sources table:

| ID | URL | Publisher | Accessed (YYYY-MM-DD) | What it establishes | Market / locale | Limitations |
|---|---|---|---|---|---|---|

Then label statements per [collaboration protocol §3](collaboration-protocol.md#3-evidence-labels). Prefer primary sources (Apple developer docs, the live listing, App Store Connect exports, the build itself). Secondary blogs are context, not proof.

## 4. Keeping documentation current
In the same change as the work:
- Update the task file (status, checklist, handoff).
- Update any doc the work makes stale (positioning, plan, baseline, listing audit).
- Add a decision record when a choice will constrain future work.
- Update `experiments/` if an experiment's state changes.
- Keep `README.md` "Current status" accurate when priorities change.

## 5. Analytics workflow
1. User exports from App Store Connect (instructions in [`analytics/baseline.md`](../analytics/baseline.md)) and places files in `analytics/imports/` locally — or pastes aggregate numbers into a PR/issue.
2. Claude reads, aggregates, and writes a report in `analytics/reports/YYYY-MM-DD-<topic>.md` using the report header in [`metric-definitions.md`](../analytics/metric-definitions.md).
3. Before committing: `git status` must show no files under `analytics/imports/` (except `.gitkeep`); `git diff --cached` inspected for emails, IDs, transaction rows, keys. Only aggregates.
4. Never fill in a missing value. Write "Not in export".

## 6. ASO workflow
Order is fixed; don't skip steps:
1. Current listing audit, per localization → [`aso/current-listing-audit.md`](../aso/current-listing-audit.md)
2. Feature verification in the build (user confirmation)
3. Keyword research, per localization → [`aso/keyword-research.md`](../aso/keyword-research.md)
4. Competitor evidence, per storefront → [`aso/competitor-research.md`](../aso/competitor-research.md)
5. Drafts with reasoning, risks and measurement plan → [`aso/listing-drafts.md`](../aso/listing-drafts.md)
6. User review → user approval → **separate** explicit approval to submit, performed by the user.

Change one localization's metadata at a time where possible so effects can be read per territory.

## 7. Content workflow
1. Idea → row in [`content/calendar.csv`](../content/calendar.csv) with `status=Idea`, hypothesis and metric.
2. Draft → `content/scripts/NNN-slug.md` (`status=Draft`, `approval=Not approved`). Real app UI only; demo data only; no unverified claims, statistics, or financial advice.
3. Raw production assets → `content/assets/` (no personal data, no real user data).
4. User approves → copy final to `content/approved/` and set `approval=Approved YYYY-MM-DD`.
5. Posting/scheduling is a separate approval and is done by the user. Record `status=Posted YYYY-MM-DD` and the URL.

Calendar `status` values: `Idea`, `Draft`, `In review`, `Approved`, `Posted`, `Dropped`.

## 8. Experiment workflow
See [`experiments/backlog.md`](../experiments/backlog.md) for the template. Backlog → (user approval) → `active.md` → `results.md`. Any paid proposal needs: hypothesis, audience/market, estimated total AUD cost, success metric, baseline, duration, stop condition, risks, and the decision it informs — and explicit approval before activation. Monthly total must stay ≤ AUD $100.

## 9. Finishing a task
1. Validate: links resolve, numbers trace to sources, no fabricated values, no sensitive data in `git diff`.
2. Fill the task's Handoff section and move it to `tasks/review/`.
3. Commit, push, open/update a draft PR.
4. Report using the end-of-session summary in [collaboration protocol §8](collaboration-protocol.md#8-end-of-session-summary-substantial-sessions).
5. The user moves it to `tasks/done/` after review (or asks Claude to).

## 10. Automation policy
No GitHub Actions, scheduled jobs, API keys, paid APIs, or third-party tracking without: stated need, cost, security implications, least-privilege permissions, and user approval. No automation may publish content, alter the App Store, or spend money. No continuous model-to-model agent.
