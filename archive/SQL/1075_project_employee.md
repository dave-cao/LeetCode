---
created: 2025-04-05T12:22
updated: 2026-01-10T12:56
---
```sql
SELECT p.project_id, ROUND(SUM(experience_years) / COUNT(experience_years), 2) AS average_years
FROM Project AS p
JOIN Employee as e ON p.employee_id = e.employee_id
GROUP BY project_id;
```
