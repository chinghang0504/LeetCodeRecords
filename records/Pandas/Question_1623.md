# [LeetCode Records](../../README.md) - Question 1623 All Valid Triplets That Can Represent a Country

### Attempt 1: Use pd.merge()
```py
import pandas as pd

def find_valid_triplets(school_a: pd.DataFrame, school_b: pd.DataFrame, school_c: pd.DataFrame) -> pd.DataFrame:
    answer = pd.merge(school_a.rename(columns={'student_id': 'id_A', 'student_name': 'member_A'}), school_b.rename(columns={'student_id': 'id_B', 'student_name': 'member_B'}), how='cross')
    answer = pd.merge(answer, school_c.rename(columns={'student_id': 'id_C', 'student_name': 'member_C'}), how='cross')
    answer = answer[(answer['id_A'] != answer['id_B']) & (answer['id_A'] != answer['id_C']) & (answer['id_B'] != answer['id_C'])]
    answer = answer[(answer['member_A'] != answer['member_B']) & (answer['member_A'] != answer['member_C']) & (answer['member_B'] != answer['member_C'])]
    return answer[['member_A', 'member_B', 'member_C']]
```
- Runtime: 608 ms (Beats: 95.24%)
- Memory: 76.53 MB (Beats: 23.81%)

<br>
