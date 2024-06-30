# [LeetCode Records](../../README.md) - Question 1266 Minimum Time Visiting All Points

### Attempt 1: Find the horizontal and vertical differences
```java
class Solution {
    public int minTimeToVisitAllPoints(int[][] points) {
        int sum = 0;

        for (int i = 1; i < points.length; i++) {
            int xDiff = Math.abs(points[i - 1][0] - points[i][0]);
            int yDiff = Math.abs(points[i - 1][1] - points[i][1]);

            if (xDiff == yDiff) {
                sum += xDiff;
            } else if (xDiff < yDiff) {
                sum += yDiff;
            } else {
                sum += xDiff;
            }
        }

        return sum;
    }
}
```
- Runtime: 1 ms (Beats: 91.68%)
- Memory: 42.86 MB (Beats: 53.25%)

<br>
