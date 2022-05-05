# 全排列2

去重复,不要重复结果

```python
# 去重复

class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        ans = []
        def isduplicate(nums, i, j):
            # 判断a[j]是否和[i,j)有重复
            while i < j:
                if nums[i] == nums[j]:
                    return True
                i+=1
            return False

        def helper(nums, idx):
            if idx == len(nums):
                ans.append(nums[:])
                return 

            for i in range(idx, len(nums)):
                if isduplicate(nums, idx, i):
                    continue

                nums[idx], nums[i] = nums[i], nums[idx]
                helper(nums, idx+1)
                nums[idx], nums[i] = nums[i], nums[idx]

        helper(nums, 0)
        return ans


```
