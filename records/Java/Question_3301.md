# [LeetCode Records](../../README.md) - Question 3301 Maximize the Total Height of Unique Towers

### Attempt 1: Compare with the neighbours
```java
class Solution {
    public long maximumTotalSum(int[] maximumHeight) {
        Arrays.sort(maximumHeight);

        long totalSum = maximumHeight[maximumHeight.length - 1];
        int nextMaxHeight = maximumHeight[maximumHeight.length - 1] - 1;
        for (int i = maximumHeight.length - 2; i >= 0; i--) {
            nextMaxHeight = Math.min(nextMaxHeight, maximumHeight[i]);
            totalSum += nextMaxHeight;
            nextMaxHeight--;
        }

        return nextMaxHeight >= 0 ? totalSum : -1;
    }
}
```
- Runtime: 49 ms (Beats: 100.00%)
- Memory: 57.70 MB (Beats: 100.00%)

<br>
