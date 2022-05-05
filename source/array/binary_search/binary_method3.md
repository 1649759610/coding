# 二分法变种问题2


```python
# 第2种情况：假设问题在有序数组中查找最后一个小于或等于x的元素， 且该元素必定存在

def bs(nums, x):
    left, right = 0, len(nums)-1
    while left <= right:
        mid = (left + right) // 2
        # left + 1 == right： 防止程序进入死循环
        if left == right or left + 1 == right:
            break
        elif nums[mid] <= x:
            left = mid
        else:
            right = mid - 1
    
    # 最后可能会剩余两个元素没有进行验证是否小于等于x，手动验证一下即可
    if nums[right] <= x:
        return nums[right]
    else:
        return nums[left]

nums = [1, 4, 7, 19, 23, 34, 56]
target = 16

bs(nums, target)
```
