# [LeetCode Records](../../README.md) - Question 2760 Longest Even Odd Subarray With Threshold

### Attempt 1: Use a helper function to test every case
```java
class Solution {
    public int longestAlternatingSubarray(int[] nums, int threshold) {
        for (int i = nums.length; i >= 1; i--) {
            for (int j = 0; j < nums.length - i + 1; j++) {
                if (isEvenOddSubarray(nums, threshold, j, j + i)) {
                    return i;
                }
            }
        }

        return 0;
    }

    private boolean isEvenOddSubarray(int[] nums, int threshold, int start, int end) {
        if (nums[start] % 2 != 0) {
            return false;
        }

        boolean prevIsEven = false;
        for (int i = start; i < end; i++) {
            if (nums[i] > threshold) {
                return false;
            }

            boolean isEven = nums[i] % 2 == 0;
            if (prevIsEven == isEven) {
                return false;
            }
            prevIsEven = isEven;
        }

        return true;
    }
}
```
- Runtime: 13 ms (Beats: 5.38%)
- Memory: 44.48 MB (Beats: 96.77%)

<br>
