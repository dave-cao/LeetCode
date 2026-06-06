---
tags:
  - leetcode
  - neetcode150
time_elapsed: 45
difficulty: medium
category: arrays-and-hashing
needed_help: true
link: https://leetcode.com/problems/product-of-array-except-self/
created: 2026-01-10T13:46
updated: 2026-01-10T13:46
---
# 238. Product of Array Except Self

## Notes
<small><i>Intuition and thought process in solving the question.</i></small>

Intuitively, I was able to get the brute force approach quite quickly,. however, I wasn't able to get the optimal solution without help from NeetCode. The idea of having a prefix and postfix array is pretty genius and I understand the concept. Basically, to get the product of the current index, you just need to multiply the product of the numbers before it as well as the numbers after it. 

So we just precompute those numbers and multiply it at the end giving us an $O(n)$ runtime.

## Code
<small><i>The solution.</i></small>
```python

class Solution:

	def productExceptSelf(self, nums: List[int]) -> List[int]:
	
		# get prefix
		prefix = []
		product = 1
		for num in nums:
			product *= num
			prefix.append(product)
			
		# get postfix
		postfix = []
		product = 1
		for i in range(len(nums) - 1, -1, -1):
			num = nums[i]
			product *= num
			postfix.insert(0, product)

		# get result
		result = []
		for i in range(len(nums)):
			previous_num = 1
			previous_i = i - 1
			
			next_num = 1
			next_i = i + 1
		
			if previous_i < 0:
				previous_num = 1
			else:
				previous_num = prefix[previous_i]
				
			if next_i > len(nums) - 1:
				next_num = 1
			else:
				next_num = postfix[next_i]
		
			product = previous_num * next_num
			result.append(product)
	return result
	
	def productExceptSelfBrute(self, nums: List[int]) -> List[int]:
		"""This is the brute force approach"""
		products = []
		for i, num in enumerate(nums):
			product = 1
			for q, num in enumerate(nums):
				if i == q:
					continue
			product *= num
			products.append(product)
		return products

```

---
## Problem Statement
<small><i>The problem to solve.</i></small>

# Products of Array Except Self

Given an integer array `nums`, return an array `output` where `output[i]` is the product of all the elements of `nums` except `nums[i]`.

Each product is **guaranteed** to fit in a **32-bit** integer.

Follow-up: Could you solve it in O(n)O(n) time without using the division operation?

**Example 1:**

```java
Input: nums = [1,2,4,6]

Output: [48,24,12,8]
```

**Example 2:**

```java
Input: nums = [-1,0,1,2,3]

Output: [0,-6,0,0,0]
```

**Constraints:**

- `2 <= nums.length <= 1000`
- `-20 <= nums[i] <= 20`