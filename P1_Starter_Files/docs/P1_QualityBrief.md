# P1 — Data Quality Audit (Records → Insights → Recommendation)

**Problem:** <one sentence on the messy/duplicate/missing data problem and where it shows up>  

**Why it matters:** <impact on accuracy, reporting, downstream ops, or decision-making>  

**Metric (success):** <e.g., duplicate rate ↓; 100% of required fields populated; time-to-clean < 30 min>  

**Data:** <dataset name/source; ~row count; key fields/IDs>  

**Deadline:** <2025-09-19>

---

## Scope & Rules
- **Duplicates:** define key = <e.g., student_id or order_id + date + sku>  
- **Missing (required):** <list required fields>  
- **Invalid format:** <e.g., date, email, phone pattern>

## Deliverables
- `checks/exception_log.csv` (running log of issues, actions, status)  
- `checks/SOP_checklist.md` (intake → validation → update)  
- 1-page brief (this file exported to PDF) with a simple issues chart
