# Superstore Profitability & Discount Leakage Diagnostic

## Executive Summary
This project analyzes **$2.29M in retail sales** across 9,994 transactions to diagnose profit leakage centers. While the business achieves an overall net profit of **$286.4K (12.47% margin)**, transaction-level analysis reveals **$156.1K in total loss amount** from negative-margin sales. Using a 5 Whys Root Cause Analysis framework, this diagnostic isolates unprofitable categories down to regional discounting practices and specific product SKUs.

---

## Business Problem & Key Metrics
The core objective is identifying why high sales volume fails to generate proportional profit in specific sub-categories, pinpointing threshold violations, and proposing actionable margin guardrails.

* **Total Sales:** $2,297,200.86
* **Total Net Profit:** $286,397.02
* **Overall Profit Margin:** 12.47%
* **Total Loss Amount:** -$156,131.29

---

## Root Cause Analysis (5 Whys Framework)

### Issue 1: Tables Sub-Category (-$17,725.48 Profit)
* **Why 1:** Tables generate $206.9K in sales but lose money due to an aggressive average discount rate of 26.13%.
* **Why 2:** Profit leakage centers in the **East Region**, contributing **-$11,025.38 (62.2%)** of total Tables losses.
* **Why 3:** East Region average discounts reach **37.38%** (Corporate segment at 38.13%), exceeding product COGS thresholds.
* **Why 4:** West Region maintains positive profit (+$1,482.61) by capping average discounts strictly at **20.00%**.
* **Root Cause:** Absence of a hard 20% discount ceiling on high-COGS furniture products in the East Region.

### Issue 2: Supplies Sub-Category (-$1,189.10 Profit)
* **Why 1:** Supplies maintain a low average discount (7.68%) and positive average margin (11.20%), yet cumulative net profit is negative.
* **Why 2:** **East Region** accounts for **-$1,155.14 (97.1%)** of all Supplies losses.
* **Why 3:** Losses do not stem from site-wide discounts, but concentrate in specific high-value items.
* **Why 4:** A single SKU, *Martin Yale Chadless Opener Electric Letter Opener*, generated **-$1,199.25** in loss.
* **Root Cause:** Single-SKU pricing mismatch where base COGS exceeds net price under standard 20% promotional discounts.

---

## Interactive Dashboard Features
Built in Google Sheets / Excel with dynamic interactivity and executive-ready visual hierarchy:
1. **KPI Scorecard Header:** Real-time visibility into Total Sales, Net Profit, Margin %, and Cumulative Loss Amount.
2. **Profitability Spectrum Chart:** Horizontal bar visualization sorting sub-categories from highest profit to deepest loss.
3. **Dual-Axis Regional Chart:** Overlaying profit bars with discount percentages to illustrate margin compression above 20% discount rates.
4. **Interactive Slicers:** Dynamic filtering across Region and Segment dimensions.

---

## Strategic Recommendations

| Domain | Finding | Actionable Strategy | Expected Financial Impact |
| :--- | :--- | :--- | :--- |
| **Furniture Pricing** | Tables loss driven by >37% discounts in East Region. | Enforce a mandatory 20% discount ceiling on all Furniture products. | Recovers up to **~$11,000** in East Region margin. |
| **SKU Governance** | *Martin Yale Electric Letter Opener* causes 103.8% of East Supplies loss. | Delist SKU or adjust baseline retail pricing. | Instantly converts East Supplies to **+$44 net profit**. |
| **Discount Policy** | Uncapped promotional discounts erode high-COGS margin. | Implement automated approval workflows for discounts exceeding 20%. | Protects baseline profitability across all regions. |

---

## Technical Stack & Tools
* **Platform:** Google Sheets / Microsoft Excel
* **Data Manipulation:** Pivot Tables, Calculated Fields, Nested Logic (`SUMIF`, `DATEDIF`, `IF`)
* **Data Visualization:** Dual-Axis Combo Charts, Dynamic Scorecards, Interactive Slicers
