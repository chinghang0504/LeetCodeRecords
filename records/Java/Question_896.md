# [LeetCode Records](../../README.md) - Question 896 Monotonic Array

### Attempt 1: 
```java
class Solution {
    public boolean isMonotonic(int[] nums) {
        if (nums.length == 1) {
            return true;
        }

        int i = 1;
        while (i < nums.length && nums[0] == nums[i]) {
            i++;
        }

        if (i >= nums.length) {
            return true;
        }

        boolean isIncreasing = nums[i] > nums[i - 1];
        if (isIncreasing) {
            for (; i < nums.length - 1; i++) {
                if (nums[i] > nums[i + 1]) {
                    return false;
                }
            }
        } else {
            for (; i < nums.length - 1; i++) {
                if (nums[i] < nums[i + 1]) {
                    return false;
                }
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 99.71%)
- Memory: 59.46 MB (Beats: 20.73%)

<br>
