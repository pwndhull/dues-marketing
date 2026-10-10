# Experiment Backlog

Ideas only. Nothing here is approved or active. An experiment moves to [`active.md`](active.md) only after the user approves that specific experiment, and to [`results.md`](results.md) when it ends.

Budget: AUD $100/month ceiling across all marketing. Prefer AUD $0 experiments.

## Template
```markdown
### EXP-NNN — Title
- **Status:** Idea | Ready for approval | Approved YYYY-MM-DD | Active | Ended
- **Hypothesis:** If we <change>, then <metric> will <direction> for <audience/storefront>, because <evidence>.
- **Audience / market / localization:**
- **Single variable changed:**
- **Primary metric (definition link) and source:**
- **Baseline (value, period, source):** must exist before approval
- **Comparison method:** before/after (weak) | Product Page Optimization A/B | holdout | other
- **Duration and minimum sample:**
- **Stop condition:**
- **Estimated total cost (AUD):**
- **Risks / confounders:** releases, seasonality, other metadata changes, small samples
- **Decision this informs:**
- **Approval:** not requested / requested YYYY-MM-DD / granted YYYY-MM-DD by user
```

## Ideas
Each depends on the Task 001 baseline; none can be evaluated without it.

### EXP-001 — Captioned screenshots in one localization
- **Status:** Idea
- **Hypothesis:** Captioned screenshots showing verified features with realistic demo data will raise impressions→download conversion in the chosen storefront, because current screenshots are uncaptioned and show overdue bills and unusual number formatting ([audit §3](../aso/current-listing-audit.md#3-screenshots--verified-public)).
- **Comparison method:** Apple Product Page Optimization if eligible (NEEDS CONFIRMATION), otherwise before/after with stated weakness.
- **Estimated cost:** AUD $0. **Depends on:** Tasks 001, 002, 004.

### EXP-002 — Subtitle positioning (split bills vs bill reminders)
- **Status:** Idea
- **Hypothesis:** A subtitle aligned with the most-searched verified use case in a storefront will increase search impressions/conversion there.
- **Note:** the US vs other-region subtitle difference already exists but is **not** a controlled test — markets differ in price, competition, and size.
- **Estimated cost:** AUD $0. **Depends on:** Tasks 001, 003.

### EXP-003 — Promotional text
- **Status:** Idea
- **Hypothesis:** Adding promotional text (currently empty) describing the 1.2.0 shared-bills update will not hurt and may help conversion; low risk because promo text can be changed without a new build.
- **Estimated cost:** AUD $0. **Depends on:** Task 001 baseline.
