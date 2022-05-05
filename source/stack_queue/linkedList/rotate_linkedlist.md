# 翻转链表

给你一个链表的头节点 head ，旋转链表，将链表每个节点向右移动 k 个位置。

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def rotateRight(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        if head == None or head.next == None:
            return head

        # 分析概况
        p = head
        prev = head
        count = 1
        i = 0
        while p.next:
            if count > 1:
                prev = prev.next
            p = p.next
            count += 1

        k = k%count
        p.next = head

        # 开始移动
        i = 0
        while i < count - k+1:
            prev = prev.next
            p = p.next
            i += 1
        prev.next = None


        
        return p
        


        


```
