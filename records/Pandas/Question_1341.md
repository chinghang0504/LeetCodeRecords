# [LeetCode Records](../../README.md) - Question 1341 Movie Rating

### Attempt 1: Use value_counts(), max(), pd.merge(), min(), dt.strftime(), groupby(), and mean()
```py
import pandas as pd

def movie_rating(movies: pd.DataFrame, users: pd.DataFrame, movie_rating: pd.DataFrame) -> pd.DataFrame:
    user_counts = movie_rating['user_id'].value_counts().reset_index()
    max_user_counts = user_counts[user_counts['count'] == user_counts['count'].max()]
    target_user_name = pd.merge(users, max_user_counts, on='user_id')['name'].min()

    movie_rating['month'] = movie_rating['created_at'].dt.strftime('%Y-%m')
    feb_movie_rating = movie_rating[movie_rating['month'] == '2020-02']
    feb_movie_rating = feb_movie_rating.groupby('movie_id')['rating'].mean().reset_index()
    max_feb_movie_rating = feb_movie_rating[feb_movie_rating['rating'] == feb_movie_rating['rating'].max()]
    target_movie_name = pd.merge(movies, max_feb_movie_rating, on='movie_id')['title'].min()

    return pd.DataFrame({
        'results': [target_user_name, target_movie_name]
    })
```
- Runtime: 464 ms (Beats: 88.15%)
- Memory: 71.26 MB (Beats: 62.14%)

<br>
