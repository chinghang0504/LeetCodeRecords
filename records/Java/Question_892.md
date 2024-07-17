# [LeetCode Records](../../README.md) - Question 892 Surface Area of 3D Shapes

### Attempt 1: Calculate the total surface area without blocking first
```java
class Solution {
    public int surfaceArea(int[][] grid) {
        int n = grid.length;
        int totalSurfaceArea = 0;
        
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] > 0) {
                    totalSurfaceArea += grid[i][j] * 4 + 2;

                    if (i - 1 >= 0) {
                        totalSurfaceArea -= Math.min(grid[i][j], grid[i - 1][j]);
                    }
                    if (i + 1 < n) {
                        totalSurfaceArea -= Math.min(grid[i][j], grid[i + 1][j]);
                    }
                    if (j - 1 >= 0) {
                        totalSurfaceArea -= Math.min(grid[i][j], grid[i][j - 1]);
                    }
                    if (j + 1 < n) {
                        totalSurfaceArea -= Math.min(grid[i][j], grid[i][j + 1]);
                    }
                }
            }
        }

        return totalSurfaceArea;
    }
}
```
- Runtime: 7 ms (Beats: 20.19%)
- Memory: 43.81 MB (Beats: 86.06%)

<br>
