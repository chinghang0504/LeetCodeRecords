# [LeetCode Records](../../README.md) - Question 79 Word Search

### Attempt 1: Use a boolean[][] to record the checked entries
```java
class Solution {

    private int m;
    private int n;
    private char[][] board;
    private boolean[][] checked;
    private char[] arr;
    
    public boolean exist(char[][] board, String word) {
        this.m = board.length;
        this.n = board[0].length;
        this.board = board;
        this.checked = new boolean[m][n];
        this.arr = word.toCharArray();
        
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (existRecursion(i, j, 0)) {
                    return true;
                }
            }
        }

        return false;
    }

    private boolean existRecursion(int startI, int stratJ, int currIndex) {
        if (currIndex >= arr.length) {
            return true;
        } else if (startI < 0 || startI >= m || stratJ < 0 || stratJ >= n || checked[startI][stratJ]) {
            return false;
        } else if (board[startI][stratJ] != arr[currIndex]) {
            return false;
        }

        checked[startI][stratJ] = true;

        if (existRecursion(startI - 1, stratJ, currIndex + 1)) {
            return true;
        } else if (existRecursion(startI + 1, stratJ, currIndex + 1)) {
            return true;
        } else if (existRecursion(startI, stratJ - 1, currIndex + 1)) {
            return true;
        } else if (existRecursion(startI, stratJ + 1, currIndex + 1)) {
            return true;
        }

        checked[startI][stratJ] = false;

        return false;
    }
}
```
- Runtime: 121 ms (Beats: 92.39%)
- Memory: 41.78 MB (Beats: 32.35%)

<br>
