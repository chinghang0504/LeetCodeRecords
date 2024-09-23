# [LeetCode Records](../../README.md) - Question 2387 Median of a Row Wise Sorted Matrix

### Attempt 1: Use an int[] to store the leftmost index of each row
```java
class Solution {
    public int matrixMedian(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int medianIndex = m * n / 2;
        int[] leftIndices = new int[m];

        int currIndex = 0;
        while (true) {
            int min = Integer.MAX_VALUE;
            int minRow = 0;

            for (int i = 0; i < m; i++) {
                if (leftIndices[i] < n && grid[i][leftIndices[i]] < min) {
                    min = grid[i][leftIndices[i]];
                    minRow = i;
                }
            }

            if (currIndex == medianIndex) {
                return grid[minRow][leftIndices[minRow]];
            }

            leftIndices[minRow]++;
            currIndex++;
        }
    }
}
```
- Runtime: 217 ms (Beats: 5.66%)
- Memory: 69.29 MB (Beats: 75.47%)

<br>
