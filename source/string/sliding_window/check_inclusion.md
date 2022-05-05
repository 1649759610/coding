# 字符串的排列

给你两个字符串 s1 和 s2 ，写一个函数来判断 s2 是否包含 s1 的排列。如果是，返回 true ；否则，返回 false 。

换句话说，s1 的排列之一是 s2 的 子串 。

 

**示例 1**：   
输入：s1 = "ab" s2 = "eidbaooo"  
输出：true  
解释：s2 包含 s1 的排列之一 ("ba").  

**示例 2**：  
输入：s1= "ab" s2 = "eidboaoo"  
输出：false  

```python
from collections import Counter
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:

        left, right = 0, len(s1)-1
        dict_t = Counter(s1)
        required = len(dict_t)
        formed = 0

        # 以len(s1)的长度的s2，初始化 window_count
        window_count = Counter()
        for c in s2[:len(s1)]:
            window_count[c] += 1
            if c in dict_t and dict_t[c] == window_count[c]:
                formed += 1
        if formed == required:
            return True

        while right < len(s2):
            # 左边缩短1个
            window_count[s2[left]] -= 1
            if s2[left] in dict_t and  window_count[s2[left]] + 1 == dict_t[s2[left]]:
                formed -= 1

            left += 1
            # 右边增加1个
            right += 1
            if right >= len(s2):
                return False
                
            window_count[s2[right]] += 1

            if s2[right] in dict_t and dict_t[s2[right]] == window_count[s2[right]]:
                formed += 1
            
            if formed == required:
                return True
        
        return False


```
