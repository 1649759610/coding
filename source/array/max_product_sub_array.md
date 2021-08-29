# 乘积最大子数组

给你一个整数数组 nums ，请你找出数组中乘积最大的连续子数组（该子数组中至少包含一个数字），并返回该子数组所对应的乘积。

```python
import numpy as np

class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        # dp[i][0]:以dp[i]结尾的最小值
        # dp[i][1]:以dp[i]结尾的最大值
        dp = np.zeros((len(nums), 2), dtype=int)
        dp[0, 0] = nums[0]
        dp[0, 1] = nums[0]

        # dp[1, 0] = min(nums[1]*dp[0, 0], nums[1]*dp[0,1], nums[i])
        # dp[1, 1]=  max(nums[1]*dp[0, 0], nums[1]*dp[0,1], nums[i])

        for i in range(0, len(nums)-1):
            dp[i+1][0] = min(nums[i+1]*dp[i,0], nums[i+1]*dp[i,1],nums[i+1])
            dp[i+1][1] = max(nums[i+1]*dp[i,0], nums[i+1]*dp[i,1],nums[i+1])
        return int(dp.max())

```
