# 替换后的最长重复字符（第424题）

给你一个字符串 s 和一个整数 k 。你可以选择字符串中的任一字符，并将其更改为任何其他大写英文字符。该操作最多可执行 k 次。

在执行上述操作后，返回包含相同字母的最长子字符串的长度。

**示例 1：**  

输入：s = "ABAB", k = 2  
输出：4  
解释：用两个'A'替换为两个'B',反之亦然。  


**示例 2：**  
输入：s = "AABABBA", k = 1  
输出：4  
解释：
将中间的一个'A'替换为'B',字符串变为 "AABBBBA"。
子串 "BBBB" 有最长重复字母, 答案为 4。  


```python
from collections import Counter
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        if len(s) == 0:
            return 0

        left, right = 0, 0
        max_char_n = 0
        windows_count = Counter()

        for right in range(len(s)):
            windows_count[s[right]] += 1
            max_char_n = max(max_char_n, windows_count[s[right]])

            if max_char_n + k < right - left +1:
                windows_count[s[left]] -= 1
                left += 1
        
        return right - left +1

```
