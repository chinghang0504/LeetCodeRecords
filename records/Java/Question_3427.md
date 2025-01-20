# [LeetCode Records](../../README.md) - Question 3427 Sum of Variable Length Subarrays

### Attempt 1: Use an int[] to store the prefix sums
```java
class Solution {
    public int subarraySum(int[] nums) {
        int[] prefixSums = new int[nums.length + 1];
        for (int i = 0; i < nums.length; i++) {
            prefixSums[i + 1] = prefixSums[i] + nums[i];
        }

        int sum = 0;
        for (int i = 0; i < nums.length; i++) {
            sum += prefixSums[i + 1] - prefixSums[Math.max(0, i - nums[i])];
        }

        return sum;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 43.94 MB (Beats: 100.00%)

<br>
