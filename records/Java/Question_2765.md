# [LeetCode Records](../../README.md) - Question 2765 Longest Alternating Subarray

### Attempt 1: Use a nested loop that tests every case
```java
class Solution {
    public int alternatingSubarray(int[] nums) {
        for (int i = nums.length; i >= 2; i--) {
            for (int j = 0; j < nums.length - i + 1; j++) {
                if (isAlternatingSubarray(nums, j, j + i)) {
                    return i;
                }
            }
        }

        return -1;
    }

    private boolean isAlternatingSubarray(int[] nums, int start, int end) {
        int first = nums[start];
        int second = nums[start + 1];

        if (second - first != 1) {
            return false;
        }

        boolean isFirst = true;
        for (int i = start + 2; i < end; i++) {
            if (isFirst) {
                if (nums[i] != first) {
                    return false;
                }
            } else {
                if (nums[i] != second) {
                    return false;
                }
            }

            isFirst = !isFirst;
        }

        return true;
    }
}
```
- Runtime: 4 ms (Beats: 13.08%)
- Memory: 44.34 MB (Beats: 36.92%)

<br>
