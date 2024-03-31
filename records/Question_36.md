# [LeetCode Records](../README.md) - Question 

### Attempt 1: Use a HashSet in each checking function
```java
class Solution {
    public boolean isValidSudoku(char[][] board) {
        for (int i = 0; i < 9; i++) {
            if (!checkRow(board, i)) {
                return false;
            }
        }
        for (int j = 0; j < 9; j++) {
            if (!checkColumn(board, j)) {
                return false;
            }
        }
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                if (!checkSubBox(board, i * 3, j * 3)) {
                    return false;
                }
            }
        }

        return true;
    }

    boolean checkRow(char[][] board, int i) {
        HashSet<Character> hashSet = new HashSet<>();

        for (int j = 0; j < 9; j++) {
            if (board[i][j] != '.') {
                if (!hashSet.add(board[i][j])) {
                    return false;
                }
            }
        }

        return true;
    }

    boolean checkColumn(char[][] board, int j) {
        HashSet<Character> hashSet = new HashSet<>();

        for (int i = 0; i < 9; i++) {
            if (board[i][j] != '.') {
                if (!hashSet.add(board[i][j])) {
                    return false;
                }
            }
        }

        return true;
    }

    boolean checkSubBox(char[][] board, int rowIndex, int rowColumn) {
        HashSet<Character> hashSet = new HashSet<>();

        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                if (board[rowIndex + i][rowColumn + j] != '.') {
                    if (!hashSet.add(board[rowIndex + i][rowColumn + j])) {
                        return false;
                    }
                }
            }
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 79.01%)
- Memory: 44.16 MB (Beats: 79.07%)

<br>

### Attempt 2: Use three 9x9 arrays
```java
class Solution {
    public boolean isValidSudoku(char[][] board) {
        int[][] rowCheck = new int[9][9];
        int[][] colCheck = new int[9][9];
        int[][] subBoxCheck = new int[9][9];

        for (int i = 0; i < 9; i++) {
            for (int j = 0; j < 9; j++) {
                // No digit
                char ch = board[i][j];
                if (ch == '.') {
                    continue;
                }

                // Check row
                int val = ch - 49;
                if (rowCheck[i][val] == 1) {
                    return false;
                } else {
                    rowCheck[i][val] = 1;
                }

                // Check column
                if (colCheck[val][j] == 1) {
                    return false;
                } else {
                    colCheck[val][j] = 1;
                }

                // Check subbox
                int subboxIndex = i / 3 * 3 + j / 3;
                if (subBoxCheck[subboxIndex][val] == 1) {
                    return false;
                } else {
                    subBoxCheck[subboxIndex][val] = 1;
                }
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.55 MB (Beats: 44.62%)

<br>
