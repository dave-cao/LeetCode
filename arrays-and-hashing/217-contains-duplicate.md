---
tag: code_problem
time_elapsed: 10
difficulty: easy
category: arrays-and-hashing
created: 2025-12-14T17:02
updated: 2025-12-14T21:28
---


# 217. Contains Duplicate

## Notes
The question is asking us to search an array to see if it has duplicate numbers in it. If it does, then return true, otherwise return false.

In premise, this question seems pretty easy. A brute force approach to this question would be to, for every number, go through every other number and see if repeats giving us $O(n)^2$  solution. 

I went a step further and introduced a hashmap to this problem. Basically created a counter. I would store each number in a map, if the count of the number is more than 1, then return True, otherwise, if it finishes, then return false.

This gives us a time complexity of $O(n)$ and a space complexity of $O(n)$

```python
class Solution:
	def containsDuplicate(self, nums: List[int]) -> bool:
	map = {}
	for num in nums:
		map[num] = map.get(num, 0) + 1
		if map[num] > 1: return True
	return False
```

---
## Problem Statement

Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.


Example 1:

Input: nums = [1,2,3,1]

Output: true

Explanation:

The element 1 occurs at the indices 0 and 3.

Example 2:

Input: nums = [1,2,3,4]

Output: false

Explanation:

All elements are distinct.

Example 3:

Input: nums = [1,1,1,3,3,4,3,2,4,2]

Output: true

 

Constraints:

    1 <= nums.length <= 105
    -109 <= nums[i] <= 109

