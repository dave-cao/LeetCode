---
tags:
  - leetcode
  - neetcode150
time_elapsed: 10
difficulty: easy
category: arrays-and-hashing
link: https://leetcode.com/problems/two-sum/description/
created: 2025-12-17T00:42
updated: 2026-01-10T12:56
---
# 1. Two Sum

## Notes
<small><i>Intuition and thought process in solving the question.</i></small>

I got easy on this one just because I have done this question before. The brute force approach to this question would be to do a double for loop, and for each number, get the total with every other number and check to see if its equal to target. If it is, then return the two indices. 

The optimal approach requires us to think a little backwards. Usually the first thought is for `num + x = target` we find all solutions of `num + x` that equal to target. But if we already have target, we can find `x` through `target - num = x`. That's the key principle of the optimal solution.  

Thus, we go through every number, and store the number as a key and the index as a value in a map. For every number that we go through, we solve for `x`. If our `x` is in the map (as in, if we encountered it before), then we can grab the index from the map and return the current index with that index. That's how you solve it.
## Code
<small><i>The solution.</i></small>

```python
class Solution:
	def twoSum(self, nums: List[int], target: int) -> List[int]:
		# go through every number
		map = {}
		for i, num in enumerate(nums):
		
			diff = target - num
			
			# check if the diff is in the map, if it is, then
			# we found our two numbers
			if diff in map:
				return [map.get(diff), i]
		
			# add current number into our map
			map[num] = i
```

---
## Problem Statement
<small><i>The problem to solve.</i></small>

Given an array of integers `nums` and an integer `target`, return the indices `i` and `j` such that `nums[i] + nums[j] == target` and `i != j`.

You may assume that _every_ input has exactly one pair of indices `i` and `j` that satisfy the condition.

Return the answer with the smaller index first.

**Example 1:**

```java
Input: 
nums = [3,4,5,6], target = 7

Output: [0,1]
```

Explanation: `nums[0] + nums[1] == 7`, so we return `[0, 1]`.

**Example 2:**

```java
Input: nums = [4,5,6], target = 10

Output: [0,2]
```

**Example 3:**

```java
Input: nums = [5,5], target = 10

Output: [0,1]
```

**Constraints:**

- `2 <= nums.length <= 1000`
- `-10,000,000 <= nums[i] <= 10,000,000`
- `-10,000,000 <= target <= 10,000,000`
- **Only one valid answer exists.**