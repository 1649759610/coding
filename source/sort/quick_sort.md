# 快速排序

```python

# 双边循环法
def partition(nums, start, end):
    pivote = nums[start]
    pivote_index = start

    while start!=end:
        while start<end and nums[end]>pivote:
            end-=1
        while start<end and nums[start]<=pivote:
            start+=1
        if start<end:
            nums[start], nums[end] = nums[end], nums[start]
    nums[pivote_index]=nums[start]
    nums[start]=pivote
    return start

# 单边循环法
def partition(nums, start, end):
    mark = start
    pivote = nums[start]

    for i in range(start+1, end+1):
        if nums[i]<pivote:
            mark+=1
            nums[i], nums[mark] = nums[mark], nums[i]

    nums[start]=nums[mark]
    nums[mark]=pivote

    return mark


def quicksort(nums, start, end):
    if start>end:
        return

    pivoted_index = partition(nums, start, end)
    quicksort(nums, start, pivoted_index-1)
    quicksort(nums, pivoted_index+1, end)


if __name__ == '__main__':
    a=[3,3,1,6,3,2,5]
    a.remove(3)
    print(a)
    quicksort(a,0, len(a)-1)
    print(a)

```
