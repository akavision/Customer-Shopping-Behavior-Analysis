# 🛍️ Customer Shopping Behavior Analysis

An end-to-end data analytics project analyzing customer shopping behavior across 3,900 transactions — combining Python-based data cleaning, PostgreSQL-powered SQL analysis, and an interactive Power BI dashboard to uncover actionable retail insights.

---

## 📌 Short Description / Purpose

This project delivers a complete analytics pipeline for understanding customer purchasing patterns, product preferences, discount behavior, and subscription trends. Starting from raw data, the project covers data cleaning and feature engineering in Python, structured business analysis using SQL in PostgreSQL, and a final interactive dashboard built in Power BI. It is intended for use by retail analysts, marketing strategists, and business decision makers who want data-driven answers to real-world customer behavior questions.

---

## 🛠️ Tech Stack

The project was built using the following tools and technologies:

- 🐍 **Python (Pandas)** – Data loading, exploration, cleaning, missing value imputation, feature engineering, and database integration.
- 🗄️ **PostgreSQL** – Structured SQL analysis to answer 10 key business questions using aggregations, CTEs, window functions, and subqueries.
- 📊 **Power BI Desktop** – Interactive dashboard for visual presentation of key insights.
- 📂 **Power Query** – Data transformation layer within Power BI for reshaping the cleaned dataset.
- 🧠 **DAX (Data Analysis Expressions)** – Calculated measures including Average Purchase Amount, Average Review Rating, and Number of Customers.
- 📁 **File Format** – `.pbix` for Power BI dashboard; `.ipynb` for Python notebook; `.sql` for SQL queries; `.xls` for raw dataset.

---

## 📂 Data Source

**Source:** Customer Shopping Behavior Dataset (Kaggle)

**Dataset Summary:**
- Rows: 3,900
- Columns: 18
- Missing Data: 37 null values in the Review Rating column (imputed using category-wise median)

**Key Features:**

- Customer Demographics: `age`, `gender`, `location`, `subscription_status`
- Purchase Details: `item_purchased`, `category`, `purchase_amount`, `season`, `size`, `color`
- Shopping Behavior: `discount_applied`, `previous_purchases`, `frequency_of_purchases`, `review_rating`, `shipping_type`, `payment_method`
- Engineered Features: `age_group` (binned from age), `purchase_frequency_days` (derived from purchase data)

---

## 🔄 Project Workflow

This project follows a complete end-to-end analytics pipeline:

```
Raw Data (.xls)
     ↓
Python (Pandas) — Cleaning, Feature Engineering
     ↓
PostgreSQL — SQL Business Analysis (10 Queries)
     ↓
Power BI — Interactive Dashboard
```

---

## ✨ Features / Highlights

### 🔴 Business Problem

Retail businesses collect large volumes of customer transaction data but often struggle to extract actionable insights from it. Key questions such as:

- Which customer segments drive the most revenue?
- Are discounts attracting high-spending customers or only bargain hunters?
- Do subscribers spend more than non-subscribers?
- Which products are most returned or highly rated?
- How do purchasing patterns vary across age groups and shipping preferences?

...require structured analysis across multiple dimensions that raw data alone cannot answer.

---

### 🎯 Goal of the Project

To build a full analytics pipeline that:

- Cleans and prepares raw retail data for analysis.
- Answers 10 structured business questions using SQL.
- Visualizes key findings in an interactive Power BI dashboard.
- Delivers actionable business recommendations based on data insights.

---

### 🐍 Python — Data Preparation

- **Data Loading:** Imported dataset using `pandas`.
- **Initial Exploration:** Used `df.info()` and `df.describe()` for structure and summary statistics.
- **Missing Data Handling:** Imputed 37 null values in `review_rating` using the median rating per product category.
- **Column Standardization:** Renamed all columns to snake_case for consistency.
- **Feature Engineering:**
  - Created `age_group` by binning customer ages into Young Adult, Adult, Middle-aged, and Senior.
  - Created `purchase_frequency_days` derived from purchase frequency data.
- **Data Consistency Check:** Verified redundancy between `discount_applied` and `promo_code_used`; dropped `promo_code_used`.
- **Database Integration:** Connected Python script to PostgreSQL and loaded the cleaned DataFrame into the database for SQL analysis.

---

### 🗄️ SQL — Business Analysis (PostgreSQL)

10 structured queries were written to answer key business questions:

| # | Question | Key Finding |
|---|----------|-------------|
| 1 | Revenue by Gender | Male: $157,890 / Female: $75,191 |
| 2 | High-Spending Discount Users | 839 customers used discounts but spent above average |
| 3 | Top 5 Products by Rating | Gloves (3.86), Sandals (3.84), Boots (3.82), Hat (3.80), Skirt (3.78) |
| 4 | Shipping Type Comparison | Express ($60.48) vs Standard ($58.46) avg spend |
| 5 | Subscribers vs Non-Subscribers | Similar avg spend (~$59) but non-subscribers contribute 73% of total revenue |
| 6 | Most Discount-Dependent Products | Hat (50%), Sneakers (49.66%), Coat (49.07%) |
| 7 | Customer Segmentation | Loyal: 3,116 / Returning: 701 / New: 83 |
| 8 | Top 3 Products per Category | Jewelry, Blouse, Sandals, Jacket lead their categories |
| 9 | Repeat Buyers & Subscriptions | Most repeat buyers (2,518) are non-subscribers |
| 10 | Revenue by Age Group | Young Adult: $62,143 / Middle-aged: $59,197 / Adult: $55,978 / Senior: $55,763 |

**SQL techniques used:** `GROUP BY`, `HAVING`, `Subqueries`, `CTEs (WITH)`, `Window Functions (ROW_NUMBER, PARTITION BY)`, `CASE WHEN`, `ROUND`, `AVG`, `SUM`, `COUNT`

---

### 📊 Power BI Dashboard — Key Visuals

**🔢 Top KPI Cards**
- **Total Revenue:** 233K
- **Number of Customers:** 3.9K
- **Average Purchase Amount:** $59.76
- **Average Review Rating:** 3.75

**🍩 % of Customers by Subscription Status (Donut Chart)**
- Non-Subscribers: 73%
- Subscribers: 27%

**📊 Revenue by Category (Bar Chart)**
Clothing leads in revenue, followed by Accessories, Footwear, and Outerwear.

**📊 Sales by Category (Bar Chart)**
Clothing also leads in sales volume, consistent with revenue ranking.

**📊 Revenue by Age Group (Bar Chart)**
Young Adults generate the highest revenue ($62K), followed closely by Middle-aged customers ($59K).

**📊 Sales by Age Group (Bar Chart)**
Young Adults and Middle-aged customers dominate in purchase volume as well.

**🎛️ Interactive Filter Panel**
Left-side slicers enable dynamic filtering by:
- Subscription Status (Yes / No)
- Gender (Female / Male)
- Category (Accessories, Clothing, Footwear, Outerwear)
- Shipping Type (2-Day, Express, Free, Next Day Air, Standard, Store Pickup)

---

### 💡 Business Recommendations

- **Boost Subscriptions:** Only 27% of customers are subscribers despite similar spending levels — promote exclusive subscriber benefits to drive conversions.
- **Customer Loyalty Programs:** With 3,116 loyal customers, reward programs can deepen engagement and increase average order value.
- **Review Discount Policy:** Products like Hat and Sneakers have ~50% discount rates — balance promotional spend with margin control.
- **Product Positioning:** Highlight top-rated products (Gloves, Sandals, Boots) in marketing campaigns to leverage positive sentiment.
- **Targeted Marketing:** Focus acquisition efforts on Young Adults and Middle-aged segments, who drive the highest revenue and purchase volumes.
- **Express Shipping Upsell:** Express shipping users spend slightly more ($60.48 vs $58.46) — promote faster shipping options as a premium upsell.

---

## 📸 Dashboard Preview

![Customer Behavior Analytics Dashboard](https://raw.githubusercontent.com/akavision/Customer-Shopping-Behavior-Analysis/main/Screenshot%20of%20the%20Dashboard.png)

---

## 🚀 How to Use

1. **Python Analysis:** Open `Customer_Shopping_Behaviour_Analysis.ipynb` in Jupyter Notebook and run all cells to reproduce the data cleaning and feature engineering steps.
2. **SQL Analysis:** Connect to PostgreSQL, load the cleaned dataset, and run queries from `customer_behavior_sql_queries.sql` to reproduce all 10 business analyses.
3. **Power BI Dashboard:** Open `customer_behavior_dashboard.pbix` in Power BI Desktop to explore the interactive dashboard.
4. Use the **filter panel** on the left to slice data by subscription status, gender, category, and shipping type.

---

*Built by Akhilesh Madwalkar | Python | SQL | PostgreSQL | Power BI | Data Analytics*
