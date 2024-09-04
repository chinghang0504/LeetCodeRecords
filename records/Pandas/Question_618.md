# [LeetCode Records](../../README.md) - Question 618 Students Report By Geography

### Attempt 1: Use pd.concat() to combine all the columns
```py
import pandas as pd

def geography_report(student: pd.DataFrame) -> pd.DataFrame:
    america_students = student[student['continent'] == 'America'][['name']].sort_values('name').rename(columns={'name': 'America'}).reset_index(drop=True)
    asia_students = student[student['continent'] == 'Asia'][['name']].sort_values('name').rename(columns={'name': 'Asia'}).reset_index(drop=True)
    europe_students = student[student['continent'] == 'Europe'][['name']].sort_values('name').rename(columns={'name': 'Europe'}).reset_index(drop=True)
    return pd.concat([america_students, asia_students, europe_students], axis=1)
```
- Runtime: 366 ms (Beats: 77.03%)
- Memory: 70.28 MB (Beats: 41.89%)

<br>
