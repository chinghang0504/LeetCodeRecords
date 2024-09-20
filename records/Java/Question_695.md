# [LeetCode Records](../../README.md) - Question 695 Max Area of Island

### Attempt 1: Use a boolean[][] to record the land that is reached
```java
class Solution {
    public int maxAreaOfIsland(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        boolean[][] colored = new boolean[m][n];

        int maxArea = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 1 && !colored[i][j]) {
                    int area = getArea(grid, m, n, colored, i, j);
                    maxArea = Math.max(maxArea, area);
                }
            }
        }

        return maxArea;
    }

    private int getArea(int[][] grid, int m, int n, boolean[][] colored, int startI, int startJ) {
        List<int[]> list = new ArrayList<>();
        list.add(new int[]{ startI, startJ });
        int count = 0;

        while (!list.isEmpty()) {
            List<int[]> nextList = new ArrayList<>();

            for (int[] coordinates : list) {
                int i = coordinates[0];
                int j = coordinates[1];
                if (!colored[i][j]) {
                    colored[i][j] = true;
                    count++;
                    
                    if (i - 1 >= 0 && grid[i - 1][j] == 1 && !colored[i - 1][j]) {
                        nextList.add(new int[]{ i - 1, j });
                    }
                    if (i + 1 < m && grid[i + 1][j] == 1 && !colored[i + 1][j]) {
                        nextList.add(new int[]{ i + 1, j });
                    }
                    if (j - 1 >= 0 && grid[i][j - 1] == 1 && !colored[i][j - 1]) {
                        nextList.add(new int[]{ i, j - 1 });
                    }
                    if (j + 1 < n && grid[i][j + 1] == 1 && !colored[i][j + 1]) {
                        nextList.add(new int[]{ i, j + 1 });
                    }
                }
            }

            list = nextList;
        }

        return count;
    }
}
```
- Runtime: 3 ms (Beats: 30.51%)
- Memory: 44.68 MB (Beats: 41.00%)

<br>
