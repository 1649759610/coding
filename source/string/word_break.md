# 单词拆分

给你一个字符串 s 和一个字符串列表 wordDict 作为字典，判定 s 是否可以由空格拆分为一个或多个在字典中出现的单词。

说明：拆分时可以重复使用字典中的单词。

```
输入: s = "leetcode", wordDict = ["leet", "code"]
输出: true
解释: 返回 true 因为 "leetcode" 可以被拆分成 "leet code"。
```

```python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> bool:
        # dp[i]:表示前s[0:i]，即前i个字符是可以用wordDict进行表示的   
        dp = [False] * (len(s)+1)
        dp[0] = True
        for i in range(len(s)+1):
            for j in range(0, i):
                if dp[j] and s[j:i] in wordDict:
                    dp[i] = True
                    break
        # print(dp)
        return dp[len(s)]

```
