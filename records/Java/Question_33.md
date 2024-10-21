# [LeetCode Records](../../README.md) - Question 33 Search in Rotated Sorted Array

### Attempt 1: Use binary search
```java
class Solution {
    public int search(int[] nums, int target) {
        int low = 0;
        int high = nums.length - 1;

        while (low <= high) {
            int middle = (low + high) / 2;

            if (nums[middle] == target) {
                return middle;
            } else if (nums[low] <= nums[middle]) {
                if (nums[low] <= target && target <= nums[middle]) {
                    high = middle - 1;
                } else {
                    low = middle + 1;
                }
            } else {
                if (nums[middle] <= target && target <= nums[high]) {
                    low = middle + 1;
                } else {
                    high = middle - 1;
                }
            }
        }

        return -1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.10 MB (Beats: 41.34%)

<br>
