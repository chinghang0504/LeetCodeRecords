# [LeetCode Records](../../README.md) - Question 531 Lonely Pixel I

### Attempt 1: Use int[] to store the number of 'B' in that row and int that column
```java
class Solution {
    public int findLonelyPixel(char[][] picture) {
        int m = picture.length;
        int n = picture[0].length;

        int[] rowCounts = new int[m];
        int[] colCounts = new int[n];
        List<int[]> list = new ArrayList<>();
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (picture[i][j] == 'B') {
                    rowCounts[i]++;
                    colCounts[j]++;
                    list.add(new int[]{ i, j });
                }
            }
        }

        int count = 0;
        for (int[] item : list) {
            if (rowCounts[item[0]] == 1 && colCounts[item[1]] == 1) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 2 ms (Beats: 98.20%)
- Memory: 46.24 MB (Beats: 92.79%)

<br>
