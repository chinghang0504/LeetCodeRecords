# [LeetCode Records](../README.md) - Question 598 Range Addition II

### Attempt 1: 
```java
class Solution {
    public int maxCount(int m, int n, int[][] ops) {
        int minRow = m;
        int minCol = n;

        for (int i = 0; i < ops.length; i++) {
            minRow = Math.min(minRow, ops[i][0]);
            minCol = Math.min(minCol, ops[i][1]);
        }

        return minRow * minCol;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 45.70 MB (Beats: 88.80%)

<br>
