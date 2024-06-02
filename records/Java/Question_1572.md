# [LeetCode Records](../../README.md) - Question 1572 Matrix Diagonal Sum

### Attempt 1: Use a loop
```java
class Solution {
    public int diagonalSum(int[][] mat) {
        int sum = 0;
        int n = mat.length;

        for (int i = 0; i < n; i++) {
            sum += mat[i][i] + mat[i][n - 1 - i];
        }

        if (n % 2 == 1) {
            sum -= mat[n / 2][n / 2];
        }

        return sum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.09 MB (Beats: 67.29%)

<br>
