# [LeetCode Records](../../README.md) - Question 3392 Count Subarrays of Length Three With a Condition

### Attempt 1: Multiply the sum by 2
```java
class Solution {
    public int countSubarrays(int[] nums) {
        int count = 0;

        for (int i = 0; i < nums.length - 2; i++) {
            int sum = nums[i] + nums[i + 2];
            if (sum * 2 == nums[i + 1]) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.99 MB (Beats: 100.00%)

<br>
