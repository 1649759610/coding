# sqrt

```python

def sqrt(val):
    n = 1000
    estimate_val = val/2
    while n > 0:
        estimate_val = (estimate_val + val/estimate_val)/2
        n -= 1

    print(estimate_val)

if __name__ == '__main__':
    sqrt(2)


```
