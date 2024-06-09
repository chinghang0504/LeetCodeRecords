# [LeetCode Records](../../README.md) - Question 3053 Classifying Triangles by Lengths

### Attempt 1: Use apply()
```py
import pandas as pd

def getTriangleType(triangle):
    a = triangle['A']
    b = triangle['B']
    c = triangle['C']

    if a < b + c and b < c + a and c < a + b:
        if a == b and b == c:
            return 'Equilateral'
        elif a == b or b == c or c == a:
            return 'Isosceles'
        else:
            return 'Scalene'
    else:
        return 'Not A Triangle'

def type_of_triangle(triangles: pd.DataFrame) -> pd.DataFrame:
    triangles['triangle_type'] = triangles.apply(getTriangleType, axis=1)
    return triangles[['triangle_type']]
```
- Runtime: 427 ms (Beats: 100.00%)
- Memory: 65.77 MB (Beats: 46.15%)

<br>
