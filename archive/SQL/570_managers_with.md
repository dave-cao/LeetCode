---
created: 2025-04-05T12:22
updated: 2026-01-10T12:56
---
```sql
WITH m_count AS
(SELECT id, managerId, COUNT(managerId) as manager_count
FROM Employee
GROUP BY managerId)

SELECT e.name 
FROM m_count
JOIN Employee AS e ON e.id = m_count.managerId
WHERE m_count.manager_count >= 5;
```
