# [LeetCode Records](../../README.md) - Question 2225 Find Players With Zero or One Losses

### Attempt 1: Use a HashSet to store the winners and a HashMap to store the losers and times
```java
class Solution {
    public List<List<Integer>> findWinners(int[][] matches) {
        Set<Integer> winPlayers = new HashSet<>();
        Map<Integer, Integer> losePlayers = new HashMap<>();

        for (int[] match : matches) {
            winPlayers.add(match[0]);
            losePlayers.merge(match[1], 1, Integer::sum);
        }

        List<Integer> ans0 = new ArrayList<>();
        for (Integer player : winPlayers) {
            if (!losePlayers.containsKey(player)) {
                ans0.add(player);
            }
        }
        ans0.sort(Integer::compare);

        List<Integer> ans1 = new ArrayList<>();
        for (Map.Entry<Integer, Integer> entry : losePlayers.entrySet()) {
            if (entry.getValue() == 1) {
                ans1.add(entry.getKey());
            }
        }
        ans1.sort(Integer::compare);

        return List.of(ans0, ans1);
    }
}
```
- Runtime: 72 ms (Beats: 82.94%)
- Memory: 78.67 MB (Beats: 98.13%)

<br>
