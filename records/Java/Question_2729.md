# [LeetCode Records](../../README.md) - Question 2729 Check if The Number is Fascinating

### Attempt 1: Use a boolean[] to check if the digit already exists
```java
class Solution {
    public boolean isFascinating(int n) {
        int[] nums = { n, 2 * n, 3 * n };
        boolean[] digits = new boolean[10];

        for (int num : nums) {
            while (num > 0) {
                int digit = num % 10;
                if (digit == 0 || digits[digit]) {
                    return false;
                } else {
                    digits[digit] = true;
                }

                num /= 10;
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 93.00%)
- Memory: 41.04 MB (Beats: 62.12%)

<br>
