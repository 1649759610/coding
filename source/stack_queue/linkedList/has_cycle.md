# 环形链表（第141题）

给你一个链表的头节点 head ，判断链表中是否有环。

```python
# 解法1：哈希法

# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        mapper = set()

        while head is not None:
            if head in mapper:
                return True
            
            mapper.add(head)

            head = head.next
        
        return False
            


# 解法2：快慢指针

# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        if head is None or head.next == None:
            return False
        
        slow, fast = head, head

        while fast is not None and fast.next is not None:
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                break

        if fast is None or fast.next is None:
            return False
        else:
            return True




```
