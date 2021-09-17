# 最长连续序列

给定一个未排序的整数数组 nums ，找出数字连续的最长序列（不要求序列元素在原数组中连续）的长度。

请你设计并实现时间复杂度为 O(n) 的算法解决此问题。

**示例**
- 输入：nums = [100,4,200,1,3,2]
- 输出：4
- 解释：最长数字连续序列是 [1, 2, 3, 4]。它的长度为 4。

## 第一种方法
先对数组元素去重，然后遍历数组。
对当前元素num， 如果num-1在数组中，则进行跳过。
否则， 开始遍历，num+1, num+2,...在不在数组里，如果在的话，则+1统计


```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        if len(nums) == 0:
            return 0

        num_set = set(nums)

        current_len = 1
        max_len = 1
        for num in num_set:
            if num -1 in num_set:
                continue
            else:
                i = 1
                while num+i in num_set:
                    print(num+i, "-")
                    current_len += 1
                    i += 1
                max_len = max(max_len, current_len)
                current_len = 1
        
        return max_len
```





## 第二种方法
先排序，再统计，时间复杂度O(nlogn)
```python

class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        if len(nums) == 0:
            return 0

        nums = sorted(nums)
        count = 1
        prev = nums[0]
        max_count = 1
        
        for i in range(1, len(nums)):
            if nums[i] == prev:
                continue
            if nums[i] == prev + 1:
                count += 1
            else:
                count = 1
        
            prev = nums[i]
            max_count = max(max_count, count)

        return max_count


```
