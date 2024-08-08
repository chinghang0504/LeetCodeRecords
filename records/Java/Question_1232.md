# [LeetCode Records](../../README.md) - Question 1232 Check If It Is a Straight Line

### Attempt 1: Use the slope formula
```java
class Solution {
    public boolean checkStraightLine(int[][] coordinates) {
        int x1 = coordinates[0][0], y1 = coordinates[0][1];
        int x2 = coordinates[1][0], y2 = coordinates[1][1];
        int yDiff1 = y2 - y1;
        int xDiff1 = x2 - x1;

        for (int i = 2; i < coordinates.length; i++) {
            int yDiff2 = y2 - coordinates[i][1];
            int xDiff2 = x2 - coordinates[i][0];

            if (yDiff1 * xDiff2 != xDiff1 * yDiff2) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.04 MB (Beats: 68.10%)

<br>
