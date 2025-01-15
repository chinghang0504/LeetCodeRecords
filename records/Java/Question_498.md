# [LeetCode Records](../../README.md) - Question 498 Diagonal Traverse

### Attempt 1: Simulate the process
```java
class Solution {
    public int[] findDiagonalOrder(int[][] mat) {
        int m = mat.length;
        int n = mat[0].length;
        int size = m * n;
        int[] ans = new int[size];

        int ansIndex = 0;
        int currI = 0;
        int currJ = 0;
        boolean isUp = true;
        while (ansIndex < size) {
            ans[ansIndex] = mat[currI][currJ];
            ansIndex++;

            if (isUp) {
                int nextI = currI - 1;
                int nextJ = currJ + 1;
                if (nextI < 0 || nextJ >= n) {
                    if (nextJ < n) {
                        currJ = nextJ;
                    } else {
                        currI++;
                    }
                    isUp = false;
                } else {
                    currI = nextI;
                    currJ = nextJ;
                }
            } else {
                int nextI = currI + 1;
                int nextJ = currJ - 1;
                if (nextI >= m || nextJ < 0) {
                    if (nextI < m) {
                        currI = nextI;
                    } else {
                        currJ++;
                    }
                    isUp = true;
                } else {
                    currI = nextI;
                    currJ = nextJ;
                }
            }
        }

        return ans;
    }
}
```
- Runtime: 3 ms (Beats: 68.94%)
- Memory: 45.52 MB (Beats: 98.74%)

<br>
