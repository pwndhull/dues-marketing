# Claude Code Instructions — Dues Marketing

## Mission
Help grow Dues: Bill Tracker Reminder through accurate App Store optimisation (ASO), useful content, low-cost distribution, and measurable experiments. Work within the user's AUD $100/month maximum marketing budget; do not spend or activate campaigns without explicit approval.

## Workflow
1. Read this file and the relevant strategy, task, and decision documents before starting.
2. Select one scoped task from `tasks/inbox/`. If work is substantial, move it to `tasks/in-progress/` and document the intended deliverable.
3. Research using primary sources where possible. Record source URLs and date accessed.
4. Draft changes locally; inspect the diff and validate facts.
5. Update relevant task status, decision log, experiment log, and documentation in the same change.
6. Use clear, descriptive commits. Do not force-push, rewrite history, delete unrelated files, or make broad changes without approval.

## Truth and evidence
- Never invent features, integrations, pricing, privacy claims, user testimonials, ratings, review quotes, downloads, conversion rates, revenue, or experiment outcomes.
- Verify all product claims against the app, current listing, or user-provided authoritative source. If unverified, mark `NEEDS CONFIRMATION`.
- Separate facts, assumptions, hypotheses, and recommendations.
- Never imply guaranteed rankings, downloads, revenue, or conversion improvements.
- For research, capture URL, publisher, date accessed, key finding, and limitations.

## Approval gates — human approval required
Do not, without explicit approval for that exact action:
- publish or submit App Store metadata/screenshots/builds;
- post or schedule public content;
- activate ads, increase spend, or make purchases;
- change pricing, subscriptions, paywalls, product functionality, or live account settings;
- reply to reviews as the developer, contact users/influencers, or send marketing emails;
- add third-party tracking or disclose user/customer data.

Creating drafts, plans, local analyses, and pull requests is allowed.

## Analytics and privacy
- Keep raw exports in `analytics/imports/` locally; the folder is Git-ignored.
- Never commit user-level/customer-level data, email addresses, identifiers, transaction rows, or secrets.
- Commit only reviewed, aggregated metrics that do not identify individuals.
- Each report must include date range, timezone if known, source, metric definitions, comparison period, caveats, and extraction date.
- Do not claim a metric exists if the source export does not contain it.

## Content and ASO
- Do keyword research before recommending metadata changes.
- Respect App Store field limits and policies; verify current limits before finalising.
- Do not keyword-stuff, copy competitors, or use unsupported superlatives.
- Maintain separate draft and approved folders. Nothing becomes publish-ready until reviewed by the user.
- Use the app's actual name and current verified features; do not infer features from its category.

## Definition of done
A task is done only when its deliverable exists, evidence and assumptions are documented, relevant links/files are referenced, and a concise summary lists changes, validation, open questions, and next steps. Mark unknowns rather than guessing.
