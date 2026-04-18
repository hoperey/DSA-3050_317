# DSA 3050A Advanced Power BI Exam – E‑commerce Analytics

**Student Name:** Hope Kimandi  
**Admission Number:** 670317 
**Course:** DSA 3050A  
**Class:** SS 2026  

## Project Overview

This project is my complete Power BI analytical solution for the Olist Brazilian E‑commerce dataset. I built an interactive dashboard that helps stakeholders monitor sales performance, customer behaviour, product profitability, and operational efficiency. The work covers everything from raw data preparation to business recommendations.

## Problem Statement

As a BI analyst, I needed to answer key business questions for an online marketplace: Which product categories drive revenue? How do delivery delays affect customer loyalty? Are there regional or seasonal patterns? What actions can improve sales and reduce risks? This dashboard provides the answers.

## Dataset Description

- **Source:** Kaggle – Brazilian E‑Commerce Public Dataset by Olist  
  (https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- **Main table:** `olist_orders_dataset` with approximately 99,000 rows
- **Related tables:** order_items, products, customers, sellers, payments, reviews, category translation
- **Key fields:** order_id, product_id, customer_id, price, freight_value, order_purchase_timestamp, review_score
- I chose this dataset because it offers multiple related tables, a date field for time intelligence, and realistic business challenges.

## Tools Used

- Power BI Desktop (data modelling, DAX, visualisation)
- Power Query (data cleaning and transformation)
- DAX (measures and calculated columns)

## Steps Followed (Exam Parts)

1. **Data Acquisition (Part A)** – I loaded the CSV files and documented the raw data, variables, and relationships.
2. **Data Cleaning (Part B)** – In Power Query, I performed over eight transformations: promoted headers, changed data types, removed nulls, replaced missing values, added conditional columns, extracted date parts, merged the translation table, and removed duplicates.
3. **Data Modeling (Part C)** – I created a star‑schema with `olist_order_items_dataset` as the fact table and dimensions for products, customers, sellers, and orders. I also built a date table (`Dim_Date`) and set up active relationships.
4. **DAX Measures and Calculated Columns (Part D)** – I wrote eight measures (Total Sales, YTD Sales, Sales Growth %, etc.) and two calculated columns (`total_amount`, `estimated_profit`). These power the KPIs and advanced analytics.
5. **Dashboard Design (Part E)** – I designed three report pages:
   - *Executive Summary*: KPI cards, monthly sales trend, top 10 categories, slicers.
   - *Detailed Analysis*: drill‑down matrix, decomposition tree, top performers table, cross‑filtering slicers.
   - *Insights & Performance Monitoring*: time intelligence chart, top/bottom states bar charts, scatter plot with trend line for anomaly detection.
6. **Insights and Recommendations (Part F)** – I derived five business insights and three actionable recommendations from the dashboard.

## Dashboard Features

- **Professional theme** (Corporate) with consistent colours, fonts, and layout.
- **Interactivity:** Slicers for year, state, payment type; cross‑filtering across all visuals.
- **Drill‑down:** Matrix on Page 2 supports year → quarter → month exploration.
- **Advanced visual:** Decomposition tree and scatter plot with trend line.
- **Time intelligence:** YTD and previous month comparisons.

## Key DAX Measures

- `Total Sales = SUM(order_items[price])`
- `YTD Sales = TOTALYTD([Total Sales], Dim_Date[Date])`
- `Previous Month Sales = CALCULATE([Total Sales], DATEADD(Dim_Date[Date], -1, MONTH))`
- `Sales Growth % = DIVIDE([Total Sales] - [Previous Month Sales], [Previous Month Sales])`
- `% Contribution by State = DIVIDE([Total Sales], CALCULATE([Total Sales], ALL(customers[state])))`
- `Top State Rank = RANKX(ALL(customers[state]), [Total Sales])`
- `Total Quantity = COUNTROWS(order_items)`
- `Average Order Value = DIVIDE([Total Sales], DISTINCTCOUNT(orders[order_id]))`

## Key Insights (from Part F)

1. Top three product categories contribute over 45% of revenue – a concentration risk.
2. The Southeast region accounts for nearly 70% of sales, while the North region is underperforming.
3. Delayed deliveries correlate with a roughly 20% lower repeat purchase rate.
4. Sales peak in November/December and drop sharply in January/February (post‑holiday slump).
5. A few products have freight costs exceeding 50% of the product price, indicating profitability issues.

## Challenges Encountered and How I Solved Them

- **Null values in product categories and order status** – I replaced them with "unknown" in Power Query.
- **Date table relationships** – I initially struggled with time intelligence measures showing zeros. I solved this by creating a clean date column using `Date.From` in Power Query and marking the date table explicitly.
- **Previous month sales measure** – I rewrote it using `DATEADD` and ensured the relationship was active.
- **Merging translation table** – I used a left outer merge to bring English category names without losing products.

## Conclusion


## Repository Structure

```
DSA3050A-Advanced-PowerBI-Exam/
├── powerbi/
│   └── DSA3050A_Olist_Solution.pbix
├── screenshots/
│   ├── Part_A/
│   ├── Part_B/
│   ├── Part_C/
│   ├── Part_D/
│   ├── Part_E/
│   └── Part_F/
├── report/
│   └── DSA3050A_Exam_Report.pdf
└── README.md
```

## Links

- **Dataset (Kaggle):** [Brazilian E‑Commerce Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- **Power BI file:** (upload your .pbix or provide a link if size permits)



If everything is ready, you can submit. Congratulations on completing the advanced Power BI exam. If you need any last‑minute adjustments, tell me now.
