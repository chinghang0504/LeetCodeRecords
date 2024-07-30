# [LeetCode Records](../../README.md) - Question 766 Toeplitz Matrix

### Attempt 1: Use a nested while loop that can change the start positions
```java
class Solution {
    public boolean isToeplitzMatrix(int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;
        int startI = m - 1;
        int startJ = 0;
        boolean isVertical = true;

        while (startJ < n - 1) {
            int item = matrix[startI][startJ];
            int i = startI + 1;
            int j = startJ + 1;
            while (i < m && j < n) {
                if (matrix[i][j] != item) {
                    return false;
                }

                i++;
                j++;
            }

            if (isVertical) {
                if (startI == 0) {
                    isVertical = false;
                    startJ++;
                } else {
                    startI--;
                }
            } else {
                startJ++;
            }
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.61 MB (Beats: 7.98%)

<br>
