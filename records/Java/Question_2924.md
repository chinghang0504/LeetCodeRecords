# [LeetCode Records](../../README.md) - Question 2924 Find Champion II

### Attempt 1: Use a boolean[] to store the weak team indices
```java
class Solution {
    public int findChampion(int n, int[][] edges) {
        boolean[] weakTeams = new boolean[n];
        for (int[] edge : edges) {
            weakTeams[edge[1]] = true;
        }

        int strongestTeam = -1;
        for (int i = 0; i < n; i++) {
            if (!weakTeams[i]) {
                if (strongestTeam == -1) {
                    strongestTeam = i;
                } else {
                    return -1;
                }
            }
        }

        return strongestTeam;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 45.34 MB (Beats: 97.99%)

<br>
