# [LeetCode Records](../../README.md) - Question 1829 Maximum XOR for Each Query

### Attempt 1: Use ~ operator to get the reversed bits
```java
class Solution {
    public int[] getMaximumXor(int[] nums, int maximumBit) {
        int[] ans = new int[nums.length];

        int totalXor = 0;
        for (int i = 0; i < nums.length; i++) {
            totalXor ^= nums[i];
        }

        for (int i = 0; i < nums.length; i++) {
            int val = ~totalXor;
            int step = 32 - maximumBit;
            val <<= step;
            val >>>= step;
            ans[i] = val;

            totalXor ^= nums[nums.length - i - 1];
        }
        
        return ans;
    }
}
```
- Runtime: 3 ms (Beats: 52.61%)
- Memory: 58.49 MB (Beats: 89.16%)

<br>
