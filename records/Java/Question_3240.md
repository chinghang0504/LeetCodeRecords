# [LeetCode Records](../../README.md) - Question 3240 Design Neighbor Sum Service

### Attempt 1: Save the grid and the position of every number
```java
class neighborSum {

    private int[][] grid;
    private int n;
    private int[] xIndices;
    private int[] yIndices;

    public neighborSum(int[][] grid) {
        this.grid = grid;
        n = grid.length;
        xIndices = new int[n * n];
        yIndices = new int[n * n];

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                int index = grid[i][j];
                xIndices[index] = i;
                yIndices[index] = j;
            }
        }
    }
    
    public int adjacentSum(int value) {
        int x = xIndices[value];
        int y = yIndices[value];
        int sum = 0;

        if (x - 1 >= 0) {
            sum += grid[x - 1][y];
        }
        if (x + 1 < n) {
            sum += grid[x + 1][y];
        }
        if (y - 1 >= 0) {
            sum += grid[x][y - 1];
        }
        if (y + 1 < n) {
            sum += grid[x][y + 1];
        }

        return sum;
    }
    
    public int diagonalSum(int value) {
        int x = xIndices[value];
        int y = yIndices[value];
        int sum = 0;

        if (x - 1 >= 0 && y - 1 >= 0) {
            sum += grid[x - 1][y - 1];
        }
        if (x - 1 >= 0 && y + 1 < n) {
            sum += grid[x - 1][y + 1];
        }
        if (x + 1 < n && y - 1 >= 0) {
            sum += grid[x + 1][y - 1];
        }
        if (x + 1 < n && y + 1 < n) {
            sum += grid[x + 1][y + 1];
        }

        return sum;
    }
}
```
- Runtime: 14 ms (Beats: 100.00%)
- Memory: 45.96 MB (Beats: 50.00%)

<br>
