# [LeetCode Records](../../README.md) - Question 2016 Maximum Difference Between Increasing Elements

### Attempt 1: Use two loops
```java
class Solution {
    public int maximumDifference(int[] nums) {
        int maxDiff = -1;

        for (int i = 0; i < nums.length - 1; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                int diff = nums[j] - nums[i];
                if (diff != 0 && diff > maxDiff) {
                    maxDiff = diff;
                }
            }
        }

        return maxDiff;
    }
}
```
- Runtime: 4 ms (Beats: 35.93%)
- Memory: 41.36 MB (Beats: 97.41%)

<br>
