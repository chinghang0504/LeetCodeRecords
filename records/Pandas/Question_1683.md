# [LeetCode Records](../../README.md) - Question 1683 Invalid Tweets

### Attempt 1: Use apply()
```py
import pandas as pd

def invalid_tweets(tweets: pd.DataFrame) -> pd.DataFrame:
    tweets['count'] = tweets.apply(lambda row: len(row['content']), axis=1)
    return tweets[tweets['count'] > 15][['tweet_id']]
```
- Runtime: 431 ms (Beats: 100.00%)
- Memory: 66.92 MB (Beats: 5.30%)

<br>
