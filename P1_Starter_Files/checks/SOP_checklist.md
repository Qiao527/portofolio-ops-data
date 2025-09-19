# Intake → Validation → Update — SOP Checklist (P1)

## Intake
- [ ] Receive data from source and save raw file to `data/` with date-stamped filename.
- [ ] Record dataset name, date, row count, and key fields in the brief.

## Validation
- [ ] Run **duplicate check** using key: <define key> (e.g., id or id+date+sku).
- [ ] Run **missing required fields** check: <list required fields>.
- [ ] Run **format checks** (dates, emails, phone, etc.).
- [ ] Log all issues in `checks/exception_log.csv` with action_suggested and status.

## Update
- [ ] For each issue: decide action (merge, fix, request update, defer) and note rationale in the log.
- [ ] Reconcile conflicts to a single source of truth; document final decision.
- [ ] Save cleaned output to `data/clean/` (create if needed) with version tag.
- [ ] Export 1-page brief (PDF) with counts by issue type and a simple bar chart.
