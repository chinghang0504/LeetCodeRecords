# [LeetCode Records](../../README.md) - Question 1605 Find Valid Matrix Given Row and Column Sums

### Attempt 1: Find the minimum of the remainder of row and the remainder of column
```java
class Solution {
    public int[][] restoreMatrix(int[] rowSum, int[] colSum) {
        int m = rowSum.length;
        int n = colSum.length;
        int[][] ans = new int[m][n];

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                int val = Math.min(rowSum[i], colSum[j]);
                ans[i][j] = val;
                rowSum[i] -= val;
                colSum[j] -= val;
            }
        }

        return ans;
    }
}
```
- Runtime: 6 ms (Beats: 51.46%)
- Memory: 52.68 MB (Beats: 92.39%)

<br>
