# 多数元素


给定一个大小为 n 的数组，找到其中的多数元素。多数元素是指在数组中出现次数 大于 ⌊ n/2 ⌋ 的元素。

你可以假设数组是非空的，并且给定的数组总是存在多数元素。


```python

class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        # 设置一个count 一个candidate， 当count==0时,candidate=num； 如果candidate=num, count+1, 否则count-1
        count = 0 
        candidate = None
        for num in nums:
            if count == 0:
                candidate=num
            count += 1 if candidate==num else -1

        return candidate

```
