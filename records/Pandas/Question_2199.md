# [LeetCode Records](../../README.md) - Question 2199 Finding the Topic of Each Post

### Attempt 1: Use a helper function to get the topics
```py
import pandas as pd

def get_topics(keywords, row):
    words = re.split('\s', row['content'].lower()) 
    topics = set()
    
    for index, keyword in keywords.iterrows():
        if keyword['word'] in words:
            topics.add(keyword['topic_id'])
    
    if len(topics) == 0:
        return 'Ambiguous!'
    else:
        topic_list = list(topics)
        topic_list.sort()
        return ','.join(str(x) for x in topic_list)
        

def find_topic(keywords: pd.DataFrame, posts: pd.DataFrame) -> pd.DataFrame:
    keywords['word'] = keywords['word'].apply(lambda word: word.lower())

    posts['topic'] = posts.apply(lambda row: get_topics(keywords, row), axis=1)
    return posts[['post_id', 'topic']]
```
- Runtime: 2214 ms (Beats: 14.29%)
- Memory: 69.95 MB (Beats: 64.29%)

<br>
