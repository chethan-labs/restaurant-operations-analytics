# Restaurant Operations Analytics — GVR Limited

> Business analytics project covering sales, inventory, delivery, and order processing performance across 5 restaurant branches (Jan–Aug 2023). Built to identify operational inefficiencies and quantify the impact of process improvements on wastage, delivery times, and order processing speed.

---

## Project Background

GVR Limited operates 5 restaurant branches across London. This project analyzes 8 months of order-level data to answer the core operational questions a Business Analyst is asked to solve: where is food being wasted, why are deliveries slow, how efficient is order processing, and which channels and branches drive the most revenue.

The dataset is split into two phases — **Pre-Optimization** (January–February 2023) and **Post-Optimization** (March–August 2023) — to measure the before/after impact of three interventions rolled out in March 2023: revised inventory control procedures, delivery route optimization, and automation of the order processing workflow.

---

## Repository Structure

```
gvr-restaurant-operations-analytics/
│
├── data/
│   └── Restaurant_Operations_Data.csv      # Raw order-level dataset (9,181 records, 19 columns)
├── Restaurant_Operations_Analytics.xlsx    # Full analytics workbook (6 sheets, charts, KPIs)
├── .gitignore
└── README.md
```

---

## Dataset Description

**File:** `data/Restaurant_Operations_Data.csv`
**Records:** 9,181 orders
**Period:** January 1 – August 31, 2023
**Branches:** 5 (Camden High Street, Shoreditch East, Canary Wharf, Greenwich Riverside, Kingston Upon Thames)

| Column | Description |
|---|---|
| `OrderID` | Unique order identifier |
| `OrderDate` | Date of order |
| `Branch` | Restaurant branch location |
| `Category` | Menu category (Starters, Mains, Desserts, Beverages) |
| `MenuItem` | Specific item ordered |
| `Quantity` | Units ordered |
| `UnitPrice` | Price per unit (£) |
| `OrderValue` | Total order value (£) |
| `OrderChannel` | Dine-In, Takeaway, or Delivery |
| `DeliveryPartner` | In-House Rider, Deliveroo, Uber Eats, Just Eat, or N/A |
| `PrepTimeMinutes` | Kitchen order processing time |
| `DeliveryTimeMinutes` | Time from dispatch to delivery (Delivery orders only) |
| `TotalTimeMinutes` | Prep + delivery time combined |
| `PaymentMethod` | Card, Cash, or Mobile Wallet |
| `CustomerRating` | Order rating, 1–5 |
| `WastageQuantityKg` | Food wastage logged against the order's ingredients |
| `Weather` | Weather condition on order date |
| `DayType` | Weekday or Weekend |
| `OptimizationPhase` | Pre-Optimization (Jan–Feb) or Post-Optimization (Mar–Aug) |

> **Note:** This is a synthetically generated dataset built for portfolio purposes. No real GVR Limited transaction data is included.

---

## Key Metrics & Insights

### Headline KPIs (Jan–Aug 2023)

| Metric | Value |
|---|---|
| Total Revenue | £115,615 |
| Total Orders | 9,181 |
| Average Order Value | £12.59 |
| Average Customer Rating (Post-Optimization) | 3.99 / 5 |

### Before vs After Optimization

| Metric | Pre-Optimization (Jan–Feb) | Post-Optimization (Mar–Aug) | Improvement |
|---|---|---|---|
| Avg Daily Food Wastage | 2.77 kg | 2.09 kg | **-25%** |
| Avg Delivery Total Time | 67.3 min | 51.2 min | **-24%** |
| Avg Order Prep Time | 22.0 min | 15.4 min | **-30%** |
| Avg Customer Rating | 3.68 / 5 | 3.99 / 5 | +0.31 |

These improvements reflect three interventions rolled out at the start of March 2023:

**Inventory control strategy** — revised stock ordering and portion-control guidance for perishable Starters and Mains reduced average daily food wastage by roughly a quarter, with the largest gains concentrated in the two highest-wastage categories.

**Delivery route optimization** — restructured delivery zones and rider allocation per branch cut average total delivery time by about 24%, benefiting both in-house riders and third-party partners.

**Order processing automation** — introducing automated order routing and kitchen display systems cut average prep time by 30%, directly addressing the bottleneck between order placement and kitchen dispatch.

### Revenue & Channel Mix

Dine-In remains the largest revenue channel, followed by Delivery and then Takeaway. Mains drive the largest share of category revenue, consistent with their higher price point relative to Starters, Desserts, and Beverages.

### Branch Performance

All 5 branches perform within a relatively tight revenue band, with Canary Wharf and Kingston Upon Thames slightly ahead — likely reflecting higher footfall in commercial and suburban high-street locations respectively.

---

## Dashboard Overview

**File:** `Restaurant_Operations_Analytics.xlsx`

A 6-sheet analytics workbook — opens directly in Excel, Google Sheets, or LibreOffice, no additional software required:

| Sheet | What It Answers |
|---|---|
| **Executive Summary** | Headline KPIs, before/after optimization comparison, branch performance, channel split |
| **Sales & Revenue Trends** | Monthly revenue trend, category breakdown, top 10 best-selling menu items |
| **Inventory & Wastage** | Monthly wastage trend, wastage by category, branch-wise before/after wastage comparison |
| **Delivery & Order Processing** | Monthly delivery time trend, delivery partner comparison, order prep time automation impact |
| **Customer Insights** | Rating distribution, payment method split, weekday vs weekend performance |
| **Raw Data** | Full 9,181-row dataset with filters enabled for ad-hoc analysis |

---

## Tools & Methodology

| Tool | Purpose |
|---|---|
| **Excel / Power BI** | Dashboard design, KPI tracking, and data visualization |
| **Python (pandas)** | Data generation, before/after impact analysis |
| **Tableau** (in original role) | Supplementary KPI reporting for stakeholders |

---

## How to Use

```bash
git clone https://github.com/chethan-labs/gvr-restaurant-operations-analytics.git
cd gvr-restaurant-operations-analytics
```

**Explore the data with Python:**
```python
import pandas as pd

df = pd.read_csv('data/Restaurant_Operations_Data.csv')

# Wastage reduction by branch
pre = df[df['OptimizationPhase'] == 'Pre-Optimization']
post = df[df['OptimizationPhase'] == 'Post-Optimization']
print(pre.groupby('Branch')['WastageQuantityKg'].sum())
print(post.groupby('Branch')['WastageQuantityKg'].sum())

# Delivery time by partner
print(df[df['OrderChannel']=='Delivery'].groupby('DeliveryPartner')['TotalTimeMinutes'].mean())
```

**Open the workbook:**
1. Open `Restaurant_Operations_Analytics.xlsx` in Excel, Google Sheets, or LibreOffice Calc
2. Navigate sheets via tabs: Executive Summary, Sales & Revenue Trends, Inventory & Wastage, Delivery & Order Processing, Customer Insights, Raw Data
3. Use the auto-filter on the Raw Data sheet to slice by branch, channel, or date

---

## Author

[github.com/chethan-labs](https://github.com/chethan-labs)

Business Analyst Internship, GVR Limited — January 2023 to August 2023.
