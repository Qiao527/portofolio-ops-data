# Intake → Validation → Update — SOP (Bank Marketing)

## Dataset
- File: `bank-additional-full.csv` (or your flagged copy)
- Goal: Make data trustworthy for analysis and modeling.

## Rules

### Duplicates
- **Definition:** exact match across **all 21 columns**.
- **Action:** keep one exemplar, remove others; log representative cases.

### Required fields
- `age, job, marital, education, contact, month, day_of_week, duration, campaign, pdays, previous, poutcome, y`

### Ranges
- `age` ∈ [18, 99]
- `duration` > 0
- `campaign` ≥ 1
- `pdays` = −1 (never contacted) or ≥ 0
- `previous` ≥ 0

### Categories
- `contact` ∈ {cellular, telephone}  
- `month` ∈ {jan,feb,mar,apr,may,jun,jul,aug,sep,oct,nov,dec}  
- `day_of_week` ∈ {mon,tue,wed,thu,fri}  
- `poutcome` ∈ {nonexistent, failure, success}

### Treat `"unknown"` as missing for
- `job, marital, education, default, housing, loan`

## Process

### Intake
- Save raw file to `data/` with a date-stamped name.
- Record row/column count in the brief.

### Validation
- Add/refresh flag columns (duplicates, ranges, categories, unknowns).
- Count issues (COUNTIF or Pivot).
- Log representative rows in `checks/exception_log.csv`.

### Update
- Remove exact duplicates (keep one).
- Keep non-positive durations, under-18 ages, and `"unknown"` **flagged**; do not invent values.
- Document next steps (exclude from modeling or request updates).
- Export a 1-page brief (baseline → actions → result → recommendation).
