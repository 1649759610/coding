# 四数之和 2（第454题）

给你四个整数数组 nums1、nums2、nums3 和 nums4 ，数组长度都是 n ，请你计算有多少个元组 (i, j, k, l) 能满足：  

- 0 <= i, j, k, l < n  
- nums1[i] + nums2[j] + nums3[k] + nums4[l] == 0

```python

class Solution:
    def fourSumCount(self, nums1: List[int], nums2: List[int], nums3: List[int], nums4: List[int]) -> int:
        res = 0
        mapper = {}
        for i in nums1:
            for j in nums2:
                mapper[i+j] = mapper.get(i+j, 0) + 1

        for i in nums3:
            for j in nums4:
                res += mapper.get(-(i+j), 0)
        
        return res


```