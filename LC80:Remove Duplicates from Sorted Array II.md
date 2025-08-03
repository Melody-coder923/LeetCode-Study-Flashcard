# LeetCode 80: Remove Duplicates from Sorted Array II
(leetcode26)
## Concept
Remove duplicates in a sorted array such that each element appears **at most twice**. Modify the array in-place and return the new length.

## Key Idea
Use two pointers (`slow` and `fast`) to overwrite duplicates beyond the allowed count (2 in this case). The `slow` pointer marks the next position to write, and the `fast` pointer scans through the array.

## Problem Constraints
- The array is sorted.
- Must do the operation in-place with O(1) extra space.
- Preserve relative order of elements.
- Handle arrays of any length including empty.

## Core Approach (Two Pointers)
1. Initialize `slow` = 0.
2. Iterate `fast` from 0 to end of the array.
3. For each `nums[fast]`, check if it's allowed to be written:
   - If `slow < 2`, always write because first two elements are allowed.
   - Otherwise, check if `nums[fast] != nums[slow - 2]` to allow at most two duplicates.
4. If allowed, write `nums[fast]` to `nums[slow]` and increment `slow`.
5. After traversal, `slow` is the length of the processed array.

## Key Logic
```python
class Solution:
    def removeDuplicates(self, nums: list[int]) -> int:
        slow = 0
        for fast in range(len(nums)):
            if slow < 2 or nums[fast] != nums[slow - 2]:
                nums[slow] = nums[fast]
                slow += 1
        return slow
```

## Edge Case Handling
- Empty array → return 0  
- All unique values → no removal, length unchanged  
- All duplicates → length becomes 2  
- Arrays with mixed duplicates handled correctly  

## Common Examples
- `[1,1,1,2,2,3]` → `[1,1,2,2,3,...]`, returns 5  
- `[0,0,1,1,1,1,2,3,3]` → `[0,0,1,1,2,3,3,...]`, returns 7  
- `[]` → return 0  

## Time & Space Complexity
- Time: O(n), one pass through the array  
- Space: O(1), in-place modification with constant extra space  

## Why This Solution Is Preferred in Interviews
- Elegant use of two pointers with clear semantics  
- Handles edge cases smoothly  
- In-place operation with no extra memory  
- Simple and efficient, easy to explain and implement  

## Tags
- Two Pointers  
- Array  
- In-place Modification  
- Duplicate Removal  
- Sorted Arrays
