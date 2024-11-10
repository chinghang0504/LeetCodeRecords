# [LeetCode Records](../../README.md) - Question 3349 Adjacent Increasing Subarrays Detection I

### Attempt 1: Use a help function to check the subarray
```java
class Solution {
    public boolean hasIncreasingSubarrays(List<Integer> nums, int k) {
        int size = nums.size();
        int end = size - k - k + 1;

        for (int i = 0; i < end; i++) {
            if (isIncreasing(nums, i, k) && isIncreasing(nums, i + k, k)) {
                return true;
            }
        }

        return false;
    }

    private boolean isIncreasing(List<Integer> nums, int start, int k) {
        int prevVal = nums.get(start);

        for (int i = 1; i < k; i++) {
            int val = nums.get(start + i);
            if (prevVal >= val) {
                return false;
            }
            prevVal = val;
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.32 MB (Beats: 100.00%)

<br>
