# [LeetCode Records](../../README.md) - Question 1037 Valid Boomerang

### Attempt 1: Change the slope formula
```java
class Solution {
    public boolean isBoomerang(int[][] points) {
        int x1 = points[0][0];
        int y1 = points[0][1];
        int x2 = points[1][0];
        int y2 = points[1][1];
        int x3 = points[2][0];
        int y3 = points[2][1];

        int xDiff1 = x1 - x2;
        int xDiff2 = x3 - x2;
        
        return (y1 - y2) * xDiff2 != (y3 - y2) * xDiff1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.34 MB (Beats: 19.42%)

<br>
