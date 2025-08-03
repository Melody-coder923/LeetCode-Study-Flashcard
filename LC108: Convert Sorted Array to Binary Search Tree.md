# Leetcode 108: Convert Sorted Array to Binary Search Tree

## Problem Description
Given a sorted (in ascending order) integer array, convert it into a height-balanced Binary Search Tree (BST).  
A height-balanced BST means the depth of the two subtrees of every node never differs by more than 1.

---

## Key Idea
- Use a divide-and-conquer approach.  
- The middle element of the current array/subarray becomes the root node.  
- Recursively apply the same process to the left subarray to build the left subtree and to the right subarray to build the right subtree.  
- This ensures the BST is balanced because the array is split evenly at each step.

```
class Solution:
    def sortedArrayToBST(self, nums: list[int]) -> TreeNode | None:
        def build(left: int, right: int) -> TreeNode | None:
            if left > right:
                return None
            mid = (left + right) // 2
            root = TreeNode(nums[mid])
            root.left = build(left, mid - 1)
            root.right = build(mid + 1, right)
            return root

        return build(0, len(nums) - 1)
```
---

## Edge Case Handling
- Empty array → return `None` (empty tree).  
- Single element array → return a node with no children.  
- Large arrays → recursive approach maintains balanced height.

---

## Time & Space Complexity
- Time: O(n), where n is the number of elements in the array (each element visited once).  
- Space: O(log n) due to recursion stack in balanced tree construction.

---

## Why This Solution Is Preferred
- Guarantees height-balanced BST due to middle element selection.  
- Simple and intuitive divide-and-conquer strategy.  
- Easy to implement and explain recursively.  
- Efficient with linear time complexity.

---

## Tags
Binary Search Tree • Divide and Conquer • Recursion • Balanced Tree • Sorted Array
