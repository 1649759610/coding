# 只出现一次的数字 2 （第137题）

给你一个整数数组 nums ，除某个元素仅出现 一次 外，其余每个元素都恰出现 三次 。请你找出并返回那个只出现了一次的元素。

```python
class Solution:
    def singleNumber(self, nums) -> int:
        res = 0
        for i in range(32):
            total = sum([(num >> i) & 1 for num in nums])
            # print(total)

            if total % 3 == 1:
                if i==31:
                    res -= (1<<i)
                else:
                    res |= (1 << i)
        
        return res

s= Solution()
nums = [2,2,2,3]
s.singleNumber(nums)


```
