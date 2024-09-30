# [LeetCode Records](../../README.md) - Question 2393 Count Strictly Increasing Subarrays

### Attempt 1: Use the formula: sum of integers
```java
class Solution {
    public long countSubarrays(int[] nums) {
        long totalCount = 0;
        
        long increasingCount = 1;
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] > nums[i - 1]) {
                increasingCount++;
            } else {
                totalCount += getSumOfSubarray(increasingCount);
                increasingCount = 1;
            }
        }
        totalCount += getSumOfSubarray(increasingCount);

        return totalCount;
    }

    private long getSumOfSubarray(long n) {
        return (1 + n) * n / 2;
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 57.08 MB (Beats: 57.14%)

<br>
