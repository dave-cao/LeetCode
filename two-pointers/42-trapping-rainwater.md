---
tags:
  - leetcode
  - neetcode150
time_elapsed: 120
difficulty: hard
category: arrays-and-hashing
needed_help: true
link: https://leetcode.com/problems/trapping-rain-water/
created: 2026-09-16T20:23
updated: 2026-09-16T20:25
---
# 42. Trapping Rain Water

## Notes
<small><i>Intuition and thought process in solving the question.</i></small>

This was not intuitive and was fking hard as fk. But once you got the basic concept, solving for the brute force option wasn't bad. You had to puzzle out the final equation which was the minimum of the max left and the max right.

## Code
<small><i>The solution.</i></small>

```python
class Solution:
    def trap(self, height: List[int]) -> int:
        max_right = [0] * len(height)
        max_left = [0] * len(height)
        minimum = [0] * len(height)

        # get left maxes
        for i in range(len(height)):
            left = i - 1
            if left < 0:
                max_left[i] = 0
            else:
                if height[i - 1] > max_left[i - 1]:
                    max_left[i] = height[i - 1]
                else:
                    max_left[i] = max_left[i - 1]

        # get right maxes
        for i in range(len(height) -1, -1, -1):
            right = i + 1
            if right > len(height) - 1:
                max_right[i] = 0
            else:
                if height[i + 1] > max_right[i + 1]:
                    max_right[i] = height[i + 1]
                else:
                    max_right[i] = max_right[i + 1]

        rain_water = 0
        for i in range(len(height)):
            left = max_left[i]
            right = max_right[i]
            minimum_unit = min(left, right)
            calculation = (minimum_unit - height[i])
            if calculation > 0:
                rain_water += calculation
        
        return rain_water


    def trap_brute(self, height: List[int]) -> int:
        # min(l, r) - h[i]


        trapped = 0
        for i in range(len(height)):
            # for each bar
            # get the right and left max
            left_max = self.get_left_max(height, i)
            right_max = self.get_right_max(height, i)

            trapped_unit = min(left_max, right_max) - height[i]
            if (trapped_unit > 0):
                trapped += trapped_unit
        return trapped

    def get_left_max(self, heights: List[int], index: int):
        current = index
        height_max = 0
        while current > 0:
            current -= 1
            current_height = heights[current]
            if (current_height > height_max):
                height_max = current_height
        return height_max

    def get_right_max(self, heights: List[int], index: int):
        current = index
        height_max = 0
        while current < len(heights) - 1:
            current += 1
            current_height = heights[current]
            if (current_height > height_max):
                height_max = current_height
        return height_max

```

---
## Problem Statement
<small><i>The problem to solve.</i></small>

# Trapping Rain Water

Hard Topics Company Tags Hints

You are given an array of non-negative integers `height` which represent an elevation map. Each value `height[i]` represents the height of a bar, which has a width of `1`.

Return the total amount of water that can be trapped between the bars.

  

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/0c25cb81-1095-4382-fff2-6ef77c1fd100/public)

```java
Input: height = [0,2,0,3,1,0,1,3,2,1]

Output: 9
```

**Constraints:**

- `1 <= height.length <= 20,000`
- `0 <= height[i] <= 100,000`