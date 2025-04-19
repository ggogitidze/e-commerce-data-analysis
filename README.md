# 🍏 E-Commerce Data Analysis Using PostgreSQL

## 📌 Overview

This project is a comprehensive end-to-end data analysis case study built entirely using **PostgreSQL and SQL**. It focuses on uncovering meaningful business insights from an e-commerce company's transaction data — without using Python, Excel, or any external statistical tools.

The purpose of this project is to simulate real-world analyst tasks such as:

- Understanding customer purchase behavior
- Measuring discount effectiveness
- Identifying sales patterns and anomalies
- Evaluating performance across segments like device, customer type, and product category

All insights are extracted via SQL queries and visualized using Tableau Public.

---

## 🌟 Business Questions Addressed

| Area                       | Key Questions Explored                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------------------- |
| 📈 Sales & Performance     | What are the most profitable products and categories? How do monthly revenues change?                |
| 🧑‍💻 Customer Behavior    | Do mobile users shop differently than web users? What devices generate higher sales?                 |
| 🏷️ Discounts & Promotions | Do discounts significantly increase sales volume?                                                    |
| 📜 Operational Insights    | Do higher shipping costs occur in specific categories? Are certain order priorities more profitable? |
| 🧪 Hypothesis Testing      | Can we statistically support the impact of device type, discount, priority, or seasonality?          |
| 🧐 Anomaly Detection       | Which orders stand out as outliers in sales, quantity, or profit?                                    |

---

## 🛠️ Tools & Technologies

- **PostgreSQL** – for data storage, cleaning, and analysis
- **pgAdmin 4** – SQL IDE for managing queries and exports
- **Tableau Public** – for interactive dashboard creation
- **CSV** – for query result exports

---

## 📃 Database Schema

**Table:** `ecommerce`

| Column            | Data Type | Description                                 |
| ----------------- | --------- | ------------------------------------------- |
| order_date        | DATE      | Date of the order                           |
| time              | TIME      | Time of order                               |
| aging             | INT       | Age of customer                             |
| customer_id       | INT       | Customer identifier                         |
| gender            | TEXT      | Customer gender                             |
| device_type       | TEXT      | Web or Mobile                               |
| customer_type     | TEXT      | Member or Non-member                        |
| product_category  | TEXT      | Category of the purchased product           |
| product           | TEXT      | Specific product name                       |
| sales             | NUMERIC   | Order value                                 |
| quantity          | INT       | Quantity ordered                            |
| discount          | NUMERIC   | Discount applied                            |
| profit            | NUMERIC   | Profit made from the order                  |
| shipping_cost     | NUMERIC   | Shipping expense                            |
| order_priority    | TEXT      | Priority level: Low, Medium, High, Critical |
| payment_method    | TEXT      | Payment method used                         |

📄 [View full schema definition](./ecommerce_schema.sql)

## 📊 Tableau Dashboards

These dashboards were created using exported query results from PostgreSQL.

1. [📌 Hypothesis Testing Dashboard](https://public.tableau.com/app/profile/giorgi.gogitidze/viz/HypothesisTesting_17200713809870/Hypothesis)

2. [📌 Sales & Profit Analysis](https://public.tableau.com/app/profile/giorgi.gogitidze/viz/SalesandProfitAnalysis_17200713244600/SalesandProfitAnalysis)

3. [📌 Anomaly Detection](https://public.tableau.com/app/profile/giorgi.gogitidze/viz/AnomalyDetection_17200714394430/AnomalyDetection)

---

## 🔍 Example SQL Analyses

### 📌 Revenue Trends Over Time

```sql
SELECT DATE_TRUNC('month', order_date) AS month, SUM(sales) AS revenue
FROM ecommerce
GROUP BY month
ORDER BY month;
```

### 📌  Device-Based Order Value Comparison

```sql
SELECT device_type, AVG(sales) AS avg_order_value, COUNT(*) AS order_count
FROM ecommerce
GROUP BY device_type;
```
### 📌  Discount Effectiveness

```sql
SELECT discount > 0 AS is_discounted, AVG(sales) AS avg_sales, COUNT(*) AS order_count
FROM ecommerce
GROUP BY is_discounted;
```
### 📌 Seasonal Trend Detection

```sql
SELECT EXTRACT(MONTH FROM order_date) AS month, SUM(sales) AS monthly_sales
FROM ecommerce
GROUP BY month
ORDER BY month;
```

## 📈 Hypothesis Tests Performed

All hypotheses were translated into SQL group-based comparisons and visualized in Tableau:

| Hypothesis                                                  | Test Type         | Confirmed |
| ----------------------------------------------------------- | ----------------- | --------- |
| Mobile users generate different order values than web users | t-test proxy      | ✅ Yes     |
| Discounts significantly increase order volume               | t-test proxy      | ✅ Yes     |
| Order priority is correlated with profitability             | ANOVA (SQL logic) | ✅ Yes     |
| Monthly sales show seasonal variation                       | ANOVA proxy       | ✅ Yes     |
| Product category impacts shipping cost                      | ANOVA proxy       | ✅ Yes     |

---

## 🚀 How to Run This Project

1. Clone this repo or download the ZIP
2. Open pgAdmin → Create a database `ecommerce_db`
3. Run [`ecommerce_schema.sql`](./_ecommerce_schema.sql) to create the table
4. Import your CSV into the `ecommerce` table
5. Run scripts in order:
   - `_remove_duplicates.sql`
   - `_fill_nulls.sql`
   - `_exploratory_data_analysis.sql`
   - `_hypothesis_testing.sql`
   - `_a_b_testing.sql`
6. Export outputs and upload them into Tableau Public
7. Customize or embed the dashboard links into your portfolio

---

## 💡 Skills Demonstrated

- Writing clean, optimized SQL for real-world business analytics
- Translating business hypotheses into testable SQL queries
- Building Tableau dashboards using query exports
- Communicating insights using visuals + markdown documentation
- A/B testing & segmentation using SQL logic

---

## 👤 Author
**Giorgi Gogitidze**
