# [LeetCode Records](../../README.md) - Question 3364 Minimum Positive Sum Subarray

### Attempt 1: Test every case
```java
class Solution {
    public int minimumSumSubarray(List<Integer> nums, int l, int r) {
        int size = nums.size();
        boolean hasMinimum = false;
        int min = Integer.MAX_VALUE;

        for (int i = l; i <= r; i++) {
            int sum = 0;
            for (int j = 0; j < i; j++) {
                sum += nums.get(j);
            }
            if (sum > 0) {
                hasMinimum = true;
                min = Math.min(min, sum);
            }

            for (int j = 0; j < size - i; j++) {
                sum = sum - nums.get(j) + nums.get(j + i);
                if (sum > 0) {
                    hasMinimum = true;
                    min = Math.min(min, sum);
                }
            }
        }

        return hasMinimum ? min : -1;
    }
}
```
- Runtime: 3 ms (Beats: 100.00%)
- Memory: 44.15 MB (Beats: 100.00%)

<br>
