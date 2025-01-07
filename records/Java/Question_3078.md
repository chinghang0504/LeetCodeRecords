# [LeetCode Records](../../README.md) - Question 3078 Match Alphanumerical Pattern in Matrix I

### Attempt 1: Use an int[] to convert a character to a digit and a boolean[] to track used digits
```java
class Solution {

    private int[][] board;
    private int pRows;
    private int pCols;
    private char[][] patternArr;

    public int[] findPattern(int[][] board, String[] pattern) {
        this.board = board;
        pRows = pattern.length;
        pCols = pattern[0].length();
        patternArr = new char[pRows][];
        for (int i = 0; i < pRows; i++) {
            patternArr[i] = pattern[i].toCharArray();
        }

        int bRows = board.length;
        int bCols = board[0].length;
        for (int i = 0; i <= bRows - pRows; i++) {
            for (int j = 0; j <= bCols - pCols; j++) {
                if (isIdentical(i, j)) {
                    return new int[]{ i, j };
                }
            }
        }

        return new int[]{ -1, -1 };
    }

    private boolean isIdentical(int startI, int startJ) {
        boolean[] usedDigits = new boolean[10];
        int[] charToDigit = new int[26];
        Arrays.fill(charToDigit, -1);

        for (int i = 0; i < pRows; i++) {
            for (int j = 0; j < pCols; j++) {
                if (patternArr[i][j] >= '0' && patternArr[i][j] <= '9') {
                    if (board[startI + i][startJ + j] != patternArr[i][j] - '0') {
                        return false;
                    }
                } else {
                    if (charToDigit[patternArr[i][j] - 'a'] == -1) {
                        if (usedDigits[board[startI + i][startJ + j]]) {
                            return false;
                        } else {
                            charToDigit[patternArr[i][j] - 'a'] = board[startI + i][startJ + j];
                            usedDigits[board[startI + i][startJ + j]] = true;
                        }
                    } else {
                        if (charToDigit[patternArr[i][j] - 'a'] != board[startI + i][startJ + j]) {
                            return false;
                        }
                    }
                }
            }
        }

        return true;
    }
}
```
- Runtime: 7 ms (Beats: 100.00%)
- Memory: 45.76 MB (Beats: 72.73%)

<br>
