# 最大数 （第179题）

给定一组非负整数 nums，重新排列每个数的顺序（每个数不可拆分）使之组成一个最大的整数。

注意：输出结果可能非常大，所以你需要返回一个字符串而不是整数。

**示例 1：**  
输入：nums = [10,2]  
输出："210"  


**示例 2：**    
输入：nums = [3,30,34,5,9]  
输出："9534330"  



```python
import functools

class Solution:
    def largestNumber(self, nums: List[int]) -> str:
        nums = [str(i) for i in nums]

        # a<b,return 负数， a>b return 正数， a=b return 0; 小于的排在前面
        # 若a应该排在前面，返回负数；若a应该排在后面，返回正数
        def comp(a, b):
            if (a+b) > (b+a):
                return 1
            if (a+b) < (b+a):
                return -1
            return 0
        
        nums= sorted(nums, reverse=True, key=functools.cmp_to_key(comp))

        return str(int("".join(nums)))

```