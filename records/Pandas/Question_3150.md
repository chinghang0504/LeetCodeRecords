# [LeetCode Records](../../README.md) - Question 3150 Invalid Tweets II

### Attempt 1: Use apply()
```py
import pandas as pd

def find_invalid_tweets(tweets: pd.DataFrame) -> pd.DataFrame:
    tweets['len'] = tweets['content'].apply(lambda x: len(x))
    tweets['mention_num'] = tweets['content'].apply(lambda x: x.count('@'))
    tweets['hashtag_num'] = tweets['content'].apply(lambda x: x.count('#'))
    invalid_tweets_df = tweets[(tweets['len'] > 140) | (tweets['mention_num'] > 3) | (tweets['hashtag_num'] > 3)]
    return invalid_tweets_df[['tweet_id']].sort_values('tweet_id')
```
- Runtime: 368 ms (Beats: 100.00%)
- Memory: 66.24 MB (Beats: 12.70%)

<br>
