# 🍽️ Nikhilé Restaurant Analytics Platform

![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?logo=powerbi)
![DAX](https://img.shields.io/badge/DAX-20%2B%20Measures-blue)
![SQL](https://img.shields.io/badge/SQL-Data%20Source-orange)
![Domain](https://img.shields.io/badge/Domain-F%26B%20%7C%20Kuwait-red)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

> **An 11-page Power BI Owner's Intelligence Dashboard for a Kuwait-based restaurant — covering operations, revenue, profitability, customer behavior, delivery performance, kitchen efficiency, and food wastage, built to turn raw restaurant data into actionable business decisions.**

## 📊 Live Dashboard 🔗 [View Live Dashboard](https://app.powerbi.com/links/PtixkxZs4k?ctid=56c1d497-700b-49cf-8f8d-3dd6b20d522f&pbi_source=linkShare) 
---

## 🎯 Business Objectives

This dashboard was built to answer the questions every restaurant owner asks daily:

- ✅ Monitor daily revenue and profitability health
- ✅ Identify peak hours and busiest days for staffing
- ✅ Analyse menu performance and dish profitability
- ✅ Control costs — salaries, utilities, inventory
- ✅ Reduce wastage and save money on ingredients
- ✅ Understand guest behaviour, loyalty, and segments
- ✅ Track delivery partners and kitchen efficiency
- ✅ Make data-driven decisions to turn loss into profit

---

## 📊 Dataset Overview

| Metric | Value |
|--------|-------|
| **Total Revenue** | KWD 368K |
| **Total Orders** | 11K |
| **Unique Customers** | 7K |
| **Net Profit** | -4,740K (KWD) |
| **Average Rating** | 4.32 |
| **Currency** | Kuwaiti Dinar (KWD) |
| **Tools** | Power BI · DAX · SQL |

---

## 📁 Dashboard Structure — 11 Pages

| # | Page | Business Question Answered |
|---|------|---------------------------|
| 1 | **Home** | Navigation hub — overview of all KPIs and objectives |
| 2 | **Executive Overview** | How is my business performing this month? |
| 3 | **Trend Analysis** | Who are my customers, when do they come, how do they pay? |
| 4 | **Peak & Off-Peak** | When exactly is my restaurant busiest? Should I staff up? |
| 5 | **Dish Performance Analysis** | Which dishes make the most money and which are inefficient? |
| 6 | **Expense Analysis** | Where is my money going and why am I losing it? |
| 7 | **Wastage Analysis** | Why am I wasting food and how much is it costing me? |
| 8 | **Customer Analysis** | Who exactly are my customers and how do I retain them? |
| 9 | **Delivery Analysis** | Which delivery partner is performing best and why? |
| 10 | **Prep Time Analysis** | How efficient is my kitchen and where are the bottlenecks? |
| 11 | **Recommendations** | What should I do now? |

---

## 🔥 Key Pages — Deep Dive

### 📈 Executive Overview
- Revenue MoM% tracking with live KPI cards
- Cost structure analysis across Inventory, Salaries, Marketing, Utilities
- Menu category revenue trends (Beverage, Dessert, Main Course, Starter)
- Sales channel mix (Dine-in vs Delivered)

### 🔥 Peak Hours Intelligence
- **Demand Heatmap** — Day of Week × Hour of Day matrix showing exact order volume
- Identified **Thursday 22:00** as peak hour with 478 average orders/hour
- Weekend vs weekday revenue comparison
- Top performing service hours table with revenue and average order value

### 🍴 Menu Performance Scorecard
A multi-dimensional dish analysis combining 4 metrics per item:
- **Orders by Item** — popularity
- **Revenue by Item** — financial contribution
- **Average Dish Rating** — customer satisfaction
- **Average Prep Time** — kitchen efficiency

This goes beyond traditional menu engineering (2 dimensions) to give a complete operational picture.

### 🗑️ Waste Control Center
Root cause analysis on food wastage:

| Category | % of Total Waste |
|----------|------------------|
| Overstocked | 30.52% |
| Over-prepared | 24.47% |
| Spoiled | 24.14% |
| Expired | 20.87% |

- **KWD 6.3K** avoidable wastage identified
- Top waste-causing ingredients: Chicken, Pasta, Flour, Chocolate
- Waste trend vs avoidable waste tracked monthly

### 🚚 Delivery Operations Hub
- Benchmarked **UberEats, Talabat, Deliveroo, In-House** delivery partners
- On-time delivery rate: only **29%**
- Delivery speed distribution: Fast (29.31%) | Average (42.5%) | Slow (28.19%)
- Revenue and order volume by partner

### 👥 Customer Intelligence Hub
- Customer Retention Funnel: 11K Orders → 7K Unique → 3K Returning → 3K Loyal Members
- Loyalty program penetration: 49.74%
- Guest demographic and age segment revenue analysis
- New vs returning customer mix trends

### 🎯 Executive Recommendations
A dedicated decision-support page — no charts, pure action items:

| Priority | Area | Recommendation | Expected Impact |
|----------|------|----------------|-----------------|
| High | Delivery | Set SLA for partners exceeding 70 mins | Improve on-time delivery |
| High | Wastage | Reduce bakery over-prep by 30% in off-peak | Save ~3.4K KWD annually |
| Medium | Loyalty | Launch digital vouchers for 18–25 segment | Target 55%+ retention |
| Low | Inventory | Implement FIFO stock rotation | Reduce expired waste |
| Medium | Menu | Bundle Sparkling Water + Coffee + Steak | Increase avg order value |
| Medium | Expenses | Audit utilities during off-peak hours | Save 10–15% costs |
| High | Peak Hours | Add 2 kitchen staff during 8–9am, 10–11pm | Reduce prep delays |

Plus a **3-Phase Business Growth Roadmap**:
- **Phase 1 (0–3 months):** Reduce wastage, optimise peak-hour staffing, launch weekday promotions
- **Phase 2 (3–6 months):** Expand loyalty to 70%, launch combo offers, reduce utilities by 10–15%
- **Phase 3 (6–12 months):** Build demand forecasting, dynamic menu pricing, expand in-house delivery

---

## ⚙️ Technical Implementation

### DAX Measures Built

```dax
Revenue MoM% =
VAR CurrentRevenue = SUM(Sales[Revenue])
VAR PreviousRevenue = CALCULATE(SUM(Sales[Revenue]), DATEADD(Date[Date], -1, MONTH))
RETURN
DIVIDE(CurrentRevenue - PreviousRevenue, PreviousRevenue)

Avoidable Waste Cost =
CALCULATE(
    SUM(Wastage[Cost]),
    Wastage[Category] IN {"Overstocked", "Over-prepared"}
)

Retention Rate% =
DIVIDE(
    CALCULATE(DISTINCTCOUNT(Customers[CustomerID]), Customers[OrderCount] > 1),
    DISTINCTCOUNT(Customers[CustomerID])
)

Avg Prep Time =
AVERAGE(Orders[PrepTimeMinutes])
```

### Data Model
- Tables: Customers, Date Table, Expenses, Feedback, Inventory, Menu, Orders, Profit Bridge, Recommendations
- Connected through a clean star schema design
- Custom DAX measures organized in dedicated measure groups

### Visuals Used
- KPI Cards with conditional formatting
- Demand Heatmap (matrix with color scale)
- Waterfall / Bridge chart for cost structure
- Donut charts for category and channel mix
- Gauge visual for Profitability Health Score
- Scatter plot for Prep Time vs Guest Satisfaction
- Funnel chart for customer retention
- Forecast visual with confidence bands

---

## 💡 Key Business Findings

1. **Profitability Crisis** — Net loss of KWD 4.74M against KWD 368K revenue, requiring urgent cost restructuring
2. **Delivery Reliability Gap** — Only 29% on-time delivery across all partners
3. **Avoidable Waste** — KWD 6.3K in preventable food waste, driven primarily by overstocking
4. **Loyalty Opportunity** — Only 49.74% of customers are loyalty members despite 50% retention rate
5. **Peak Hour Staffing Gap** — Thursday evenings consistently understaffed relative to demand

---

## 🛠️ Tools & Technologies

| Category | Tools |
|----------|-------|
| BI Platform | Power BI Desktop |
| Data Modeling | Star Schema, Relationships |
| Calculations | DAX (20+ measures) |
| Data Source | SQL, Excel |
| Visuals | Matrix Heatmap, Waterfall, Gauge, Funnel, Donut, Scatter |

---

## 🔮 Future Enhancements

- Integrate live POS (Point of Sale) data via direct SQL connection for real-time refresh
- Add predictive demand forecasting using Power BI's built-in forecast or Python integration
- Implement Row-Level Security for multi-location franchise reporting
- Add a mobile-optimized layout for on-the-go owner access
- Build automated alert system for SLA breaches and wastage thresholds

---

## 👩‍💻 Author

**Nithu Anna Ninan**
- 🔗 LinkedIn: [linkedin.com/in/nithu-ninan](https://linkedin.com/in/nithu-ninan)
- 📧 Email: nithuanna24@gmail.com
- 🐙 GitHub: [github.com/nithu-ninan](https://github.com/nithu-ninan)

---

## ⭐ If you found this project useful, please give it a star!

---

*Built with Power BI · DAX · SQL | Domain: Restaurant Business Intelligence | Region: Kuwait*
