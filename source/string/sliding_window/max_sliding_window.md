#  滑动窗口最大值（第239题）

给定一个数组nums，有一个大小为k的滑动窗口从数组的最左侧移动到数组的最右侧。你只可以看到滑动窗口内的k个数字，滑动窗口每次只向右移动1位。返回滑动窗口的最大值。

```python
import numpy as np


# 解法一：暴力法

def maxSlidingWindow(nums, k):
    left, right = 0, k-1
    outputs = []
    while right < len(nums):
        max_val = nums[left]
        for i in range(left, right+1):
            max_val = max(max_val, nums[i])
        outputs.append(max_val)
        left += 1
        right += 1

    return outputs

nums = [1, 3, -1, -3, 5, 3, 6, 7]
k = 3

maxSlidingWindow(nums, k)

import numpy as np
import collections

# 解法二： 双端队列法, 队首元素为当前队列中的最大元素

def maxSlidingWindow(nums, k):
    d = collections.deque()
    out = []

    for i, n in enumerate(nums):
        # n为当前待插入的元素, 从尾部开始移除比新加入元素小的元素
        while d and nums[d[-1]] < n:
            d.pop()
        # 将新加入的元素添加到双端队列的尾部
        d.append(i)
        # 如果窗口外的元素仍然在双端队列中，则将其移除
        if d[0] == i - k:
            d.popleft()
        # 将头部元素即当前最大元素对应的数字放入结果数组中
        if i >= k-1:
            out.append(nums[d[0]])
    
    return out

nums = [1, 3, -1, -3, 5, 3, 6, 7]
k = 3

maxSlidingWindow(nums, k)
```
