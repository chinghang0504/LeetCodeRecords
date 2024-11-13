# [LeetCode Records](../../README.md) - Question 1465 Maximum Area of a Piece of Cake After Horizontal and Vertical Cuts

### Attempt 1: Get the maximum horizontal and vertical differences
```java
class Solution {
    public int maxArea(int h, int w, int[] horizontalCuts, int[] verticalCuts) {
        Arrays.sort(horizontalCuts);
        Arrays.sort(verticalCuts);

        long maxHorizontalDiff = horizontalCuts[0];
        for (int i = 1; i < horizontalCuts.length; i++) {
            maxHorizontalDiff = Math.max(maxHorizontalDiff, horizontalCuts[i] - horizontalCuts[i - 1]);
        }
        maxHorizontalDiff = Math.max(maxHorizontalDiff, h - horizontalCuts[horizontalCuts.length - 1]);

        long maxVerticalDiff = verticalCuts[0];
        for (int i = 1; i < verticalCuts.length; i++) {
            maxVerticalDiff = Math.max(maxVerticalDiff, verticalCuts[i] - verticalCuts[i - 1]);
        }
        maxVerticalDiff = Math.max(maxVerticalDiff, w - verticalCuts[verticalCuts.length - 1]);

        return (int)(maxHorizontalDiff * maxVerticalDiff % 1_000_000_007L);
    }
}
```
- Runtime: 15 ms (Beats: 96.77%)
- Memory: 54.92 MB (Beats: 84.97%)

<br>
