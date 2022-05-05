# 四数之和

```python
# 解法1
class Solution:
    def fourSum(self, nums: List[int], target: int) -> List[List[int]]:
        ans = []
        visited = {}
        nums = sorted(nums)
        def helper(nums, idx, tmpList, target):
            if len(tmpList) > 4:
                return
            
            if len(tmpList) == 4 and sum(tmpList) == target:
                if str(tmpList) not in visited:
                    visited[str(tmpList)] = True
                    ans.append(tmpList)
                return 
            
            for i in range(idx, len(nums)):
                # tmpList.append(nums[i])
                helper(nums, i+1, tmpList+[nums[i]], target)
        
        helper(nums, 0, [], target)
        return ans

    
# 解法2

class Solution:
    def fourSum(self, nums: List[int], target: int) -> List[List[int]]:
        ans = []
        nums = sorted(nums)
        visited = {}

        def helper(nums, idx, tmpList, target):
            if len(tmpList) > 4:
                return

            if len(tmpList) == 4 and sum(tmpList) == target:
                if str(tmpList) not in visited:
                    ans.append(tmpList)
                return
            
            for i in range(idx, len(nums)):
                helper(nums, idx+1, tmpList+[nums[i]], target)
        
        helper(nums, 0, [], 6)
        return ans
```