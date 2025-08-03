# LC26: Remove Duplicates from Sorted Array
(leetcode80)
## Concept  
Given a sorted array `nums`, remove the duplicates **in-place** such that each element appears only once and return the new length.  
You must do this using **O(1) extra memory**.

---

## Key Idea  
Since the array is sorted, duplicates will be **adjacent**.  
Use **two pointers**:  
- One pointer (`slow`) tracks the position of the last unique element.  
- The other pointer (`fast`) scans through the array.

When `nums[fast] != nums[slow]`, we have found a new unique value, so we move `slow` forward and write the new value there.

---

## Problem Constraints  
- Input is a sorted array of integers.  
- You **cannot use extra space**; must modify the array in-place.  
- The order of elements must be maintained.  

---

## Core Approach (Two Pointers)
- Initialize two pointers:  
  - `slow = 0`: points to the last unique element  
  - `fast = 1`: scans the array from the second element  
- Iterate until `fast` reaches the end:
  - If `nums[fast] != nums[slow]`:  
    - Move `slow` forward  
    - Copy `nums[fast]` to `nums[slow]`  
  - Always move `fast` forward
- Return `slow + 1` as the new length.

---

## Key Logic

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        if not nums:
            return 0
        
        slow = 0
        for fast in range(1, len(nums)):
            if nums[fast] != nums[slow]:
                slow += 1
                nums[slow] = nums[fast]
        
        return slow + 1
```

## Edge Case Handling
- Empty array → return `0`  
- All unique values → nothing is removed  
- All duplicates → result length is `1`  

---

## Common Examples
- `[1,1,2]` → `[1,2,_]`, return `2`  
- `[0,0,1,1,1,2,2,3,3,4]` → `[0,1,2,3,4,...]`, return `5`  
- `[]` → return `0`  

---

## Time & Space Complexity
- **Time**: `O(n)`, single pass through the array  
- **Space**: `O(1)`, in-place modification  

---

## Why This Solution Is Preferred in Interviews
- Efficient linear-time solution  
- Demonstrates solid grasp of the two-pointer technique  
- Modifies the array in-place without additional space  
- Easy to explain, intuitive, and robust under edge cases  

---

## Tags
- Two Pointers  
- In-Place Modification  
- Array  
- Duplicate Removal  
- Sorted Arrays  
