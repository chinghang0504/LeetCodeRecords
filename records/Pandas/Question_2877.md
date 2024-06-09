# [LeetCode Records](../../README.md) - Question 2877 Create a DataFrame from List

### Attempt 1: Get two 1d lists
```py
import pandas as pd

def createDataframe(student_data: List[List[int]]) -> pd.DataFrame:
    id_list = []
    age_list = []
    for data in student_data:
        id_list.append(data[0])
        age_list.append(data[1])

    return pd.DataFrame({
        'student_id': id_list,
        'age': age_list
    })
```
- Runtime: 374 ms (Beats: 97.80%)
- Memory: 64.83 MB (Beats: 56.52%)

<br>

### Attempt 2: Use constructor only
```py
import pandas as pd

def createDataframe(student_data: List[List[int]]) -> pd.DataFrame:
    return pd.DataFrame(student_data, columns=['student_id', 'age'])
```
- Runtime: 345 ms (Beats: 99.20%)
- Memory: 64.60 MB (Beats: 76.40%)

<br>
