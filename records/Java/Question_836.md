# [LeetCode Records](../../README.md) - Question 836 Rectangle Overlap

### Attempt 1: Use Math.max() and Math.min()
```java
class Solution {
    public boolean isRectangleOverlap(int[] rec1, int[] rec2) {
        int a_x1 = rec1[0], a_x2 = rec1[2], a_y1 = rec1[1], a_y2 = rec1[3];
        int b_x1 = rec2[0], b_x2 = rec2[2], b_y1 = rec2[1], b_y2 = rec2[3];

        int x1 = Math.max(a_x1, b_x1);
        int x2 = Math.min(a_x2, b_x2);
        int y1 = Math.max(a_y1, b_y1);
        int y2 = Math.min(a_y2, b_y2);

        return x2 > x1 && y2 > y1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.60 MB (Beats: 66.52%)

<br>
