# 📉 Customer Churn Analysis

**Repository name:** `customer-churn-analysis`

An end-to-end **SQL + Python** data analysis project that investigates why customers churn — from raw, multi-table data to cleaned datasets, engineered features, business KPIs, and visual insights.

---

## 📌 Overview

This project analyzes customer churn for a subscription-based business using SQL and Python. Raw customer, subscription, and support data — spread across three separate tables — is extracted, cleaned, and merged into a single dataset, then explored to uncover the key drivers behind churn, the revenue impact of losing customers, and where the business should focus retention efforts.

---

## 📌 Overview

This project simulates a real-world churn analysis workflow for a subscription-based business. Raw customer, subscription, and support data is pulled from a SQL database, cleaned and merged into a single analysis-ready dataset, and explored to uncover the key drivers behind customer churn — along with the revenue impact of losing those customers.

---

## 🛠️ Tools & Technologies

- **Python** — Pandas, NumPy for data manipulation and feature engineering
- **SQL / SQLite** — relational data storage and querying
- **Matplotlib & Seaborn** — data visualization
- **Jupyter Notebook** — analysis environment

---

## 🧹 Data Cleaning & Preparation

- Connected to a SQLite database and dynamically loaded multiple tables (customer, subscription, support) into separate DataFrames
- Dropped irrelevant/garbage columns and renamed columns for clarity
- Converted date fields from string to proper datetime type across all three tables
- Standardized inconsistent categorical values (e.g., unifying gender labels)
- Filled missing `country` values using a state-to-country mapping derived from existing records
- **Caught and resolved a real data quality issue:** merging the three tables initially produced more rows than expected. Traced the cause to duplicate complaint records in the support table, engineered a `complaint_count` feature to preserve that information, then deduplicated before the final merge — avoiding inflated churn/revenue numbers

---

## ⚙️ Feature Engineering

- **`churn_flag`** — derived from whether a cancellation date exists
- **`tenure`** — days a customer has been active (cancellation date minus start date, or today's date for active customers)
- **`age`** — calculated from date of birth
- **`churn_risk`** — a 3-tier segmentation (Low / Medium / High) built from churn score using conditional logic

---

## 📊 Key Business Metrics Derived

- Overall **churn rate** and **retention rate**
- Churn rate broken down by **plan type** and **subscription type**
- Churn rate by **state**, paired with **total revenue** and **user count** per state
- **ARPU** (Average Revenue Per User)
- **Average customer tenure**
- **Revenue at risk** — total revenue lost from churned customers
- **Escalation rate** and **average complaints per user**
- **Correlation between escalations and churn** — handled missing values carefully (kept as unknown rather than defaulting to "no escalation") to avoid a misleading correlation result

---

## 📈 Visualizations

- Monthly churn trend over time (line chart)
- Churn rate by plan type and by state (bar charts)
- Correlation heatmap across churn-related features — including a comparison between naive label encoding and priority-based ordinal encoding, to show why encoding choice matters for correlation analysis
- Pairplot for exploring relationships across multiple churn-related variables
- Multi-dimensional category plot comparing monthly charges across plan type, gender, and churn risk
- Pivot tables summarizing churn rate, revenue, and user counts by plan type

---

## 🎯 What This Project Demonstrates

- Writing SQL queries to extract and explore multi-table relational data
- Identifying and resolving real data quality issues (duplicates, missing values) before drawing conclusions
- Feature engineering to translate raw fields into business-relevant metrics
- Careful handling of missing data in correlation analysis, rather than silently treating "unknown" as "no"
- Translating a cleaned dataset into a full set of business KPIs a stakeholder would actually ask for
- Choosing the correct encoding strategy (ordinal vs. nominal) before running correlation analysis — a common but easy-to-miss analytical mistake

---

## 🔍 Sample Insight

Escalations show a measurable relationship with customer churn — highlighting the value of tracking and resolving customer complaints early to reduce churn risk, rather than treating escalation handling as a purely reactive process.
