# 二分法变种问题1

```python
# 二分法变种问题：不能确定中间元素是否是
# 第1种情况：假设问题是在有序数组中查找第1个大于或等于x的元素，且该元素必定存在
# 一直找下去，直到最后

def bs(nums, x):
    left, right = 0, len(nums)-1
    while left <= right:
        mid = (left+ right) // 2 
        if left == right:
            break
        elif nums[mid] >= x:
            right = mid
        else:
            left = mid +1

    return nums[left]

nums = [1, 4, 7, 19, 23, 34]
target = 16

bs(nums, target)

```
