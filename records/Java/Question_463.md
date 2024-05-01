# [LeetCode Records](../../README.md) - Question 463 Island Perimeter

### Attempt 1: Check the neighbours of land cells
```java
class Solution {
    public int islandPerimeter(int[][] grid) {
        int perimeter = 0;
        int rowSize = grid.length;
        int colSize = grid[0].length;

        for (int i = 0; i < rowSize; i++) {
            for (int j = 0; j < colSize; j++) {
                if (grid[i][j] == 0) {
                    continue;
                }

                int localPerimeter = 4;
                if (i - 1 >= 0 && grid[i - 1][j] == 1) {
                    localPerimeter--;
                }
                if (i + 1 < rowSize && grid[i + 1][j] == 1) {
                    localPerimeter--;
                }
                if (j - 1 >= 0 && grid[i][j - 1] == 1) {
                    localPerimeter--;
                }
                if (j + 1 < colSize && grid[i][j + 1] == 1) {
                    localPerimeter--;
                }

                perimeter += localPerimeter;
            }
        }
        
        return perimeter;
    }
}
```
- Runtime: 4 ms (Beats: 99.62%)
- Memory: 46.21 MB (Beats: 5.66%)

<br>
