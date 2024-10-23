# [LeetCode Records](../../README.md) - Question 223 Rectangle Area

### Attempt 1: Calculate the intersected area
```java
class Solution {
    public int computeArea(int ax1, int ay1, int ax2, int ay2, int bx1, int by1, int bx2, int by2) {
        int area1 = (ax2 - ax1) * (ay2 - ay1);
        int area2 = (bx2 - bx1) * (by2 - by1);

        int xStart = Math.max(ax1, bx1);
        int xEnd = Math.min(ax2, bx2);
        int yStart = Math.max(ay1, by1);
        int yEnd = Math.min(ay2, by2);
        int width = xEnd - xStart;
        int heigth = yEnd - yStart;
        int intersectedArea = width <= 0 || heigth <= 0 ? 0 : width * heigth;

        return area1 + area2 - intersectedArea;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.15 MB (Beats: 92.98%)

<br>
