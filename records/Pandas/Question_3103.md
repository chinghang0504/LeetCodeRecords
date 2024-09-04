# [LeetCode Records](../../README.md) - Question 3103 Find Trending Hashtags II

### Attempt 1: Use apply() to get a data frame of all the hashtags in each row
```py
import pandas as pd

def get_hashtags(row):
    return pd.DataFrame({
        'hashtag': re.findall('#[a-zA-Z]+', row['tweet'])
    })


def find_trending_hashtags(tweets: pd.DataFrame) -> pd.DataFrame:
    hashtags = pd.concat([*tweets.apply(get_hashtags, axis=1)])

    hashtag_counts = hashtags.value_counts().reset_index()
    return hashtag_counts.sort_values(['count', 'hashtag'], ascending=[False, False]).head(3)
```
- Runtime: 381 ms (Beats: 64.29%)
- Memory: 70.75 MB (Beats: 35.71%)

<br>
