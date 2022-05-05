# 最接近的三数之和（第16题）

给你一个长度为 n 的整数数组 nums 和 一个目标值 target。请你从 nums 中选出三个整数，使它们的和与 target 最接近。

返回这三个数的和。

假定每组输入只存在恰好一个解。


```python
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        nums = sorted(nums)
        ans = sum(nums[:3])

        for i in range(len(nums)):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            
            l, r = i+1, len(nums)-1
            
            while l < r:
                threeSum = nums[i] + nums[l] + nums[r]
                if threeSum == target:
                    return threeSum
                
                if abs(threeSum - target) < abs(ans - target):
                    ans = threeSum
                
                if threeSum < target:
                    l += 1
                elif threeSum > target:
                    r -= 1
        
        return ans
                
                



```