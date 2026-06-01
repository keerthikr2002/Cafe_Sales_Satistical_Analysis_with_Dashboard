# FINAL PORTFOLIO REPORT: CAFÉ SALES PERFORMANCE & DIAGNOSTIC ANALYTICS

**Target Audience:** Executive Stakeholders / Operations Management  
**Prepared By:** Data Analyst Portfolio  
[cite_start]**Methodology:** End-to-End Power Query ETL & Advanced Statistical Inferencing [cite: 46]  

---

## 1. Executive Summary & Core KPIs
[cite_start]This report provides a data-driven diagnostic evaluation of the café’s annual footprint across **9,518 individual transactions** [cite: 5, 46][cite_start], generating a total top-line revenue of **\$85,138.00**[cite: 46]. [cite_start]The fundamental goal of this analysis is to isolate core revenue engines, evaluate demand volatility, and scientifically validate operational categories to maximize margin efficiency[cite: 46].

### Key Performance Baselines
* [cite_start]**Total Revenue:** \$85,138.00 [cite: 46]
* [cite_start]**Total Transaction Volume:** 9,518 orders [cite: 5, 46]
* [cite_start]**Average Order Value (AOV / Mean):** \$8.94 [cite: 46]
* [cite_start]**Median Transaction Value:** \$8.00 [cite: 46]
* [cite_start]**Daily Sales Baseline:** \$233.25 / day [cite: 6]
* [cite_start]**Top Velocity Product:** Juice (1,121 total orders) [cite: 46]
* [cite_start]**Macro Revenue Peak:** October (\$7,391.00) [cite: 38, 46]
* [cite_start]**Macro Revenue Lull:** February (\$6,622.50) [cite: 38, 46]

---

## 2. Statistical Distribution & Outlier Diagnostics
An evaluation of transaction dispersion reveals critical pricing boundaries and purchase patterns:

* [cite_start]**Core Spread:** Transactions range from a strict minimum of \$1.00 to a maximum ceiling of \$25.00[cite: 46].
* [cite_start]**Volatility Profile:** The standard deviation sits at **5.87** with a Coefficient of Variation (CV) of **65.61%**[cite: 46]. [cite_start]This indicates a moderate-to-high variation in cart sizes, proving that revenue is highly sensitive to customer menu selections rather than flat-rate entry costs[cite: 46].
* [cite_start]**Skewness Metric:** The skewness calculation returns **0.81**, establishing a **Log-Normal / Right-Skewed distribution**[cite: 46]. [cite_start]This mathematically confirms that while the majority of customers purchase lower-cost routine items (Q1 at \$4.00, Median at \$8.00), a consistent volume of premium or bulk orders stretches the revenue curve upward[cite: 46].
* [cite_start]**Outlier Boundary:** Using the Interquartile Range method (IQR=8), the statistical upper outlier boundary is established at **\$24.00**[cite: 46]. [cite_start]A total of **239 transactions (\$25.00)** sit as high-value outliers [cite: 36, 46][cite_start], representing 7% of total revenue and offering excellent opportunities for targeted premium product positioning[cite: 36, 46].

---

## 3. Operational Performance Matrices (Top vs. Bottom)
[cite_start]To optimize supply chains and inventory cycles, performance has been broken down across three distinct corporate dimensions: Revenue Contribution, Ticket Frequency, and Physical Volume[cite: 46].

### A. Revenue Performance Matrix
* [cite_start]**Product Categories:** **Salads** represent the premier cash engine, yielding **\$16,575.00**[cite: 11, 46]. [cite_start]Conversely, **Cookies** sit at the financial bottom, generating only **\$3,076.00**[cite: 46].
* [cite_start]**Temporal Cycles:** **October** marks the peak operational month (\$7,391.00) [cite: 38, 46][cite_start], while **February** marks the lowest seasonal contraction (\$6,622.50)[cite: 38, 46].
* [cite_start]**Weekly Waves:** **Fridays** serve as the primary weekly revenue driver (\$12,453.00) [cite: 46][cite_start], whereas **Wednesdays** represent the lowest mid-week operational lull (\$11,673.50)[cite: 46].

### B. Order Frequency & Volumetric Matrices
* [cite_start]**Velocity Leaders:** While Salads dominate raw money [cite: 11, 46][cite_start], **Juice** drives the highest transactional velocity with **1,121 unique tickets**[cite: 46].
* [cite_start]**Physical Turnover:** **Coffee** represents the highest supply chain inventory movement, tracking **3,407 individual units sold** [cite: 46][cite_start], making it the vital anchor for daily physical foot traffic[cite: 46].

---

## 4. Advanced Inferential Modeling & Hypothesis Testing
[cite_start]To ensure business decisions are backed by statistical certainty rather than visual assumptions, multiple Single-Factor ANOVA tests and a Two-Sample t-Test were conducted[cite: 46].

### A. Fulfillment Channel Variance (ANOVA)
* [cite_start]**Groups Evaluated:** In-Store, Online, Takeaway [cite: 46]
* [cite_start]**Statistical Output:** $F\text{-Stat} = 55.91$, $P\text{-value} = 0.00$ [cite: 46]
* [cite_start]**Conclusion:** **Highly Significant.** Fulfillment method heavily influences order size[cite: 46]. [cite_start]**Online orders** boast a commanding average of **\$92.20 per cycle**, vastly outpacing physical In-Store (\$71.36) and Takeaway (\$69.69) alternatives[cite: 46].

### B. Payment System Variance (ANOVA)
* [cite_start]**Groups Evaluated:** Cash, Credit Card, Digital Wallet, Prepaid [cite: 46]
* [cite_start]**Statistical Output:** $F\text{-Stat} = 45.81$, $P\text{-value} = 2.74 \times 10^{-28}$ [cite: 46]
* [cite_start]**Conclusion:** **Highly Significant.** **Prepaid accounts** yield a massive average ticket size of **\$72.70** [cite: 46][cite_start], while Cash, Credit, and Digital Wallets remain perfectly flat, clustered tightly around **...**[cite: 46].

### C. Menu Mix Variance (ANOVA)
* [cite_start]**Groups Evaluated:** 9 Unique Menu Classifications [cite: 46]
* [cite_start]**Statistical Output:** $F\text{-Stat} = 155.15$, $P\text{-value} = 4.35 \times 10^{-222}$ [cite: 46]
* [cite_start]**Conclusion:** **Highly Significant.** Menu item variance is the single most powerful driver of ticket scale in the entire business ecosystem, led heavily by the high unit price of **Salads (\$45.41 average)**[cite: 46].

---

## 5. Day-Type Operational Elasticity
[cite_start]To resolve uneven sample sizes across a calendar year, a new categorical feature, `Day_Type` (Weekday vs. Weekend), was engineered via Power Query[cite: 5]. [cite_start]Data was aggregated on a weekly basis across 52 balanced operational periods to execute a **Two-Sample t-Test Assuming Unequal Variances**[cite: 5].

### t-Test Results Summary
* [cite_start]**Mean Weekly Weekday Revenue (5 days combined):** \$1,167.54 [cite: 5]
* [cite_start]**Mean Weekly Weekend Revenue (2 days combined):** \$466.29 [cite: 5]
* [cite_start]**Calculated t-Stat:** 37.78 (Critical Two-Tail threshold: 1.98) [cite: 5]
* [cite_start]**Calculated P-value:** $5.21 \times 10^{-61}$ [cite: 5]

### The Core Analytical Revelation
[cite_start]Because the P-value sits infinitely below our standard alpha threshold ($p < 0.05$), we **reject the null hypothesis** with absolute statistical certainty[cite: 5]. [cite_start]The gross difference between weekday and weekend sales is an undeniable structural feature of the café's business model[cite: 5]. 

[cite_start]However, the deeper value comes from **Statistical Normalization**[cite: 5]:

$$\text{Normalized Daily Weekday Performance} = \frac{\$1,167.54}{5 \text{ operating days}} = \$233.51 \text{ / day}$$

$$\text{Normalized Daily Weekend Performance} = \frac{\$466.29}{2 \text{ operating days}} = \$233.15 \text{ / day}$$

* [cite_start]**Conclusion:** The spending density and customer velocity per operating day are **virtually identical** between weekdays and weekends[cite: 5]. [cite_start]The gross volume dominance of weekdays is purely a function of calendar duration (5 days vs. 2 days), proving that the café maintains incredibly stable consumer demand across all 7 days of the week[cite: 5].

---

## 6. Data-Driven Strategic Recommendations

1. [cite_start]**Double-Down on the Prepaid Ecosystem:** Since Prepaid users buy significantly larger tickets (\$72.70 vs. \$53.50) [cite: 46][cite_start], launch an aggressive loyalty or mobile app program offering a 5% bonus incentive for reloading prepaid accounts[cite: 6]. [cite_start]This locks in customer loyalty and instantly scales up average order value[cite: 6].
2. [cite_start]**Optimize Digital Fulfillment Infrastructure:** Online orders are the premium revenue engine of the café, yielding the highest average transaction values (\$92.20)[cite: 46]. [cite_start]Management should allocate capital to refine the digital user experience, prioritize online order pickup lanes, and streamline mobile app interfaces to remove friction from this highly lucrative channel[cite: 6].
3. [cite_start]**Balanced Staffing Models:** Since the normalized daily revenue is practically identical on a Saturday compared to a Tuesday (\$233.15 vs. \$233.51) [cite: 5][cite_start], management should maintain consistent baseline staffing patterns across the entire week rather than drastically cutting personnel on weekends, ensuring service quality stays high during these shorter, high-density traffic windows[cite: 6].
