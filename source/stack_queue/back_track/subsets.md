# 子集（第78题）

给你一个整数数组 nums ，数组中的元素 互不相同 。返回该数组所有可能的子集（幂集）。

解集 不能 包含重复的子集。你可以按 任意顺序 返回解集。

 

**示例 1**：
输入：nums = [1,2,3]  
输出：[[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]  

**示例 2**：  
输入：nums = [0]  
输出：[[],[0]]  


```python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        ans = []
        def helper(idx, path):
            if idx == len(nums):
                ans.append(path[:])
                return 
            
            helper(idx+1, path+[nums[idx]])
            helper(idx+1, path)
        
        helper(0,[])
        return ans



```
