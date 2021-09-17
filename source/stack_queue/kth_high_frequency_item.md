# 前K个高频元素

给你一个整数数组 nums 和一个整数 k ，请你返回其中出现频率前 k 高的元素。你可以按 任意顺序 返回答案。


```python
from collections import Counter
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        result  = []
        counter = Counter(nums)

        items = sorted(counter.items(), key=lambda x: x[1], reverse=True)

        for item in items[:k]:
            result.append(item[0])
        
        return result

```
