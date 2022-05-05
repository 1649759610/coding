# 水壶问题

```python
# 解法1：暴力法，遍历所有状态
class Solution:
    def canMeasureWater(self, jug1Capacity: int, jug2Capacity: int, targetCapacity: int) -> bool:
        x, y, z = jug1Capacity, jug2Capacity, targetCapacity
        if x + y < z:
            return False
        
        queue = [(0,0)]
        seen = set((0,0))

        while len(queue) > 0:
            a, b = queue.pop()
            if a == z or b == z or a+b == z:
                return True
            
            states = set()
            states.add((0, b))
            states.add((a, 0))
            states.add((x, b))
            states.add((a, y))
            states.add((min(x, b+a), 0 if b<x-a else b-(x-a)))
            states.add((0 if a+b<y else a-(y-b), min(b+a, y)))

            for state in states:
                if state in seen:
                    continue
                queue.append(state)
                seen.add(state)

        return False

```
