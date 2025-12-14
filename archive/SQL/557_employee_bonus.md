---
created: 2025-04-05T12:22
updated: 2025-12-14T11:49
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
