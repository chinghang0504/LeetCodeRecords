# [LeetCode Records](../../README.md) - Question 610 Triangle Judgement

### Attempt 1: 
```py
import pandas as pd

def isTriangle(row):
    x = row['x']
    y = row['y']
    z = row['z']
    
    if x + y <= z:
        return 'No'
    if y + z <= x:
        return 'No'
    if z + x <= y:
        return 'No'
    return 'Yes'

def triangle_judgement(triangle: pd.DataFrame) -> pd.DataFrame:
    triangle['triangle'] = triangle.apply(isTriangle, axis=1)
    return triangle
```
- Runtime: 587 ms (Beats: 78.55%)
- Memory: 65.68 MB (Beats: 31.70%)

<br>
