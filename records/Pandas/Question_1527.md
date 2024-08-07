# [LeetCode Records](../../README.md) - Question 1527 Patients With a Condition

### Attempt 1: Use split(), re.match(), and apply()
```py
import pandas as pd

def has_diabetes_type_1(conditions):
    condition_list = conditions.split()
    hasPrefix = False
    for condition in condition_list:
        if re.match(r'^DIAB1', condition):
            hasPrefix = True
            break
            
    return hasPrefix


def find_patients(patients: pd.DataFrame) -> pd.DataFrame:
    patients['has_diabetes_type_1'] = patients['conditions'].apply(lambda x: has_diabetes_type_1(x))
    return patients[patients['has_diabetes_type_1']][['patient_id','patient_name','conditions']]

```
- Runtime: 345 ms (Beats: 80.43%)
- Memory: 69.83 MB (Beats: 9.52%)

<br>
