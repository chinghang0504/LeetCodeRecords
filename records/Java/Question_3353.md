# [LeetCode Records](../../README.md) - Question 3353 Minimum Total Operations

### Attempt 1: Compare the previous numbers
```java
class Solution {
    public int minOperations(int[] nums) {
        int count = 0;

        for (int i = 0; i < nums.length - 1; i++) {
            if (nums[i] != nums[i + 1]) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 5 ms (Beats: 100.00%)
- Memory: 57.13 MB (Beats: 100.00%)

<br>
