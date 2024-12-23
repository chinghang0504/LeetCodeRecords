# [LeetCode Records](../../README.md) - Question 3394 Check if Grid can be Cut into Sections

### Attempt 1: Use Arrays.sort() to store the x-points and y-points
```java
class Solution {
    public boolean checkValidCuts(int n, int[][] rectangles) {
        int[][] yPoints = new int[rectangles.length][2];
        int[][] xPoints = new int[rectangles.length][2];

        for (int i = 0; i < rectangles.length; i++) {
            yPoints[i][0] = rectangles[i][1];
            yPoints[i][1] = rectangles[i][3];

            xPoints[i][0] = rectangles[i][0];
            xPoints[i][1] = rectangles[i][2];
        }

        Arrays.sort(yPoints, (point1, point2) -> {
            return point1[0] != point2[0] ? point1[0] - point2[0] : point1[1] - point2[1];
        });
        Arrays.sort(xPoints, (point1, point2) -> {
            return point1[0] != point2[0] ? point1[0] - point2[0] : point1[1] - point2[1];
        });

        int cutCount = 0;
        int currMax = yPoints[0][1];
        for (int i = 1; i < rectangles.length; i++) {
            currMax = Math.max(currMax, yPoints[i - 1][1]);
            if (currMax <= yPoints[i][0]) {
                cutCount++;
                if (cutCount == 2) {
                    return true;
                }
            }
        }

        cutCount = 0;
        currMax = xPoints[0][1];
        for (int i = 1; i < rectangles.length; i++) {
            currMax = Math.max(currMax, xPoints[i - 1][1]);
            if (currMax <= xPoints[i][0]) {
                cutCount++;
                if (cutCount == 2) {
                    return true;
                }
            }
        }
        
        return false;
    }
}
```
- Runtime: 131 ms (Beats: 100.00%)
- Memory: 122.24 MB (Beats: 100.00%)

<br>
