# Instacart Market Basket Analysis

**Customer segmentation and behavioral profiling** across ~32 million order rows using Python, Pandas, and Matplotlib.

[![Python](https://img.shields.io/badge/Python-3.11+-3dd68c?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-3dd68c?style=flat-square)](https://pandas.pydata.org)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-3dd68c?style=flat-square)](https://matplotlib.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-888888?style=flat-square)](LICENSE)

---

## Overview

Instacart needed deeper insight into customer purchasing behavior to improve targeting and marketing. This analysis uses order-level transaction data merged with customer demographics to answer four core business questions:

1. **When are customers most active?** Which hours and days drive the most orders?
2. **What distinguishes loyal from new customers?** Segmentation by order history.
3. **How do demographics relate to spending?** Age, income, and regional patterns.
4. **Which customer profiles are highest value?** Multi-variable profiling.

**Result:** 6 validated customer segments, 9 charts, and 6 actionable business findings across a dataset of ~32 million rows and ~206,000 customers.

---

## Notebooks

| Notebook | Description |
|---|---|
| [`4.2 IC Data import and descriptive analysis.ipynb`](4.2%20IC%20Data%20import%20and%20descriptive%20analysis.ipynb) | Import orders + products, basic profiling |
| [`4.3 IC Data wrangling and subsetting.ipynb`](4.3%20IC%20Data%20wrangling%20and%20subsetting.ipynb) | Rename columns, create subsets, export cleaned data |
| [`4.4 IC Data consistency checks.ipynb`](4.4%20IC%20Data%20consistency%20checks.ipynb.ipynb) | Fix mixed types, handle 260K missing values |
| [`4.5 IC Combining & Exporting Data.ipynb`](4.5%20IC%20Combining%20%26%20Exporting%20Data.ipynb.ipynb) | Merge orders + order_products + products |
| [`4.6 IC Deriving New Variables.ipynb`](4.6%20IC%20Deriving%20New%20Variables.ipynb.ipynb) | Create price_label, busiest_day, busiest_period_of_day |
| [`4.7 IC Grouping Data.ipynb`](4.7%20IC%20Grouping%20Data.ipynb) | Loyalty flag, spending flag, order frequency flag |
| [`4.8 IC Customer Data Wrangling.ipynb`](4.8%20IC%20Customer%20Data%20Wrangling.ipynb) | Merge 206K customer demographics |
| [`4.8 IC Visualizations.ipynb`](4.8%20IC%20Visualizations.ipynb) | 8 charts: orders, loyalty, prices, demographics |
| [`4.9 IC Final Analysis & Profiling.ipynb`](4.9%20IC%20Final%20Analysis%20%26%20Profiling.ipynb) | PII removal, regional segmentation, customer profiles |

---

## Key Findings

**1. Orders peak between 9 AM and 4 PM**
Instacart is a daytime platform. The 10:00 AM hour is the single busiest period. Late-night promotions are unlikely to move volume.

**2. Product price is stable across all hours**
Average basket price does not vary meaningfully by time of day. Promotions should target segments, not hours.

**3. Regular customers drive the most order volume**
While Loyal customers (20+ orders) have higher per-order value, Regular customers (11–20 orders) generate the most total volume. A loyalty conversion strategy has the highest revenue upside.

**4. Adults (30–49) are the dominant demographic**
This age group represents the largest share of customers. Marketing should optimize for family-stage purchasing: household staples, fresh produce, and meal planning.

**5. Middle-income customers are the core demographic**
The $40k–$80k income range dominates. Core catalog pricing should remain accessible while premium placement targets the high-income segment.

**6. High-frequency customers are the largest single group**
Customers with 20+ orders outnumber both medium and low-frequency groups. Retention (subscriptions, loyalty rewards) has a larger addressable base than acquisition.

---

## Data Quality Issues Resolved

| Issue | Column | Resolution |
|---|---|---|
| Price outlier (max = 99,999) | `products.prices` | Flagged as data entry error — labeled High |
| 260,290 missing values | `days_since_prior_order` | Expected for first-ever orders — filled with 0 |
| Mixed data type (object) | `days_since_prior_order` | Converted with `pd.to_numeric(errors="coerce")` |
| PII in customer data | `first_name`, `last_name` | Dropped before profiling |
| Duplicate columns after merge | `total_orders (_x/_y)` | Rebuilt cleanly with groupby + merge |

---

## Customer Segmentation Variables

| Variable | Logic | Labels |
|---|---|---|
| `loyalty_flag` | mean order_number > 20 / 11–20 / ≤10 | Loyal / Regular / New Customer |
| `spending_flag` | avg item price ≥ $10 / < $10 | High spender / Low spender |
| `age_group` | < 30 / 30–49 / 50–64 / 65+ | Young adult / Adult / Middle-aged / Senior |
| `income_group` | < $40k / $40k–$80k / > $80k | Low / Middle / High income |
| `family_status` | 0 / 1–2 / 3+ dependents | No dependents / Small / Large family |
| `order_frequency` | 5–9 / 10–19 / 20+ orders | Low / Medium / High frequency |

---

## Dataset Scale

| Metric | Value |
|---|---|
| Total order rows | ~32.4 million |
| Total customers | ~206,000 |
| Orders after low-activity filter | ~31.0 million |
| Products | 49,688 |
| Departments | 21 |
| U.S. states | 50 |
| U.S. Census regions | 4 |

---

## Installation

```bash
git clone https://github.com/ageelalramadhan/Project-4-Instacart-.git
cd Project-4-Instacart-
pip install -r requirements.txt
```

---

## Dependencies

```
pandas
numpy
matplotlib
seaborn
os
```

---

## Portfolio

Full case study with all charts and findings:
**[ageelalramadhan.github.io/instacart-case-study.html](https://ageelalramadhan.github.io/instacart-case-study.html)**

---

## Author

**Ageel Alramadhan** — Data Analyst · Hamburg
[LinkedIn](https://www.linkedin.com/in/ageel-alramadhan/) · [Portfolio](https://ageelalramadhan.github.io)

*CareerFoundry Data Analytics Program · DEKRA-certified · AfA-approved · 1221 UE*
