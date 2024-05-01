# [LeetCode Records](../../README.md) - Question 74 Search a 2D Matrix

### Attempt 1: Compare the first element of each row
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        for (int i = 1; i < matrix.length; i++) {
            if (target < matrix[i][0]) {
                int[] row = matrix[i - 1];
                for (int j = 0; j < row.length; j++) {
                    if (target == row[j]) {
                        return true;
                    }
                }
                return false;
            }
        }
        
        int[] row = matrix[matrix.length - 1];
        for (int j = 0; j < row.length; j++) {
            if (target == row[j]) {
                return true;
            }
        }

        return false;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.98 MB (Beats: 62.29%)

<br>
