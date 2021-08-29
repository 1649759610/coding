# 移动零

给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。


```python

class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        # 使用双指着，让left先走，找到一个0，然后让right在left基础上，找到非0的元素进行交换，如此往复

        left, right = 0, 0
        while left<len(nums) and right<len(nums):
            while left<len(nums) and nums[left]!=0:
                left+=1
            right = left+1
            while right<len(nums) and nums[right]==0:
                right+=1
            if right<len(nums) and left<len(nums):
                nums[left], nums[right] = nums[right], nums[left]
                left+=1
                right+=1

```

