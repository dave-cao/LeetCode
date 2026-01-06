---
tags:
  - leetcode
  - neetcode150
time_elapsed: 16
difficulty: medium
category: arrays-and-hashing
link: https://leetcode.com/problems/top-k-frequent-elements/description/
created: 2026-01-06T00:58
updated: 2026-01-06T01:19
---
# 347. Top K Frequent Elements

## Notes
<small><i>Intuition and thought process in solving the question.</i></small>

The intuition here was pretty straight forward. We organize the list of numbers into a map by count. Then we sort the map by highest to lowest count. Then we get the  top $k$ from those items.

## Code
<small><i>The solution.</i></small>

```python
class Solution:

def topKFrequent(self, nums: List[int], k: int) -> List[int]:

	# get a count of each item into a dictionary
	map = {}
	for num in nums:
		map[num] = map.get(num, 0) + 1
	
	# sort by value instead of key
	sorted_by_count = sorted(map.items(), key=lambda item: item[1], reverse=True)

	# return top k
	top_k_list = [sorted_by_count[i][0] for i in range(k)]
	return top_k_list

```

---
## Problem Statement
<small><i>The problem to solve.</i></small>

# Top K Frequent Elements

Given an integer array `nums` and an integer `k`, return the `k` most frequent elements within the array.

The test cases are generated such that the answer is always **unique**.

You may return the output in **any order**.

**Example 1:**

```java
Input: nums = [1,2,2,3,3,3], k = 2

Output: [2,3]
```

**Example 2:**

```java
Input: nums = [7,7], k = 1

Output: [7]
```

**Constraints:**

- `1 <= nums.length <= 10^4`.
- `-1000 <= nums[i] <= 1000`
- `1 <= k <= number of distinct elements in nums`.