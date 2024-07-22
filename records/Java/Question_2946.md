# [LeetCode Records](../../README.md) - Question 2946 Matrix Similarity After Cyclic Shifts

### Attempt 1: Use three nested loops
```java
class Solution {
    public boolean areSimilar(int[][] mat, int k) {
        int m = mat.length;
        int n = mat[0].length;
        int[][] matrix = new int[m][n];
        int steps = k % n;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                matrix[i][j] = mat[i][j];
            }
        }

        for (int x = 0; x < steps; x++) {
            for (int i = 0; i < m; i++) {
                if (i % 2 == 0) {
                    int head = matrix[i][0];
                    for (int j = 0; j < n - 1; j++) {
                        matrix[i][j] = matrix[i][j + 1];
                    }
                    matrix[i][n - 1] = head;
                } else {
                    int tail = matrix[i][n - 1];
                    for (int j = n - 1; j >= 1; j--) {
                        matrix[i][j] = matrix[i][j - 1];
                    }
                    matrix[i][0] = tail;
                }
            }
        }

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (matrix[i][j] != mat[i][j]) {
                    return false;
                }
            }
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 29.83%)
- Memory: 45.48 MB (Beats: 5.46%)

<br>
