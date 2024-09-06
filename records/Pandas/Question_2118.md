# [LeetCode Records](../../README.md) - Question 2118 Build the Equation

### Attempt 1: Get the equation of each term
```py
import pandas as pd

def get_equation(row):
    factor = row['factor']
    power = row['power']
    
    equation = ''
    if factor > 0:
        equation = '+' + str(factor)
    else:
        equation = str(factor)
    
    if power == 1:
        equation = equation + 'X'
    elif power > 1:
        equation = equation + 'X^' + str(power)
    
    return equation


def build_the_equation(terms: pd.DataFrame) -> pd.DataFrame:
    sorted_terms = terms.sort_values('power', ascending=False)
    sorted_terms['equation'] = sorted_terms.apply(get_equation, axis=1)

    return pd.DataFrame({
        'equation': [sorted_terms['equation'].str.cat() + '=0']
    })
```
- Runtime: 423 ms (Beats: 90.00%)
- Memory: 69.66 MB (Beats: 40.00%)

<br>
