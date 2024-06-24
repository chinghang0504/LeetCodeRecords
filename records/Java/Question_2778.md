# [LeetCode Records](../../README.md) - Question 2778 Sum of Squares of Special Elements

### Attempt 1: Use a loop
```java
class Solution {
    public int sumOfSquares(int[] nums) {
        int n = nums.length;
        int sum = 0;

        for (int i = 0; i < n; i++) {
            if (n % (i + 1) == 0) {
                sum += nums[i] * nums[i];
            }
        }

        return sum;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.27 MB (Beats: 37.87%)

<br>
