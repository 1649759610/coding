# 1. 删除排序数组中的重复项

![](../.gitbook/assets/image%20%284%29.png)

![](../.gitbook/assets/image%20%283%29.png)

```python
"""
设置前后两个指针：
如果前面的指针end 指向的数值和 start指向的数值相同，那么end++
否则，start+1前移一个位置，接收end指向的新数值，然后end++, count++
"""
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        if len(nums)==1:
            return 1

        start, end = 0, 1
        count = 1
        while end < len(nums):
            if nums[start] == nums[end]:
                end += 1
            else:
                start += 1
                nums[start]=nums[end]
                end += 1
                count += 1
        
        return count
```



