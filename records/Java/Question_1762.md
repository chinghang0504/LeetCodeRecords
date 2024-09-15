# [LeetCode Records](../../README.md) - Question 1762 Buildings With an Ocean View

### Attempt 1: Use an int[] to save the indices
```java
class Solution {
    public int[] findBuildings(int[] heights) {
        int currMax = heights[heights.length - 1];
        int[] saved = new int[heights.length];
        saved[0] = heights.length - 1;
        int savedCount = 1;

        for (int i = heights.length - 2; i >= 0; i--) {
            if (heights[i] > currMax) {
                saved[savedCount] = i;
                savedCount++;
                currMax = heights[i];
            }
        }

        int[] ans = new int[savedCount];
        for (int i = savedCount - 1, j = 0; i >= 0; i--, j++) {
            ans[j] = saved[i];
        }

        return ans;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 67.36 MB (Beats: 5.30%)

<br>
