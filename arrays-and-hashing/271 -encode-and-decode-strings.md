---
tags:
  - leetcode
  - neetcode150
time_elapsed: 15
difficulty: medium
category: arrays-and-hashing
link: https://leetcode.com/problems/encode-and-decode-strings/description/
created: 2026-01-08T07:25
updated: 2026-01-08T07:26
---
# 271. Encode and Decode Strings

## Notes
<small><i>Intuition and thought process in solving the question.</i></small>

Definitely did not feel like a medium. It felt more like a hard. But that might just be because I used the simplest encoding and decoding mechanism possible. With hard mechanisms, it may have took more time. 

The challenge was how to differentiate between an empty list and a list with an empty string within it. I just had a separate base case to account for this.

My solution has a time complexity of $O(n)$ and a space complexity of $O(n)$

## Code
<small><i>The solution.</i></small>

```python
class Solution:
	def encode(self, strs: List[str]) -> str:
		if strs == []:
			return "NONE"
		return "~~".join(strs)
		
	def decode(self, s: str) -> List[str]:
		if s == "NONE":
			return []
		return s.split("~~")
```
---
## Problem Statement
<small><i>The problem to solve.</i></small>

# Encode and Decode Strings

Solved

Design an algorithm to encode **a list of strings** to **a string**. The encoded string is then sent over the network and is decoded back to the original list of strings.

Machine 1 (sender) has the function:

```text
string encode(vector<string> strs) {
    // ... your code
    return encoded_string;
}
```

Machine 2 (receiver) has the function:

```text
vector<string> decode(string s) {
    //... your code
    return strs;
}
```

So Machine 1 does:

```text
string encoded_string = encode(strs);
```

and Machine 2 does:

```text
vector<string> strs2 = decode(encoded_string);
```

`strs2` in Machine 2 should be the same as `strs` in Machine 1.

Implement the `encode` and `decode` methods.

**Example 1:**

```java
Input: dummy_input = ["Hello","World"]

Output: ["Hello","World"]

Explanation:
Machine 1:
Codec encoder = new Codec();
String msg = encoder.encode(strs);
Machine 1 ---msg---> Machine 2

Machine 2:
Codec decoder = new Codec();
String[] strs = decoder.decode(msg);
```

**Example 2:**

```java
Input: dummy_input = [""]

Output: [""]
```

  

**Constraints:**

- `0 <= strs.length < 100`
- `0 <= strs[i].length < 200`
- `strs[i]` contains any possible characters out of `256` valid ASCII characters.

  

**Follow up**: Could you write a generalized algorithm to work on any possible set of characters?