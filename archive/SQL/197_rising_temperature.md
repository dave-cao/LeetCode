---
created: 2025-04-05T12:22
updated: 2026-01-10T12:56
---
```sql
SELECT W1.id
FROM 
    Weather as W1
JOIN 
    Weather as W2 ON DATEDIFF(W1.recordDate, W2.recordDate) = 1
WHERE W2.temperature < W1.temperature;

```
