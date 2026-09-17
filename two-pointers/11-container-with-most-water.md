---
tags:
  - leetcode
  - neetcode150
time_elapsed: 52
difficulty: medium
category: two-pointers
needed_help: true
link: https://leetcode.com/problems/container-with-most-water/description/
created: 2026-08-29T20:18
updated: 2026-08-29T20:23
---
# 11. Container With Most Water


## Notes
<small><i>Intuition and thought process in solving the question.</i></small>

This was a pretty good question. The trick was actually to figure out the limiting factor, and moving the pointers based on those limiting factors. For example, if the right pointer was larger then the left, then moving the right pointer will not do anything and only make it smaller, therefore you have to move the left pointer. As in, move the limiting factor continously until the left and right meet.

## Code
<small><i>The solution.</i></small>

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        """
        Plan

        - So you have a list of heights
        - You need to find the container that holds the most water
        - This is a two pointer question

        - The question I should be asking now is should I start with two pointers in the front or 
            - one pointer at the front and one at the back?

        - I guess the initial brute force way to solve this problem is to just do pointers on each side
         and then slowly close it. Calculate each, and then grab the max. 
        """
        # brute force approach
        # get every possible answer and shrink - store and get max
        max_volume = 0
        left_index = 0
        right_index = len(height) - 1
        while left_index < right_index:

            container_range = right_index - left_index
            
            left_pointer = height[left_index]
            right_pointer = height[right_index]

            # the container will always be the min of the smaller pointer
            min_pointer = min(left_pointer, right_pointer)

            volume = min_pointer * container_range

            # need to figure out the logic in increasing
            # or decreasing the index
            # maybe we both start as a left pointer?
            if (volume > max_volume):
                max_volume = volume

            print(left_pointer, right_pointer, volume)
            if (left_pointer < right_pointer):
                left_index += 1
            elif (left_pointer > right_pointer):
                right_index -= 1
            else:
                left_index += 1
        
        return max_volume
```

---
## Problem Statement
<small><i>The problem to solve.</i></small>