# [LeetCode Records](../../README.md) - Question 1909 Remove One Element to Make the Array Strictly Increasing

### Attempt 1: Use two while loops to traverse the array
```java
class Solution {
    public boolean canBeIncreasing(int[] nums) {
        int i = 0;

        // First while loop
        while (i < nums.length - 1 && nums[i] < nums[i + 1]) {
            i++;
        }
        // Remove any number
        if (i == nums.length - 1) {
            return true;
        }

        // Record the breakpoint
        int middle = i;

        // Second while loop
        i++;
        while (i < nums.length - 1 && nums[i] < nums[i + 1]) {
            i++;
        }

        // Unable to reach the last index
        if (i != nums.length - 1) {
            return false;
        }
        // The breakpoint is at the head
        else if (middle == 0) {
            return true;
        }
        // Check before and after the breakpoint
        else if (nums[middle - 1] < nums[middle + 1]) {
            return true;
        }
        // The breakpoint is at the last second tail
        else if (middle + 2 == nums.length) {
            return true;
        }
        
        // Check the breakpoint and after the breakpoint
        return nums[middle] < nums[middle + 2];
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.51 MB (Beats: 49.82%)

<br>
