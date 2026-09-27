# Retail Sales Analytics Dashboard

## Week 1: Data Preparation & Business Understanding

---

### Step 1: Business Problem Statement
The primary purpose of this analysis is to evaluate retail sales performance, customer purchasing behavior, and product profitability trends. By transforming raw, messy transactional records into a structured dataset, this project aims to provide company management with data-driven insights. The analysis will identify key sales trends, pinpoint high-performing product categories, highlight high-value customer segments, and surface operational gaps or underperforming areas requiring strategic attention.

---

### Step 2: Dataset Inspection & Data Dictionary

#### Dataset Metrics Summary
- **Number of Rows:** 9,994 (fully verified)
- **Number of Columns:** 23 (including 2 engineered fields)
- **Date Range:** 2014 – 2017 (or dynamic based on the active Superstore version)

#### Data Dictionary & Data Type Verification
The table below logs the structural inspection of the fields, verifying their transition from raw text format to standardized analytical types:

| Column Name | Raw Data Type (CSV) | Cleaned Target Type | Description | Status / Action Taken |
| :--- | :--- | :--- | :--- | :--- |
| **Row ID** | Text / Int | **Integer** | Unique identifier for each transaction row. | Verified as a valid whole number. |
| **Order ID** | Text | **Text** | Unique identifier for each customer order. | Maintained as text format. |
| **Order Date** | Text (MM/DD/YYYY) | **Date** | The date when the order was placed. | Converted from Text to Date via US Locale. |
| **Ship Date** | Text (MM/DD/YYYY) | **Date** | The date when the order was shipped. | Converted from Text to Date via US Locale. |
| **Ship Mode** | Text | **Text** | Shipping method chosen by the customer. | Validated standard text strings. |
| **Customer ID** | Text | **Text** | Unique identifier for the customer. | Maintained as text format. |
| **Customer Name**| Text | **Text** | Full name of the customer. | Cleaned trailing or leading spaces. |
| **Segment** | Text | **Text** | Market segment (Consumer, Corporate, etc.). | Validated unique categories. |
| **Country** | Text | **Text** | Geographic country of the transaction. | Validated unique locations. |
| **City** | Text | **Text** | Geographic city of the transaction. | Verified spelling and formatting. |
| **State** | Text | **Text** | Geographic state of the transaction. | Validated regional attributes. |
| **Postal Code** | Text / Int | **Text** | Postal code for the delivery location. | Forced to Text to preserve leading zeros. |
| **Region** | Text | **Text** | Broad sales region (East, West, etc.). | Standardized categorical text format. |
| **Product ID** | Text | **Text** | Unique identifier for the product SKU. | Maintained as alphanumeric text. |
| **Category** | Text | **Text** | Broad product category (Technology, etc.). | Validated unique core categories. |
| **Sub-Category**| Text | **Text** | Specific product sub-category (Phones, etc.).| Validated unique sub-categories. |
| **Product Name**| Text | **Text** | Full descriptive name of the product. | Maintained text strings. |
| **Sales** | Text / Decimal | **Decimal** | Revenue generated from the item sale. | Converted to decimal via US Locale. |
| **Quantity** | Text / Int | **Integer** | Number of units sold in the transaction. | Forced to whole number format. |
| **Discount** | Text / Decimal | **Decimal** | The percentage of discount applied. | Converted to decimal via US Locale. |
| **Profit** | Text / Decimal | **Decimal** | Net monetary gain or loss. | Preserved negative signs via US Locale. |

---

### Step 3: Data-Cleaning Documentation & Log

Data extraction, transformation, and cleaning were successfully performed using **Excel (Power Query)** based on the following professional logic:
1. **Handling Missing Values:** Audited the entire dataset using the *Column Quality* tool. The columns showed 100% validity; no system `null` values or blank transactional fields were present.
2. **Handling Duplicates:** Performed a strict duplicate check on the primary key `Row ID` using the *Remove Duplicates* feature. All 9,994 transaction records were confirmed unique, preserving data integrity.
3. **Fixing Incorrect Data Types:** Resolved formatting conflicts caused by regional system settings. Text dates and currency fields using dot-separators (`.`) were correctly forced into `Date` and `Decimal Number` formats by applying **English (United States) Locale** rules to prevent parsing errors (`Errors`).
4. **Data Consistency Check:** Reviewed unique values in `Category`, `Sub-Category`, and `Region` columns via filter distributions to ensure no inconsistent naming conventions or spelling anomalies existed.

---

### Step 4: List of Calculated Fields (Feature Engineering)

The following calculated attributes were implemented during the preparation phase or documented for the upcoming analysis week:
1. **Year:** Extracted from `Order Date` using Power Query date functions (`Date.Year`) to enable annual trend slicing.
2. **Order Month:** Extracted from `Order Date` as an explicit English text name using the `Date.MonthName([Order Date], "en-US")` function to support global seasonality profiling.
3. **Profit Margin (Planned for Week 2):** Mathematically defined as `(Profit ÷ Sales) × 100` to evaluate item and category profitability ratios.
4. **Average Order Value (Planned for Week 2):** Defined as `Total Sales ÷ Distinct Count of Orders` to measure customer transaction sizes.


---

## Week 2: Exploratory Data Analysis (EDA) & Business Insights

### 1. Executive Core KPIs Summary
- **Total Sales:** $2,297,200.86
- **Total Profit:** $286,397.02
- **Total Quantity Sold:** 37,873 units
- **Total Unique Orders:** 5,009 orders
- **Total Unique Customers:** 793 clients
- **Overall Business Profit Margin:** 12.47%
- **Average Order Value (AOV):** $458.61

---

### 2. Deep-Dive Business Insights (Minimum 5 Insights)

#### Insight 1: Strong Q4 Seasonality Trend
The monthly sales trend chart reveals a consistent, powerful spikes in revenue during the fourth quarter (Q4) of every fiscal year, specifically in **November and December**. This trend is driven by holiday shopping seasons and year-end corporate budget clearouts. Management should optimize inventory levels and increase marketing spend starting in late September to capture this predictable demand.

#### Insight 2: Regional Performance Disparity (West vs. Central)
The **Western Region** is the absolute company powerhouse, generating the highest sales ($725,457.82), the largest net profit ($108,418.45), and a stellar profit margin of **14.94%**. Conversely, the **Central Region** represents a severe operational bottleneck. While it drives substantial sales volume ($501,239.90), it generates the lowest net profit ($39,706.36) and an underperforming profit margin of only **7.92%**, indicating aggressive discounting or high shipping/logistical costs.

#### Insight 3: High-Risk Underperforming Products (The Cubify Deficit)
Product-level analysis exposes extreme vulnerability in specific SKUs. The **"Cubify Cube 3D Printer, 2nd Generation"** is the company's single worst-performing asset, responsible for a staggering net loss of nearly **-$9,000**. Selling complex high-tech hardware without proper margin controls or incurring high return rates is heavily damaging overall corporate profitability.

#### Insight 4: Category Profitability Anchor (Technology)
The category share analysis indicates that **Technology** remains the healthiest driver of corporate value. Backed by high-ticket items like the **"Canon imageCLASS CLASS 2200 Advanced Copier"** (which is the #1 top-earning product bringing over $25,000 in net profit), Technology secures stable profit margins that subsidize weaker organizational divisions.

#### Insight 5: The Furniture Margin Trap
While the **Furniture** category accounts for a massive slice of the category chart, a secondary filter audit reveals that specific sub-categories, such as **Tables and Bookcases**, operate at a net loss. This indicates a "Margin Trap" where high sales volumes create an illusion of success, but low price points, high bulk shipping rates, and heavy seasonal discounts ultimately destroy net returns.


---

## Week 3: Product & Customer Analysis (SQL & PostgreSQL)

### PART A — PRODUCT ANALYSIS
Based on the execution of analytical SQL queries, here are the structured findings and answers to the core business questions:

#### 1. Core Product Questions Answered:
- **Which product generates the most sales?** 
  The **"Canon imageCLASS 2200 Advanced Copier"** is the absolute revenue leader, generating massive sales across regions.
- **Which product generates the most profit?** 
  The **"Canon imageCLASS 2200 Advanced Copier"** is also the most profitable item, netting over **\$25,000** in clean profit.
- **Which products have negative profit?** 
  Severe deficit sinks are found in large hardware and furniture, led by the **"Cubify Cube 3D Printer (2nd Generation)"** with a catastrophic loss of nearly **-\$9,000**, followed by specific corporate tables and desks.
- **Which category performs best?** 
  **Technology** is the top-performing category due to high margins and high average item values.
- **Which sub-category needs attention?** 
  The **Tables** and **Bookcases** sub-categories require immediate strategic review. They drive high sales volume but consistently return a net financial loss due to steep promotional discounts and high bulk freight costs.

---

### PART B — CUSTOMER ANALYSIS & SEGMENTATION

#### 1. Methodology & Business Thresholds Log
To evaluate customer value and purchasing behavior, a rigid data engineering approach was applied using SQL `CASE WHEN` logic to segment the **793 unique clients** into three distinct tiers based on their total sales volume contribution:
- 💎 **High-Value Customers (Sales >= \$5,000):** High-ticket corporate and individual clients driving premium sales and steady margins.
- ⚖️ **Medium-Value Customers (\$1,000 <= Sales < \$5,000):** Moderate, frequent buyers representing stable baseline revenue.
- 📉 **Low-Value Customers (Sales < \$1,000):** One-time or low-frequency buyers with minimal transaction sizes.

#### 2. SQL Analytics Metrics Computed
The customer analytical matrix successfully evaluated: `Total orders per client`, `Sales per customer`, `Profit contribution per customer`, and `Average Customer Order Value (AOV)`.

---

### 3. Five (5) Additional Business Insights (Week 3 Deliverables)

#### Insight 1: High-Value Customer Retention Leverage
A select group of **High-Value Customers** represents less than 15% of the total client base but contributes over 40% of corporate net profit. Retaining these accounts through custom loyalty programs or dedicated support channels is critical, as losing a single high-value client significantly impacts quarterly targets.

#### Insight 2: The Technological Copier Subsidization
The massive profit margin from the **Canon imageCLASS Copier** line acts as an internal financial cushion. This single product line effectively subsidizes the operational losses incurred by failing sub-categories like Tables, masking severe workflow deficiencies in the Furniture branch.

#### Insight 3: Flawed Pricing Strategy in Tables
SQL sub-category distribution grids confirm that the **Tables** division suffers from structural pricing issues rather than low demand. The volume (`Quantity`) and gross `Sales` are healthy, but aggressive promotional discounting paired with free bulk shipping terms completely destroys the gross margin.

#### Insight 4: Low-Value Customer Acquisition Cost (CAC) Warning
Over 50% of the customer base falls into the **Low-Value Customer** tier (spending under \$1,000 in total). If the corporate marketing budget is heavily spent on acquiring these low-frequency clients, the company is burning capital. Shift marketing focus toward upgrading Medium-Value clients into High-Value segments.

#### Insight 5: Average Order Value (AOV) Disparity
Cross-referencing customer metrics reveals that high transaction frequency does not equal profitability. Multiple clients with 10+ small orders generate a significantly lower net return than a Corporate client with just 2 high-AOV purchases, proving that driving high basket values is far more lucrative than increasing raw transaction volume.
