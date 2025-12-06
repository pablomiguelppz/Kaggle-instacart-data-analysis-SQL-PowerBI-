# Kaggle-instacart-data-analysis-SQL-PowerBI-
Sales data extracted from kaggle, 6 csv including orders, products, etc... Analysis was done using SQL and PowerBI

Retail Analytics with SQL & Power BI — Instacart Case Study
1. Project Motivation

Modern data roles — Data Analyst, Business Intelligence Analyst, Data Engineer — all require fluency in:

SQL (data extraction, cleaning, aggregation)

Power BI or Excel (data visualization & reporting)

Realistic business context (not toy datasets)

This project was created to showcase exactly those skills in a clean, end-to-end, employer-ready workflow.

2. Why SQL?

SQL is the primary language used across the industry to:

Extract data from relational databases

Clean & transform raw tables

Generate aggregated business metrics

Build datasets ready for dashboards

Unlike Python notebooks, SQL reflects how real analysts work inside Redshift, Snowflake, BigQuery, or PostgreSQL.
SQL is essential — every job listing requires it.

This project demonstrates:

Joins across 6+ tables

Window functions

Aggregated tables

Data modeling

Real business KPIs

3. Why the Instacart Dataset?

The Instacart Online Grocery Shopping Dataset is one of the best public retail datasets:

Real-world transactions

3 million+ orders

High cardinality (products, aisles, departments)

Multi-table relational structure

Supports realistic business questions

This makes it perfect for showcasing:

SQL skills on medium-large datasets

Metrics that look like actual retail/e-commerce analytics

A workflow that mirrors real BI teams

4. Business Questions

These questions were chosen because they mirror exactly what BI analysts solve in retail & e-commerce:

A. What departments generate the most sales?

Which product categories drive the business?

Which departments should be prioritized in promotions?

B. What products have the highest reorder rate?

Which products have strong customer loyalty?

Which items should have inventory priority?

C. At what times do customers place the most orders?

Staffing decisions

Promotion timing

Delivery logistics

D. What is the lifetime order behavior of customers?

Heavy vs casual users

Retention analysis

Frequency of purchase

These questions lead to the creation of clean aggregated tables that serve as sources for Power BI dashboards.

5. Project Steps
Step 1 — Load CSVs into PostgreSQL

Created schema instacart

Created all 6 tables (orders, products, departments, etc.)

Used COPY FROM to load data

Step 2 — SQL EDA

Simple queries to understand:

Row counts

Most sold products

Ordering times

User ordering patterns

Step 3 — Business Aggregations

Materialized tables:

agg_department_sales

agg_reorder_rate

agg_time_patterns

agg_user_lifetime

Step 4 — Power BI Dashboard

A dashboard that answers the business questions with visuals:

Top-selling departments

Reorder likelihood by product

Order heatmap (day vs hour)

User retention metrics

6. Skills Demonstrated
Technical Skills

PostgreSQL

SQL joins & aggregations

Schema design

Data cleaning

Power BI visualization

Git version control

Business Skills

KPI design

Retail category analysis

Customer retention analysis

Demand seasonality & time patterns

Communicating insights clearly
