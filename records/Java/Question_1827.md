# [LeetCode Records](../../README.md) - Question 1827 Minimum Operations to Make the Array Increasing

### Attempt 1: The next value should be previous value + 1
```java
class Solution {
    public int minOperations(int[] nums) {
        int count = 0;
        int prevVal = nums[0];

        for (int i = 1; i < nums.length; i++) {
            if (nums[i] > prevVal) {
                prevVal = nums[i];
            } else {
                prevVal++;
                count += prevVal - nums[i];
            }
        }

        return count;
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 44.63 MB (Beats: 85.61%)

<br>
