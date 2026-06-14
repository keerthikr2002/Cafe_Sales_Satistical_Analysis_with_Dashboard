# Café Sales Intelligence & Advanced Excel Diagnostic Analytics (2023)
**Source:** Kaggle (Annual 2023 Cycle)

## Project Overview
This project delivers an end-to-end data engineering and diagnostic analytics solution built entirely inside **Microsoft Excel**. Working with an annual cafe sales dataset covering **9,518 unique orders**, the project lifecycle handles data ingestion and extraction using Power Query (ETL), data profiling and quality mitigation, statistical optimization through the Excel Data Analysis Toolpak, and dynamic, executive-facing visual reporting.

The primary objective is to isolate core revenue engines, evaluate demand volatility, verify backend transformations, and scientifically validate operational categories to maximize throughput and margin efficiency.

---

## 1. Advanced Excel Technical Stack & Skills Demonstrated
* **ETL & Data Engineering:** Power Query implemented for advanced data profiling, schema validation, handling hidden formatting gaps, and merging categorical fields.
* **Feature Engineering:** Advanced conditional nesting logic (`IF`, `IFS`, `XLOOKUP`) used to build time-intelligent dimensions (`Day_Type`), price buckets, and item-category lookups.
* **Statistical Modeling:** Excel Data Analysis Toolpak implementation for descriptive statistics, parametric hypothesis testing (Single-Factor ANOVA and Two-Sample t-Tests assuming unequal variances), and multi-variable regression profiling.
* **Dynamic Visualization:** Interactive Excel dashboard design utilizing advanced slicer routing, dynamic pivot connections, conditional data bars, and KPI card mapping.

---

## 2. Executive Summary & Core Business Scale
This report details the café’s annual footprint across **9,518 individual transactions**, generating a total top-line revenue of **\$85,138.00**. The analysis removes operational guesswork by isolating exactly what drives our cash flow and mapping out where sales fluctuate to maximize overall profit margins.

### High-Level Core KPIs
* **Total Revenue:** \$85,138.00 (Cumulative gross sales across the 365-day cycle)
* **Total Transaction Volume:** 9,518 orders (Operational throughput baseline)
* **Average Order Value (AOV / Mean):** \$8.94 per ticket
* **Median Transaction Value:** \$8.00 (Confirms standard customer behavior is locked near an \$8 ceiling)
* **Total Units Sold:** 28,757 units
* **Daily Sales Baseline:** \$233.25 / day
* **Weekly Sales Baseline:** \$1,606.38 / week
* **Monthly Sales Baseline:** \$7,094.83 / month
* **Top Velocity Product:** Juice (1,121 total orders)
* **Macro Revenue Peak:** October (\$7,391.00)
* **Macro Revenue Lull:** February (\$6,622.50)

---

## 3. Data Quality & Power Query ETL Transformation Log
Before processing any statistical equations or building the visual frontend, the raw dataset underwent rigorous data profiling and engineering via Power Query to guarantee absolute analytical integrity.

### Row Counts Summary
* **Original Records:** The raw dataset started with 10,000 original rows.
* **Cleaned Records:** After applying transformation filters, 9,518 rows remained.
* **Data Filtration:** A total of 482 rows were removed due to unrecoverable time-series errors.
* **Data Quality Score:** The process achieved an overall data quality threshold of 95.18%, safely clearing the standard 90% industry benchmark.

### Data Cleaning & Values Replaced per Column
* **Item:** Found 969 instances containing UNKNOWN, ERROR, or null records; missing items were safely categorized under the fallback string value `"Other"`.
* **Quantity:** Tracked 479 instances of UNKNOWN, ERROR, or nulls; values were mathematically calculated and backfilled using the formula: `(Total Spent ÷ Price)`.
* **Price Per Unit:** Identified 533 missing values; resolved via an item-based index lookup to pull the appropriate baseline menu item cost.
* **Total Spent:** Systemwide cleaning applied to all rows by recalculating the transaction value using the formula `(Quantity × Price)` to eliminate input corruptions.
* **Payment Method:** Found 3,178 instances of UNKNOWN, null, or ERROR fields; standardized to `"Prepaid"` as the default baseline.
* **Location:** Found 3,961 instances of UNKNOWN, null, or ERROR entries; standardized to `"Online"` based on transactional metadata.
* **Transaction Date:** Identified 460 critical rows containing completely missing or broken dates; these 460 corrupted rows were filtered out to ensure time-series accuracy.

### Schema Standardization & Data Type Audits
* **Transaction Date:** Shifted from Text (object) to Date type to enable deep time-series analysis.
* **Quantity:** Transformed from mixed Text strings into a strict Whole Number formatting to allow mathematical aggregations.
* **Price Per Unit & Total Spent:** Converted from mixed Text formats into Decimal Numbers to establish precise financial calculations and revenue tracking.
* **Text Categoricals:** Columns for Item, Payment Method, and Location were validated as Text with no further type shifts needed.

### Feature Engineering & Advanced Metadata Additions
* **Item_category:** Built an item-lookup conditional column to evaluate broader high-level consumer interest trends (e.g., grouping items into "Cold & Crisp").
* **Price_category:** Categorized menu options into Low, Mid, and High price classifications to track macro profit drivers.
* **Order_size:** Grouped items by quantity into Standard, Group, and Bulk to determine structural order impacts.
* **Transaction_value_tier:** Segmented gross customer ticket sizes into High, Low, and Medium tiers to understand revenue weights.
* **Time-Series Columns:** Used Power Query Date tools to isolate Year, Month Name, Week Number, Quarter, and Day of Week fields, unlocking precise trend analysis.
* **Total Sales, Price per unit, & Quantity:** Engineered custom column formulas to overwrite initial database gaps and establish a clean financial ledger.

---

## 4. Interactive Analytics Dashboard Interface
To translate cleaned data metrics into dynamic operational control, an interactive sales intelligence dashboard was engineered. This interactive canvas serves as the primary visual interface for executive stakeholders.

### Interactive Components & Slicer Routing
* **Executive KPI Tiles:** Summary blocks linked directly to hidden pivot tables display values for Revenue, Orders, AOV, Total Units, and Top Velocity items.
* **Multi-Dimensional Pivot Slicers:** Connected across multiple matrix cards on the sheet, enabling stakeholders to filter the entire layout instantly by:
  * *Payment Method:* Cash, Credit Card, Digital Wallet, Prepaid
  * *Fulfillment Location:* In-Store, Online, Takeaway
  * *Menu Item Selectors:* Tracking for all food/beverage classifications
  * *Temporal Filters:* Filtering by Month and Day of the Week

### Dashboard Preview
![Café Sales Intelligence Dashboard](Excel_Cafe_Sales_Dashboard.png)

---

## 5. Statistical Distribution & Outlier Diagnostics
When we study the spread of our transactions, it reveals a lot about how our customers spend money. Our tickets range from a bare minimum of \$1.00 for small add-ons up to a top ceiling of \$25.00 for full meals.

* **Volatility Profile:** The standard deviation sits at **5.87** with a Coefficient of Variation (CV) of **65.61%**. In plain business terms, this means our cart sizes fluctuate heavily throughout the day. Our revenue isn't driven by a flat, predictable entry cost; instead, it is highly sensitive to the specific items customers choose to mix and match from the menu.
* **Skewness Metric:** The skewness calculation returns **0.81**, establishing a **Log-Normal / Right-Skewed distribution**. This mathematically confirms a classic retail pattern: while the vast majority of our daily customers buy lower-cost routine items (meaning half of our total orders sit right at or below an \$8.00 median price ceiling), a highly consistent group of premium or bulk buyers spend much more, stretching our revenue curve upward and lifting our overall average order value to \$8.94 per ticket.
* **Outlier Boundary:** Using the Interquartile Range method ($IQR = \$8.00$, Q1: \$4.00, Q3: \$12.00) calculated via Excel formulas, the statistical upper boundary is established at **\$24.00**. 
* **Premium Order Segment:** Exactly 239 transactions hit our absolute maximum ceiling of \$25.00. These behave as high-value outliers. Even though they represent a small slice of total volume, they single-handedly generate 7% of our entire annual revenue (\$5,975.00), giving us a perfect target for high-end customer loyalty perks.

---

## 6. Market Elasticity & Regression Proofs
We ran correlation models and linear regressions within the Excel Data Analysis Toolpak to take the guesswork out of our strategy. The math proves exactly how price and volume impact our bottom line:

* **Perfect Price Inelasticity (Correlation = 0.01 | $R^2 = 0.00$):** We discovered a flat zero statistical relationship between our menu prices and the quantity of items people order. In businessman terms, changing our menu prices has a 0% impact on customer purchase volume. Adjusting our prices upward will **not** scare away customers or cause them to buy less, giving us a clear green light to optimize our margins.
* **Volume Drives the Variances (Correlation = 0.72 | $R^2 = 52.23\%$):** Multi-unit transactions are the primary engine of major daily revenue spikes. The volume of items per ticket explains over half of our daily revenue variations.
* **Price Explains the Rest (Correlation = 0.63 | $R^2 = 39.63\%$):** Our menu pricing structure directly accounts for roughly 40% of our gross daily revenue changes. Higher-priced selections systematically secure higher total dollar returns.

---

## 7. Deep-Dive Category Performance & Operational Insights

### The Ultimate Champion: Cold & Crisp
The **Cold & Crisp** menu category—which includes our Salads, Smoothies, and Juices—is the undeniable powerhouse of the entire café. It dominates every single performance metric we track, bringing in 3,264 orders (34% of café total) and moving 9,850 individual physical units (34.45% of café total). Ultimately, this single category accounts for a massive 46% of our total annual revenue, bringing in **\$39,374.00**.

### Micro-Item Performance Diagnostics
* **The Salad Financial Engine:** Thanks to its higher \$5.00 price point, Salad is our biggest individual money-maker. It brought in **\$16,575.00**, which accounts for nearly a fifth (**19.47%**) of our entire annual revenue, even though it only accounted for roughly 11.53% of our orders (1,097).
* **The Juice Velocity King:** While Salad wins on raw dollar amounts, Juice wins on pure customer frequency. It captured our highest transaction rate with **1,121 unique orders** (11.78%), bringing in a highly respectable \$10,023.00.
* **The Coffee Foot-Traffic Anchor:** Coffee is what keeps our physical supply chain moving, tracking a massive **3,407 individual units sold** over the year. It only represents 8% of our financial revenue (\$6,814.00) simply because its price is low (\$2.00), not because people aren't buying it. It remains the vital anchor for daily physical foot traffic.
* **The Low-Price Trap:** Our hot beverages, teas, and cookies stay highly competitive with items like smoothies when it comes to raw order counts. However, because their price points are so low (\$1.00 to \$1.76), they generate very little total revenue. They are popular, but they lack the price weight to drive the bottom line.

### Order Size & Spend Segmentation
* **Group Orders are the Sweet Spot:** Transactions containing 2 to 4 items are our most profitable segment. They make up 38.86% of our order volume but generate a huge **44.95% of our revenue (\$38,267.50)** and 45% of total units sold (12,940). When you combine Group orders with Bulk orders (more than 4 items), they make up 60% of our total transactions but bring in a massive 80% of our top-line revenue.
* **Standard Orders are Inefficient:** Small orders of fewer than 2 items drain operational time for little return. They eat up 40.07% of our daily order tickets but only generate 19.97% of our total revenue (\$17,003.50).
* **The Dominant Medium Tiers:** Our **Medium Price Category** (\$3.00 to \$4.00 items like Cake, Juice, Sandwiches, and Smoothies) anchors the business portfolio, bringing in **63.44% of our total revenue (\$54,008.00)**, 55.10% of orders, and 55.11% of unit volume. Similarly, on a per-ticket basis, Medium Spend orders (\$4.00 to \$12.00 total) are our most reliable daily driver, pulling in 45.82% of total sales (\$39,012.50) across 4,693 transactions.

---

## 8. Performance Boundaries & System Stability
When we look at our best and worst performance boundaries across the year, we get a clear picture of our operational limits:

* **Quarterly Cycle:** Our fourth quarter (Q4) was our peak at \$21,549.00, while our third quarter (Q3) was our lowest at \$20,945.50—showing a tight 3% variance (\$603.50 spread).
* **Macro Month:** October marks the peak operational month (\$7,391.00), while February marks the lowest seasonal contraction (\$6,622.50), reflecting a standard 10% seasonal gap (\$768.50 spread).
* **Weekly Trajectory:** Week 15 served as the high-water mark (\$1,832.50), while Week 53 showed an end-of-year holiday contraction down to \$179.00.
* **Day of the Week:** Fridays serve as our biggest weekly cash drivers (\$12,453.00), while Wednesdays represent our lowest mid-week operational lull (\$11,673.50), reflecting a small 6% swing (\$779.50 spread).
* **Day Type Baseline:** Weekdays generated \$60,712.00 cumulative versus Weekends at \$24,426.00. However, daily baselines remain perfectly flat and identical at **\$232.61/day vs. \$234.87/day**.
* **Order Fulfillment Channel:** Online sales are our absolute dominant pipeline, bringing in **\$33,653.50 across 3,773 orders**, while Takeaway sits at the bottom with \$25,438.00. In-store and takeaway mirror each other tightly at roughly 30% order and revenue shares each.
* **Payment Ecosystem:** Prepaid accounts serve as our top settlement method at \$26,536.00, whereas Cash sits at the low end at \$19,526.50.

### The Main Takeaway on Day-to-Day Stability
Outside of expected, minor calendar anomalies, our café runs an incredibly stable, steady ship. The statistical variance between weekdays and weekends, day-to-day operations, order locations, and payment types sits at a flat **1% margin**. This mathematically indicates that day-to-day fluctuations are just normal background noise, not actual structural shifts in consumer demand. Our customers buy consistently and steadily every single day of the week.

---

## 9. Strategic Recommendations & Data-Driven Growth Levers

* **Implement a Systemic Menu Price Increase:** Our regression models mathematically prove that our customers are entirely price-insensitive (0.01 correlation). Raising prices across our high-volume, low-margin staples—like Coffee, Tea, and Cookies—will pump money directly into our bottom line without risking any drop in order volume.
* **Capitalize on Digital Sales Channel Dominance:** Online orders are our largest single sales pipeline (\$33,653.50). We should introduce targeted online coupon discounts and digital bundles to protect this volume and push online basket sizes even higher.
* **Incentivize the Premium Spenders:** We have a highly valuable bucket of 239 premium transactions completely locked at our current \$25.00 maximum ticket ceiling. We need to cater to these high-value outliers by introducing exclusive loyalty offers and high-end combo packages to break past that \$25.00 limit and capture more margin.

---

## 10. Schema Verification Matrix
If you wish to test your own data against this analytical infrastructure, verify your data source mirrors the following configuration requirements:
* `Transaction_ID` (Text / Unique Key)
* `Item` (Text / Categorical Classification)
* `Quantity` (Integer / Product Volume)
* `Price_Per_Unit` (Decimal / Item Valuation)
* `Total_Spent` (Decimal / Derived Revenue Metric)
* `Payment_Method` (Text / Settlement Type)
* `Location` (Text / Fulfillment Channel)
* `Transaction_Date` (Date / Temporal Key)
