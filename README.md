# 🛍️ Customer Shopping Behavior Analysis

> End-to-end retail analytics project — from raw transactional data to a business-ready Power BI dashboard.

Analyzing **3,900 customer transactions** to uncover *who* buys, *what* they buy, and *why* — turning shopping behavior into actionable business recommendations for revenue growth, loyalty, and marketing strategy.

---

## 🧰 Tech Stack

<p align="left">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas"/>
  <img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white" alt="Jupyter"/>
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL"/>
  <img src="https://img.shields.io/badge/SQLAlchemy-D71F00?style=for-the-badge&logo=python&logoColor=white" alt="SQLAlchemy"/>
  <img src="https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black" alt="Power BI"/>
</p>

| Layer | Tool | Purpose |
|---|---|---|
| 🐍 Data Prep & Cleaning | `Python`, `pandas` | Load, clean, and engineer features on the raw dataset |
| 📓 Exploration | `Jupyter Notebook` | Interactive EDA and transformation pipeline |
| 🗄️ Data Storage & Querying | `PostgreSQL`, `SQLAlchemy`, `psycopg2` | Load cleaned data into a relational DB and run business queries |
| 📊 Visualization | `Power BI` | Interactive dashboard for stakeholder-facing insights |
| 📄 Reporting | PDF Report | Written summary of findings and recommendations |

---

## 📌 Business Problem

A retail company wants to understand shifting purchase patterns across demographics, product categories, and channels — and to know **which factors (discounts, reviews, seasons, payment type) actually drive repeat purchases and loyalty.**

**Core question:**
> How can the company leverage consumer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategy?

---

## 📂 Dataset

- **Rows:** 3,900 transactions
- **Columns:** 18
- **Includes:** demographics (age, gender, location, subscription status), purchase details (item, category, amount, season, size, color), and behavior signals (discounts, promo codes, previous purchases, purchase frequency, review rating, shipping type)

📁 [`customer_shopping_behavior.csv`](./customer_shopping_behavior.csv)

---

## 🔄 Project Workflow

```
Raw CSV
   │
   ▼
[ Python / Pandas ]  →  clean data, impute missing ratings, engineer features
   │
   ▼
[ PostgreSQL via SQLAlchemy ]  →  load cleaned data, run business queries
   │
   ▼
[ Power BI ]  →  build interactive dashboard
   │
   ▼
[ Report ]  →  summarize insights & recommendations
```

### 1️⃣ Data Preparation (Python)
- Loaded and inspected data with `df.info()` / `df.describe()`
- Imputed 37 missing `Review Rating` values using the **median rating per category**
- Standardized columns to `snake_case`
- Engineered `age_group` (quartile-based: Young Adult / Adult / Middle-aged / Senior)
- Engineered `purchase_frequency_days` by mapping purchase frequency labels (Weekly, Monthly, Annually, etc.) to numeric day intervals
- Verified `discount_applied` and `promo_code_used` were redundant → dropped the duplicate column
- Loaded the cleaned DataFrame into **PostgreSQL** for downstream SQL analysis

📓 [`Customer_Shopping_Behavior_Analysis.ipynb`](./Customer_Shopping_Behavior_Analysis.ipynb)

### 2️⃣ Business Analysis (SQL)
Structured queries were designed to answer key business questions, including:
1. Revenue by gender
2. High-spending customers who still used discounts
3. Top 5 products by review rating
4. Standard vs. Express shipping — spend comparison
5. Subscribers vs. non-subscribers — spend comparison
6. Products most dependent on discounts
7. Customer segmentation — New / Returning / Loyal
8. Top 3 products per category
9. Correlation between repeat purchases (>5) and subscriptions
10. Revenue contribution by age group

🗃️ [`customer_behavior_sql_queries.sql`](./customer_behavior_sql_queries.sql)

### 3️⃣ Visualization (Power BI)
An interactive dashboard surfaces the findings above for non-technical stakeholders.

📊 [`customer_behavior_dashboard.pbix`](./customer_behavior_dashboard.pbix)

### 4️⃣ Reporting
Full write-up of methodology, EDA, and analysis:

📄 [`Customer Shopping Behavior Analysis.pdf`](./Customer%20Shopping%20Behavior%20Analysis.pdf)
📄 [`Business Problem Document.pdf`](./Business%20Problem%20%20Document.pdf)

---

## 💡 Key Business Recommendations

- **Boost subscriptions** — promote exclusive perks to convert casual shoppers into subscribers
- **Reward loyalty** — build programs that move repeat buyers into the "Loyal" segment
- **Rethink discounting** — balance short-term sales lift against long-term margin health
- **Double down on winners** — spotlight top-rated, best-selling products in campaigns
- **Target smart** — focus marketing spend on the highest-revenue age groups and express-shipping customers

---

## 📁 Repository Structure

```
customer_behavior_analysis/
├── customer_shopping_behavior.csv              # Raw dataset (3,900 rows × 18 cols)
├── Customer_Shopping_Behavior_Analysis.ipynb   # Python data cleaning & feature engineering
├── customer_behavior_sql_queries.sql           # SQL business queries
├── customer_behavior_dashboard.pbix            # Power BI dashboard
├── Business Problem  Document.pdf              # Problem statement & deliverables
├── Customer Shopping Behavior Analysis.pdf     # Full analysis report
└── README.md
```

---

## 🚀 Getting Started

```bash
# Clone the repo
git clone https://github.com/mehulagarwal17/customer_behavior_analysis.git
cd customer_behavior_analysis

# Install dependencies
pip install pandas sqlalchemy psycopg2-binary

# Open the notebook
jupyter notebook Customer_Shopping_Behavior_Analysis.ipynb
```

To reproduce the SQL analysis, load the cleaned DataFrame into a local PostgreSQL instance and open `customer_behavior_dashboard.pbix` in Power BI Desktop for the visual layer.

---

## 🙋 Author

**Mehul Agarwal**
Data & Community Builder · https://github.com/mehulagarwal17
