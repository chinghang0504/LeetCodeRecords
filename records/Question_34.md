# [LeetCode Records](../README.md) - Question 34 Find First and Last Position of Element in Sorted Array

### Attempt 1: Find the target first
```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int[] result = { -1, -1 };

        // Find the target
        int start = 0;
        int end = nums.length - 1;
        int middle = 0;
        while (start <= end) {
            middle = (start + end) / 2;

            if (nums[middle] == target) {
                break;
            } else if (nums[middle] < target) {
                start = middle + 1;
            } else {
                end = middle - 1;
            }
        }

        // Unable to find the target
        if (start > end) {
            return result;
        }

        // Find the start position
        for (int i = middle; i >= 0 && nums[i] == target; i--) {
            result[0] = i;
        }

        // Find the end position
        for (int i = middle; i < nums.length && nums[i] == target; i++) {
            result[1] = i;
        }

        return result;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 45.83 MB (Beats: 46.18%)

<br>
