# [LeetCode Records](../../README.md) - Question 2970 Count the Number of Incremovable Subarrays I

### Attempt 1: Use a helper function to check if the array is incremovable
```java
class Solution {
    public int incremovableSubarrayCount(int[] nums) {
        int count = 0;

        for (int i = 1; i <= nums.length; i++) {
            for (int j = 0; j < nums.length - i + 1; j++) {
                if (isIncremovable(nums, j, j + i)) {
                    count++;
                }
            }
        }

        return count;
    }

    private boolean isIncremovable(int[] nums, int start, int end) {
        for (int i = 1; i < start; i++) {
            if (nums[i - 1] >= nums[i]) {
                return false;
            }
        }

        if (start - 1 >= 0 && end < nums.length && nums[start - 1] >= nums[end]) {
            return false;
        }

        for (int i = end + 1; i < nums.length; i++) {
            if (nums[i - 1] >= nums[i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 4 ms (Beats: 56.08%)
- Memory: 43.12 MB (Beats: 35.29%)

<br>
