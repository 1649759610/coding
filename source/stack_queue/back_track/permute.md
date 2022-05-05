# 全排列

```python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:

        ans = []
        def helper(nums, idx):
            if idx == len(nums):
                ans.append(nums[:])

            for i  in range(idx, len(nums)):
                nums[i], nums[idx] = nums[idx], nums[i]
                helper(nums, idx+1)
                nums[i], nums[idx] = nums[idx], nums[i]
        
        helper(nums, 0)

        return ans

```
