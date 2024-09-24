# [LeetCode Records](../../README.md) - Question 1817 Finding the Users Active Minutes

### Attempt 1: Use a HashMap to store the id and unique time key-value pairs
```java
class Solution {
    public int[] findingUsersActiveMinutes(int[][] logs, int k) {
        Map<Integer, Set<Integer>> map = new HashMap<>();
        for (int[] log : logs) {
            int id = log[0];
            int time = log[1];

            Set<Integer> set = map.get(id);
            if (set == null) {
                set = new HashSet<>();
                map.put(id, set);
            }

            set.add(time);
        }

        int[] ans = new int[k];
        for (Map.Entry<Integer, Set<Integer>> entry : map.entrySet()) {
            int uam = entry.getValue().size();
            ans[uam - 1]++;
        }

        return ans;
    }
}
```
- Runtime: 15 ms (Beats: 95.04%)
- Memory: 57.15 MB (Beats: 22.34%)

<br>
