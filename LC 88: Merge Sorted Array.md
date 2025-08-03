# Leetcode 88: Merge Sorted Array

## Problem Description
Merge two sorted integer arrays `nums1` and `nums2` into one sorted array in-place.  
- `nums1` has a length of `m + n`, where the first `m` elements are valid, and the last `n` elements are zeros to accommodate `nums2`.  
- `nums2` has `n` valid elements.  
The goal is to merge `nums2` into `nums1` as one sorted array.

---

## Key Idea
Use three pointers starting from the end of the arrays to merge in reverse order:  
- `p1` at the end of the valid elements in `nums1`  
- `p2` at the end of `nums2`  
- `p` at the end of `nums1` (total length `m + n`)  
Compare elements pointed by `p1` and `p2`, place the larger one at position `p`, and move pointers accordingly.  
Continue until all elements in `nums2` are merged.

```
class Solution:
    def merge(self, nums1, m, nums2, n):
        p1 = m - 1
        p2 = n - 1
        p = m + n - 1

        while p1 >= 0 and p2 >= 0:
            if nums1[p1] > nums2[p2]:
                nums1[p] = nums1[p1]
                p1 -= 1
            else:
                nums1[p] = nums2[p2]
                p2 -= 1
            p -= 1

        # 如果 nums2 还有剩余，继续复制
        while p2 >= 0:
            nums1[p] = nums2[p2]
            p2 -= 1
            p -= 1
```

---

## Edge Case Handling
- One or both arrays are empty.  
- All elements of one array are smaller or larger than the other.  
- Arrays with duplicates.

---

## Time & Space Complexity
- Time: O(m + n) — each element is processed once.  
- Space: O(1) — merge done in-place without extra space.

---

## Why This Solution Is Preferred
- Efficient in time and space.  
- Avoids overwriting unprocessed elements by merging from the back.  
- Simple pointer logic that’s easy to explain and implement.  
- Handles all edge cases cleanly.

---

## Tags
Array • Two Pointers • In-Place Modification • Merge • Sorted Arrays
