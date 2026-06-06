---
created: 2025-04-05T12:22
updated: 2026-01-10T12:56
---
```sql
SELECT 
    name, bonus
FROM 
    Employee as e
LEFT JOIN
    Bonus as b ON e.empId = b.empId
WHERE b.bonus < 1000 OR b.bonus IS NULL;
```
