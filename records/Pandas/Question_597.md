# [LeetCode Records](../../README.md) - Question 597 Friend Requests I: Overall Acceptance Rate

### Attempt 1: 
```py
import pandas as pd

def acceptance_rate(friend_request: pd.DataFrame, request_accepted: pd.DataFrame) -> pd.DataFrame:
    friend_request_size = len(friend_request.index)
    accept_rate = 0.0

    if friend_request_size != 0:
        friend_request_no_repeated = friend_request[['sender_id', 'send_to_id']].drop_duplicates()
        request_accepted_no_repeated = request_accepted[['requester_id', 'accepter_id']].drop_duplicates()
        merged = pd.merge(friend_request_no_repeated, request_accepted_no_repeated, left_on=['sender_id', 'send_to_id'], right_on=['requester_id', 'accepter_id'], how='right')
        accept_rate = len(merged.index) / len(friend_request_no_repeated.index)

    return pd.DataFrame({
        'accept_rate': [round(accept_rate, 2)]
    })
```
- Runtime: 565 ms (Beats: 87.50%)
- Memory: 67.06 MB (Beats: 8.04%)

<br>
