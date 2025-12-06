# Instacart Data Analysis with SQL and Power BI

This project analyzes Instacart’s online grocery dataset (6 CSV files from Kaggle) using PostgreSQL for data preparation and Power BI for visualization. The goal is to demonstrate a realistic retail analytics workflow using SQL and standard BI practices.

---

## 1. Project Motivation

Data roles such as Data Analyst, BI Analyst, and Data Engineer rely heavily on SQL for working with relational data. This project uses the Instacart dataset to practice SQL-based exploration, build aggregated tables for analysis, and create a dashboard that answers common retail business questions.

---

## 2. Why SQL

Since SQL is the main tool used across analytics teams, due to the proficient extracting and cleaning of data from databases, I wanted to use SQL even if it isn't the most common sense answer for a Kaggle dataset. For this I used PostgreSQL locally. 

---

## 3. Why the Instacart Dataset from Kaggle

The dataset contains over 3 million orders with detailed information on products, departments, aisles, and user ordering patterns.

Because it is multi-table and resembles real retail data, it is realistic in the sense of needing thoughtful cleaning before analyzing it, and it easily allows for meaningful business questions such as:

- Which product categories perform best?  
- How loyal are customers to specific products?  
- When do users place orders?  
- How frequently do customers return?
- etc

---

## 4. Business Questions

My analysis focuses on four easy-to-come-up-with questions, commonly addressed in e-commerce analytics, all answered/explored using PostgreSQL and SQL's aggregated tables creation:

### A. Which departments generate the most orders?
Useful for understanding category performance and prioritizing promotions.

### B. What products show strong reorder behavior?
Helps identify loyal-user items and potential inventory priorities.

### C. When do customers place orders (hour/day patterns)?
Relevant for staffing, delivery operations, and promotion timing.

### D. What does customer lifetime behavior look like?
Basic retention metrics such as order frequency and time between purchases.

---

## 5. Project Steps

### Step 1 — Load Data
All six CSV files were imported into PostgreSQL using `CREATE TABLE` and `COPY FROM`.

### Step 2 — Exploratory SQL
Initial queries were used to check table size, product counts, user ordering behavior, and ordering times.

### Step 3 — Aggregated Tables
The following tables were created to answer business questions, these tables transfer to PowerBI for visualization:

- `agg_department_sales`  
- `agg_reorder_rate`  
- `agg_time_patterns`  
- `agg_user_lifetime`

### Step 4 — Power BI Dashboard
A simple dashboard was created to visualize category performance, reorder rates, order timing patterns, and user lifetime metrics.

---

## 6. Skills Demonstrated

**Technical**
- PostgreSQL  
- SQL joins, grouping, and window logic  
- Data modeling and cleaning  
- Power BI visualization  
- Git version control  

**Business**
- Category performance analysis  
- Customer retention and reorder behavior  
- Demand timing patterns  
- KPI design and communication  

---
