# [LeetCode Records](../../README.md) - Question 1984 Minimum Difference Between Highest and Lowest of K Scores

### Attempt 1: Use Arrays.sort()
```java
class Solution {
    public int minimumDifference(int[] nums, int k) {
        if (k == 1) {
            return 0;
        }

        Arrays.sort(nums);

        int minDiff = Integer.MAX_VALUE;

        for (int i = 0; i < nums.length - k + 1; i++) {
            int diff = nums[i + k - 1] - nums[i];
            minDiff = Math.min(minDiff, diff);
        }

        return minDiff;
    }
}
```
- Runtime: 5 ms (Beats: 97.40%)
- Memory: 43.96 MB (Beats: 87.81%)

<br>
