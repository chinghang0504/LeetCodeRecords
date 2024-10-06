# [LeetCode Records](../../README.md) - Question 1861 Rotating the Box

### Attempt 1: Use a while loop to find the next empty space for each stone
```java
class Solution {
    public char[][] rotateTheBox(char[][] box) {
        int m = box.length;
        int n = box[0].length;

        for (int i = 0; i < m; i++) {
            for (int j = n - 2; j >= 0; j--) {
                if (box[i][j] == '#') {
                    int nextJ = j;
                    while (nextJ + 1 < n && box[i][nextJ + 1] == '.') {
                        nextJ++;
                    }
                    if (j != nextJ) {
                        box[i][j] = '.';
                        box[i][nextJ] = '#';
                    }
                }
            }
        }

        char[][] ans = new char[n][m];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                ans[i][j] = box[m - j - 1][i];
            }
        }

        return ans;
    }
}
```
- Runtime: 14 ms (Beats: 28.17%)
- Memory: 80.08 MB (Beats: 7.43%)

<br>
