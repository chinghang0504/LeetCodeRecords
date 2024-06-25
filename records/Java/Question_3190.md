# [LeetCode Records](../../README.md) - Question 3190 Find Minimum Operations to Make All Elements Divisible by Three

### Attempt 1: Use a Math.min() to compare the remainder and 3 - remainder
```java
class Solution {
    public int minimumOperations(int[] nums) {
        int sum = 0;

        for (int num : nums) {
            int remainder = num % 3;
            sum += Math.min(remainder, 3 - remainder);
        }

        return sum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.15 MB (Beats: 15.36%)

<br>
