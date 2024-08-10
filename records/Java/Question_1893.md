# [LeetCode Records](../../README.md) - Question 1893 Check if All the Integers in a Range Are Covered

### Attempt 1: Use a boolean[] to record the numbers
```java
class Solution {
    public boolean isCovered(int[][] ranges, int left, int right) {
        boolean[] colored = new boolean[51];

        for (int[] range : ranges) {
            int start = Math.max(range[0], left);
            int end = Math.min(range[1], right);

            for (int i = start; i <= end; i++) {
                colored[i] = true;
            }
        }

        for (int i = left; i <= right; i++) {
            if (!colored[i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.39 MB (Beats: 88.62%)

<br>
