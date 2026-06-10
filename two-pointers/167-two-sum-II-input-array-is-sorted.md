---
tags:
  - leetcode
  - neetcode150
time_elapsed: 10
difficulty: medium
category: two-pointers
needed_help: false
link: https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/
---
# 167. Two Sum II - Input Array Is Sorted

## Notes
<small><i>Intuition and thought process in solving the question.</i></small>

The mistake here is thinking about this in terms of the regular two sum problem. This is 100% a pointer problem. The key point here is that the list is already sorted and its in non-decreasing order. That means if we have two numbers, and they don't add up, we can decide whether to move the left or right pointer. 

In this case, if the number is too large, we move the right pointer left one. If the number is too small, we move the number to the right once.

## Code
<small><i>The solution.</i></small>

```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        # The challenge here is using constant space while still being good
        left_pointer_index = 0
        right_pointer_index = len(numbers) - 1

        while left_pointer_index < right_pointer_index:
            left_num = numbers[left_pointer_index]
            right_num = numbers[right_pointer_index]

            current_sum = left_num + right_num
            if current_sum == target:
                return [left_pointer_index + 1, right_pointer_index + 1]
            
            if current_sum > target:
                right_pointer_index -= 1
            else:
                left_pointer_index += 1
        return []
```

---
## Problem Statement
<small><i>The problem to solve.</i></small>

# Two Integer Sum II

Medium Topics Company Tags Hints

Given an array of integers `numbers` that is sorted in **non-decreasing order**.

Return the indices (**1-indexed**) of two numbers, `[index1, index2]`, such that they add up to a given target number `target` and `index1 < index2`. Note that `index1` and `index2` cannot be equal, therefore you may not use the same element twice.

There will always be **exactly one valid solution**.

Your solution must use O(1)O(1) additional space.

**Example 1:**

```java
Input: numbers = [1,2,3,4], target = 3

Output: [1,2]
```

Explanation:  
The sum of 1 and 2 is 3. Since we are assuming a 1-indexed array, `index1` = 1, `index2` = 2. We return `[1, 2]`.

**Constraints:**

- `2 <= numbers.length <= 1000`
- `-1000 <= numbers[i] <= 1000`
- `-1000 <= target <= 1000`