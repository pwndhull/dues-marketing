# Decision 0003 — Marketing Source of Truth Across Repositories

**Status:** Proposed — **needs the user's choice** (no option has been adopted)
**Date:** 2026-10-10
**Decided by:** user (proposed by Claude Code, [Task 006](../../tasks/review/006-reconcile-with-app-repositories.md))

## Context
On 2026-10-10 the user pointed Claude to the app repositories (`pwndhull/Easy-bills-ios`, `pwndhull/Easy-bills-web`). The iOS repo already contains substantial marketing work that this repository didn't know about:
- `docs/PLAN.md` describes itself as "the source of truth". It is a 12-week plan (5 Oct – 27 Dec 2026) with numeric targets and weekly tasks.
- `docs/strategy/ACQUISITION.md`, `DISTRIBUTION.md` and `ROADMAP.md` cover per-locale ASO sets, Reddit, SEO pages, video, Custom Product Pages, an Apple Ads test, referrals and partnerships.
- `docs/APP-STORE-LISTING.md` and `fastlane/metadata/` hold the 2.0 listing for 12 locales, entered in App Store Connect.
- `tools/aso/` and `marketing/promo-video` hold screenshot and video tooling. `website/` holds a Firebase-hosted site with SEO tax-deadline pages.

The two repositories now overlap and **conflict** on several points:

| Topic | This repo | App repo (`docs/PLAN.md`, `ACQUISITION.md`) |
|---|---|---|
| Targets | None until a verified baseline; any target is a hypothesis | 1,000–1,500 installs, 200+ WAU, 25% D7 retention, 4.4★ with 40+ ratings, 20+ subscribers by 27 Dec. It does say "the week 1 baseline replaces any guess" |
| Paid spend | AUD $100/month ceiling, explicit approval per spend | Apple Ads "$10/day for 14 days = $140 per country test" (currency not stated). A single test exceeds AUD $100/month |
| Outreach | Contacting users, creators or press needs explicit approval for that action | Plan schedules emailing paying users, creator outreach and community posting |
| ASO | Audit → verify → keyword evidence → drafts → review | 2.0 per-locale metadata already written and entered in App Store Connect |
| Screenshots | Task 004 brief | Already planned, scripted, and partly uploaded for 2.0 |

The app repo's plan is the user's own plan, so its actions are the user's to take. The conflicts matter because this repo's rules (budget, approvals, no targets) are also the user's own stated constraints, and both repos claim to be the source of truth.

## Options
1. **App repo owns the marketing plan; this repo is the evidence and review layer.** Strategy and tasks stay in `Easy-bills-ios/docs/`. This repo holds audits, baselines, verification, experiment records and ChatGPT reviews, and links to the app repo plan. Least duplication; the app repo is private and mixes code with marketing.
2. **This repo owns marketing; the app repo keeps only release and engineering docs.** Marketing parts of `PLAN.md` and `ACQUISITION.md` move here (or are frozen with a pointer). One marketing home that ChatGPT can review without code; requires a migration and changing the app repo's working habits.
3. **Split by type.** Engineering and release (fastlane metadata, screenshots tooling, website code) stay in the app repo. Plan, priorities, budget, experiments and metrics live here. Each repo links to the other, and conflicts are resolved in favour of this repo's guardrails.

Whatever is chosen, the budget conflict (Apple Ads test vs AUD $100/month) needs a separate explicit decision: raise the ceiling for that test, shorten or shrink the test, or defer it.

## Recommendation (Claude)
Option 3. It keeps working release tooling where it is, gives one place for priorities and guardrails, and avoids migrating code-adjacent files. This is a recommendation only.

## Consequences
Until the user decides, this repository treats the app repo as a **read-only evidence source** (see [`CLAUDE.md`](../../CLAUDE.md)). It does not duplicate the app repo's plan, and it flags conflicts rather than resolving them.
