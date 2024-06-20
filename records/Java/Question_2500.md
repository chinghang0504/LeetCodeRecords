# [LeetCode Records](../../README.md) - Question 2500 Delete Greatest Value in Each Row

### Attempt 1: Use a loop, a nested loop, and Arrays.sort()
```java
class Solution {
    public int deleteGreatestValue(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int sum = 0;

        for (int[] arr : grid) {
            Arrays.sort(arr);
        }

        for (int j = 0; j < n; j++) {
            int max = 0;
            for (int i = 0; i < m; i++) {
                max = Math.max(max, grid[i][j]);
            }
            sum += max;
        }

        return sum;
    }
}
```
- Runtime: 3 ms (Beats: 98.35%)
- Memory: 44.29 MB (Beats: 48.48%)

<br>
