
# 🔍 Customer & Sales SQL Data Analysis

> Advanced SQL-based analysis on 10,000+ records to uncover revenue concentration, customer segments, and pricing strategies using MySQL.

---

## 📌 Project Overview

This project performs deep-dive **customer and sales analysis** using Advanced SQL techniques including CTEs, Window Functions, and Cohort Queries on a 10,000+ record MySQL database.

---

## 🛠️ Tools & Technologies

| Tool | Usage |
|------|-------|
| MySQL | Core database & querying |
| Advanced SQL | CTEs, Window Functions, JOINs, Subqueries |
| Microsoft Excel | Result visualization & reporting |

---

## 📊 Key Features

### 1. 💰 Revenue Concentration Analysis
- Identified **25% of total revenue** concentrated in just **2 customer segments**
- Used window functions to rank customers by revenue contribution

### 2. 👥 Customer Cohort Analysis
- Tracked customer purchase behavior over time
- Identified high-value vs churned customer groups

### 3. 📦 Sales Trend Analysis
- Month-over-month and quarter-over-quarter sales trends
- Product-wise and region-wise revenue breakdown

### 4. 🎯 Pricing & Retention Strategy Insights
- Data-driven recommendations for targeted pricing
- Retention strategy based on segment behavior

---

## 📁 Project Structure

```
customer-sales-sql-analysis/
│
├── sql/
│   ├── 01_data_exploration.sql
│   ├── 02_revenue_concentration.sql
│   ├── 03_cohort_analysis.sql
│   ├── 04_window_functions.sql
│   └── 05_pricing_insights.sql
│
├── results/
│   └── analysis_summary.xlsx
│
└── README.md
```

---

## 💡 Sample Queries

### Revenue Concentration (Window Function)
```sql
SELECT 
    customer_segment,
    SUM(revenue) AS total_revenue,
    ROUND(SUM(revenue) * 100.0 / SUM(SUM(revenue)) OVER(), 2) AS revenue_pct
FROM sales
GROUP BY customer_segment
ORDER BY total_revenue DESC;
```

### Cohort Analysis (CTE)
```sql
WITH cohort AS (
    SELECT 
        customer_id,
        MIN(DATE_FORMAT(order_date, '%Y-%m')) AS cohort_month
    FROM orders
    GROUP BY customer_id
)
SELECT 
    c.cohort_month,
    COUNT(DISTINCT o.customer_id) AS active_customers
FROM cohort c
JOIN orders o ON c.customer_id = o.customer_id
GROUP BY c.cohort_month;
```

---

## 🔍 Key Insights

- Top **2 segments** drive **25% of total revenue** — high priority for retention
- **Month 3 cohort** shows highest churn — needs targeted re-engagement
- Segment-specific pricing can improve margins by **10-15%**

---

## 👤 Author

**Deepak Kumar** — Data Analyst  
📧 dk5373189@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/deepak-kumar-39317a25b)  
💻 [GitHub](https://github.com/Deepakkumar62022)

---

## 📜 Skills Demonstrated

`MySQL` `Advanced SQL` `CTEs` `Window Functions` `JOINs` `Subqueries` `Cohort Analysis` `Revenue Analysis` `Data Analytics`
