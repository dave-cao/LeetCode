---
tags:
  - leetcode
  - neetcode150
time_elapsed: 48
difficulty: medium
category: arrays-and-hashing
link: https://leetcode.com/problems/group-anagrams/
created: 2025-12-29T02:37
updated: 2026-01-10T12:56
---
# 49. Group Anagrams

## Notes
<small><i>Intuition and thought process in solving the question.</i></small>

This question took me a lot longer to solve then I thought. Thought it would be easier since I already solved the related question (Is Anagram). I did end up figuring out the solution and the intuition was there in using some sort of hashmap to group the anagrams, but the problem was that it exceeded the time limit. 

I got a hint from hint1 on NeetCode150 saying that sorting would be useful here. So I first sorted each word, checked if it was in the map, if it was, then put it in its group, and if it wasn't then create a new bucket. It worked relatively well. 

Gives a time complexity of $O(m * log(n))$ because for every word, we sort through every letter. And it has a space complexity of $O(m)$ because we are storing at most all the words in the original list.

## Code
<small><i>The solution.</i></small>

```python
class Solution:
	def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
		map = {}
		for word in strs:
			sorted_word_list = sorted(word)
			sorted_word = "".join(sorted_word_list)
			if (map.get(sorted_word) is not None):
				group = map.get(sorted_word)
				group.append(word)
			else:
				map[sorted_word] = [word]
		
		return (list(map.values()))
```


---
## Problem Statement
<small><i>The problem to solve.</i></small>

# 49. Group Anagrams - Explanation

[Problem Link](https://neetcode.io/problems/anagram-groups/)

## Description

Given an array of strings `strs`, group all _anagrams_ together into sublists. You may return the output in **any order**.

An **anagram** is a string that contains the exact same characters as another string, but the order of the characters can be different.

**Example 1:**

```java
Input: strs = ["act","pots","tops","cat","stop","hat"]

Output: [["hat"],["act", "cat"],["stop", "pots", "tops"]]
```

**Example 2:**

```java
Input: strs = ["x"]

Output: [["x"]]
```

**Example 3:**

```java
Input: strs = [""]

Output: [[""]]
```

**Constraints:**

- `1 <= strs.length <= 1000`.
- `0 <= strs[i].length <= 100`
- `strs[i]` is made up of lowercase English letters.