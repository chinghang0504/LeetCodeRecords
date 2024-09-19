# [LeetCode Records](../../README.md) - Question 1314 Matrix Block Sum

### Attempt 1: Calculate all the entries
```java
class Solution {
    public int[][] matrixBlockSum(int[][] mat, int k) {
        int m = mat.length;
        int n = mat[0].length;
        int[][] ans = new int[m][n];

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                ans[i][j] = getSum(mat, m, n, k, i, j);
            }
        }

        return ans;
    }

    private int getSum(int[][] mat, int m, int n, int k, int r, int c) {
        int sum = 0;

        int startI = r - k;
        if (startI < 0) {
            startI = 0;
        }
        int endI = r + k;
        if (endI >= m) {
            endI = m - 1;
        }

        int startJ = c - k;
        if (startJ < 0) {
            startJ = 0;
        }
        int endJ = c + k;
        if (endJ >= n) {
            endJ = n - 1;
        }

        for (int i = startI; i <= endI; i++) {
            for (int j = startJ; j <= endJ; j++) {
                sum += mat[i][j];
            }
        }

        return sum;
    }
}
```
- Runtime: 75 ms (Beats: 26.88%)
- Memory: 45.52 MB (Beats: 27.29%)

<br>
