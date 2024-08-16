# [LeetCode Records](../../README.md) - Question 1440 Evaluate Boolean Expression

### Attempt 1: Use pd.merge() and apply()
```py
import pandas as pd

def getResult(row):
    if row['operator'] == '>':
        ans = row['value_x'] > row['value_y']
    elif row['operator'] == '<':
        ans = row['value_x'] < row['value_y']
    else:
        ans = row['value_x'] == row['value_y']   
    return str(ans).lower()


def eval_expression(variables: pd.DataFrame, expressions: pd.DataFrame) -> pd.DataFrame:
    ans = pd.merge(expressions, variables, left_on='left_operand', right_on='name')
    ans = pd.merge(ans, variables, left_on='right_operand', right_on='name')
    ans['value'] = ans.apply(getResult, axis=1)

    return ans[['left_operand', 'operator', 'right_operand', 'value']]
```
- Runtime: 494 ms (Beats: 84.00%)
- Memory: 73.21 MB (Beats: 6.00%)

<br>
