# [LeetCode Records](../../README.md) - Question 3402 Minimum Operations to Make Columns Strictly Increasing

### Attempt 1: Track the previous value
```java
class Solution {
    public int minimumOperations(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int count = 0;

        for (int j = 0; j < n; j++) {
            int prev = grid[0][j];

            for (int i = 1; i < m; i++) {
                int target = prev + 1;
                if (grid[i][j] < target) {
                    count += target - grid[i][j];
                    prev = target;
                } else {
                    prev = grid[i][j];
                }
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 45.41 MB (Beats: 100.00%)

<br>
