# [LeetCode Records](../../README.md) - Question 1725 Number Of Rectangles That Can Form The Largest Square

### Attempt 1: Record the max length and count
```java
class Solution {
    public int countGoodRectangles(int[][] rectangles) {
        int maxLen = Math.min(rectangles[0][0], rectangles[0][1]);
        int count = 1;

        for (int i = 1; i < rectangles.length; i++) {
            int len = Math.min(rectangles[i][0], rectangles[i][1]);
            if (len > maxLen) {
                maxLen = len;
                count = 1;
            } else if (len == maxLen) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 2 ms (Beats: 99.38%)
- Memory: 44.72 MB (Beats: 57.00%)

<br>
