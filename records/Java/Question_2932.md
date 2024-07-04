# [LeetCode Records](../../README.md) - Question 2932 Maximum Strong Pair XOR I

### Attempt 1: Use a nested loop
```java
class Solution {
    public int maximumStrongPairXor(int[] nums) {
        int max = Integer.MIN_VALUE;

        for (int i = 0; i < nums.length; i++) {
            int x = nums[i];

            for (int j = 0; j < nums.length; j++) {
                int y = nums[j];
                if (Math.abs(x - y) <= Math.min(x, y)) {
                    max = Math.max(max, x ^ y);
                }
            }
        }

        return max;
    }
}
```
- Runtime: 3 ms (Beats: 61.80%)
- Memory: 42.67 MB (Beats: 91.65%)

<br>
