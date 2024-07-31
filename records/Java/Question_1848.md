# [LeetCode Records](../../README.md) - Question 1848 Minimum Distance to the Target Element

### Attempt 1: Use two for loops to find the minimum distance
```java
class Solution {
    public int getMinDistance(int[] nums, int target, int start) {
        int minDistance = Integer.MAX_VALUE;

        for (int i = 0; i <= start; i++) {
            if (nums[i] == target) {
                minDistance = Math.min(minDistance, start - i);
            }
        }
        for (int i = start + 1; i < nums.length; i++) {
            if (nums[i] == target) {
                minDistance = Math.min(minDistance, i - start);
            }
        }

        return minDistance;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.18 MB (Beats: 32.80%)

<br>
