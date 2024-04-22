# [LeetCode Records](../README.md) - Question 59 Spiral Matrix II

### Attempt 1: Record the current direction
```java
class Solution {
    public int[][] generateMatrix(int n) {
        int[][] board = new int[n][n];
        int curr = 1;
        int nSquare = n * n;
        int turn = 0;               // 0: right, 1: down, 2: left, 3: up
        int row = 0, col = 0;

        while (curr <= nSquare) {
            board[row][col] = curr++;

            if (turn == 0) {
                col++;
            } else if (turn == 1) {
                row++;
            } else if (turn == 2) {
                col--;
            } else if (turn == 3) {
                row--;
            }

            if (row < 0 || row >= n || col < 0 || col >= n || board[row][col] != 0) {
                if (turn == 0) {
                    turn = 1;
                    col--;
                    row++;
                } else if (turn == 1) {
                    turn = 2;
                    row--;
                    col--;
                } else if (turn == 2) {
                    turn = 3;
                    col++;
                    row--;
                } else if (turn == 3) {
                    turn = 0;
                    row++;
                    col++;
                }
            }
        }

        return board;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.51 MB (Beats: 14.53%)

<br>
