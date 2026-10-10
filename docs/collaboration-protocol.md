# Collaboration Protocol — User, Claude Code, ChatGPT

GitHub is the only shared memory. Claude and ChatGPT **cannot message each other** and **do not see each other's conversations**. Anything not written in this repository (or a cited, verifiable source) must be treated as unknown by the other party.

## 1. Roles
| Party | Does | Does not |
|---|---|---|
| **User** (repo owner) | Sets priorities; provides account exports and confirmations; approves or rejects; performs every live action (App Store Connect, posting, spending) | — |
| **Claude Code** | Executes scoped tasks in the repo: research, drafts, analysis of user-provided aggregate data, documentation, commits, PRs | Publish, submit, spend, contact anyone, change live settings |
| **ChatGPT** | Reviews repo state and handoffs; challenges evidence and reasoning; proposes changes as task suggestions | Treat its suggestions as verified facts; edit history |

## 2. Shared source of truth
| Topic | Lives in | Notes |
|---|---|---|
| Strategy, positioning, plan | `strategy/` | `30-day-plan.md` holds current priorities |
| Policies and procedures | `docs/` | This file; [`operating-manual.md`](operating-manual.md) |
| Tasks and status | `tasks/` | Folder = status. See [`tasks/README.md`](../tasks/README.md) |
| Verified metrics | `analytics/` | Aggregates only; raw exports stay local in `analytics/imports/` |
| Listing evidence and drafts | `aso/` | Per localization |
| Content drafts / approved | `content/scripts/`, `content/approved/` | |
| Experiments | `experiments/` | backlog → active → results |
| Decisions | `docs/decisions/` | Numbered, never rewritten — superseded instead |
| App code, release docs, 2.0 listing text | `pwndhull/Easy-bills-ios` (read-only for marketing work) | Overlaps this repo; ownership pending [decision 0003](decisions/0003-marketing-source-of-truth-across-repositories.md) |

If a fact is not in the repository or a cited source, do not assume the other model knows it. Conversational claims ("I think the app has X") are not evidence until recorded with a source.

## 3. Evidence labels
Every important statement in a deliverable carries one of:
- **Verified fact** — with source URL, publisher, date accessed, locale, and limitation.
- **User-provided** — with date and where it was provided (e.g. "user, PR comment 2026-10-12").
- **Hypothesis** — a testable belief; state how it could be tested.
- **Recommendation** — an action, linked to the evidence above.
- **Unknown / NEEDS CONFIRMATION** — say who can resolve it.

Never invent features, integrations, downloads, revenue, conversion rates, rankings, testimonials, ratings, review quotes, search volume, keyword difficulty, competitor data, or experiment results. Correlation is not causation.

## 4. Task handoff format
Every meaningful task file (see [`tasks/_template.md`](../tasks/_template.md)) includes: ID and title · priority · owner · status · objective and business reason · current state and file links · evidence and source URLs · constraints · deliverables and acceptance criteria · open questions and assumptions · approval requirements · next recommended action.

## 5. Handoff to ChatGPT for review
When Claude finishes work that needs review:
1. Move the task file to `tasks/review/` (or create a short handoff file there for multi-task sessions).
2. Add a **Handoff** section: what changed (file links) · why · evidence · what specifically needs review · open questions · next step.
3. Open or update a pull request; the PR description links the handoff.
4. Include a copy-paste prompt for ChatGPT (template below).

**ChatGPT review prompt template**
```text
You are reviewing the GitHub repository pwndhull/dues-marketing (branch: <branch>, PR: <url>).
Read in this order: README.md, CLAUDE.md, docs/collaboration-protocol.md, then <handoff file>, then the files it links.
Review for: factual accuracy against cited sources, unsupported claims, missing evidence, contradictions between files, privacy risks, and whether the next task is the right one.
Rules: GitHub is the source of truth; do not assume facts not in the repo; label each point as Verified / Hypothesis / Recommendation / Unknown; do not invent metrics or search volumes.
Output: (1) blocking issues, (2) non-blocking suggestions, (3) questions for the user, (4) proposed task changes written in the format of tasks/_template.md so Claude can implement them.
```

## 6. Handoff from ChatGPT back to Claude
ChatGPT's output reaches the repo only through the user: as a PR review comment, an issue (use the "ChatGPT review" issue template), or a task file added to `tasks/inbox/`.

Before implementing any ChatGPT proposal, Claude must:
1. `git status` and check the current branch and latest commits.
2. Read the files the proposal refers to **as they are now** — they may have changed since ChatGPT read them.
3. Verify factual claims in the proposal against sources; treat unsourced claims as hypotheses.
4. Record in the task file which suggestions were accepted, rejected (with reason), or need the user.

## 7. Preventing conflicting work
- One task file per meaningful unit of work; one branch/PR per task where practical.
- Do not modify files outside the task's scope without saying so in the handoff.
- Check `git status` and `git diff` before starting and before committing.
- Avoid two parties editing the same file at once; the task in `tasks/in-progress/` "owns" the files it lists.
- Never force-push, rewrite shared history, or discard uncommitted user changes without explicit approval.
- Small, descriptive commits (`area: what changed`).
- Never mark a task done until its deliverables exist and validation is recorded.

## 8. End-of-session summary (substantial sessions)
**Every session ends by updating [`docs/handoff.md`](handoff.md)** (user instruction, 2026-10-10) with: session date and objective; work completed with commit SHAs; files changed and validation performed; outstanding issues, assumptions and blockers; next recommended task with acceptance criteria; actions requiring explicit human approval. It is committed with the related work, stays factual (no "tests passed" unless run), and never contains secrets, customer data, or raw analytics. It replaces the previous session's entry; history is in Git. Never assume ChatGPT or another AI has reviewed changes unless the repo records that review.

Also update the task file, then report:
1. What was completed
2. Files created or modified
3. Evidence gathered and sources
4. Validation performed
5. Decisions made (and decision records added)
6. Questions requiring the user's input
7. Next recommended task
8. A ready-to-use ChatGPT review prompt, when useful

Don't create reports for trivial interactions; link to existing documents instead of repeating them.
