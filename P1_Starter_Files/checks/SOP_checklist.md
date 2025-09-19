# Intake → Validation → Update — SOP Checklist (Bank Marketing Data)

## Dataset
- File: `bank-additional-full.csv` (rows: 41188, cols: 21)
- Purpose: campaign analytics / modeling; ensure trustworthy inputs.

## Rules
**Duplicates**
- Definition: exact duplicate **across all 21 columns**.
- Action: remove duplicates (keep one exemplar), log a sample in `checks/exception_log.csv`.

**Required fields**
- age, job, marital, education, default, housing, loan, contact, month, day_of_week, duration, campaign, pdays, previous, poutcome, y

**Ranges**
- age ∈ [18, 99]
- duration > 0
- campaign ≥ 1
- pdays ∈ {999} or ≥ 0  (999 = not previously contacted)
- previous ≥ 0

**Categories**
- contact ∈ {cellular, telephone}
- month ∈ {jan,feb,mar,apr,may,jun,jul,aug,sep,oct,nov,dec}
- day_of_week ∈ {mon,tue,wed,thu,fri}
- poutcome ∈ {nonexistent, failure, success}

**Treat the literal string `"unknown"` as missing** for: job, marital, education, default, housing, loan.

## Procedure
### Intake
- [ ] Save raw file in `data/` with date-stamped name.
- [ ] Record row/column counts in brief.

### Validation (create helper columns or use the provided flagged CSV)
- [ ] Build an **all-column hash** to detect exact duplicates.
- [ ] Flag ranges and categories per rules above.
- [ ] Flag the string `"unknown"` in the six columns.
- [ ] Tally issue counts and add representative rows to `checks/exception_log.csv`.

### Update
- [ ] Remove exact duplicates (keep one).
- [ ] Do not invent values; leave invalid ranges and unknowns **flagged** until source fixes.
- [ ] Export a 1-page PDF brief with baseline → actions → results → recommendation.

## Baselines (from initial scan)
- Exact duplicate rows (to drop): **12**
- Rows involved in duplicates (pairs): **24**
- Non-positive duration: **4**
- Under-18 ages: **5** (min age: 17, max age: 98)
- "unknown" rates:
  - job: 330 (0.80%)
  - marital: 80 (0.19%)
  - education: 1731 (4.20%)
  - default: 8597 (20.87%)
  - housing: 990 (2.40%)
  - loan: 990 (2.40%)
