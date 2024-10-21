# [LeetCode Records](../../README.md) - Question 81 Search in Rotated Sorted Array II

### Attempt 1: Search from left or right
```java
class Solution {
    public boolean search(int[] nums, int target) {
        int start = nums[0];

        if (target == start) {
            return true;
        } else if (target > start) {
            for (int i = 1; i < nums.length; i++) {
                if (nums[i] == target) {
                    return true;
                } else if (nums[i - 1] > nums[i]) {
                    return false;
                }
            }
        } else {
            for (int i = nums.length - 1; i >= 1; i--) {
                if (nums[i] == target) {
                    return true;
                } else if (nums[i - 1] > nums[i]) {
                    return false;
                }
            }
        }

        return false;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.18 MB (Beats: 54.38%)

<br>
