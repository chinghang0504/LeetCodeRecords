# [LeetCode Records](../../README.md) - Question 355 Design Twitter

### Attempt 1: Use a HashMap to record the followers and an ArrayList to record the posts
```java
class Twitter {

    private static class Post {
        private final int userId;
        private final int tweetId;

        public Post(int userId, int tweetId) {
            this.userId = userId;
            this.tweetId = tweetId;
        }
    }

    private final Map<Integer, Set<Integer>> followerMap;
    private final List<Post> posts;

    public Twitter() {
        followerMap = new HashMap<>();
        posts = new ArrayList<>();
    }

    public void postTweet(int userId, int tweetId) {
        posts.add(new Post(userId, tweetId));
    }

    public List<Integer> getNewsFeed(int userId) {
        Set<Integer> set = followerMap.get(userId);
        List<Integer> result = new ArrayList<>();

        int count = 0;
        if (set != null) {
            for (Post post : posts.reversed()) {
                if (post.userId == userId || set.contains(post.userId)) {
                    result.add(post.tweetId);
                    count++;
                }

                if (count >= 10) {
                    break;
                }
            }
        } else {
            for (Post post : posts.reversed()) {
                if (post.userId == userId) {
                    result.add(post.tweetId);
                    count++;
                }

                if (count >= 10) {
                    break;
                }
            }
        }

        return result;
    }

    public void follow(int followerId, int followeeId) {
        Set<Integer> set = followerMap.get(followerId);
        if (set == null) {
            set = new HashSet<>();
            followerMap.put(followerId, set);
        }

        set.add(followeeId);
    }

    public void unfollow(int followerId, int followeeId) {
        Set<Integer> set = followerMap.get(followerId);
        if (set != null) {
            set.remove(followeeId);
        }
    }
}
```
- Runtime: 8 ms (Beats: 89.74%)
- Memory: 41.17 MB (Beats: 92.86%)

<br>
