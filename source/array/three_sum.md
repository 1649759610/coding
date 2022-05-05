# 三数之和

给你一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？请你找出所有和为 0 且不重复的三元组。

注意：答案中不可以包含重复的三元组。

```python

class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        ans = []

        nums = sorted(nums)
        n = len(nums)
        # 要找到3个数，因此只需要找到导数n-3个数即可
        for i in range(n-2):
            # 去重
            if i > 0 and nums[i] == nums[i-1]:
                continue
            # 固定i， 寻找l 和r, 使用双指针法
            l = i + 1
            r = n -1

            while l < r:
                if nums[i] + nums[l] + nums[r] < 0:
                    l += 1
                elif  nums[i] + nums[l] + nums[r] > 0:
                    r -= 1
                else:
                    ans.append((nums[i], nums[l], nums[r]))
                    # 去重
                    while l<r and nums[l] == nums[l+1]:
                        l += 1
                    while l < r and nums[r] == nums[r-1]:
                        r -= 1
                    l += 1
                    r -= 1
        
        return ans

```
