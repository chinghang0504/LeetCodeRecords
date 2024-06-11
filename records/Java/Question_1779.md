# [LeetCode Records](../../README.md) - Question 1779 Find Nearest Point That Has the Same X or Y Coordinate

### Attempt 1: Use a loop
```java
class Solution {
    public int nearestValidPoint(int x, int y, int[][] points) {
        int minPointIndex = -1;
        int minDistance = Integer.MAX_VALUE;

        for (int i = 0; i < points.length; i++) {
            if (points[i][0] == x || points[i][1] == y) {
                int distance = Math.abs(x - points[i][0]) + Math.abs(y - points[i][1]);
                if (distance < minDistance) {
                    minDistance = distance;
                    minPointIndex = i;
                }
            }
        }

        return minPointIndex;
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 48.99 MB (Beats: 91.95%)

<br>
