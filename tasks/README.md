# Tasks

The folder a task file is in **is** its status.

```
inbox/  →  in-progress/  →  review/  →  done/
              │
              └─ Status: Blocked — <reason, who unblocks>   (stays in in-progress/)
```

| Folder | Meaning | Who moves it |
|---|---|---|
| `inbox/` | Scoped and ready, not started | Anyone may add; user sets priority |
| `in-progress/` | Being worked on, or blocked (see Status line) | Claude or user when starting |
| `review/` | Deliverables exist; awaiting ChatGPT and/or user review | Claude when handing off |
| `done/` | Reviewed and accepted by the user | User (or Claude on user's instruction) |

Move files with `git mv` so history follows them.

## Naming and IDs
`NNN-short-slug.md`, IDs sequential and never reused. Next free ID: **006**.

## Priorities
- **P0** — blocks evidence-based decisions or fixes a live trust/compliance problem.
- **P1** — important next step once P0 evidence exists.
- **P2** — useful, not time-sensitive.

Don't add speculative busywork. A task needs a clear deliverable and a reason it matters now.

## Owners
`Claude`, `ChatGPT review`, or `User`. Mixed tasks name who does which part.

## Template
Use [`_template.md`](_template.md).

## Current tasks
| ID | Title | Priority | Owner | Folder |
|---|---|---|---|---|
| 000 | [Repository bootstrap](review/000-repository-bootstrap.md) | P0 | Claude → ChatGPT review → User | review |
| 001 | [ASO and performance baseline audit](in-progress/001-aso-baseline-audit.md) | P0 | Claude + User | in-progress (blocked on exports) |
| 002 | [Listing trust and compliance fixes](inbox/002-listing-trust-and-compliance-fixes.md) | P0 | User (Claude drafts) | inbox |
| 003 | [Keyword research per localization](inbox/003-keyword-research-per-localization.md) | P1 | Claude | inbox (blocked on keyword fields) |
| 004 | [Screenshot narrative brief](inbox/004-screenshot-narrative-brief.md) | P1 | Claude drafts, User captures | inbox |
| 005 | [Reconcile App Store listing evidence](review/005-reconcile-listing-evidence.md) | P0 | Claude → ChatGPT review → User | review |
