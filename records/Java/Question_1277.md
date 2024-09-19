# [LeetCode Records](../../README.md) - Question 1277 Count Square Submatrices with All Ones

### Attempt 1: Start from each one
```java
class Solution {
    public int countSquares(int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;
        int maxLength = Math.min(m, n);
        int sum = 0;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (matrix[i][j] == 1) {
                    sum += getSum(matrix, m, n, i, j, maxLength);
                }
            }
        }

        return sum;
    }

    private int getSum(int[][] matrix, int m, int n, int startI, int startJ, int maxLength) {
        int sum = 1;

        for (int length = 2; length <= maxLength; length++) {
            int endI = startI + length;
            if (endI > m) {
                break;
            }
            int endJ = startJ + length;
            if (endJ > n) {
                break;
            }

            if (isAllOnes(matrix, m, n, startI, endI, startJ, endJ)) {
                sum++;
            } else {
                break;
            }
        }

        return sum;
    }

    private boolean isAllOnes(int[][] matrix, int m, int n, int startI, int endI, int startJ, int endJ) {
        for (int i = startI; i < endI; i++) {
            for (int j = startJ; j < endJ; j++) {
                if (matrix[i][j] != 1) {
                    return false;
                }
            }
        }

        return true;
    }
}
```
- Runtime: 7 ms (Beats: 45.63%)
- Memory: 56.09 MB (Beats: 24.84%)

<br>
