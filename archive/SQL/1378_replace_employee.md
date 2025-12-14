---
created: 2025-04-05T12:22
updated: 2025-12-14T11:49
---
```sql
# Write your MySQL query statement below
# table = Employees

SELECT unique_id, name FROM Employees as E LEFT JOIN EmployeeUNI as U ON E.id = U.id;
```
