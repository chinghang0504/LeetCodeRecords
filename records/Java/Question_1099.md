# [LeetCode Records](../../README.md) - Question 1099 Two Sum Less Than K

### Attempt 1: Use two loops
```java
class Solution {
    public int twoSumLessThanK(int[] nums, int k) {
        int max = Integer.MIN_VALUE;

        for (int i = 0; i < nums.length - 1; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                int sum = nums[i] + nums[j];
                if (sum < k) {
                    max = Math.max(max, sum);
                }
            }
        }

        return max == Integer.MIN_VALUE ? -1 : max;
    }
}
```
- Runtime: 3 ms (Beats: 37.62%)
- Memory: 41.64 MB (Beats: 69.79%)

<br>
