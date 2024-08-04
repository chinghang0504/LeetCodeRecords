# [LeetCode Records](../../README.md) - Question 2133 Check if Every Row and Column Contains All Numbers

### Attempt 1: Use two helper functions to check if the row and the column are valid
```java
class Solution {
    public boolean checkValid(int[][] matrix) {
        int n = matrix.length;

        for (int i = 0; i < n; i++) {
            if (!isRowValid(matrix, n, i)) {
                return false;
            }
        }
        for (int i = 0; i < n; i++) {
            if (!isColValid(matrix, n, i)) {
                return false;
            }
        }

        return true;
    }

    private boolean isRowValid(int[][] matrix, int n, int row) {
        boolean[] counts = new boolean[n];

        for (int i = 0; i < n; i++) {
            counts[matrix[row][i] - 1] = true;
        }

        for (int i = 0; i < n; i++) {
            if (!counts[i]) {
                return false;
            }
        }

        return true;
    }

    private boolean isColValid(int[][] matrix, int n, int col) {
        boolean[] counts = new boolean[n];

        for (int i = 0; i < n; i++) {
            counts[matrix[i][col] - 1] = true;
        }

        for (int i = 0; i < n; i++) {
            if (!counts[i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 99.69%)
- Memory: 45.28 MB (Beats: 50.68%)

<br>
