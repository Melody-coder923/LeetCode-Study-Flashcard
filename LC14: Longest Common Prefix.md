# LC14: Longest Common Prefix

## Concept
- Find the longest common prefix string among an array of strings.
- If no common prefix exists, return an empty string.
- Key idea: progressively narrow down the prefix by comparing strings.

## Problem Constraints
- All strings are lowercase letters.
- Input array may contain empty strings.
- Must be efficient for many short strings.

## Core Approach (Horizontal Scan)
- Initialize prefix as the first string.
- For each remaining string:
  - While it does not start with the prefix, remove the last character from prefix.
  - Stop early if prefix becomes empty.


## Key Logic

```
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        if not strs:
            return ""

        prefix = strs[0]
        for s in strs[1:]:
            while not s.startswith(prefix):
                prefix = prefix[:-1]
                if not prefix:
                    return ""
        return prefix
```

## Edge Case Handling
- Empty input list → return `""`
- One or more strings are empty → return `""`
- No common prefix at all → return `""`

## Common Examples
- ["flower", "flow", "flight"] → `"fl"`
- ["dog", "racecar", "car"] → `""`
- ["interview", "interval", "integrate"] → `"int"`

## Time & Space Complexity
- **Time**: O(S) → S is the total number of characters in all strings
- **Space**: O(1) → Only constant extra space used for prefix

## Why This Solution Is Preferred in Interviews
- Simple and efficient one-pass solution
- Clear logic that's easy to walk through verbally
- Good string method usage (`.startswith`)
- Graceful early stopping if prefix becomes empty

## Tags
- String
- Horizontal Scan
- Prefix Matching
- Edge Case Handling
