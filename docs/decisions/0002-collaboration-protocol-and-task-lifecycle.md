# Decision 0002 — Collaboration Protocol, Task Lifecycle, Per-Localization ASO

**Status:** Proposed — awaiting user acceptance (merge of the bootstrap PR counts as acceptance unless the user says otherwise)
**Date:** 2026-10-10
**Decided by:** user (proposed by Claude Code)

## Context
Decision [0001](0001-workspace-and-guardrails.md) established GitHub as the shared workspace but did not define how Claude and ChatGPT hand work to each other, how tasks move, or where status lives. The 2026-10-10 listing audit ([`aso/current-listing-audit.md`](../../aso/current-listing-audit.md) §1a) found that the App Store listing differs by region (the US subtitle differs from AU/GB/CA and others; prices differ per storefront), so treating the listing as a single global entity would produce wrong keyword work.

## Decision
1. Collaboration follows [`docs/collaboration-protocol.md`](../collaboration-protocol.md): repo-only handoffs, evidence labels, ChatGPT proposals verified before implementation.
2. Task lifecycle is folder-based: `inbox → in-progress → review → done`, with `Blocked` as a status inside `in-progress/` ([`tasks/README.md`](../../tasks/README.md)). Priorities P0/P1/P2.
3. ASO evidence, keyword research, competitor research, and drafts are recorded **per localization / storefront**.
4. Every session ends by updating `docs/handoff.md` (instructed by the user on 2026-10-10).
5. No GitHub Actions workflows are added during bootstrap. A minimal read-only guard workflow is proposed in the bootstrap handoff for the user to accept or reject.

## Alternatives considered
- GitHub Issues/Projects as the task system: richer UI, but ChatGPT reads files more reliably than project boards, and folder state is visible in every clone. Issue templates are provided for intake; the task file remains canonical.
- A single global keyword list: simpler, but contradicted by the observed regional listing.

## Consequences
- Status is visible from the file tree; moving a file is a status change and appears in history.
- More files for ASO work (per localization), in exchange for accuracy.
- Revisit if the volume of tasks makes folders hard to scan, or if a model gains reliable direct repo-integrated task tooling.
