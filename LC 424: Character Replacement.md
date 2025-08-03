# LeetCode 424: Character Replacement

## Problem Description

Given a string `s` and an integer `k`, you can replace at most `k` characters in the string to make a substring with all the same characters. Return the length of the longest such substring.

## Core Idea

Use a sliding window to find the longest valid substring where the number of characters to replace is at most `k`.

```
def characterReplacement(s: str, k: int) -> int:
    from collections import defaultdict

    count = defaultdict(int)
    max_count = 0
    left = 0
    max_length = 0

    for right in range(len(s)):
        count[s[right]] += 1
        max_count = max(max_count, count[s[right]])

        while (right - left + 1) - max_count > k:
            count[s[left]] -= 1
            left += 1

        max_length = max(max_length, right - left + 1)

    return max_length
```

### Key Principle

Within any window:

```
number of characters to replace = window size - max frequency of a character in the window
```
If this number exceeds `k`, shrink the window from the left.

## Algorithm Steps

1. Use a hashmap (or array) to record character frequencies in the current window.
2. Maintain the frequency of the most common character in the window.
3. Expand the right pointer and update the frequency count.
4. If the window is invalid (needs more than `k` replacements), move the left pointer.
5. Track the maximum valid window size.

## Time and Space Complexity

- **Time Complexity**: O(n), where n is the length of the string.
- **Space Complexity**: O(1), since the alphabet size is fixed (only 26 uppercase letters).

## Examples

- `s = "ABAB", k = 2` → Output: `4`
- `s = "AABABBA", k = 1` → Output: `4`

## Summary

- Use sliding window and frequency map.
- Maintain the count of the most frequent character in the window.
- Shrink the window when more than `k` replacements are needed.
