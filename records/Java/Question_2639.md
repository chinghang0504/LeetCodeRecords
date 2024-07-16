# [LeetCode Records](../../README.md) - Question 2639 Find the Width of Columns of a Grid

### Attempt 1: Use String.valueOf() and length()
```java
class Solution {
    public int[] findColumnWidth(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int[] answer = new int[n];

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                answer[j] = Math.max(answer[j], String.valueOf(grid[i][j]).length());
            }
        }

        return answer;
    }
}
```
- Runtime: 6 ms (Beats: 43.16%)
- Memory: 45.92 MB (Beats: 38.95%)

<br>

### Attempt 2: Use custom get size function
```java
class Solution {
    public int[] findColumnWidth(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int[] answer = new int[n];

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                answer[j] = Math.max(answer[j], getSize(grid[i][j]));
            }
        }

        return answer;
    }

    private int getSize(int num) {
        if (num >= 0) {
            if (num < 10) {
                return 1;
            } else if (num < 100) {
                return 2;
            } else if (num < 1000) {
                return 3;
            } else if (num < 10000) {
                return 4;
            } else if (num < 100000) {
                return 5;
            } else if (num < 1000000) {
                return 6;
            } else if (num < 10000000) {
                return 7;
            } else if (num < 100000000) {
                return 8;
            } else if (num < 1000000000) {
                return 9;
            } else {
                return 10;
            }
        } else {
            if (num > -10) {
                return 2;
            } else if (num > -100) {
                return 3;
            } else if (num > -1000) {
                return 4;
            } else if (num > -10000) {
                return 5;
            } else if (num > -100000) {
                return 6;
            } else if (num > -1000000) {
                return 7;
            } else if (num > -10000000) {
                return 8;
            } else if (num > -100000000) {
                return 9;
            } else if (num > -1000000000) {
                return 10;
            } else {
                return 11;
            }
        }
    }
}
```
- Runtime: 4 ms (Beats: 75.09%)
- Memory: 45.82 MB (Beats: 56.49%)

<br>
