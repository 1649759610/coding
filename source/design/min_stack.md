# 最小栈 (第155题)

设计一个支持 push ，pop ，top 操作，并能在常数时间内检索到最小元素的栈。

实现 MinStack 类:

- MinStack() 初始化堆栈对象。  
- void push(int val) 将元素val推入堆栈。  
- void pop() 删除堆栈顶部的元素。  
- int top() 获取堆栈顶部的元素。  
- int getMin() 获取堆栈中的最小元素。  


```python
class MinStack:

    def __init__(self):
        self.stack = []
        self.helper = []
        self.min_val = float("inf")


    def push(self, val: int) -> None:
        if not self.stack:
            self.stack.append(val)
            self.helper.append(val)
            self.min_val = val
        else:
            self.stack.append(val)
            if val < self.min_val:
                self.min_val=val
            self.helper.append(self.min_val)

    def pop(self) -> None:
        self.stack.pop()
        self.helper.pop()
        self.min_val = self.helper[-1] if self.helper else float("inf")


    def top(self) -> int:
        return self.stack[-1]


    def getMin(self) -> int:
        return self.helper[-1]

```
