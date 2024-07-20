# [LeetCode Records](../../README.md) - Question 812 Largest Triangle Area

### Attempt 1: Use a nested loop to test every case
```java
class Solution {
    public double largestTriangleArea(int[][] points) {
        double maxArea = 0.0;
        
        for (int i = 0; i < points.length - 2; i++) {
            for (int j = i + 1; j < points.length - 1; j++) {
                for (int k = j + 1; k < points.length; k++) {
                    maxArea = Math.max(maxArea, getTriangleArea(points[i], points[j], points[k]));
                }
            }
        }

        return maxArea;
    }
    private double getTriangleArea(int[] point1, int[] point2, int[] point3) {
        return 0.5 * Math.abs(point1[0] * (point2[1] - point3[1]) + point2[0] * (point3[1] - point1[1]) + point3[0] * (point1[1] - point2[1]));
    }
}
```
- Runtime: 5 ms (Beats: 87.75%)
- Memory: 41.60 MB (Beats: 19.15%)

<br>
