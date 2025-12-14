---
created: 2025-04-05T12:22
updated: 2025-12-14T11:49
---
```sql
SELECT r.contest_id, ROUND(COUNT(r.user_id) / (SELECT COUNT(*) FROM Users) * 100, 2) AS percentage
FROM Users AS u
JOIN Register AS r ON u.user_id = r.user_id
GROUP BY r.contest_id
ORDER BY percentage DESC, r.contest_id ASC;
```
