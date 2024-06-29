# [LeetCode Records](../../README.md) - Question 3065 Minimum Operations to Exceed Threshold Value I

### Attempt 1: Use a loop
```java
class Solution {
    public int minOperations(int[] nums, int k) {
        int count = 0;

        for (int num : nums) {
            if (num < k) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.79 MB (Beats: 32.65%)

<br>
