# [LeetCode Records](../../README.md) - Question 931 Minimum Falling Path Sum

### Attempt 1: Caluate the minimum cumulative sum for each row
```java
class Solution {
    public int minFallingPathSum(int[][] matrix) {
        int n = matrix.length;
        int[][] cumSums = new int[n][n];
        for (int j = 0; j < n; j++) {
            cumSums[0][j] = matrix[0][j];
        }

        for (int i = 1; i < n; i++) {
            for (int j = 0; j < n; j++) {
                cumSums[i][j] = Integer.MAX_VALUE;
            }

            for (int j = 0; j < n; j++) {
                if (j - 1 >= 0) {
                    cumSums[i][j - 1] = Math.min(cumSums[i][j - 1], cumSums[i - 1][j] + matrix[i][j - 1]);
                }

                cumSums[i][j] = Math.min(cumSums[i][j], cumSums[i - 1][j] + matrix[i][j]);

                if (j + 1 < n) {
                    cumSums[i][j + 1] = Math.min(cumSums[i][j + 1], cumSums[i - 1][j] + matrix[i][j + 1]);
                }
            }
        }

        int lastIndex = n - 1;
        int minCumSum = cumSums[lastIndex][0];
        for (int j = 1; j < n; j++) {
            minCumSum = Math.min(minCumSum, cumSums[lastIndex][j]);
        }

        return minCumSum;
    }
}
```
- Runtime: 6 ms (Beats: 68.49%)
- Memory: 44.99 MB (Beats: 84.57%)

<br>
