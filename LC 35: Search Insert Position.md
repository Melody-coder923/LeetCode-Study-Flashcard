# Leetcode 35: Search Insert Position

## Problem

Given a sorted array `nums` and a target value `target`, return the index if the target is found.  
If not, return the index where it would be if it were inserted in order.

---

## Idea

Use **binary search** to find the target or the correct insertion position efficiently.

---

## Algorithm

1. Initialize two pointers: `left = 0`, `right = len(nums) - 1`.
2. While `left <= right`:
   - Calculate `mid = left + (right - left) // 2`.
   - If `nums[mid] == target`, return `mid`.
   - If `nums[mid] < target`, move `left = mid + 1`.
   - Else, move `right = mid - 1`.
3. If target not found, `left` will be the insertion position; return `left`.

---

## Code

```python
class Solution:
    def searchInsert(self, nums: list[int], target: int) -> int:
        left, right = 0, len(nums) - 1
        while left <= right:
            mid = left + (right - left) // 2
            if nums[mid] == target:
                return mid
            elif nums[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
        return left
```
### Complexity

- Time: O(log n)  
- Space: O(1)

---

### Edge Cases

- Empty array → return 0  
- Target less than all elements → return 0  
- Target greater than all elements → return len(nums)  
- Target equal to an element → return that element's index

---

### Tags

- Binary Search  
- Sorted Array  
- Search  
- Insert Position
