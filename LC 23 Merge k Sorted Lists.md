```
from heapq import heappush, heappop
class Solution:
    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        heap=[]
        for i, node in enumerate(lists):
            if node:
                heappush(heap, (node.val, i, node)) #i是用来区分相同值的不同点
        dummy=ListNode(-1)
        cur=dummy
        while heap:
            val, i, node = heappop(heap)
            cur.next=node
            cur=cur.next
            if cur.next:
                heappush(heap,((node.next.val, i, node.next)))
        return dummy.next
```
