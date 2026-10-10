# Session Handoff

Updated at the end of every session (see [`CLAUDE.md`](../CLAUDE.md#finish-every-session)). This file holds the **latest** session; earlier versions are in Git history.

## 1. Session
- **Date:** 2026-10-10
- **Agent:** Claude Code (cloud session)
- **Branch:** `claude/zen-turing-jrudn0` (based on `main` @ `8d4f809`)
- **Objective:** Audit the repository and bootstrap it into an evidence-driven marketing workspace shared by the user, Claude Code, and ChatGPT. Mid-session the user pointed out that the App Store listing is region-specific; the audit was extended to cover each English storefront.
- **Review status:** Nobody — neither ChatGPT nor the user — has reviewed these changes yet.

## 2. Work completed (commits, oldest first)
| SHA | Summary |
|---|---|
| `118cb56` | Public listing audit, 16 storefronts, incl. regional differences (`aso/current-listing-audit.md`, `aso/competitor-research.md`) |
| `1ee5fcd` | Per-localization keyword research and listing-draft templates |
| `77c6c4c` | Collaboration protocol, operating manual, decision index, decision 0002 (proposed) |
| `3a8d245` | Task lifecycle + template; Task 001 restructured and moved to in-progress; Tasks 002–004 added |
| `cfb4e0f` | Metric dictionary, baseline export instructions, `.gitignore` hardening |
| `c11d578` | Positioning and 30-day plan updated; audience and market research added |
| `b0da459` | Experiment backlog; calendar row for missing script 001 flagged |
| `436244c` | README and CLAUDE.md rewritten; `docs/handoff.md` made mandatory |
| `87730f4` | Issue templates (task, ChatGPT review) and PR template |
| *(this commit)* | This handoff; Task 000 moved to `tasks/review/` |

## 3. Files changed
**Created:** `aso/{current-listing-audit,keyword-research,competitor-research,listing-drafts}.md` · `analytics/metric-definitions.md` · `docs/{collaboration-protocol,operating-manual,handoff}.md` · `docs/decisions/{README,0002-collaboration-protocol-and-task-lifecycle}.md` · `experiments/backlog.md` · `strategy/{audience-research,market-research}.md` · `tasks/{README,_template}.md` · `tasks/review/000-repository-bootstrap.md` · `tasks/inbox/{002,003,004}-*.md` · `.github/ISSUE_TEMPLATE/{task,chatgpt-review}.md`, `config.yml` · `.github/pull_request_template.md` · `.gitkeep` in `tasks/review/`, `content/assets/`
**Modified:** `README.md` · `CLAUDE.md` · `.gitignore` (append only) · `analytics/baseline.md` · `strategy/{positioning,30-day-plan}.md` · `content/calendar.csv` (row 1 status/note only)
**Moved:** `tasks/inbox/001-aso-baseline-audit.md` → `tasks/in-progress/` (content restructured; original steps kept)
**Unchanged (preserved):** decision 0001, `experiments/{active,results}.md`, content scripts 002/003, `.gitkeep` files.
**Deleted:** nothing.

## 4. Validation performed
These checks were actually run:
- Relative Markdown links checked with a script across all `.md` files: 0 broken after this commit (before it, only links to this file were missing).
- `content/calendar.csv` parsed with Python's `csv` module: all rows have 10 columns.
- `.gitignore` tested with `git check-ignore -v`: raw CSVs under `analytics/` ignored; `analytics/reports/*-aggregate.csv` and `content/calendar.csv` not ignored; `*.p12`, `AuthKey_*` ignored.
- Whole tree grepped for email addresses and `key/secret/token/password =` patterns: none found (apart from the commit co-author address). Only `.gitkeep` is tracked in `analytics/imports/`.
- Field lengths computed from source data: name 29/30, subtitles 28/30 and 29/30, description 3,216/4,000.
- Listing facts were cross-checked between Apple's lookup API and the product page for each storefront. Descriptions and screenshot URLs were compared by hash.
- **Not run:** there is no test suite or linter in this repo. The iPad screenshots were not reviewed. Hong Kong IAP prices could not be parsed.

## 5. Outstanding issues, assumptions, blockers
- **Blocker:** there are no analytics yet. Claude has no access to App Store Connect, subscription dashboards, Search Ads, social, or ads accounts.
- **Blocker:** the keyword field for each localization, and which storefronts use which localization, are not public.
- **Live issues (user-owned, Task 002):** the Terms of Use URL returns 404; the privacy policy is titled "BillFlow", is dated 2026-03-22, and appears narrower than the App Privacy label; screenshot 3 appears to show a real email address; the description contains a stale "NEW IN VERSION 1.1.0" section.
- **Assumption:** facts from the public listing are as of 2026-10-10. Apple may change pages at any time.
- **Assumption:** feature claims in the listing are the developer's own. None have been verified in the build.
- **Unknown:** free-plan limits, trial terms, the "works offline" and "no third-party tracking" claims, and whether "BillFlow" was a former name.
- Decision 0002 is *proposed* until the user accepts it.

## 6. Next recommended task
**Task 001 — ASO and performance baseline audit** ([file](../tasks/in-progress/001-aso-baseline-audit.md)). It needs these inputs from the user:
1. Aggregate App Store Connect exports (instructions: [`analytics/baseline.md`](../analytics/baseline.md#how-to-obtain-the-data)), by territory and by source type.
2. For each English localization: name, subtitle, keyword field, and promotional text.
3. Confirmation of which listed features are live in 1.2.0.

**Acceptance criteria:** `analytics/reports/YYYY-MM-DD-baseline.md` exists with the required report header. English storefronts are ranked using verified data. The keyword fields table in `aso/keyword-research.md` is filled. No values are fabricated, and no raw exports are committed.

Task 002 can run in parallel; it consists entirely of user actions.

## 7. Actions requiring explicit human approval
Nothing in this session required approval, and no live action was taken. Pending decisions:
- Task 002 fixes (website, privacy policy URL, screenshot replacement, description edit) are **live changes**. Only the user can make them.
- **Proposed, not added: minimal guard workflow.** A GitHub Action on `pull_request` with `permissions: contents: read`. It would fail if any file under `analytics/imports/` other than `.gitkeep` is tracked, or if the diff matches secret patterns such as `.p8` or `AuthKey_`. Cost: free on GitHub-hosted runners for normal usage. Security: read-only, no secrets, no publishing. Benefit: a second safety net beyond `.gitignore`. **Add it only if you approve.**
- Accept or amend decision 0002.

## 8. ChatGPT review prompt
```text
You are reviewing the GitHub repository pwndhull/dues-marketing, branch claude/zen-turing-jrudn0 (see its open pull request).
You cannot see Claude's conversation; rely only on the repository and sources it cites.
Read in this order: README.md, CLAUDE.md, docs/handoff.md, docs/collaboration-protocol.md, aso/current-listing-audit.md, strategy/30-day-plan.md, tasks/README.md, then tasks/review/000-repository-bootstrap.md.
Check:
1. Are the listing facts in aso/current-listing-audit.md (including the per-storefront table in section 1a) consistent with the cited Apple URLs? Flag anything stated as fact without a source.
2. Are any claims, metrics, or features presented as verified without evidence?
3. Do any files contradict each other (priorities, task status, product name, approval rules)?
4. Are tasks 001–004 the right next steps and correctly prioritised? Is anything missing or speculative?
5. Is there any privacy or security risk in the repository contents or .gitignore?
Label each point Verified / Hypothesis / Recommendation / Unknown. Do not invent metrics or search volumes.
Output: (a) blocking issues, (b) non-blocking suggestions, (c) questions for the user, (d) proposed task changes in the format of tasks/_template.md.
```
