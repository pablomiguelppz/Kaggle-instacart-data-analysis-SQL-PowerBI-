### Table row counts

```sql
SELECT 'orders' AS table, COUNT(*) FROM orders
UNION ALL SELECT 'products', COUNT(*) FROM products
UNION ALL SELECT 'order_products_prior', COUNT(*) FROM order_products_prior
UNION ALL SELECT 'order_products_train', COUNT(*) FROM order_products_train
UNION ALL SELECT 'aisles', COUNT(*) FROM aisles
UNION ALL SELECT 'departments', COUNT(*) FROM departments;
```

**Result:**

| table                 | count     |
|----------------------|-----------|
| orders               | 3,421,083 |
| products             | 49,688    |
| order_products_prior | 32,434,489|
| order_products_train | 1,384,617 |
| aisles               | 134       |
| departments          | 21        |

---

### Query to check users with the most orders

```sql
SELECT user_id, COUNT(*) AS n_orders
FROM orders
GROUP BY user_id
ORDER BY n_orders DESC
LIMIT 10;
```

---

### Most sold items (raw count)

```sql
SELECT op.product_id, 
       p.product_name, 
       COUNT(*) AS times_sold
FROM order_products_prior op
JOIN products p 
     ON p.product_id = op.product_id
GROUP BY op.product_id, p.product_name
ORDER BY times_sold DESC
LIMIT 20;
```

---

### Most common order times

```sql
SELECT order_hour_of_day,
       COUNT(*) AS n_orders
FROM orders
GROUP BY order_hour_of_day
ORDER BY order_hour_of_day;
```

---

## 📊 Business Question A — Which departments generate the most orders?

We create a materialized summary table showing which departments sell the most items and appear in the most orders.

> This is a physical aggregated table — something real analytics teams store for dashboards.

### ✅ SQL — Create aggregated department sales table

```sql
CREATE TABLE agg_department_sales AS
SELECT
    d.department,
    COUNT(op.product_id) AS total_items_sold,
    COUNT(DISTINCT o.order_id) AS total_orders
FROM order_products_prior op
JOIN products p ON op.product_id = p.product_id
JOIN departments d ON p.department_id = d.department_id
JOIN orders o ON op.order_id = o.order_id
GROUP BY d.department;
```
Customer Reorder Behavior

```sql
CREATE TABLE agg_reorder_rate AS
SELECT
    op.product_id,
    p.product_name,
    SUM(CASE WHEN reordered = 1 THEN 1 ELSE 0 END)::float / COUNT(*) AS reorder_rate,
    COUNT(*) AS total_orders
FROM order_products_prior op
JOIN products p ON op.product_id = p.product_id
GROUP BY op.product_id, p.product_name
HAVING COUNT(*) > 50;  -- avoid noise from uncommon products
```
Customer Lifetime Metrics

```sql
CREATE TABLE agg_time_patterns AS
SELECT
    order_dow,
    order_hour_of_day,
    COUNT(*) AS n_orders
FROM orders
GROUP BY order_dow, order_hour_of_day;
```
```sql
CREATE TABLE agg_user_lifetime AS
SELECT
    user_id,
    COUNT(*) AS total_orders,
    AVG(days_since_prior_order) AS avg_days_between_orders,
    MIN(order_number) AS first_order_number,
    MAX(order_number) AS last_order_number
FROM orders
GROUP BY user_id;


---

