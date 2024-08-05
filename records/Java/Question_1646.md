# [LeetCode Records](../../README.md) - Question 1646 Get Maximum in Generated Array

### Attempt 1: Generate the array and find the maximum value
```java
class Solution {
    public int getMaximumGenerated(int n) {
        if (n == 0) {
            return 0;
        } else if (n == 1) {
            return 1;
        }

        int[] nums = new int[n + 1];

        nums[0] = 0;
        nums[1] = 1;

        for (int i = 1; 2 * i + 1 <= n; i++) {
            nums[2 * i] = nums[i];
            nums[2 * i + 1] = nums[i] + nums[i + 1];
        }

        if (n % 2 == 0) {
            nums[n] = nums[n / 2];
        }

        int max = nums[0];
        for (int i = 1; i < nums.length; i++) {
            max = Math.max(max, nums[i]);
        }

        return max;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.18 MB (Beats: 68.53%)

<br>
