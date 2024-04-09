# [LeetCode Records](../README.md) - Question 485 Max Consecutive Ones

### Attempt 1: Call the max() when num == 0
```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int max = Integer.MIN_VALUE;
        int count = 0;

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == 0) {
                max = Math.max(max, count);
                count = 0;
            } else {
                count++;
            }
        }

        return Math.max(max, count);
    }
}
```
- Runtime: 2 ms (Beats: 90.94%)
- Memory: 45.52 MB (Beats: 41.47%)

<br>
