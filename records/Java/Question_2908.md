# [LeetCode Records](../../README.md) - Question 2908 Minimum Sum of Mountain Triplets I

### Attempt 1: Use a nested loop to test each case
```java
class Solution {
    public int minimumSum(int[] nums) {
        int minSum = Integer.MAX_VALUE;
        boolean isFound = false;

        for (int i = 0; i < nums.length - 2; i++) {
            for (int j = i + 1; j < nums.length - 1; j++) {
                if (nums[i] >= nums[j]) {
                    continue;
                }
                for (int k = j + 1; k < nums.length; k++) {
                    if (nums[k] < nums[j]) {
                        minSum = Math.min(minSum, nums[i] + nums[j] + nums[k]);
                        isFound = true;
                    }
                }
            }
        }

        return isFound ? minSum : -1;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 41.78 MB (Beats: 72.47%)

<br>
