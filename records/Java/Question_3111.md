# [LeetCode Records](../../README.md) - Question 3111 Minimum Rectangles to Cover Points

### Attempt 1: Use Arrays.sort() to sort the array
```java
class Solution {
    public int minRectanglesToCoverPoints(int[][] points, int w) {
        Arrays.sort(points, (p1, p2) -> p1[0] - p2[0]);

        int minX = points[0][0];
        int maxX = minX + w;
        int count = 1;
        for (int i = 1; i < points.length; i++) {
            if (points[i][0] > maxX) {
                minX = points[i][0];
                maxX = minX + w;
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 4 ms (Beats: 98.82%)
- Memory: 96.94 MB (Beats: 81.18%)

<br>
