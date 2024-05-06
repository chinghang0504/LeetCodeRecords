# [LeetCode Records](../../README.md) - Question 883 Projection Area of 3D Shapes

### Attempt 1: Calculate the area of each projection
```java
class Solution {
    public int projectionArea(int[][] grid) {
        int n = grid.length;
        int totalArea = 0;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] != 0) {
                    totalArea++;
                }
            }
        }

        for (int i = 0; i < n; i++) {
            int max = 0;
            for (int j = 0; j < n; j++) {
                max = Math.max(max, grid[i][j]);
            }
            totalArea += max;
        }

        for (int j = 0; j < n; j++) {
            int max = 0;
            for (int i = 0; i < n; i++) {
                max = Math.max(max, grid[i][j]);
            }
            totalArea += max;
        }

        return totalArea;
    }
}
```
- Runtime: 2 ms (Beats: 89.13%)
- Memory: 44.26 MB (Beats: 30.00%)

<br>
