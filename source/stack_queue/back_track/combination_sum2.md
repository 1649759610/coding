# 组合总和2 （第40题）
给定一个候选人编号的集合 candidates 和一个目标数 target ，找出 candidates 中所有可以使数字和为 target 的组合。

candidates 中的每个数字在每个组合中只能使用 一次 。

注意：解集不能包含重复的组合。 

 

**示例 1**:  
输入: candidates = [10,1,2,7,6,1,5], target = 8,  
输出:  
[  
[1,1,6],  
[1,2,5],  
[1,7],  
[2,6]  
]  

**示例 2**:  
输入: candidates = [2,5,2,1,2], target = 5,  
输出:  
[  
[1,2,2],  
[5]  
]  




```python
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        ans = []
        visited = set()
        candidates.sort()

        def helper(idx, cur, path):
            if cur == 0:
                ans.append(path[:])
                return 
            if idx == len(candidates):
                return 
            
            if idx!=0 and candidates[idx] == candidates[idx-1] and (idx-1) not in visited:
                helper(idx+1, cur, path)
                return 
            
            if candidates[idx] <= cur:
                # 加入nums[i]
                visited.add(idx)
                helper(idx+1, cur-candidates[idx], path+[candidates[idx]])
                visited.remove(idx)

            # 不加入nums[i]
            helper(idx+1, cur, path)
        
        helper(0, target, [])

        return ans

```
