# 求众数 2 （第229题）

给定一个大小为 n 的整数数组，找出其中所有出现超过 ⌊ n/3 ⌋ 次的元素。

**示例 1**：  
输入：[3,2,3]  
输出：[3]  

**示例 2**：   
输入：nums = [1]  
输出：[1]  

**示例 3**：  
输入：[1,1,1,3,3,2,2,2]  
输出：[1,2]  


```python
class Solution:
    def majorityElement(self, nums: List[int]) -> List[int]:
        num1, num2 = None, None
        count1, count2 = 0, 0

        for i in range(len(nums)):
            if nums[i] == num1:
                count1 += 1
            elif nums[i] == num2:
                count2 += 1
            elif count1 == 0:
                count1 = 1
                num1 = nums[i]
            elif count2 == 0:
                count2 = 1
                num2 = nums[i]
            else:
                count1 -= 1
                count2 -= 1
        
        # 下面的count 用于统计数字出现的次数
        count1 = 0
        count2 = 0
        ans = []
        for i in range(len(nums)):
            if nums[i] == num1:
                count1 += 1
            elif nums[i] == num2:
                count2 += 1
        
        if count1 > len(nums) // 3:
            ans.append(num1)
        if count2 > len(nums) // 3:
            ans.append(num2)
        
        return ans

```
