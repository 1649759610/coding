# 只出现一次的数字 3 （第260题）

给定一个整数数组 nums，其中恰好有两个元素只出现一次，其余所有元素均出现两次。 找出只出现一次的那两个元素。你可以按 任意顺序 返回答案。

```python

class Solution:
    def singleNumber(self, nums: List[int]) -> List[int]:
        res = 0
        for num in nums:
            res ^= num
        
        # 找到第1位不为0的数字
        h = 1
        while res & h == 0:
            h <<= 1
        
        a, b = 0, 0
        for num in nums:
            if num & h == 0:
                a ^= num
            else:
                b ^= num

        return [a, b]





```
