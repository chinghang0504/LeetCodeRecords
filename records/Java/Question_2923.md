# [LeetCode Records](../../README.md) - Question 2923 Find Champion I

### Attempt 1: Use a nested loop to find the champion
```java
class Solution {
    public int findChampion(int[][] grid) {
        int n = grid.length;

        for (int i = 0; i < n; i++) {
            boolean isChampion = true;
            
            for (int j = 0; j < n; j++) {
                if (i == j) {
                    continue;
                }

                if (grid[i][j] != 1) {
                    isChampion = false;
                    break;
                }
            }

            if (isChampion) {
                return i;
            }
        }

        return -1;
    }
}
```
- Runtime: 1 ms (Beats: 77.56%)
- Memory: 44.83 MB (Beats: 97.35%)

<br>
