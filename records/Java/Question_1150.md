# [LeetCode Records](../../README.md) - Question 1150 Check If a Number Is Majority Element in a Sorted Array

### Attempt 1: Use a loop
```java
class Solution {
    public boolean isMajorityElement(int[] nums, int target) {
        int count = 0;

        for (int num : nums) {
            if (num == target) {
                count++;
            }
        }

        return count > nums.length / 2;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.86 MB (Beats: 28.51%)

<br>
