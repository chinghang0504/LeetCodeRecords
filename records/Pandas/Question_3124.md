# [LeetCode Records](../../README.md) - Question 3124 Find Longest Calls

### Attempt 1: Use tail(), pd.concat(), pd.merge(), apply(), strftime(), and gmtime()
```py
import pandas as pd
from time import strftime
from time import gmtime

def find_longest_calls(contacts: pd.DataFrame, calls: pd.DataFrame) -> pd.DataFrame:
    incoming_calls = calls[calls['type'] == 'incoming'].sort_values('duration').tail(3)
    outgoing_calls = calls[calls['type'] == 'outgoing'].sort_values('duration').tail(3)
    selected_calls = pd.concat([incoming_calls, outgoing_calls])

    ans = pd.merge(selected_calls, contacts, left_on='contact_id', right_on='id')
    ans = ans.sort_values(['type', 'duration', 'first_name'], ascending=[True, False, False])
    ans['duration_formatted'] = ans['duration'].apply(lambda x: strftime("%H:%M:%S", gmtime(x)))

    return ans[['first_name', 'type', 'duration_formatted']]
```
- Runtime: 367 ms (Beats: 93.48%)
- Memory: 70.72 MB (Beats: 30.43%)

<br>
