# [LeetCode Records](../../README.md) - Question 2428 Maximum Sum of an Hourglass

### Attempt 1: Compare all the possible cases
```java
class Solution {
    public int maxSum(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;

        int maxSum = Integer.MIN_VALUE;
        for (int i = 0; i < m - 2; i++) {
            for (int j = 0; j < n - 2; j++) {
                int sum = getSum(grid, i, j);
                maxSum = Math.max(maxSum, sum);
            }
        }

        return maxSum;
    }

    private int getSum(int[][] grid, int startI, int startJ) {
        int sum = 0;

        for (int i = 0; i < 3; i++) {
            sum += grid[startI][startJ + i];
            sum += grid[startI + 2][startJ + i];
        }
        sum += grid[startI + 1][startJ + 1];

        return sum;
    }
}
```
- Runtime: 4 ms (Beats: 88.34%)
- Memory: 44.79 MB (Beats: 56.33%)

<br>
