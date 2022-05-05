# 最大连续子数组（第53题）

给你一个整数数组 nums ，请你找出一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

子数组 是数组中的一个连续部分。

```python

# 解法1
import numpy as np
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        # dp[i]:以i结尾的最大和

        dp = [0] * len(nums)
        dp[0] = nums[0]

        for i in range(1, len(nums)):
            if dp[i-1] > 0:
                dp[i] = dp[i-1] + nums[i]
            else:
                dp[i] = nums[i]
        
        # 找出最大子数组
        lastId = np.argmax(dp)
        i = lastId-1
        path = [nums[lastId]]
        while i>=0:
            if sum(path)!=dp[lastId]:
                path.append(nums[i])
            else:
                break
            i-=1

        print(list(reversed(path)))

        return max(dp)
    


```

```python
# 解法2： 分治法

class Solution:
    def maxSubArray(self, nums: List[int]) -> int:

        def helper(nums, l, r):
            if l > r:
                return float("-inf")

            mid = (l+r) // 2
            left = helper(nums, l, mid-1)
            right = helper(nums, mid+1, r)
            left_suffix_sum, right_prefix_sum = 0, 0 
            total = 0
            for i in reversed(range(l, mid)):
                total += nums[i]
                left_suffix_sum = max(left_suffix_sum, total)
            
            total = 0
            for i in range(mid+1, r+1):
                total += nums[i]
                right_prefix_sum = max(right_prefix_sum, total)
            
            cross_max_sum = left_suffix_sum + right_prefix_sum + nums[mid]

            return max(left, cross_max_sum, right)

        return helper(nums, 0, len(nums)-1)


```


```python
# 解法3： 前缀和
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        
        maxSum = nums[0]
        minSum, total = 0, 0
        
        for i in range(len(nums)):
            total += nums[i]
            maxSum = max(maxSum, total - minSum)
            minSum = min(total, minSum)
        
        return maxSum


```