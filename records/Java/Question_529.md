# [LeetCode Records](../../README.md) - Question 529 Minesweeper

### Attempt 1: Use recursion to search the next unrevealed empty square
```java
class Solution {
    public char[][] updateBoard(char[][] board, int[] click) {
        int m = board.length;
        int n = board[0].length;

        char ch = board[click[0]][click[1]];
        if (ch == 'M') {
            board[click[0]][click[1]] = 'X';
        } else {
            updateEmptySquare(board, m, n, click[0], click[1]);
        }

        return board;
    }

    private void updateEmptySquare(char[][] board, int m, int n, int centerI, int centerJ) {
        if (centerI < 0 || centerI >= m || centerJ < 0 || centerJ >= n || board[centerI][centerJ] != 'E') {
            return;
        }

        int sum = 0;
        sum += countMine(board, m, n, centerI - 1, centerJ - 1);
        sum += countMine(board, m, n, centerI - 1, centerJ);
        sum += countMine(board, m, n, centerI - 1, centerJ + 1);
        sum += countMine(board, m, n, centerI, centerJ - 1);
        sum += countMine(board, m, n, centerI, centerJ + 1);
        sum += countMine(board, m, n, centerI + 1, centerJ - 1);
        sum += countMine(board, m, n, centerI + 1, centerJ);
        sum += countMine(board, m, n, centerI + 1, centerJ + 1);

        if (sum == 0) {
            board[centerI][centerJ] = 'B';
            updateEmptySquare(board, m, n, centerI - 1, centerJ - 1);
            updateEmptySquare(board, m, n, centerI - 1, centerJ);
            updateEmptySquare(board, m, n, centerI - 1, centerJ + 1);
            updateEmptySquare(board, m, n, centerI, centerJ - 1);
            updateEmptySquare(board, m, n, centerI, centerJ + 1);
            updateEmptySquare(board, m, n, centerI + 1, centerJ - 1);
            updateEmptySquare(board, m, n, centerI + 1, centerJ);
            updateEmptySquare(board, m, n, centerI + 1, centerJ + 1);
        } else {
            board[centerI][centerJ] = (char)('0' + sum);
        }
    }

    private int countMine(char[][] board, int m, int n, int centerI, int centerJ) {
        if (centerI < 0 || centerI >= m || centerJ < 0 || centerJ >= n || board[centerI][centerJ] != 'M') {
            return 0;
        }

        return 1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.66 MB (Beats: 82.94%)

<br>
