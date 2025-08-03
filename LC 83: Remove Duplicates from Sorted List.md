# Leetcode 83: Remove Duplicates from Sorted List

## Problem

Given the `head` of a **sorted** linked list, delete all duplicates such that each element appears only once.  
Return the linked list **sorted** as well.

---

## Idea

Since the list is already **sorted**, all duplicates will be **consecutive**.  
We can simply iterate the list and remove consecutive nodes with the same value.

```
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        cur = head
        while cur and cur.next:
            if cur.val == cur.next.val:
                cur.next = cur.next.next  # Skip duplicate
            else:
                cur = cur.next  # Move to next distinct value
        return head
```

---

## Algorithm (In-place)

1. Initialize a pointer `cur = head`.
2. While `cur` is not null and `cur.next` is not null:
   - If `cur.val == cur.next.val`, skip the next node:  
     `cur.next = cur.next.next`
   - Else, move forward: `cur = cur.next`
3. Return `head`.

---

## Complexity

- Time: O(n) – traverse each node once  
- Space: O(1) – modify in-place without extra space

---

## Edge Cases

- Empty list → return None  
- Single node → return as-is  
- All nodes have the same value → only one node kept  
- No duplicates → return original list

---

## Tags

- Linked List  
- In-place Modification  
- One-pass  
- Duplicate Removal  
- Sorted Data
