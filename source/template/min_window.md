# 最小覆盖子串（第76题）

给出一个字符串S，一个字符串T，请在字符串S里找到包含T所有字母的最小子串。

输入： S="ADOBECODEBANC"， T="ABC"  
输出： "BANC"  

```python
from collections import Counter

class Solution:
    def minWindow(self, s: str, t: str) -> str:
        if not s and not t:
            return ""

        dict_t = Counter(t)
        required = len(dict_t)

        windows_count = {}
        formed = 0

        left, right = 0, 0

        # 长度，左边界，右边界
        ans = float("inf"), 0, 0

        while right < len(s):
            character = s[right]
            windows_count[character] = windows_count.get(character, 0) + 1
            if character in dict_t and windows_count[character] == dict_t[character]:
                formed += 1
            
            # 找到包含T中所有自付的字符串后，移动left指针，缩小窗口， 即满足条件后开始缩小范围
            while left <= right and formed == required:
                if ans[0] > right-left + 1:
                    ans = right-left+1, left, right
                character = s[left]
                windows_count[character] -= 1
                if windows_count[character] < dict_t[character]:
                    formed -= 1
                left += 1
            # 当窗口不符合条件时，移动right指针，扩大窗口
            right += 1
        
        # 查找完整个字符串S后，返回结果
        if ans[0] == float("inf"):
            return ""
        else:
            return s[ans[1]:ans[2]+1]
            










```
