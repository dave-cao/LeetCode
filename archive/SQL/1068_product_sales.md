---
created: 2025-04-05T12:22
updated: 2026-01-10T12:56
---
```sql
# Write your MySQL query statement below
# tables
# Sales, Product

SELECT P.product_name, S.year, S.price
FROM Sales as S
INNER JOIN Product as P
ON S.product_id = P.product_id;

```
