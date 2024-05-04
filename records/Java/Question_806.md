# [LeetCode Records](../../README.md) - Question 806 Number of Lines To Write String

### Attempt 1: 
```java
class Solution {
    public int[] numberOfLines(int[] widths, String s) {
        int lineNum = 1;
        int currPixels = 0;
        for (char ch : s.toCharArray()) {
            int pixels = widths[ch - 'a'];
            if (currPixels + pixels <= 100) {
                currPixels += pixels;
            } else {
                lineNum++;
                currPixels = pixels;
            }
        }

        return new int[]{lineNum, currPixels};
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.49 MB (Beats: 49.47%)

<br>
