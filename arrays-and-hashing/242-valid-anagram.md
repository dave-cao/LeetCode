---
tags:
  - leetcode
  - neetcode150
time_elapsed: 3
difficulty: easy
category: arrays-and-hashing
link: https://leetcode.com/problems/valid-anagram/description/
created: 2025-12-17T00:27
updated: 2026-01-10T12:56
---
# 242. Valid Anagram

## Notes
<small><i>Intuition and thought process in solving the question.</i></small>

An anagram is when the source string has the same number of letters as the target string exactly. My simple solution was to get a count of both strings, and if they are equal to each other, then return true, otherwise return false.

I use a map to get the count of each string. Each string needs a single pass, therefore the time complexity is $O(n)$ and each require a map, so the space complexity is $O(n)$
## Code
<small><i>The solution.</i></small>
```python
class Solution:
	def isAnagram(self, s: str, t: str) -> bool:
		# an anagram is if the word contains the same number of 
		# letters as each other 
		# method: use a hashmap to count the number of letters of each string
		
		# if the letter count matches, then return true
		s_count = {}
		t_count = {}
		  
		# count for s string
		for char in s:
			s_count[char] = s_count.get(char, 0) + 1
		
		# count for t string
		for char in t:
			t_count[char] = t_count.get(char, 0) + 1
		return s_count == t_count
```

---
## Problem Statement
<small><i>The problem to solve.</i></small>

Given two strings `s` and `t`, return `true` if the two strings are anagrams of each other, otherwise return `false`.

An **anagram** is a string that contains the exact same characters as another string, but the order of the characters can be different.

**Example 1:**

```java
Input: s = "racecar", t = "carrace"

Output: true
```

**Example 2:**

```java
Input: s = "jar", t = "jam"

Output: false
```

**Constraints:**

- `s` and `t` consist of lowercase English letters.
