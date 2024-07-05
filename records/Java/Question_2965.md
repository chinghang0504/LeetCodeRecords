# [LeetCode Records](../../README.md) - Question 2965 Find Missing and Repeated Values

### Attempt 1: Use an int[] to count the numbers
```java
class Solution {
    public int[] findMissingAndRepeatedValues(int[][] grid) {
        int n = grid.length;
        int[] counts = new int[n * n + 1];

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                counts[grid[i][j]]++;
            }
        }

        int a = -1;
        int b = -1;
        for (int i = 1; i < counts.length; i++) {
            if (counts[i] == 2) {
                a = i;

                if (a != -1 && b != -1) {
                    break;
                }
            } else if (counts[i] == 0) {
                b = i;

                if (a != -1 && b != -1) {
                    break;
                }
            }
        }

        return new int[]{a, b};
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.81 MB (Beats: 98.48%)

<br>
