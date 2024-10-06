# [LeetCode Records](../../README.md) - Question 1244 Design A Leaderboard

### Attempt 1: Use a HashMap to store the player ID and score key-value pairs
```java
class Leaderboard {

    private Map<Integer, Integer> map;

    public Leaderboard() {
        map = new HashMap<>();
    }
    
    public void addScore(int playerId, int score) {
        map.merge(playerId, score, Integer::sum);
    }
    
    public int top(int K) {
        List<Integer> list = new ArrayList<>(map.values());
        list.sort(null);

        int sum = 0;
        int index = list.size() - 1;
        for (int i = 0; i < K; i++) {
            sum += list.get(index - i);
        }

        return sum;
    }
    
    public void reset(int playerId) {
        map.put(playerId, 0);
    }
}

/**
 * Your Leaderboard object will be instantiated and called as such:
 * Leaderboard obj = new Leaderboard();
 * obj.addScore(playerId,score);
 * int param_2 = obj.top(K);
 * obj.reset(playerId);
 */
```
- Runtime: 19 ms (Beats: 46.43%)
- Memory: 44.52 MB (Beats: 44.81%)

<br>
