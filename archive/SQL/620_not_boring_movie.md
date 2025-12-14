---
created: 2025-04-05T12:22
updated: 2025-12-14T11:49
---
```sql
SELECT *
FROM Cinema
WHERE id % 2 = 1 AND description != "boring"
ORDER BY rating DESC;
```
