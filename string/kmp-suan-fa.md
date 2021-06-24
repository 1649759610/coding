# KMP算法

## 经典KMP算法

```python
def getNext(pattern_str):
    pattern = list(pattern_str)
    next = [-1]*len(pattern)
    k, j = -1, 0

    while j < len(next)-1:
        # 此刻，k=next[j-1], 且 p[k]表示前缀， p[j]表示后缀
        # 注：k==-1 表示未找到k前缀与k后缀相等， 首次分析可忽略
        if k == -1 or pattern[j] == pattern[k]:
            j += 1
            k += 1
            next[j] = k
        else:
            k = next[k]

    return next

def kmp(main_str, pattern_str):
    # 获取next数组
    next = getNext(pattern_str)

    # 开始匹配
    i, j = 0, 0
    while i < len(main_str) and j < len(pattern_str):
        if j == -1 or main_str[i] == pattern_str[j]:
            i += 1
            j += 1
        else:
            j = next[j]

        if j == len(pattern_str):
            return i - len(pattern_str)

    return -1


if __name__ == '__main__':
    main_str  = "ccababaabcabacba"
    pattern_str = "abaabcaba"
    next = kmp(main_str, pattern_str)
    print(next)
```

![](https://github.com/1649759610/interview_coding/tree/e7461202f2a8c87ddd55e166a94d97365e69d722/.gitbook/assets/image%20%2812%29.png)

![](https://github.com/1649759610/interview_coding/tree/e7461202f2a8c87ddd55e166a94d97365e69d722/.gitbook/assets/image%20%281%29.png)

![](https://github.com/1649759610/interview_coding/tree/e7461202f2a8c87ddd55e166a94d97365e69d722/.gitbook/assets/image%20%287%29.png)

## KMP算法改进版

![](https://github.com/1649759610/interview_coding/tree/e7461202f2a8c87ddd55e166a94d97365e69d722/.gitbook/assets/image.png)

![](https://github.com/1649759610/interview_coding/tree/e7461202f2a8c87ddd55e166a94d97365e69d722/.gitbook/assets/image%20%282%29.png)

```python
def getNext(pattern_str):
    pattern = list(pattern_str)
    next = [-1]*len(pattern)
    k, j = -1, 0

    while j < len(next)-1:
        # 此刻，k=next[j-1], 且 p[k]表示前缀， p[j]表示后缀
        # 注：k==-1 表示未找到k前缀与k后缀相等， 首次分析可忽略
        if k == -1 or pattern[j] == pattern[k]:
            j += 1
            k += 1
            if pattern[j] == pattern[k]:
                next[j] = next[k]
            else:
                next[j] = k
        else:
            k = next[k]

    return next

def kmp(main_str, pattern_str):
    # 获取next数组
    next = getNext(pattern_str)

    # 开始匹配
    i, j = 0, 0
    while i < len(main_str) and j < len(pattern_str):
        if j == -1 or main_str[i] == pattern_str[j]:
            i += 1
            j += 1
        else:
            j = next[j]

        if j == len(pattern_str):
            return i - len(pattern_str)

    return -1


if __name__ == '__main__':
    main_str  = "ccababaabcabacba"
    pattern_str = "abaabcaba"
    next = kmp(main_str, pattern_str)
    print(next)
```

