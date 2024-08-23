# [LeetCode Records](../../README.md) - Question 3087 Find Trending Hashtags

### Attempt 1: Use apply(), re.search(), groupby(), count(), and head()
```py
import pandas as pd
import re

def find_trending_hashtags(tweets: pd.DataFrame) -> pd.DataFrame:
    selected_tweets = tweets[(tweets['tweet_date'].dt.year == 2024) & (tweets['tweet_date'].dt.month == 2)]
    selected_tweets['hashtag'] = selected_tweets['tweet'].apply(lambda text: re.search("#[^\s]*", text)[0])

    hashtag_counts = selected_tweets.groupby('hashtag')['hashtag'].count().rename('hashtag_count').reset_index()
    hashtag_counts = hashtag_counts.sort_values(['hashtag_count', 'hashtag'], ascending=[False, False])
    return hashtag_counts.head(3)
```
- Runtime: 348 ms (Beats: 92.68%)
- Memory: 70.04 MB (Beats: 48.78%)

<br>
