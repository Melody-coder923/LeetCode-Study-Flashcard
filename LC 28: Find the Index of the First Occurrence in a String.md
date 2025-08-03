# Leetcode 28: Find the Index of the First Occurrence in a String

## Problem

Given two strings `haystack` and `needle`, return the index of the first occurrence of `needle` in `haystack`, or `-1` if it is not part of `haystack`.

Return `0` if `needle` is empty.

---

## Method 1: Sliding Window (Brute Force)

### Idea

Slide a window of length `len(needle)` over `haystack`, compare substrings.

### Code

```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        n, m = len(haystack), len(needle)
        if m == 0:
            return 0
        for i in range(n - m + 1):
            if haystack[i:i + m] == needle:
                return i
        return -1
```
### Complexity

- Time: O(n * m)
- Space: O(1)

---

## Method 2: KMP Algorithm

### Idea

Build LPS (Longest Prefix which is also Suffix) table to avoid unnecessary comparisons.

```
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        if not needle:
            return 0

        def build_lps(pattern):
            lps = [0] * len(pattern)
            length = 0
            i = 1
            while i < len(pattern):
                if pattern[i] == pattern[length]:
                    length += 1
                    lps[i] = length
                    i += 1
                else:
                    if length != 0:
                        length = lps[length - 1]
                    else:
                        lps[i] = 0
                        i += 1
            return lps

        lps = build_lps(needle)

        i = j = 0
        while i < len(haystack):
            if haystack[i] == needle[j]:
                i += 1
                j += 1
                if j == len(needle):
                    return i - j
            else:
                if j != 0:
                    j = lps[j - 1]
                else:
                    i += 1

        return -1
```

### Complexity

- Time: O(n + m)
- Space: O(m)

---

### Edge Cases

- `needle == ""` → return 0  
- `needle` not in `haystack` → return -1  
- `needle == haystack` → return 0

---

### Examples

```python
haystack = "sadbutsad", needle = "sad"     → 0
haystack = "leetcode",  needle = "leeto"   → -1
haystack = "abc",       needle = ""        → 0
```

### Tags

- String  
- Sliding Window  
- KMP  
- Substring Matching

