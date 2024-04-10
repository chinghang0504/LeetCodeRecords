# [LeetCode Records](../README.md) - Question 62 Unique Paths

### Attempt 1: Use an int array to record previous calculation
```java
class Solution {

    private int[][] saved;

    public int uniquePaths(int m, int n) {
        saved = new int[m + 1][n + 1];
        for (int i = 0; i < m + 1; i++) {
            for (int j = 0; j < n + 1; j++) {
                saved[i][j] = -1;
            }
        }

        return uniquePathsRecursion(m, n);
    }

    private int uniquePathsRecursion(int m, int n) {
        if (m == 0 || n == 0) {
            return 0;
        } else if (m == 1 || n == 1) {
            return 1;
        }

        if (saved[m][n] == -1) {
            saved[m][n] = uniquePathsRecursion(m - 1, n) + uniquePathsRecursion(m, n - 1);
        }

        return saved[m][n];
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.04 MB (Beats: 82.89%)

<br>
