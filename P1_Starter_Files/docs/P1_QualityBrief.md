# P1 — Data Quality Audit (Records → Insights → Recommendation)

**Problem:** Bank marketing table contains exact duplicate rows, non-positive call durations, under-18 ages, and “unknown” values in key attributes.  

**Why it matters:** Bad or ambiguous data skews campaign reporting, model training, and segment performance tracking  

**Metric (success):** Remove exact duplicates; flag all non-positive durations; flag under-18; quantify and isolate “unknown” values; publish exception log + checklist.  

**Data:** `bank-additional-full.csv` (41,188 rows, 21 cols).  


---

## Scope & Rules
- **Duplicates:** define key = <e.g., student_id or order_id + date + sku>  
- **Missing (required):** <list required fields>  
- **Invalid format:** <e.g., date, email, phone pattern>

## Deliverables
- `checks/exception_log.csv` (running log of issues, actions, status)  
- `checks/SOP_checklist.md` (intake → validation → update)  
- 1-page brief (this file exported to PDF) with a simple issues chart
