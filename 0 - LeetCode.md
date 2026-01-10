---
created: 2023-12-14T00:03
updated: 2026-01-10T12:56
---

# Code Problems Database

## Overview

```dataview
TABLE WITHOUT ID
  length(rows) as "Total solved",
  sum(rows.time_elapsed) as "Total mins",
  round(sum(rows.time_elapsed) / length(rows.time_elapsed), 1) as "Avg mins",
  min(rows.time_elapsed) as "Fastest mins",
  max(rows.time_elapsed) as "Slowest mins",
  dateformat(max(rows.created), "MMM dd, yyyy") as "Most recent"
FROM ""
WHERE
  !contains(file.path, "Templates")
  AND !contains(file.path, "archive")
  AND (
    contains(file.tags, "#leetcode")
    OR tag = "leetcode"
    OR contains(tags, "leetcode")
  )
FLATTEN default(created, file.ctime) as created
GROUP BY true
```

## List of all coding problems
```dataview
TABLE WITHOUT ID
  file.link as Completed,
  time_elapsed as Time,
  difficulty as Difficulty,
  dateformat(created, "MMM dd, yyyy") as Date
FROM #leetcode
WHERE !contains(file.path, "Templates")
AND !contains(file.path, "archive")
SORT created DESC
```


## Steps to Solve

- What is data structures and variables do you need to use here?
- What is the brute force method or the easy to approach method?
- Optimize