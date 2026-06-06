---
tags:
  - leetcode
  - neetcode150
time_elapsed: 5
difficulty: easy
category: two-pointers
needed_help: false
link: https://leetcode.com/problems/valid-palindrome/description/
created: 2026-06-06T17:07
updated: 2026-06-06T17:07
---
# 125. Valid Palindrome

## Notes
<small><i>Intuition and thought process in solving the question.</i></small>

Initial intuition was just to reverse the string and compare them but that uses pythons internal tools. So instead I went a different approach and actually used pointers. I stripped everything and then had a back and front pointer that would compare each other until the middle point (when they cross). This is an O(n/2) solution so its pretty optimal.

## Code
<small><i>The solution.</i></small>

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        stripped = [letter.lower() for letter in s if letter.isalnum()]
        stripped = "".join(stripped)
        for i in range(len(stripped)):
            right_pointer_index = len(stripped) - i - 1
            left_pointer_index = i

            right_pointer_letter = stripped[right_pointer_index]
            left_pointer_letter = stripped[left_pointer_index]

            if right_pointer_letter != left_pointer_letter:
                return False

            if left_pointer_index >= right_pointer_index:
                break
        return True

```

---
## Problem Statement
<small><i>The problem to solve.</i></small>

# Valid Palindrome

Easy Topics Company Tags Hints

Given a string `s`, return `true` if it is a **palindrome**, otherwise return `false`.

A **palindrome** is a string that reads the same forward and backward. It is also case-insensitive and ignores all non-alphanumeric characters.

**Note:** Alphanumeric characters consist of letters `(A-Z, a-z)` and numbers `(0-9)`.

**Example 1:**

```java
Input: s = "Was it a car or a cat I saw?"

Output: true
```

Explanation: After considering only alphanumerical characters we have "wasitacaroracatisaw", which is a palindrome.

**Example 2:**

```java
Input: s = "tab a cat"

Output: false
```

Explanation: "tabacat" is not a palindrome.

**Constraints:**

- `1 <= s.length <= 1000`
- `s` is made up of only printable ASCII characters.