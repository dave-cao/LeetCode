---
tags:
  - leetcode
  - neetcode150
time_elapsed: 46
difficulty: medium
category: arrays-and-hashing
needed_help: false
link: https://leetcode.com/problems/longest-consecutive-sequence/description/
created: 2026-06-06T16:07
updated: 2026-06-06T16:07
---
# 128. Longest Consecutive Sequence

## Notes
<small><i>Intuition and thought process in solving the question.</i></small>

The initial intuition of this question is to sort the array and then just count the sorted array sequences. However that would then just give us a complexity of $O(nlogn)$ which is not what we want. 

The key here is to figure out how a number is a starting sequence or not. My initial idea was to turn it into a hashset and get the smallest number in that hashset. Then remove the numbers as we iterate. Little did I know that getting the smallest number is another $O(n)$ operation which wasn't ideal. 

However, you can find the starting sequences by just checking to see if the number - 1 is within the hashset! If it doesn't, then its a starting sequence!


## Code
<small><i>The solution.</i></small>
```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        """
        """
        if len(nums) == 0:
            return 0

        # turn nums array into a hashset
        num_set = set()
        for num in nums:
            num_set.add(num)

        # get the starting sequences
        starting_numbers = []
        for num in num_set:
            decrement = num - 1
            if decrement not in num_set:
                starting_numbers.append(num)

        max_record = 1
        for starting_num in starting_numbers:
            record = 1
            increment = starting_num + 1
            while increment in num_set:
                record += 1
                increment += 1
            if (record > max_record):
                max_record = record
        return max_record
```

---
## Problem Statement
<small><i>The problem to solve.</i></small>

# Longest Consecutive Sequence

Medium Topics Company Tags Hints

Given an array of integers `nums`, return _the length_ of the longest consecutive sequence of elements that can be formed.

A _consecutive sequence_ is a sequence of elements in which each element is exactly `1` greater than the previous element. The elements do _not_ have to be consecutive in the original array.

You must write an algorithm that runs in `O(n)` time.