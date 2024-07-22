# [LeetCode Records](../../README.md) - Question 1886 Determine Whether Matrix Can Be Obtained By Rotation

### Attempt 1: Rotate the matrix and test it
```java
class Solution {
    public boolean findRotation(int[][] mat, int[][] target) {
        if (isEqualMatrix(mat, target)) {
            return true;
        }

        for (int i = 0; i < 3; i++) {
            rotateMatrix(mat);

            if (isEqualMatrix(mat, target)) {
                return true;
            }
        }

        return false;
    }

    private void rotateMatrix(int[][] matrix) {
        int n = matrix.length;

        for (int i = 0; i < n - 1; i++) {
            for (int j = i + 1; j < n; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }

        for (int j = 0; j < n / 2; j++) {
            for (int i = 0; i < n; i++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[i][n - 1 - j];
                matrix[i][n - 1 - j] = temp;
            }
        }
    }

    private boolean isEqualMatrix(int[][] m1, int[][] m2) {
        int n = m1.length;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (m1[i][j] != m2[i][j]) {
                    return false;
                }
            }
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.59 MB (Beats: 65.84%)

<br>
