# PROJECT DEFENSE: SUPERSTORE RETAIL PERFORMANCE DASHBOARD
**Presenter:** Emil Asqarov, Data Analyst  
**Project Context:** NexAfrica Data Analytics Internship — Final Submission  

---

## Slide 1: Executive Core KPIs Summary
- **Gross Revenue:** \$2,297,200.86
- **Net Corporate Profit:** \$286,397.02
- **Corporate Profit Margin:** 12.47%
- **Average Order Value (AOV):** \$458.61
- **Active Customer Ledger:** 793 Unique Clients
- **Total Shipped Volume:** 37,873 Units

---

## Slide 2: Data Engineering & Validation (Weeks 1 & 2)
- **Problem Statement:** Raw transaction logs suffered from inconsistent regional locale configurations and critical date parsing errors.
- **Data Cleaning Workflow:** Utilized Power Query to resolve American/European date format syntax, handle duplicate indices, and cast uniform mathematical types.
- **Calculated Fields Added:** Extracted calendar logic (`order_year`, `order_month`), and compiled automated margin metrics to stabilize core reports.

---

## Slide 3: Relational Infrastructure & Database Load (Week 3)
- **Database Architecture:** Deployed a structured SQL schema mirroring clean enterprise tables to establish a verified data source.
- **Data Engineering:** Resolved localized numeric notation barriers (converted string commas `261,96` to numeric database dots `261.96`) using PostgreSQL `ALTER TABLE` transformations.
- **Query Execution:** Loaded 9,994 transactional rows to enable sub-category and customer cohort segmentation via optimized SQL grouping scripts.

---

## Slide 4: Interactive Architecture (Week 4 Dashboard)
- **Design Philosophy:** Built a 3-page interactive visualization suite in Power BI Desktop featuring cross-filtering slicers, customized layout grids, and neutral visual boundaries.
- **Page 1 (Executive Overview):** Connects high-level KPIs with a line trend map, explicitly charting robust, predictable retail sales spikes in late Q3 and throughout Q4.
- **Page 2 (Product Performance):** Isolates Technology as the main engine (\$836K sales), backed by premium Canon Copiers, while identifying massive product capital leaks.

---

## Slide 5: Advanced Discount Elasticity Insights (Week 4 Deep-Dive)
- **DAX Implementation:** Built a dedicated `Discount Profit Margin` DAX measure to test profit health against aggressive pricing models.
- **The Core Discovery:** Proved that a 10%–20% discount structure maintains a healthy net return, but pushing past a 50% discount ceiling triggers exponential decay. At 70% and 80% off, net margin drops to a catastrophic floor of nearly -150%.

---

## Slide 6: Strategic Recommendations for Leadership
-  **Discount Cap:** Enforce a hard 30% ceiling on promotional discounts for large furniture and high-tech lines.
-  **Logistics Restructuring:** Terminate blanket free bulk shipping policies for oversized sub-categories (Tables, Bookcases) to protect net margins.
-  **Loyalty Matrix:** Implement custom account management systems for the top-tier High-Value corporate accounts that secure the baseline of net recurring revenue.
