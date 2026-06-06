---
created: 2025-04-05T12:22
updated: 2026-01-10T12:56
---
```sql
SELECT *
FROM Cinema
WHERE id % 2 = 1 AND description != "boring"
ORDER BY rating DESC;
```
