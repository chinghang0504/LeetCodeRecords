# [LeetCode Records](../../README.md) - Question 1752 Check if Array Is Sorted and Rotated

### Attempt 1: Find the minimum value from the right to left
```java
class Solution {
    public boolean check(int[] nums) {
        int min = nums[0];
        int minIndex = 0;
        for (int i = nums.length - 1; i >= 0; i--) {
            if (nums[i] <= min) {
                min = nums[i];
                minIndex = i;
            } else {
                break;
            }
        }

        return isSorted(nums, 0, minIndex) && isSorted(nums, minIndex, nums.length);
    }

    private boolean isSorted(int[] nums, int start, int end) {
        for (int i = start + 1; i < end; i++) {
            if (nums[i - 1] > nums[i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.82 MB (Beats: 5.19%)

<br>
