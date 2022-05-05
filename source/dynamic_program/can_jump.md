# 跳跃游戏(第55题)

给定一个非负整数数组 nums ，你最初位于数组的 第一个下标 。

数组中的每个元素代表你在该位置可以跳跃的最大长度。

判断你是否能够到达最后一个下标。

 

**示例 1**：  
输入：nums = [2,3,1,1,4]  
输出：true  
解释：可以先跳 1 步，从下标 0 到达下标 1, 然后再从下标 1 跳 3 步到达最后一个下标。  

**示例 2**：  
输入：nums = [3,2,1,0,4]  
输出：false  
解释：无论怎样，总会到达下标为 3 的位置。但该下标的最大跳跃长度是 0 ， 所以永远不可能到达最后一个下标。  


```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        # dp[i]：i位置是否可达到
        dp = [False] * len(nums)
        dp[0] = True

        for i in range(1, len(nums)):
            for j in range(0, i):
                if dp[j]==True and j+nums[j] >= i:
                    dp[i] = True
                    break
        
        return dp[-1]


class Solution:
    def canJump(self, nums: List[int]) -> bool:
        # dp[i]：0-i位置能达到的最远位置
        # dp[i] = max(dp[i-1], i+nums[i]) 
        dp = [0] * len(nums)
        dp[0] = nums[0]

        for i in range(1, len(nums)):
            if dp[i-1] < i:
                dp[i] = dp[i-1]
            else:
                dp[i] = max(dp[i-1], i+nums[i])
        
        return dp[-1] >= len(nums)-1


```
