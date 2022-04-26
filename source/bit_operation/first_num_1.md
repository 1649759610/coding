# 只出现一次的数字(第136题)

给定一个非空整数数组，除某个元素只出现1次外，其余每个元素均出现2次。找出那个只出现1次的元素。

```python

class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        tmp = nums[0]
        for num in nums[1:]:
            tmp ^= num
        
        return tmp


```
