# LC21: Merge Two Sorted Lists

## Concept
Merge two sorted linked lists into one sorted linked list and return the merged list's head.

---

## Key Idea
Compare the current nodes of both lists and append the smaller one to the merged list until all nodes are processed.

---

## Problem Constraints
- Both input linked lists are sorted in ascending order.
- Either or both lists may be empty.
- Merge should be done in O(m + n) time complexity.

---

## Core Approach (Pointer Manipulation)
- Create a dummy node to simplify list operations.
- Use a pointer to iterate through both lists:
  - Compare the current nodes of both lists.
  - Attach the smaller node to the merged list.
  - Move the pointer in the list from which the node was taken.
- After one list is exhausted, append the remaining nodes of the other list.
- Return the next node of the dummy node as the head of the merged list.

---

## Key Logic

```
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def mergeTwoLists(l1: ListNode, l2: ListNode) -> ListNode:
    dummy = ListNode()  # Dummy node to ease operations
    current = dummy

    while l1 and l2:
        if l1.val < l2.val:
            current.next = l1
            l1 = l1.next
        else:
            current.next = l2
            l2 = l2.next
        current = current.next

    # Append remaining nodes
    current.next = l1 if l1 else l2

    return dummy.next
```

## Edge Case Handling
- One list is empty → return the other list directly.
- Both lists are empty → return empty list.
- Lists of unequal length → append the leftover nodes directly.

---

## Common Examples
- l1 = [1,2,4], l2 = [1,3,4] → [1,1,2,3,4,4]
- l1 = [], l2 = [] → []
- l1 = [], l2 = [0] → [0]

---

## Time & Space Complexity
- Time: O(m + n), where m and n are lengths of the two lists.
- Space: O(1), only constant extra space used (dummy node excluded).

---

## Why This Solution Is Preferred in Interviews
- Intuitive and easy to understand, based on merge step of merge sort.
- Clean code and clear pointer operations.
- In-place merging, efficient space usage.
- Explicit and clear handling of edge cases.

---

## Tags
- Linked List
- Two Pointers
- Merge
- In-place Modification
