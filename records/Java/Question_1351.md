# [LeetCode Records](../../README.md) - Question 1351 Count Negative Numbers in a Sorted Matrix

### Attempt 1: Check every entry
```java
class Solution {
    public int countNegatives(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int count = 0;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] < 0) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 54.65%)
- Memory: 45.29 MB (Beats: 45.68%)

<br>
