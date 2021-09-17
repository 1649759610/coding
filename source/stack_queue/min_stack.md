# 最小栈

设计一个支持 push ，pop ，top 操作，并能在常数时间内检索到最小元素的栈。
- push(x) —— 将元素 x 推入栈中。
- pop() —— 删除栈顶的元素。
- top() —— 获取栈顶元素。
- getMin() —— 检索栈中的最小元素。

## 题解
设置一个栈和一个辅助栈，每当入栈一个元素的时候，此刻对应最小的值存入辅助栈中，也就是说，辅助栈中每个元素都对应着正式的栈对应的最小元素。

具体来说：
1. 当一个元素要入栈时，我们取当前辅助栈的栈顶存储的最小值，与当前元素比较得出最小值，将这个最小值插入辅助栈中；

2. 当一个元素要出栈时，我们把辅助栈的栈顶元素也一并弹出；

3. 在任意一个时刻，栈内元素的最小值就存储在辅助栈的栈顶元素中。


```python
import math

class MinStack:

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.stack = []
        self.min_stack = [math.inf]


    def push(self, val: int) -> None:
        self.stack.append(val)
        self.min_stack.append(min(val, self.min_stack[-1]))


    def pop(self) -> None:
        self.stack.pop()
        self.min_stack.pop()


    def top(self) -> int:
        return self.stack[-1]


    def getMin(self) -> int:
        return self.min_stack[-1]



# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(val)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()


```
