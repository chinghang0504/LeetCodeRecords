# [LeetCode Records](../../README.md) - Question 1615 Maximal Network Rank

### Attempt 1: Use an int[] to store the number of edges in each vertice
```java
class Solution {
    public int maximalNetworkRank(int n, int[][] roads) {
        int[] counts = new int[n];
        boolean[][] edges = new boolean[n][n];

        for (int[] road : roads) {
            counts[road[0]]++;
            counts[road[1]]++;
            edges[road[0]][road[1]] = true;
            edges[road[1]][road[0]] = true;
        }

        int maxCount = 0;
        for (int i = 0; i < n - 1; i++) {
            for (int j = i + 1; j < n; j++) {
                int count = counts[i] + counts[j];
                if (edges[i][j]) {
                    count--;
                }
                maxCount = Math.max(maxCount, count);
            }
        }

        return maxCount;
    }
}
```
- Runtime: 4 ms (Beats: 99.39%)
- Memory: 45.60 MB (Beats: 54.17%)

<br>
