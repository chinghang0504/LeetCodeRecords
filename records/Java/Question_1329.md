# [LeetCode Records](../../README.md) - Question 1329 Sort the Matrix Diagonally

### Attempt 1: Use an ArrayList to store the diagonal entries
```java
class Solution {
    public int[][] diagonalSort(int[][] mat) {
        int m = mat.length;
        int n = mat[0].length;

        for (int i = m - 1; i >= 1; i--) {
            sortDiagonal(mat, m, n, i, 0);
        }
        for (int j = 0; j < n; j++) {
            sortDiagonal(mat, m, n, 0, j);
        }

        return mat;
    }

    private void sortDiagonal(int[][] mat, int m, int n, int startI, int startJ) {
        List<Integer> list = new ArrayList<>();

        int currI = startI;
        int currJ = startJ;
        while (currI < m && currJ < n) {
            list.add(mat[currI][currJ]);
            currI++;
            currJ++;
        }

        list.sort(null);

        currI = startI;
        currJ = startJ;
        for (int num : list) {
            mat[currI][currJ] = num;
            currI++;
            currJ++;
        }
    }
}
```
- Runtime: 4 ms (Beats: 87.31%)
- Memory: 44.51 MB (Beats: 88.29%)

<br>
