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
