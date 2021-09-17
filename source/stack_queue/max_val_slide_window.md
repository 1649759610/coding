# 滑动窗口最大值

给你一个整数数组 nums，有一个大小为 k 的滑动窗口从数组的最左侧移动到数组的最右侧。你只可以看到在滑动窗口内的 k 个数字。滑动窗口每次只向右移动一位。

返回滑动窗口中的最大值。



## 解法
不断使用窗口内的元素建立最大堆，堆中的元素为（val, index）。
起初，先使用前k个元素建立初始最大堆，后续不断向里面加元素。  
在加元素的过程中注意，如果当前的最大堆顶元素超出了当前窗口范围，则pop出来。


```python
class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        # 注意python默认的优先队列的小根堆
        q = [(-nums[i], i) for i in range(k)]
        heapq.heapify(q)

        ans = [-q[0][0]]
        for i in range(k, len(nums)):
            heapq.heappush(q, (-nums[i],i))
            while q[0][1]<=i-k:
                heapq.heappop(q)
            ans.append(-q[0][0])
        
        return ans
```
