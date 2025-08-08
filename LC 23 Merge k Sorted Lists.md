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
            if cur.next:  #也可以是node.next
                heappush(heap,((node.next.val, i, node.next)))
        return dummy.next
```
```
def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        if not lists:
            return None
        if len(lists) == 1:
            return lists[0]
        heap = []
        count = 0
        for node in lists:
            if node is not None:
                heapq.heappush(heap,(node.val, count, node))
                count += 1
        dummy = ListNode(0)
        curr = dummy
        while heap:
            val, count, node = heapq.heappop(heap) 
            curr.next = node
            curr = curr.next
            if node.next:
                heapq.heappush(heap,(node.next.val, count, node.next))
        return dummy.next
```
