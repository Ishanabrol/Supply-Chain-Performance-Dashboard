# 📦 Supply Chain Performance & Operations Analytics Dashboard

[![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)](https://python.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](https://jupyter.org)
[![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?logo=powerbi)](https://powerbi.microsoft.com)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3+-green?logo=scikit-learn)](https://scikit-learn.org)
[![Pandas](https://img.shields.io/badge/Pandas-2.0+-150458?logo=pandas)](https://pandas.pydata.org)
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

> An end-to-end supply chain analytics pipeline combining Python-based
> data engineering, Isolation Forest anomaly detection, weighted supplier
> risk scoring, and a 4-page interactive Power BI dashboard — built to
> surface delivery inefficiencies, financial anomalies, and supplier risk
> across 65,749 orders and 23 global regions.

---

## 💼 Business Problem

Global supply chains generate enormous volumes of transactional data —
but most organisations lack the analytical infrastructure to extract
actionable insights from it. Operations managers are left asking the
same questions every month without reliable answers:

**1. Why are more than half our deliveries late?**
With a 57.3% late delivery rate sustained across 3 consecutive years
(2015–2017), the company has a systemic logistics problem that is not
improving. Standard reporting cannot pinpoint whether the root cause
is geographic, carrier-related, or product-category specific.

**2. Which supplier segments are genuinely high-risk?**
With 92 supplier segments (Region × Shipping Mode combinations) varying
widely in reliability, procurement teams have no objective way to rank
or prioritise which relationships need immediate attention.

**3. Where is money being lost without anyone noticing?**
18.7% of all order items are sold at a loss — yet the problem is
invisible in aggregate revenue figures. A subset of Same Day shipping
orders carries profit margins between -159% and -269%, meaning the
company loses up to $2.69 for every $1.00 of revenue on those orders.
This is a pricing problem masquerading as a logistics problem.

**This project addresses all three challenges** through a structured
5-phase pipeline: data ingestion, cleaning and feature engineering,
ML-based anomaly detection, supplier risk scoring, and an interactive
Power BI dashboard that makes these insights accessible to non-technical
decision-makers.

---

## 📌 Project Overview

This project builds a complete business analytics solution on the
DataCo Global Supply Chain dataset — from raw CSV to a published
Power BI dashboard — using Python for all data preparation and machine
learning, and Power BI for interactive visualisation.

**Five-Phase Pipeline:**
- **Phase 1** — Data ingestion, EDA, and quality assessment
- **Phase 2** — Cleaning, feature engineering, and star schema export
- **Phase 3** — Isolation Forest anomaly detection + supplier risk scoring
- **Phase 4** — Power BI data modelling, DAX measures, and dashboard build
- **Phase 5** — Validation, documentation, and publication

**Key analytical outputs:**
- 8 engineered features including `actual_delay_days`, `is_late`,
  `profit_margin_pct`, and `supplier_segment`
- 3,288 anomalous orders identified (5% contamination threshold)
- 92 supplier segments scored on a 0–100 weighted risk scale
- 4-page interactive Power BI dashboard with drill-through and
  decomposition tree

---

## 🛠️ Tech Stack

| Category | Tool | Purpose |
|---|---|---|
| **Language** | Python 3.10+ | Data pipeline and ML |
| **Notebooks** | Jupyter Notebook | Analysis and documentation |
| **Data** | Pandas, NumPy | Cleaning and feature engineering |
| **Visualisation** | Matplotlib, Seaborn | EDA charts and analysis plots |
| **ML** | scikit-learn (Isolation Forest) | Anomaly detection |
| **Scaling** | StandardScaler | Feature normalisation for ML |
| **Dashboard** | Microsoft Power BI Desktop | Interactive 4-page dashboard |
| **DAX** | Power BI DAX | Dynamic KPI measures |
| **Data modelling** | Power BI Model View | Star schema relationships |
| **Dataset** | DataCo Global Supply Chain | Source data (Kaggle) |

---

## 📊 Dashboard — 4 Pages at a Glance

### Page 1 — Executive Overview
> Top-level KPIs, monthly late delivery trend, shipping mode breakdown,
> and an interactive decomposition tree for root cause analysis.

| KPI | Value |
|---|---|
| Total Unique Orders | 65,749 |
| Total Sales | $128.20M |
| Late Delivery Rate | 57.3% |
| Avg Delay Days | 0.57 |
| Anomaly Count | 3,288 |

### Page 2 — Supplier Scoreboard
> Risk-scored supplier segments with conditional formatting (Red / Amber /
> Green), donut chart showing tier distribution, and a ranked bar chart
> of the highest-risk segments.

| Metric | Value |
|---|---|
| Segments scored | 92 |
| High Risk (≥65) | 3 |
| Medium Risk (40–64) | 59 |
| Low Risk (<40) | 30 |
| Avg Risk Score | 45.1 |
| Highest risk segment | Eastern Asia \| Second Class — 68.3 |

### Page 3 — Sales & Profitability
> Revenue and profit trends by month, profit margin by product category,
> year-over-year sales, and an anomaly scatter plot showing the financial
> pattern of flagged orders.

| Metric | Value |
|---|---|
| Total Profit | $13.76M |
| Overall Profit Margin % | 10.73% |
| Loss-Making Orders | 24,649 items |
| Most profitable category | Golf Bags & Carts (17.5%) |
| Least profitable category | Men's Clothing (4.57%) |

### Page 4 — Logistics Map
> Global bubble map of order locations, anomaly rate by region bar chart,
> and a regional performance table sorted by late delivery rate.

| Metric | Value |
|---|---|
| Countries covered | 164 |
| Regions covered | 23 |
| Highest anomaly region | Oceania (6.4%) |
| Highest late delivery region | Central Africa (60.6%) |

---

## 🔍 Key Findings

**Finding 1 — Late delivery is systemic, not trending**
The late delivery rate holds at ~57% across all three complete years
(2015, 2016, 2017) with no improvement. This is a structural
scheduling problem: First Class shipping is consistently promised in
1 day but takes 2 days across all regions — producing a 100% late
delivery rate for the most premium shipping option.

**Finding 2 — Anomalies are financial, not operational**
The most important finding of the project: anomalous orders are
**less likely to be late** than normal orders (37.4% vs 58.4%).
They are flagged because of extreme profit margin deterioration
(-38.98% avg vs +13.48% for normal orders). Top anomalies are
Same Day bulk orders losing between -116% and -269% margin —
delivered on time, but financially catastrophic.

**Finding 3 — Second Class shipping is the highest-risk segment**
All 3 High Risk supplier segments use Second Class shipping, with
late delivery rates of 80–84%. This is a different failure mode
from First Class — erratic and unpredictable rather than
consistently wrong — which is why it scores higher on the risk model.

**Finding 4 — Loss-making orders are order-specific, not category-wide**
All 50 product categories maintain positive average profit margins.
The loss-making problem is concentrated in specific high-discount
orders within categories — not in the categories themselves. This
points to a discounting policy problem rather than structural
category pricing issues.

---

## ⚙️ Methodology

### Feature Engineering

| Column | Formula | Finding |
|---|---|---|
| `actual_delay_days` | real − scheduled days | Mean: +0.57, Range: -2 to +4 |
| `is_late` | 1 if delay > 0 else 0 | 57.3% of orders late |
| `profit_margin_pct` | (profit ÷ sales) × 100 | Mean: 10.83%, Min: -275% |
| `supplier_segment` | Region \| Shipping Mode | 92 unique proxies |

### Anomaly Detection — Isolation Forest

| Parameter | Value | Reasoning |
|---|---|---|
| Algorithm | Isolation Forest | Unsupervised — no labels needed |
| Contamination | 5% | Industry convention for unlabelled data |
| Features | 7 | Delay days, margin, discount, quantity, is_late |
| Grain | Order level (65,749) | Not item level — avoids double-counting |
| n_estimators | 100 | Standard default |

> Anomaly detection intentionally runs at **order level** — not on the
> 180,516 item rows. Running on item rows would flag the same order
> multiple times if it contains multiple products.

### Supplier Risk Scoring — Weighted Formula

| Metric | Weight | Reasoning |
|---|---|---|
| Late delivery rate | 35% | Highest customer-facing impact |
| Avg delay days | 25% | Severity of delays, not just frequency |
| Anomaly rate | 20% | Unpredictability signals systemic risk |
| Avg profit margin | 10% | Financial fragility of the segment |
| Loss order rate | 10% | Recurring losses are unsustainable |

All metrics normalised to 0–1 using Min-Max normalisation before
applying weights. Final score scaled to 0–100.

### Power BI Data Model

All relationships: Many to One, Single cross-filter direction.

---


## 🗄️ Dataset

**DataCo Smart Supply Chain for Big Data Analysis**
Source: [Kaggle](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis)

| Property | Value |
|---|---|
| Raw rows | 180,519 |
| Dataset grain | Order-item level |
| Unique orders | 65,749 |
| Avg items per order | 2.75 |
| Columns | 53 |
| Date range | Jan 2015 – Jan 2018 |
| Regions | 23 |
| Countries | 164 |
| Product categories | 50 |
| Shipping modes | 4 |

> ⚠️ **Dataset note:** DataCo is a synthetic dataset created for
> academic research. Patterns are more uniform than real supply chains.
> The Same Day anomaly pattern and First Class 100% late rate reflect
> the dataset's generation logic rather than confirmed real-world
> behaviour. All insights are framed as observations, not causal claims.

### Key EDA Findings

| Finding | Value | Implication |
|---|---|---|
| Late delivery risk (pre-existing flag) | 54.8% | Predicted at order time |
| Late delivery (actual, calculated) | 57.3% | 2.5pp worse than predicted |
| Loss-making item rate | 18.7% | 33,784 items sold below cost |
| Worst profit margin | -275% | Extreme discounting or data error |
| 2018 data | Jan only | Exclude from YoY trend analysis |
| Product Description column | 100% missing | Dropped entirely |
| Order Zipcode | 86.2% missing | Dropped — covered by Region/Lat/Long |

---

## 📈 Results at a Glance

| Analysis | Key Number | Business Meaning |
|---|---|---|
| Late delivery rate | **57.3%** | Systemic problem — flat for 3 years |
| Anomalies detected | **3,288 orders (5%)** | Financially broken, not operationally late |
| Avg anomaly margin | **-38.98%** | vs +13.48% for normal orders |
| Same Day anomaly rate | **~40%** | Premium shipping sold well below cost |
| High Risk segments | **3 of 92** | All Second Class, 80–84% late rate |
| Top risk score | **68.3 / 100** | Eastern Asia \| Second Class |
| Loss-making orders | **13,909 unique orders** | 21.2% of all orders |
| All-category margins | **Positive** | Loss is order-level, not category-level |

---

## ⚠️ Limitations

**Dataset**
- Synthetic data — patterns too uniform for real-world generalization
- No real supplier identity — segments are Region + Shipping Mode proxies
- 2018 is a partial year (January only) — excluded from trend analysis
- Geographic coordinates are city-level approximations, not precise addresses

**Methodology**
- Contamination = 5% is a convention, not a validated threshold
- Risk score weights (35/25/20/10/10) are judgment-based, not derived from data
- Isolation Forest does not explain which feature caused the flag
- Small segments (< 50 orders) have statistically unreliable risk scores
- No causal analysis — all findings are correlational observations

**Power BI**
- All order-level KPIs use `DISTINCTCOUNT(Order Id)` due to order-item grain
- `fact_orders_enriched` has 180,516 rows — item level, not order level
- `supplier_segment` is a text join key — slower than integer keys at scale

---

## 🚀 Future Work

- **Real-time pipeline** — connect Power BI to a live SQL database via
  DirectQuery for daily-refreshing operational dashboards
- **Predictive delivery** — train a classification model to predict late
  delivery risk at order placement time using order features
- **Pricing optimisation** — build a discount elasticity model to identify
  the maximum discount level before an order becomes loss-making
- **Explainable anomalies** — add SHAP values to explain which features
  drove each anomaly flag, making results actionable for operations teams
- **Supplier clustering** — apply K-Means to supplier segments to identify
  natural groupings beyond the manual Region × Shipping Mode proxy
- **Power BI Service** — publish to Power BI Service with scheduled
  refresh for a live, shareable portfolio link

---

## 👤 Author

**Ishan**

Supply Chain Performance & Operations Analytics Dashboard

*An end-to-end analytics project combining Python, machine learning,
and Power BI for operational business intelligence.*
