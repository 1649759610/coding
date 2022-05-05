# LRU缓存机制

请你设计并实现一个满足  LRU (最近最少使用) 缓存 约束的数据结构。
实现 LRUCache 类：  
LRUCache(int capacity) 以 正整数 作为容量 capacity 初始化 LRU 缓存  
int get(int key) 如果关键字 key 存在于缓存中，则返回关键字的值，否则返回 -1 。  
void put(int key, int value) 如果关键字 key 已经存在，则变更其数据值 value ；如果不存在，则向缓存中插入该组 key-value 。如果插入操作导致关键字数量超过 capacity ，则应该 逐出 最久未使用的关键字。  
函数 get 和 put 必须以 O(1) 的平均时间复杂度运行。


```python
class ListNode():
    def __init__(self, key=None, val=None):
        self.key = key
        self.val = val
        self.next = None
        self.prev = None

class LRUCache:

    def __init__(self, capacity: int):
        self.capacity = capacity
        self.head = ListNode()
        self.tail = ListNode()
        self.hashmap = {}

        # 初始化双向链表
        self.head.next = self.tail
        self.tail.prev = self.head


    def move_to_tail(self, key):
        node = self.hashmap[key]

        # 先断开当前位置的链接
        node.prev.next = node.next
        node.next.prev = node.prev

        # 将node弄到链表尾端
        node.prev = self.tail.prev
        node.next = self.tail
        self.tail.prev.next = node
        self.tail.prev = node

    def get(self, key: int) -> int:
        if key in self.hashmap:
            self.move_to_tail(key)
            val = self.hashmap[key].val
            return val
        
        return -1

    def put(self, key: int, value: int) -> None:
        if key in self.hashmap:
            node = self.hashmap[key]
            node.val = value
            self.move_to_tail(key)
        else:
            if len(self.hashmap) == self.capacity:
                # pop the first node
                self.hashmap.pop(self.head.next.key)
                self.head.next = self.head.next.next
                self.head.next.prev = self.head
            
            # 插入链表尾部
            newNode = ListNode(key, value)
            self.hashmap[key] = newNode
            newNode.next = self.tail
            newNode.prev = self.tail.prev
            self.tail.prev.next = newNode
            self.tail.prev = newNode
            

```
