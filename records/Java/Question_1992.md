# [LeetCode Records](../../README.md) - Question 1992 Find All Groups of Farmland

### Attempt 1: Find the bottom-right corners of the farmland
```java
class Solution {

    private int m;
    private int n;
    private int[][] land;

    public int[][] findFarmland(int[][] land) {
        this.m = land.length;
        this.n = land[0].length;
        this.land = land;
        List<int[]> list = new ArrayList<>();

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (land[i][j] != 0) {
                    int[] end = getEndPoint(i, j);
                    list.add(new int[]{ i, j, end[0], end[1] });
                }
            }
        }

        return list.toArray(int[][]::new);
    }

    private int[] getEndPoint(int startI, int startJ) {
        int currI = startI;
        int currJ = startJ;
        while (currJ + 1 < n && isFarmLand(currI, currJ + 1)) {
            currJ++;
        }
        while (currI + 1 < m && isFarmLand(currI + 1, currJ)) {
            currI++;
        }

        for (int i = startI; i <= currI; i++) {
            for (int j = startJ; j <= currJ; j++) {
                land[i][j] = 0;
            }
        }
        
        return new int[]{ currI, currJ };
    }

    private boolean isFarmLand(int startI, int startJ) {
        if (startI < 0 || startI >= m || startJ < 0 || startJ >= n || land[startI][startJ] == 0) {
            return false;
        }

        return true;
    }
}
```
- Runtime: 4 ms (Beats: 90.30%)
- Memory: 60.68 MB (Beats: 64.93%)

<br>
